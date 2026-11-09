# Bài 3: Sử dụng AI an toàn khi xử lý lỗi phần mềm

## 1. Báo cáo phân tích IPO

| Thành phần | Nội dung |
|---|---|
| **Input** (Đầu vào) | Câu hỏi gửi AI: "Lỗi *Path not found* khi cài Python thì sửa thế nào?". AI trả lời bằng một lệnh gạch đầu dòng, bảo dán vào Terminal. Lệnh này có dùng `sudo` và đụng vào thư mục hệ thống nên trông rất lạ. |
| **Process** (Xử lý) | Không chạy ngay mà kiểm chứng: (1) tìm trên Stack Overflow bằng `site:stackoverflow.com python "path not found"`, xem câu trả lời có tích xanh và nhiều upvote; (2) đối chiếu với tài liệu chính thức ở python.org; (3) tra từng phần của lệnh xem nó làm gì, có xóa hoặc ghi đè file hệ thống không; (4) thử xem có nguồn nào khác dùng đúng lệnh đó không. |
| **Output** (Kết quả) | **KHÔNG an toàn.** Không tìm thấy nguồn nào xác nhận lệnh này, và nó can thiệp sâu vào hệ thống. Cách an toàn hơn là thêm Python vào biến môi trường PATH (Environment Variables) hoặc cài lại Python và tick ô *Add Python to PATH*. |

## 2. Vì sao cần kiểm chứng?

AI có thể bị **ảo giác (AI Hallucination)**: đưa ra lệnh không có thật hoặc chỉ đúng với phiên bản hệ điều hành khác. Chạy lệnh sai, nhất là có `sudo`, có thể làm hỏng máy.

## 3. Prompt "hỏi ngược lại" AI

```
Trước khi mình chạy lệnh bạn vừa đưa, hãy giải thích:
1. Từng phần của lệnh làm gì?
2. Lệnh có xóa, sửa hoặc ghi đè file hệ thống không? Có rủi ro gì?
3. Nguồn tài liệu chính thức nào xác nhận lệnh này đúng với phiên bản hệ điều hành của mình?
4. Có cách khác an toàn hơn, không cần sudo không?
Nếu bạn không chắc chắn thì hãy nói thẳng là không chắc, đừng đoán.
```

## 4. Quy định nộp bài (GitHub)

> *(Ảnh đề bị cắt ở phần này. Em xem lại đúng định dạng thầy/cô yêu cầu rồi đặt tên theo đó.)*

Gợi ý cấu trúc nếu đề không nói gì thêm:

```
IT101_Bai3/
├── README.md        (báo cáo IPO)
└── prompt_hoi_nguoc.md
```

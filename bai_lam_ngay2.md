# BÀI LÀM – ÔN TẬP NGÀY 2

- **Họ tên:** Đào Tuấn Đạt
- **Lớp:** HNKS26CNTT3
- **Link repository:** [GitHub](https://github.com/tuandatdzquatroihihi/HNKS26CNTT3_Nhap-mon-CNTT_OnTap-Ngay2)
- **Hệ điều hành (Windows/macOS):** Windows

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```powershell
cat .\logs\access.log | select-string "ERROR" > .\logs\error_report.txt
cat .\logs\error_report.txt
```

### 2 dòng lỗi đầu tiên trong error_report.txt

```text
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
```

## Bài 2. Đếm bằng pipeline

### Lệnh

```powershell
(cat .\logs\access.log | select-string "WARNING").count
(cat .\logs\payment.log | select-string "ERROR").count
```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
WARNING trong access.log: 4
ERROR trong payment.log: 3
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```powershell
.\auto_warning.ps1
```

### Nội dung file logs/warning_report.txt

```text
=== CANH BAO THANH TOAN ===

2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi
```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
new-item .\logs\tong_hop_ngay_2.txt
"=== TONG HOP ACCESS LOG ===" > .\logs\tong_hop_ngay_2.txt
cat .\logs\access.log | Select-String "ERROR" >> .\logs\tong_hop_ngay_2.txt
cat .\logs\payment.log | Select-String "WARNING" >> .\logs\tong_hop_ngay_2.txt
```

### Nội dung file logs/tong_hop_ngay2.txt

```text
=== TONG HOP ACCESS LOG ===

2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)



2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi
```

## Bài 5. Câu hỏi ngắn

- **a)** Lệnh > và >> khác nhau:

">" là ghi đè nội dung vào file, có nghĩa là nếu trong file đó đã có nội dung gì thì sẽ bị xóa sạch đi để thay thế bằng nội dung mới sau ">" vào file đó

Còn ">>" là nối tiếp, có nghĩa file đó nếu có nội dung gì thì sẽ được enter xuống 1 dòng rồi ghi tiếp nội dung sau ">>" vào file đó
- **b)** Nếu dùng > thay cho >> thì nội dung trong file tong_hop_ngay_2.txt sẽ thay đổi như sau:

Mất dòng "=== TONG HOP ACCESS LOG ===", nội dung các dòng chứa "ERROR" vẫn được in ra bình thường
- **c)** Bởi vì nếu sử dụng đường dẫn tuyệt đối sẽ bị lộ thông tin cá nhân, đồng thời khi chuyển file sang máy khác thì sẽ bị lỗi không tìm thấy đường dẫn

## Tự chấm (điền sau khi có đáp án)

- **Điểm tự chấm:** 100/100
- **Lỗi mình đã mắc và cách sửa:** Không có lỗi

# Báo cáo cá nhân — HoVaTen-MSSV

Đổi tên file theo quy tắc `MSSV_HoTen.md`. Ví dụ: `20241234_NguyenVanAn.md`.

Đoạn video: MOT17-09, 150 frame (frame 1–150), nguồn MOTChallenge, giấy phép CC BY-NC-SA 3.0.

## 0. Thông tin học viên

- Họ tên: Nguyen Manh Quang
- MSSV:2A202603241
- Mã đề (A/B/C): A
- Email:quangkebg123@gmail.com
- Link repository: https://github.com/quangkebg123/K5-L2-Day05-NguyenManhQuang-2A202603241-MOTTracking/tree/main
- Giờ bắt đầu:16h30
- Giờ kết thúc: 21h

## 1. Xem trước đoạn video (CP0)

Ghi **trước khi vẽ**, mỗi người một dòng.

| Mã  | Frame xuất hiện | Frame cuối thấy được | Rẽ / dừng / đổi tốc độ ở frame                                  | Bị che ở frame             | Ghi chú                                                           |
| --- | --------------- | -------------------- | --------------------------------------------------------------- | -------------------------- | ----------------------------------------------------------------- |
| P1  | 0               | 149                  | Khoảng 105–120 đổi hướng/nhịp, tiến gần camera                  | 0–54, 69, 75, 125–128, 145 | Bị che một phần lâu ở đầu đoạn; cần chú ý lúc đổi hướng cuối đoạn |
| P2  | 61              | 149                  | 87–121 di chuyển ra khỏi vùng khuất và tiến gần camera          | 61–86                      | Xuất hiện muộn, lúc đầu bị che một phần                           |
| P3  | 0               | 149                  | 105–140 tiếp tục đi chéo về bên trái và gần camera              | Không thấy rõ              | Đi từ phía phải, kích thước tăng khi tiến gần                     |
| P4  | 40              | 149                  | 93–115 đổi nhịp khi đi chéo về bên trái, gần camera             | 40–52, 60–65               | Xuất hiện từ mép phải, có đoạn bị che                             |
| P5  | 0               | 146                  | 0–38 đi chậm/đứng gần cửa; về cuối bị che khi có người đi ngang | 106–110, 135–146           | Ở gần khu vực cửa hàng; cuối đoạn chỉ còn thấy từng phần          |

_Frame dùng chỉ số CVAT 0–149; tương ứng frame MOT17 1–150._

## 2. Keyframe và thời gian (CP1, CP4)

Số keyframe lấy từ kết quả `src/check_submission.py`.

| Mã       | Số keyframe | Keyframe ở frame                                                                                                                   | Số frame có mặt | Keyframe / 100 frame | Thời gian (phút) | Chỗ khó                                            |
| -------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------- | --------------- | -------------------- | ---------------- | -------------------------------------------------- |
| P1       | 30          | 0, 14, 20, 48, 53, 55, 61, 64, 69, 70, 71, 75, 76, 77, 85, 95, 97, 100, 105, 111, 115, 121, 125, 129, 135, 137, 140, 145, 146, 149 | 150             | 20.0                 | 12               | Rẽ nhiều, đổi tốc độ và gần camera ở cuối đoạn     |
| P2       | 13          | 61, 63, 67, 77, 87, 92, 102, 113, 121, 127, 140, 143, 146                                                                          | 89              | 14.6                 | 8                | Xuất hiện muộn, cần giữ khớp khi đi gần khung      |
| P3       | 24          | 0, 7, 21, 28, 46, 58, 63, 69, 78, 83, 89, 97, 105, 107, 111, 113, 119, 120, 125, 132, 137, 140, 143, 148                           | 150             | 16.0                 | 10               | Thay đổi hướng và nhịp bước ở nhiều đoạn           |
| P4       | 26          | 40, 53, 60, 66, 67, 72, 79, 86, 89, 93, 99, 101, 104, 106, 108, 110, 111, 115, 118, 122, 126, 130, 137, 141, 145, 149              | 110             | 23.6                 | 15               | Bị che dài và có nhiều điểm đổi hướng / kích thước |
| P5       | 12          | 0, 5, 9, 16, 20, 26, 36, 38, 106, 135, 141, 142                                                                                    | 123             | 9.8                  | 9                | Bị che ngắn nhưng có đoạn vắng và thay đổi góc đi  |
| **Tổng** | **105**     | **-**                                                                                                                              | **622**         | **16.9**             | **54**           | **-**                                              |

Keyframe / 100 frame của cả bài = tổng keyframe ÷ tổng số frame có mặt × 100 = 105 ÷ 622 × 100 = 16.9 keyframe / 100 frame.

Bạn đặt keyframe nhiều nhất ở người nào? Vì sao (người đó rẽ, dừng, lại gần camera hay bị che)?

Tôi đặt keyframe nhiều nhất ở P1, với 30 keyframe trên 150 frame, tương đương 20.0 keyframe / 100 frame. Lý do là P1 có nhiều điểm chuyển hướng và thay đổi tốc độ, đặc biệt ở giữa và cuối đoạn video khi người đó rẽ và đi sát camera hơn, nên hộp cần được cập nhật thường xuyên để tránh drift và sai khớp khi nội suy. P4 cũng là người khó vì bị che và đổi kích thước nhưng P1 vẫn cần nhiều keyframe hơn do sự thay đổi hướng rõ hơn.

## 3. Đoạn bị che (CP2)

Người bị che: `P1`

| Mốc                                      |                     Frame |
| ---------------------------------------- | ------------------------: |
| Bắt đầu bị che một phần (bật `occluded`) | 0 (đã bị che từ đầu đoạn) |
| Mất hẳn (bật `outside`)                  |              Không xảy ra |
| Hiện lại (tắt `outside`)                 |              Không xảy ra |
| Thấy rõ trở lại (tắt `occluded`)         |                        55 |

- Thời gian khuất hẳn: **0 frame = 0 giây**.
- Quyết định: **giữ cùng ID P1**.
- Lý do: P1 không mất hẳn khỏi khung hình nên thời gian khuất hẳn là 0 frame, thấp hơn ngưỡng 60 frame. Ngoại hình và vị trí của người vẫn nhận ra được trong đoạn bị che một phần. Không có lần hiện lại sau khi mất hẳn để so hướng và tốc độ; chuyển động trước và sau đoạn che một phần vẫn thuộc cùng track.

Lưu ý: trong export CVAT hiện tại, track P1 không có frame nào bật `outside`; vì vậy không có mốc mất hẳn hoặc hiện lại để ghi.

Ảnh chụp màn hình:

![Trước khi che](images/che_1_truoc.png)
![Giữa đoạn che, thấy cờ trên panel object](images/che_2_giua.png)
![Sau khi hiện lại, cùng ID](images/che_3_sau.png)

## 4. Tự review ID (CP3)

Lượt 1 theo người (đi ngược từ frame 149 về 0 trên CVAT), lượt 2 theo cảnh (nhảy 10 frame). Ít nhất 3 dòng; không có lỗi thì ghi một dòng "đã kiểm hai lượt, không lỗi".

Loại lỗi dùng đúng một trong 7 mã: `id_switch`, `fragmentation`, `lost`, `merge`, `false_track`, `drift`, `flag`.

| Frame | Mã người | Loại lỗi | Mô tả một câu                | Phát hiện ở lượt | Đã sửa?       |
| ----: | -------- | -------- | ---------------------------- | ---------------- | ------------- |
| 0–149 | P1–P5    | —        | Đã kiểm hai lượt, không lỗi. | Cả hai lượt      | Không cần sửa |

Tổng hợp số lỗi theo loại:

| `id_switch` | `fragmentation` | `lost` | `merge` | `false_track` | `drift` | `flag` |
| ----------: | --------------: | -----: | ------: | ------------: | ------: | -----: |
|           0 |               0 |      0 |       0 |             0 |       0 |      0 |

Lỗi nào chỉ lượt 2 (theo cảnh) mới thấy, lượt 1 (theo người) không thấy? Vì sao?

Không có lỗi nào chỉ được phát hiện ở lượt 2; cả hai lượt đều không phát hiện lỗi ID.

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra                                                  | Kết quả                                                 |
| --------------------------------------------------------- | ------------------------------------------------------- |
| Tên file MOT 1.1                                          | `NguyenManhQuang_mot.zip`                               |
| Tên file CVAT for video 1.1                               | `NguyenManhQuang_cvat_video.zip`                        |
| Số track ID khác nhau trong `gt/gt.txt` (phải là 5)       | 5                                                       |
| Frame `outside` không có dòng trong `gt.txt` (đúng / sai) | Đúng — P5 không có dòng ở CVAT frame 111–134 và 147–149 |
| Job đã completed trên CVAT máy cá nhân                    | OK                                                      |

Dán phần tóm tắt in ra từ `src/check_submission.py`:

```text
=== Tóm tắt ===
  Lỗi: 0   |   Cảnh báo: 0
  Đạt. Dán phần tóm tắt này vào báo cáo mục 5.
```

## 6. Ba câu kết

1. Nếu được gán lại, bạn sẽ đặt keyframe khác ở đâu? Vì sao?

    Nếu được gán lại, tôi sẽ kiểm tra kỹ hơn các đoạn P1 đổi hướng và tiến gần camera ở khoảng frame 105–129, cùng các đoạn P4 bị che và thay đổi kích thước quanh frame 60–72 và 104–122. Tôi sẽ chỉ bổ sung keyframe tại những frame nội suy làm box lệch khỏi người.

2. Có chỗ nào bạn không chắc "cùng ID hay ID mới"? Bạn đã quyết định và ghi chú thế nào?

    Ở đoạn P1 bị che một phần đầu clip, tôi giữ nguyên ID P1 vì người vẫn nhận diện được và không có đoạn mất hẳn khỏi khung hình. Export hiện tại cũng không ghi `outside` cho P1, nên không có căn cứ để tạo track mới.

3. Một lỗi ID trong job của bạn (nếu không còn sót, chọn lỗi đã sửa) có thể làm xe tự lái dự đoán sai chuyển động của người đó như thế nào? Lỗi đó ảnh hưởng MOTA hay IDF1 nhiều hơn?

    Nếu xảy ra `id_switch` giữa hai người đang đi gần nhau, xe có thể ghép vận tốc và hướng của người này cho người kia, dẫn đến dự đoán sai quỹ đạo và phản ứng phanh không phù hợp. Lỗi này ảnh hưởng IDF1 nhiều hơn vì box vẫn có thể đúng vị trí nhưng ID bị gán nhầm; MOTA cũng bị trừ điểm do ID switch.

## 7. Tài liệu tham khảo và công cụ AI đã dùng

...

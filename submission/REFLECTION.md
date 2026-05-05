# Reflection — Lab 19

**Tên:** Nguyễn Văn Thạch - 2A202600237
**Cohort:** A20-K1
**Path đã chạy:** lite

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

**Kết quả phân tích:**

- **Exact (Keyword thắng/hòa):** Keyword và Hybrid đều đạt 96.7%. BM25 cực mạnh khi query chứa từ khóa chính xác có trong văn bản. Hybrid giữ được phong độ này nhờ RRF bảo toàn hạng cao từ BM25.
- **Mixed (Hybrid thắng tuyệt đối):** Hybrid đạt 100% Precision, vượt qua cả Keyword (97%) và Semantic (98.5%). Điều này minh chứng Hybrid cực kỳ hiệu quả khi user viết query kết hợp cả từ khóa và ý nghĩa ngữ nghĩa.
- **Paraphrase:** Cả 3 mode đều giảm điểm do model `bge-small-en` (Lite path) chưa tối ưu cho tiếng Việt, nhưng Keyword vẫn nhỉnh hơn một chút (33.3%) so với Semantic (24%).

**Khi nào KHÔNG dùng Hybrid:**

- Dùng **pure BM25** khi hệ thống yêu cầu độ trễ cực thấp (P99 < 2ms) và tập dữ liệu chứa nhiều thuật ngữ chuyên môn, mã số, hoặc tên riêng mà người dùng thường tìm chính xác.
- Dùng **pure Vector** khi muốn tiết kiệm tài nguyên tính toán (không phải chạy 2 luồng search và RRF) và bạn sở hữu một embedding model rất mạnh (như bge-m3) có khả năng hiểu ngữ nghĩa vượt trội hơn hẳn từ khóa.

---

## Điều ngạc nhiên nhất khi làm lab này

Tôi ngạc nhiên khi thấy Hybrid đạt được độ chính xác 100% đối với loại query "mixed". Điều này cho thấy trong thực tế, việc kết hợp các phương pháp tìm kiếm truyền thống và hiện đại là cách tốt nhất để xử lý các câu hỏi đa dạng của người dùng.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_

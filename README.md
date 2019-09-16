# Cấu hình và cài đặt công tắc zigbee cảm ứng

## 1. Định nghĩa

  * **wtls-z3-dev**: Bộ công tắc cảm ứng gắn tường
  * **wtls-z3-coordinator-dev**: Thiết bị khởi tạo
  * **wtls-z3-dev**: Thiết bị tham gia
  * **wtls-z3-app**: App điều khiển bộ công tắc cảm ứng gắn tường
  * **mht-zigbee-gateway**: zigbee <> ip gateway

## 2. Tổng quan
  2.1 Hardware platform
  * Chip điều khiển: Silicon labs EFR32MG1 Mighty Gecko Multi-Protocol
SoC Family
  * Hỗ trợ tối đa 4 công tắc
  * Điều khiển: 4 nut cảm ứng + 1 nút vật lý
  * Chỉ thị: 4 led RGB + 1 led đơn

  2.2 Zigbee platform
  * Hỗ trợ 2 chế độ làm việc:
    * Normal: Thiết bị gắn với 1 mạng zigbee
    * Touchlink: Thiết bị đóng vai trò khởi tạo mạng, không cần có mặt **mht-zigbee-gateway** 

  2.3 App platform
  * Hỗ trợ điều khiển trong mạng ip-local thông qua **mht-zigbee-gateway**
  * Hỗ trợ điều khiển qua giao thức Homekit trong mạng ip-local thông qua **mht-zigbee-gateway**

## 3. Phần dành cho người sử dụng & cài đặt

  3.1 Cài đặt thiết bị **wtls-z3-dev** mới:
  * Cài đặt mạng zigbee Normal-mode:
    * Sử dụng **wtls-z3-app** để cài đặt **mht-zigbee-gateway**
    * Cho phép thiết bị tham gia mạng ở phía **mht-zigbee-gateway**
    * Nhấn giữ phím vật lý trong vòng 5s, đèn chỉ thị nhấp nháy đỏ-xanh lá
    * Kết thúc quá trình đèn chỉ thị dừng nhấp nháy, ở phía **mht-zigbee-gateway** quan sát thấy có thiết bị mới tham gia mạng

  * Cài đặt mạng với chế độ Touchlink:
    * Áp dụng với 2 công tắc:
      * Thiết bị **wtls-z3-dev-1** đóng vai trò khởi tạo:
        * Tắt nguồn thiết bị **wtls-z3-dev-2** để tránh **wtls-z3-dev-1** join vào mạng đang có của **wtls-z3-dev-2**
        * Nhấn giữ phím vật lý trong vòng 5s, đèn chỉ thị nhấp nháy đỏ-xanh lam
        * Nhấn thêm 1 lần phím vật lý để dừng tìm mạng, đèn chỉ thị dừng nhấp nháy

      * Thiết bị **wtls-z3-dev-2** tham gia vào mạng do thiết bị **wtls-z3-dev-1** khởi tạo:
        * Đặt thiết bị **wtls-z3-dev-2** **lại gần** thiết bị **wtls-z3-dev-1**
        * Sau khi thiết bị **wtls-z3-dev-1** khởi tạo mạng, tiến hành cài đặt thiết bị **wtls-z3-dev-2**
        * Nhấn giữ phím vật lý trong vòng 5s, đèn chỉ thị nhấp nháy đỏ-xanh lam
        * Nhấn thêm 1 lần phím vật lý để dừng tìm mạng, đèn chỉ thị dừng nhấp nháy
        * Nhấn giữ phím vật lý trong vòng 5s, đèn chỉ thị nhấp nháy đỏ-xanh lục
        * Kết thúc quá trình, đèn chỉ thị dừng nhấp nháy

      * Xác nhận **wtls-z3-dev-2** đã tham gia vào mạng do **wtls-z3-dev-1** khởi tạo bằng cách nhấn phím vật lí trên **wtls-z3-dev-2**, nó sẽ điều khiển on/off toàn bộ 4 công tắc trên **wtls-z3-dev-1**

  * Cài đặt binding
    * Cài đặt binding cho công tắc đích
      * Nhấn phím vật lý cho tới khi đèn chỉ thị xanh lam
      * Nhấn giữ 1 phím cảm ứng chọn làm nguồn cho tới khi đèn phím nhấp nháy

    * Cài đặt binding cho phím nguồn
      * Nhấn phím vật lý cho tới khi đèn chỉ thị xanh lục
      * Nhấn giữ 1 phím cảm ứng chọn làm nguồn cho tới khi đèn phím nhấp nháy

    * Kết thúc quá trình cả 2 đèn tắt, phím **nguồn** có thể điều khiển công tắc ở **đích**

## 4. Phần dành cho **wtls-z3-app** developer


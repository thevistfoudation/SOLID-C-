# SOLID- In -C#
## Mục Lục
- [I.SOLID là gì ?](#What)
- [II.SOLID gồm những gì ?](#How)
- [III.Tổng kết  ?](#When)
<a name="What"></a>
## I.SOLID là gì ?
`SOLID` là Cứng ? , đùa thôi là 5 nguyên tắc cơ bản , giúp xây dựng 1 kiến trúc phần mềm tốt .Hầu như tất cả các desgin pattern đều được dựa trên các nguyên tắc này để phát triển.
<a name="How"></a>
## II.SOLID gồm những gì ?
- Như đã trao đổi ở trên `SOLID` là 5 nguyên tắc giúp phát triển phần mềm tốt hơn gồm :
- [`S` is single responsibility principle (SRP)](#Single)
- [`O` stands for open closed principle (OCP)](#Open)
- [`L` Liskov substitution principle (LSP)](#Liskov)
- [`I` interface segregation principle (ISP)](#Interface)
- [`D` Dependency injection principle (DIP)](#Dependency)
<a name="Single"></a>
### Single responsibility principle (SRP)
- Hay còn gọi là nguyên tắc Trách nhiệm đơn lẻ
- Nguyên lý đầu tiên tương ứng với chữ `S` trong SOLID: một class chỉ nên giữ 1 trách nhiệm duy nhất 
- ví dụ : mỗi 1 game object nên chỉ có 1 script hành vi của object đó 
- ví dụ 1 class đã vi phạm hành vi như sau :
- ![image](https://user-images.githubusercontent.com/47918431/137583851-b59bdf4a-e2e9-406c-95f5-bb3ea4824022.png)
- `Problem` Có thể thấy class này đã vi phạm nguyên tắc vì đã đảm nhiệm cùng lúc 3 nhiệm vụ gồm đọc dữ liệu từ DataBase, xử lý dữ liệu và in kết quả . Do đó, chỉ cần thay đổi DataBase, thay đổi cách xuất kết quả ,... kéo theo việc ta sẽ phải sửa đổi class này và càng về sau code sẽ càng mang tính chắp vá khiến cấu trúc code phình to ra và khó kiểm soát 
- `Solution` Vậy theo đúng nguyên lí ta chỉ cần tách class này thành 3 class riêng , mặc dù số lượng class nhiều hơn nhưng việc sửa chữa sẽ đơn giản hơn giúp cho phần mềm ít bug hơn
- Tổng kết: Vậy nên, cách tốt nhất để hạn chế toàn bộ những rủi ro như vậy là cho mỗi lớp một chức năng riêng biệt. Không nên gộp nhiều hoạt động vào cùng một lớp.
<a name="Open"></a>
### Open closed principle (OCP)
- Nguyên tắc đóng mở
- Nguyên lí thứ 2 , tương ứng với `O` trong SOLID: Có thể thoải mái mở rộng 1 class , nhưng không được sửa đổi bên trong class đó 
- Dựa trên nguyên lí này , mỗi khi ta muốn thêm chức năng mới, thay vì phải sửa đổi và chắp vá lại class cũ chúng ta sẽ kế thừa class cũ và phát triển tiếp 
- `Problem` Hình dung nhé! chúng ta đang có 1 nhân vật Knight có khả năng cận chiến mà game GD muốn chúng ta phát triển 1 nhân vật Knight level 2 mà có thêm kỹ năng không chiến bay nhảy và tấn công từ xa , theo lối tư duy mòn chắc chúng ta sẽ viết tiếp 1 hàm hỗ trợ cho việc không chiến chứ? vậy là vi phạm nguyên tắc rồi -_- 🕵️‍♀️
- ![image](https://user-images.githubusercontent.com/47918431/137584283-5d784f9f-cf14-4efd-bc75-cafb11fc2779.png) 
- `Solution` Vậy theo đúng nguyên lí chúng ta sẽ viết 1 class là KnightController2 kế thừa lại class KnightController để phát triển tiếp 🐱‍👓
- Tổng kết: Đây là phương án rất an toàn và thiện thiện, vừa giúp phát triển code mới mà lại không lo làm hỏng code cũ.
<a name="Liskov"></a>
### Liskov substitution principle (LSP)
- Nguyên tắc Phân vùng Liskov
- Nguyên kí thứ 3, tương ứng với chữ `L` trong SOLID: Trong một chương trình, các object của class con có thể thay thế class cha mà không làm thay đổi tính đúng đắn của chương trình 
- `Problem` Ví dụ khi ta muốn viết một chương trình để mô tả các loài chim có thể bay thế nhưng trong danh sách có 1 con 🐧🐧🐧 sẽ gây ra lỗi và cụ thể là `NoFlyException`
- ![image](https://user-images.githubusercontent.com/47918431/137585126-84bc01a6-22eb-4311-a08f-4d6f2a014832.png)
- `Solution` Để có thể giải quyết vấn đề này ta sẽ tách class chim cánh cụt ra 1 Interface riêng 
- Tổng kết:  Nguyên tắc này xuất hiện là để nhắc nhở lập trình viên chú ý đến tính sai phạm của nội dung các đoạn mã lập trình. Nếu không khi để đến lúc hoàn thành mới phát hiện ra lỗi thì sửa lại rất khó khăn và mất thời gian.
<a name="Interface"></a>
### Interface segregation principle (ISP)
- Nguyên tắc Phân Tách giao diện 
- Nguyên tắc thứ 4, tương ứng với chữ `I` trong SOLID: Thay vì dùng 1 Interface lớn, ta nên tách thành nhiều interface nhỏ, với nhiều mục đích cụ thể.
- `Problem` Ví dụ khi khi chúng ta code Skill cho 1 nhân vật nào đó thì lúc thiết kế chúng ta sẽ nghĩ tới việc thiết kế 1 Interface là Skill do chỉ có duy nhất 1 sự khác biệt nên nhét hết tất cả các Skill( lửa , băng , gió , đất , sấm sét ,...) vào trong Interface này do đó dẫn đến vấn đề nếu như 1 nhân vật Firen 1 pháp sư hệ lửa thì chỉ dùng skill lửa thế nhưng lại có thêm cả băng , gió ??? ủa pháp sư hệ lửa mà 🙄
- ![image](https://user-images.githubusercontent.com/47918431/137585714-5349feb6-69d4-4f61-af02-865799d29c5b.png)
- `Solution` Để giải quyết vấn đề này chúng ta sẽ chia các Skill thành nhiều Interface như Skill Lửa , Skill Băng , Skill Gió rồi nhân vật hệ nào sẽ sử dụng Interface chứa Skill hệ đó 
- Tổng kết: Nguyên lý SOLID này giúp bạn dễ dàng mở rộng quy mô một cách đơn giản.
###



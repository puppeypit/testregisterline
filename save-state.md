# 📌 Save State: App Portal & Registration (Combined SPA)

## 🎯 เป้าหมายหลักของระบบ (Project Goal)
รวมระบบ **"ลงทะเบียนผู้ใช้ใหม่"** และ **"Dashboard แสดงผลข้อมูลแอปพลิเคชัน"** ให้ทำงานร่วมกันเป็นหน้าเว็บเดียว (Single Page Application - SPA) ควบคู่กับ **"ระบบจัดการแอดมิน (Admin Panel)"** สำหรับจัดการสิทธิ์และตัวแอปแบบครบวงจร

- **Frontend**: โฮสต์บน GitHub Pages (`index.html`) ทำงานร่วมกับ LINE LIFF SDK (v2) (มี Fallback ให้ Login แบบปกติได้)
- **Backend API**: โฮสต์บน Google Apps Script (`code.js`) เป็น REST API รองรับ `doPost`
- **Database**: Google Sheets (`Login`, `Apps`, `Categories`)

## ✅ สิ่งที่ดำเนินการเสร็จแล้ว (Completed Features)
1. **ออกแบบ UI เป็น Single Page Application (Glassmorphism)**
   - รวมหน้า Loader, Registration Form, Login, Dashboard, และ Admin ให้อยู่ในหน้าเดียว
2. **ระบบ Backend (REST API)**
   - เขียนฟังก์ชันรองรับการทำงานทั้งหมดผ่าน `doPost` (`loginUser`, `registerUser`, `getUserStatus`, `adminManageApps`, `adminManageCategories`, `updateUserApps`, `getAllUsers`)
3. **ระบบผู้ใช้และการเข้าสู่ระบบ (User & Auth)**
   - รองรับการ Login ผ่านระบบ Local (Username/Password) และ LINE LIFF
   - ระบบลงทะเบียนใหม่ โดยป้องกัน Username ซ้ำ
4. **ระบบจัดการแอดมิน (Admin Panel - จัดการสิทธิ์ผู้ใช้)**
   - โชว์พนักงานทั้งหมด พร้อมระบบ Search อัจฉริยะ (ค้นหาตามชื่อ/แผนก)
   - แอดมินสามารถคลิกพนักงานเพื่อปรับเปลี่ยนสิทธิ์ว่าให้มองเห็นแอปใดได้บ้าง หรือให้เข้าถึงทั้งหมด (All)
5. **ระบบจัดการแอดมิน (Admin Panel - จัดการแอประบบและหมวดหมู่)**
   - เพิ่มระบบ **เพิ่ม/แก้ไข/ลบ** หมวดหมู่ (Category) โดยตรงจากหน้าเว็บ
   - เพิ่มระบบ **เพิ่ม/แก้ไข/ลบ** แอปพลิเคชัน (Apps)
   - **(ใหม่!)** ระบบ *Quick Emoji Picker* ให้แอดมินกดเลือกไอคอนแอปได้รวดเร็วทันใจกว่า 20 แบบ
6. **ระบบหน้าต่างแอปพลิเคชัน (App Dashboard สำหรับพนักงาน)**
   - ดึงแอปและหมวดหมู่ทั้งหมดจาก Database มาแสดงแบบ Dynamic
   - กรองแอปตามหมวดหมู่ได้ (Tab Filter) และกรองเฉพาะสิทธิ์ที่ได้รับอนุญาต
   - ระบบ *Smart Search Bar* ให้พนักงานพิมพ์ค้นหาแอปที่ต้องการได้แบบ Real-time และทำงานร่วมกับ Tab หมวดหมู่อัตโนมัติ
7. **ระบบหน้าต่างโปรไฟล์ส่วนตัว (Profile)**
   - ปรับการแสดงผลให้พอดีกับ 1 หน้าจอ (No scrolling)
   - นำปุ่มเปลี่ยนรูปโปรไฟล์ออกตามความต้องการ
   - เปลี่ยนรหัสผ่านผ่านปุ่มแบบ Pop-up (กรอกรหัสผ่านเก่าและใหม่)
   - ปรับปุ่มย้อนกลับหน้าหลักให้โดดเด่นและชัดเจนขึ้น
8. **ระบบการกำหนดสิทธิ์แบบรวม (Combine Mode RBAC)**
   - เพิ่มแผ่นงาน `DeptPermissions` ควบคุมสิทธิ์ตั้งต้นแบบกลุ่มตามแผนก
   - แอดมินสามารถจัดการสิทธิ์ของแต่ละแผนกได้ผ่านแท็บ "จัดการสิทธิ์แผนก"
   - ในหน้าแก้ไขสิทธิ์รายบุคคล (User Management) ระบบจะแสดงสิทธิ์ที่สืบทอดมาจากแผนกแบบล็อกไว้ (พร้อมป้ายกำกับ) และแอดมินสามารถติ๊กเพิ่มแอปเฉพาะบุคคล (Individual Extra) ได้

## 🚧 แผนงานถัดไปหรือสิ่งที่ต้องทำต่อไป (Next Steps)
1. **ทดสอบใช้งานจริง (User Acceptance Testing - UAT):**
   - ทดสอบลงทะเบียน, เข้าสู่ระบบ, ปรับแต่งสิทธิ์ และกดเข้าแอปผ่านหน้า Dashboard เพื่อเช็ค Flow ทั้งหมด
2. **ฟีเจอร์เพิ่มเติมในอนาคต (ถ้าต้องการ):**
   - การจัดเรียงลำดับแอป (Drag & Drop) หรือลำดับหมวดหมู่
   - บอร์ดประกาศข่าวสาร (Announcement)
   - ระบบแจ้งเตือนผ่าน LINE (LINE Notify / Messaging API) เมื่อมีแอปใหม่

## 🔗 ข้อมูลสำคัญของโปรเจกต์ (Important Constants)
- **LIFF ID:** `2009229714-weBHiK8i`
- **Spreadsheet ID:** `1Qtu-oqWyOFTbJl7D8fqj8vMBQIFOgSASTqtqNINxA94`
- **Frontend URL (GitHub):** `https://puppeypit.github.io/testregisterline/`

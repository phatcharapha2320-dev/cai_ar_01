# 📱 CAI Courseware: วิทยาการคำนวณ (ความจริงเสริม AR) - ม.4
**ระบบคอมพิวเตอร์ช่วยสอน (CAI) และแผงควบคุมผู้สอน บนระบบหลังบ้าน Supabase**  
*โรงเรียนอากาศอำนวย อำเภออากาศอำนวย จังหวัดสกลนคร*

---

## 📌 ภาพรวมโครงการ (Project Overview)

แอปพลิเคชันบทเรียนคอมพิวเตอร์ช่วยสอน (CAI) รายวิชา **วิทยาการคำนวณ (ความจริงเสริม AR)** ชั้นมัธยมศึกษาปีที่ 4 ออกแบบมาเพื่อเป็นสื่อการเรียนรู้แบบโต้ตอบ (Interactive Learning) ร่วมกับเทคโนโลยี **WebAR** โดยมีระบบหลังบ้านบน **Supabase** สำหรับจัดการสิทธิ์ความปลอดภัย (Row Level Security), การยืนยันตัวตน, การจัดเก็บไฟล์สื่อ และการประเมินพัฒนาการเรียนรู้ของผู้เรียนด้วยค่าดัชนีประสิทธิผล (Normalized Gain)

---

## ✨ คุณสมบัติเด่น (Features)

### 🎓 สำหรับผู้เรียน (Student Dashboard)
* **ระบบลงทะเบียนรหัสนักศึกษา**: ตรวจสอบกับรายชื่อในระบบโรงเรียนอัตโนมัติด้วย 11-Digit Student ID Matching
* **แบบทดสอบขนาน (Parallel Tests - Set A / Set B)**: สลับชุดข้อสอบก่อนเรียน (Pre-test) และหลังเรียน (Post-test) ตามเลขท้ายรหัสนักศึกษา (คู่/คี่) เพื่อลดผลกระทบจากการจำข้อสอบ
* **เนื้อหาการเรียนรู้ 5 หน่วย**:
  1. *พื้นฐานความจริงเสริม (Augmented Reality)* - Azuma (1997), Milgram & Kishino (1994)
  2. *ชนิดและเทคโนโลยี AR* - Marker, Markerless, Location-based, Projection-based
  3. *การออกแบบสื่อ AR เพื่อการเรียนรู้* - หลักมัลติมีเดียของ Mayer & Cognitive Load
  4. *ปฏิบัติการสร้างสื่อ WebAR* - ปฏิบัติจริงผ่านตัวอย่าง 3D Model และส่งงานปฏิบัติ
  5. *การทดสอบและประเมินสื่อ AR* - ค่า IOC (Rovinelli & Hambleton, 1977), E1/E2, Normalized Gain (Hake, 1998)
* **กิจกรรมคำถามแทรก (Interactive Checkpoints)**: ตรวจสอบความเข้าใจรายหน่วยทันที
* **การส่งงานปฏิบัติ AR**: รองรับการแนบ URL ลิงก์ WebAR หรืออัปโหลดไฟล์หลักฐาน (ภาพ/วิดีโอ)
* **การจัดการโปรไฟล์**: อัปโหลดรูปโปรไฟล์พร้อมระบบย่อขนาดภาพอัตโนมัติบนเบราว์เซอร์
* **สรุปผลพัฒนาการ**: คำนวณและแสดงผลค่า $g$ (Normalized Gain) พร้อมเฉลยละเอียดหลังทำ Post-test

### 👨‍🏫 สำหรับผู้สอน (Teacher Dashboard)
* **ตารางติดตามคะแนนและความก้าวหน้า**: ดูผลคะแนน Pre-test, Post-test, ค่า Gain ($g$) และจำนวนหน่วยที่เรียนเสร็จรายบุคคล
* **ระบบตรวจงานปฏิบัติ**: ให้คะแนน (0-100) และป้อนข้อเสนอแนะต่องาน AR ของนักเรียน
* **คลังสื่อการสอน (Materials Management)**: อัปโหลดเอกสารประกอบการสอน (.pptx, .docx, .pdf) หรือเพิ่มลิงก์/วิดีโอ
* **ส่งออกรายงาน (CSV Export)**: ส่งออกข้อมูลคะแนนผู้เรียนรองรับภาษาไทยใน Microsoft Excel (UTF-8 with BOM)

---

## 🛠 เทคโนโลยีที่ใช้ (Tech Stack)

* **Frontend**: Single-File HTML5, CSS3, JavaScript (Vanilla ES6+)
* **Styling & Fonts**: Custom CSS (Navy/Slate Theme), Google Fonts (Sarabun), FontAwesome Icons
* **3D / AR Renderer**: Official Google `<model-viewer>` v3.4.0 (WebXR, Scene Viewer, Quick Look)
* **Backend & Database**: Supabase (PostgreSQL)
  * **Auth**: Email Authentication (Custom domain binding)
  * **Database Security**: Row Level Security (RLS) & Security Definer Functions
  * **Storage Buckets**: Private Buckets (`photos`, `submissions`, `materials`)
* **Mathematical Notation**: LaTeX Engine ($g = \frac{\text{Post} - \text{Pre}}{10 - \text{Pre}}$)

---

## 📁 โครงสร้างไฟล์ในโครงการ (File Structure)

```text
.
├── courseware.html        # แอปพลิเคชันหลัก Single-File Web App (HTML + CSS + JS)
├── setup.sql              # สคริปต์ SQL ตั้งค่าตาราง, RLS Policies, Triggers และ Mock Data
├── courseware_manual.md   # คู่มือการติดตั้งระบบฉบับละเอียด ตารางทดสอบ และ Self-Check
└── README.md              # เอกสารอธิบายภาพรวมโครงการ (ไฟล์นี้)
```

---

## 🚀 ขั้นตอนการติดตั้งอย่างรวดเร็ว (Quick Start)

1. **เตรียมฐานข้อมูล Supabase**:
   * สร้าง Project ใหม่บน [Supabase](https://supabase.com)
   * ไปที่ **Authentication -> Providers -> Email** และปิดสวิตช์ `Confirm email`
2. **รันสคริปต์ SQL**:
   * คัดลอกข้อความในไฟล์ `setup.sql` ไปวางและรันในเมนู **SQL Editor** บน Supabase
3. **สร้าง Private Storage Buckets**:
   * สร้าง Bucket จำนวน 3 อัน: `photos`, `submissions`, และ `materials` (กำหนดเป็น Private)
4. **ตั้งค่าไฟล์ HTML**:
   * เปิดไฟล์ `courseware.html` แก้ไขตัวแปรด้านบนของสคริปต์:
     ```javascript
     const SUPABASE_URL = "https://your-project-ref.supabase.co";
     const SUPABASE_ANON_KEY = "your-anon-public-key";
     ```
5. **แต่งตั้งสิทธิ์ผู้สอน**:
   * สมัครบัญชีครูผู้สอนในระบบ คัดลอก `User ID` (UUID) แล้วนำไปรันใน SQL Editor:
     ```sql
     INSERT INTO public.teachers (user_id) VALUES ('YOUR_TEACHER_UUID');
     ```

*(ดูขั้นตอนการตั้งค่าอย่างละเอียดเพิ่มเติมได้ในไฟล์ `courseware_manual.md`)*

---

## 📚 แหล่งอ้างอิงทางวิชาการ (Academic References)

* **Azuma, R. T. (1997).** *A survey of augmented reality.* Presence: Teleoperators & Virtual Environments, 6(4), 355–385.
* **Hake, R. R. (1998).** *Interactive-engagement versus traditional methods: A six-thousand-student survey of mechanics test data for introductory physics courses.* American Journal of Physics, 66(1), 64–74.
* **Milgram, P., & Kishino, F. (1994).** *A taxonomy of mixed reality visual displays.* IEICE TRANSACTIONS on Information and Systems, 77(12), 1321–1329.
* **Rovinelli, R. J., & Hambleton, R. K. (1977).** *On the use of content specialists in the assessment of criterion-referenced test item validity.* Dutch Journal of Educational Research, 2, 49–60.

---

## 📄 ใบอนุญาตการใช้งาน (License)

สื่อการเรียนรู้นี้จัดทำขึ้นเพื่อประโยชน์ทางการศึกษาสำหรับโรงเรียนอากาศอำนวย สงวนสิทธิ์ตามกฎหมาย
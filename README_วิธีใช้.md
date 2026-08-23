# 🌐 เว็บไซต์ห้องเรียนออนไลน์
## ครูวีระวัฒน์ ภูสมหมาย | แผนกอิเล็กทรอนิกส์ฯ วท.ศรีสะเกษ

---

## ✨ คุณสมบัติของเว็บไซต์

- **HTML ไฟล์เดียว** – ไม่ต้องติดตั้งอะไร เปิดได้ทันที
- **Responsive** – ใช้งานได้ทั้งคอมพิวเตอร์ มือถือ และแท็บเล็ต
- **5 รายวิชาครบ** – มีหน้าเฉพาะของแต่ละวิชาพร้อมสีประจำ
- **15 สัปดาห์/วิชา** – คลิกเลือกสัปดาห์เพื่อดูเอกสารของหน่วยนั้น
- **เชื่อม Discord, Google Form, Drive** – ลิงก์ครบทุกเครื่องมือ
- **ตารางสอนสวย** – แสดงตารางสอนรายสัปดาห์ทั้ง 5 วัน
- **โหลดเร็ว** – ใช้ Tailwind CSS via CDN

---

## 🚀 วิธีใช้งาน

### วิธีที่ 1: เปิดดูในเครื่องตนเอง

1. ดับเบิลคลิกที่ไฟล์ `classroom_website.html`
2. เว็บจะเปิดในเบราว์เซอร์ (Chrome, Firefox, Safari, Edge)
3. ใช้งานได้ทันที

> ⚠️ จำเป็นต้องเชื่อมต่ออินเทอร์เน็ตเพราะใช้ Tailwind CSS, Google Fonts จาก CDN

---

### วิธีที่ 2: เผยแพร่ออนไลน์ (Hosting ฟรี)

#### Option A: GitHub Pages ⭐ แนะนำ

1. สร้างบัญชี GitHub ที่ https://github.com (ฟรี)
2. สร้าง Repository ใหม่ชื่อ `classroom` หรือ `username.github.io`
3. อัปโหลดไฟล์ `classroom_website.html` เปลี่ยนชื่อเป็น `index.html`
4. ไปที่ Settings → Pages → Source: main branch → Save
5. รอ 1-2 นาที จะได้ลิงก์ เช่น `https://username.github.io/classroom`

#### Option B: Netlify Drop ⚡ ง่ายที่สุด

1. เข้าเว็บ https://app.netlify.com/drop
2. ลากไฟล์ `classroom_website.html` (เปลี่ยนชื่อเป็น `index.html`) ลงในกรอบ
3. ได้ลิงก์ทันที เช่น `https://magical-name-1234.netlify.app`
4. สามารถเปลี่ยนชื่อ subdomain ได้ในการตั้งค่า

#### Option C: Vercel

1. สมัครที่ https://vercel.com (ใช้ GitHub login ได้)
2. New Project → Import Repository หรือ Upload
3. Deploy

#### Option D: Cloudflare Pages

1. สมัครที่ https://pages.cloudflare.com
2. Direct Upload หรือเชื่อม GitHub
3. Deploy

---

## 🛠 วิธีปรับแต่ง (สำหรับครู)

เปิดไฟล์ `classroom_website.html` ด้วย Text Editor เช่น Notepad++ หรือ VS Code แก้ไขส่วนต่าง ๆ ดังนี้

### 1. เปลี่ยนข้อมูลครู

ค้นหาคำว่า `wpoosommai@gmail.com` แล้วเปลี่ยนเป็น Email ของครู
ค้นหาคำว่า `0812661861` แล้วเปลี่ยนเป็นเบอร์โทร
ค้นหาคำว่า `Pwerawat` แล้วเปลี่ยนเป็น Line ID

### 2. เพิ่มลิงก์เอกสารของแต่ละสัปดาห์

ในส่วน JavaScript ของไฟล์ ค้นหา `RESOURCES_PER_UNIT` เปลี่ยนเป็น

```javascript
const RESOURCES_PER_UNIT = [
  { type: "handout",  icon: "📄", label: "ใบความรู้",  color: "blue",
    url: "https://drive.google.com/file/d/YOUR_ID/view" },
  { type: "slide",    icon: "🎬", label: "PowerPoint", color: "orange",
    url: "https://drive.google.com/..." },
  { type: "lab",      icon: "📝", label: "ใบงาน",      color: "green",
    url: "https://forms.gle/..." },
  { type: "pretest",  icon: "❓", label: "Pre-test",   color: "purple",
    url: "https://forms.gle/..." },
  { type: "posttest", icon: "✅", label: "Post-test",  color: "pink",
    url: "https://forms.gle/..." },
  { type: "video",    icon: "▶️", label: "วิดีโอ",     color: "red",
    url: "https://youtube.com/..." },
];
```

แล้วในฟังก์ชัน `renderContent()` เปลี่ยนบรรทัด `onclick="..."` เป็น `href="${res.url}"`

### 3. เพิ่มลิงก์ Discord

ค้นหา `discordBtn` ในส่วน JavaScript แล้วเปลี่ยนเป็น

```javascript
document.getElementById('discordBtn').addEventListener('click', (e) => {
  e.preventDefault();
  window.open('https://discord.gg/YOUR_INVITE_CODE', '_blank');
});
```

### 4. เปลี่ยนสีประจำวิชา

ค้นหา `colors:` ในส่วน `tailwind.config` เปลี่ยนค่า HEX ของสีแต่ละวิชา

### 5. เพิ่ม/ลบ รายวิชา

ค้นหา `const SUBJECTS = [` แก้ไข Array นี้
แต่ละวิชาต้องมี: code, color, icon, name, nameEn, classGroup, credit, hours, room, days, desc, units (15 หน่วย)

---

## 📁 โครงสร้างไฟล์แนะนำ (เมื่อ Deploy ออนไลน์)

```
classroom/
├── index.html              ← เปลี่ยนชื่อจาก classroom_website.html
├── assets/
│   ├── teacher-photo.jpg   ← รูปครู (ใส่ใน <img> แทน emoji)
│   └── logo.png            ← โลโก้วิทยาลัย
└── files/
    ├── handouts/           ← เก็บใบความรู้
    ├── slides/             ← เก็บ PowerPoint
    └── worksheets/         ← เก็บใบงาน
```

---

## 🎨 การปรับแต่งขั้นสูง

### เพิ่มรูปครูแทน Emoji 👨‍🏫

ค้นหาบรรทัด `<div class="w-full h-full rounded-3xl bg-white flex items-center justify-center text-8xl">👨‍🏫</div>`

เปลี่ยนเป็น:
```html
<img src="assets/teacher-photo.jpg" class="w-full h-full rounded-3xl object-cover" alt="ครูวีระวัฒน์ ภูสมหมาย" />
```

### เปลี่ยน Favicon

ค้นหา `<link rel="icon"` เปลี่ยนเป็น

```html
<link rel="icon" href="assets/favicon.ico" />
```

### เพิ่ม Google Analytics

ใส่ก่อน `</head>` ดังนี้

```html
<script async src="https://www.googletagmanager.com/gtag/js?id=YOUR_GA_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'YOUR_GA_ID');
</script>
```

---

## ✅ Checklist เปิดใช้งาน

- [ ] เปิดไฟล์ทดสอบในเครื่อง ดูว่าแสดงผลถูกต้อง
- [ ] เพิ่มลิงก์ Discord
- [ ] เพิ่มลิงก์ Google Form แต่ละหน่วย
- [ ] เพิ่มลิงก์ Google Drive ของเอกสาร
- [ ] เปลี่ยนข้อมูลติดต่อ (Email, Line, Tel)
- [ ] อัปโหลดเว็บขึ้น Hosting
- [ ] แชร์ลิงก์ให้นักศึกษา
- [ ] ทดสอบบนมือถือ

---

## 📞 ติดต่อ

- ครูผู้สอน: **นายวีระวัฒน์ ภูสมหมาย**
- Email: wpoosommai@gmail.com
- Tel: 081-266-1861

© 2569 วิทยาลัยเทคนิคศรีสะเกษ

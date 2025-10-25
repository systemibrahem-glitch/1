# دليل النشر - نظام إبراهيم للمحاسبة

## 🌐 النشر على Netlify

### الخطوة 1: إعداد المستودع على GitHub

1. **إنشاء مستودع جديد**
   - اذهب إلى [GitHub](https://github.com)
   - اضغط على "New repository"
   - اسم المستودع: `ibrahim-accounting-system`
   - اجعله عام (Public)

2. **رفع الكود**
```bash
# في مجلد المشروع
git init
git add .
git commit -m "Initial commit: نظام إبراهيم للمحاسبة"
git branch -M main
git remote add origin https://github.com/systemibrahem-glitch/50.git
git push -u origin main
```

### الخطوة 2: إعداد Netlify

1. **تسجيل الدخول إلى Netlify**
   - اذهب إلى [netlify.com](https://netlify.com)
   - سجل الدخول بحساب GitHub

2. **إنشاء موقع جديد**
   - اضغط على "New site from Git"
   - اختر GitHub كمصدر
   - اختر المستودع: `systemibrahem-glitch/50`

3. **إعدادات البناء**
   ```
   Build command: cd client && pnpm install && pnpm build
   Publish directory: client/dist
   ```

4. **متغيرات البيئة**
   - اذهب إلى Site settings > Environment variables
   - أضف المتغيرات التالية:
   ```
   VITE_SUPABASE_URL=your_supabase_url
   VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
   VITE_APP_TITLE=نظام إبراهيم للمحاسبة
   ```

### الخطوة 3: إعداد Supabase

1. **إنشاء مشروع جديد**
   - اذهب إلى [supabase.com](https://supabase.com)
   - اضغط على "New project"
   - اختر اسم المشروع: `ibrahim-accounting`

2. **إعداد قاعدة البيانات**
   - استخدم SQL Editor لإنشاء الجداول
   - أو استخدم Migration files الموجودة في مجلد `drizzle`

3. **إعداد المصادقة**
   - اذهب إلى Authentication > Settings
   - فعّل "Enable email confirmations"
   - أضف Domain الخاص بـ Netlify

### الخطوة 4: اختبار النشر

1. **التحقق من البناء**
   - انتظر حتى يكتمل البناء على Netlify
   - تأكد من عدم وجود أخطاء

2. **اختبار الموقع**
   - افتح الرابط المقدم من Netlify
   - تأكد من عمل جميع الصفحات
   - اختبر تسجيل الدخول

## 🔧 إعدادات إضافية

### إعدادات الأمان
```toml
# في ملف netlify.toml
[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-Content-Type-Options = "nosniff"
    X-XSS-Protection = "1; mode=block"
    Referrer-Policy = "strict-origin-when-cross-origin"
```

### إعدادات إعادة التوجيه
```toml
[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

## 📱 النشر على منصات أخرى

### Vercel
```bash
# تثبيت Vercel CLI
npm i -g vercel

# النشر
vercel --prod
```

### GitHub Pages
```bash
# بناء المشروع
cd client
pnpm build

# رفع مجلد dist إلى gh-pages branch
```

## 🚀 نصائح للنشر الناجح

1. **تحسين الأداء**
   - استخدم lazy loading للمكونات
   - ضغط الصور قبل الرفع
   - فعّل Gzip compression

2. **مراقبة الأخطاء**
   - استخدم Sentry لمراقبة الأخطاء
   - راقب أداء الموقع باستخدام Google Analytics

3. **النسخ الاحتياطي**
   - احتفظ بنسخة احتياطية من قاعدة البيانات
   - استخدم Git tags للإصدارات المهمة

## 🔍 استكشاف الأخطاء

### مشاكل شائعة

1. **خطأ في البناء**
   - تأكد من صحة متغيرات البيئة
   - تحقق من إصدار Node.js (يجب أن يكون 18+)

2. **مشاكل في قاعدة البيانات**
   - تأكد من صحة اتصال Supabase
   - تحقق من إعدادات RLS

3. **مشاكل في المصادقة**
   - تأكد من إعدادات Domain في Supabase
   - تحقق من إعدادات CORS

## 📞 الدعم

إذا واجهت أي مشاكل في النشر، تواصل معنا:
- **البريد الإلكتروني**: systemibrahem@gmail.com
- **الواتساب**: +963 994 054 027

---

**تم إعداد هذا الدليل بعناية لضمان نشر ناجح لنظام إبراهيم للمحاسبة.**
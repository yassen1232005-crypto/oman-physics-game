# تحدّي الفيزياء — دليل إعداد مختصر

## الملفات
- `index.html`, `style.css`, `app.js`: واجهة الموقع.
- `config.js`: بيانات الاتصال العامة.
- `supabase/setup.sql`: جداول ووظائف السيرفر وسياسات الأمان وأسئلة البداية.

## 1) إعداد قاعدة البيانات
في Supabase افتح SQL Editor ثم New query، وانسخ `supabase/setup.sql` كاملًا وشغّله مرة واحدة. الملف لا يحذف الجداول. لو ظهر خطأ، توقف ولا تعاود تشغيله عشوائيًا؛ أرسل نص الخطأ.

## 2) الاتصال بالمشروع
من Supabase Project Settings → API انسخ Project URL والمفتاح العام anon/publishable فقط. ضع القيمتين في `config.js`. لا تستخدم service_role أو secret key ولا كلمة مرور قاعدة البيانات داخل الموقع.

## 3) تسجيل البريد
في Authentication إعدادات URL Configuration، اضبط Site URL ورابط Redirect بعد النشر. إعدادات البريد قد تتطلب تأكيد البريد الإلكتروني.

## 4) Google
من Authentication → Providers فعّل Google. ستحتاج Google Cloud Console لإنشاء OAuth Client ID/Secret، ثم تضيف Callback URL الذي يعرضه Supabase إلى إعدادات Google. لا تشارك Client Secret مع أحد.

## 5) التحديث المباشر
فعّل Realtime لجداول `rooms` و`room_players` من إعدادات Database/Replication حسب واجهة Supabase.

## 6) نشر مجاني
ارفع ملفات المجلد إلى مستودع GitHub، ثم اربط المستودع بخدمة استضافة ثابتة مثل Netlify. بعد النشر أضف رابط الموقع إلى Supabase Redirect URLs وإعدادات Google. حدود الخطط المجانية قابلة للتغيير.

## تنبيه
هذه نسخة أولية تحتاج اختبارًا حقيقيًا على حسابين قبل مشاركتها. Google OAuth لا يعمل حتى إكمال إعداداته. إن كانت بنية الجداول الحالية مختلفة، قد يحتاج SQL إلى تعديل حسب رسالة الخطأ.

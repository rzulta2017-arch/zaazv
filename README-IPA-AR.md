# 📱 تحويل Merge Studio Pro إلى ملف IPA للآيفون (iOS)

هاد الملف (`MergeStudio-iOS-IPA-Project.zip`) فيه كاع الملفات واجدة باش تخرج تطبيق `.ipa` ديالك بطريقتين (سواء عندك Mac أو غير Windows/تليفون):

---

## الطريقة 1: بلا Mac (عن طريق GitHub Actions مجاناً فـ 3 دقائق)
إلا ما عندكش Mac وبغيتي تخرج ملف `MergeStudio-Unsigned.ipa` باش تثبتو بـ **AltStore / Sideloadly / ESign / Scarlet / TrollStore**:
1. فك الضغط على هاد الـ ZIP ولوح الملفات كاملة فـ Repository جديد فـ **GitHub**.
2. سير لـ تبويب **Actions** فـ GitHub، وغادي تلقى Workflow سميتو **Build Unsigned iOS IPA** خدام بوحدو (كيخدم على سيرفر macOS ديال GitHub).
3. ملي يسالي (كياخد تقريباً دقيقتين)، هبط لتحت فـ **Artifacts** وحمّل ملف **`MergeStudio-Unsigned-IPA`** واجد!

---

## الطريقة 2: إلا عندك Mac و Xcode (أو Capacitor)
1. فك الضغط على الملف، وحل Terminal وسط المجلد:
   ```bash
   npm install
   npx cap add ios
   npx cap sync ios
   npx cap open ios
   ```
2. غادي يتحل ليك المشروع فـ **Xcode** واجد، أو تقدر تستعمل ملف `Xcode-Native-Wrapper/ViewController.swift` و `Info.plist` مباشرة فـ مشروع Swift جديد وتجر مجلد `www` لوسط Xcode، ودير **Product -> Archive** باش تخرج الـ `.ipa`.

---

## محتويات المجلد:
* `www/index.html` : اللعبة معدلة بقياس 9:16 (Reels/TikTok) + صفحة الإعدادات معزولة ومخفية + بدون زر التسجيل (Record).
* `www/manifest.json` + `icon-1024.png` : أيقونة التطبيق وإعدادات الشاشة الكاملة.
* `capacitor.config.json` & `package.json` : إعدادات Capacitor iOS.
* `.github/workflows/build-ipa.yml` : سكريبت بناء ملف `.ipa` تلقائياً عبر GitHub.
* `Xcode-Native-Wrapper/` : كود `ViewController.swift` و `Info.plist` جاهز لأصحاب Xcode.

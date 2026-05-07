# Poutine Hub — Deployment Guide

## Files in this folder
| File | Purpose |
|---|---|
| index.html | Customer-facing website + PWA |
| admin.html | Admin dashboard |
| manifest.json | PWA manifest (app install metadata) |
| sw.js | Service worker (offline caching) |
| capacitor.config.json | iOS + Android app config |
| package.json | Capacitor dependencies |

---

## Web Deployment (Netlify) — Already Live
1. Drag this folder to netlify.com
2. Customer site: https://poutinehub.netlify.app/
3. Admin: https://poutinehub.netlify.app/admin.html

---

## Adding Real Photos (Admin Panel)
1. Upload photos to any free host:
   - Cloudinary: cloudinary.com (best quality)
   - ImgBB: imgbb.com (simplest)
   - Google Drive: upload → right-click → Get link → convert to direct URL
     Format: https://drive.google.com/uc?id=FILE_ID
2. In Admin → Menu Manager → Edit any item → paste URL in "Image URL" field
3. For logo: Admin → Settings → Logo URL field

---

## iOS App (App Store) — Requires Mac + $99/year Apple Developer
### Prerequisites
- Mac with Xcode installed
- Apple Developer account ($99/year)
- Node.js installed

### Steps
```bash
# Install dependencies
npm install

# Add iOS platform
npm run cap:add:ios

# Sync web code to native
npm run cap:sync

# Open in Xcode
npm run cap:open:ios

# In Xcode:
# 1. Select your development team
# 2. Update Bundle ID to com.poutinehub.app
# 3. Add app icons (1024x1024 PNG, no transparency)
# 4. Add splash screen
# 5. Product → Archive → Distribute to App Store
```

---

## Android App (Google Play) — Requires $25 one-time fee
### Prerequisites
- Android Studio installed
- Google Play Developer account ($25 one-time)
- Node.js installed

### Steps
```bash
# Install dependencies
npm install

# Add Android platform
npm run cap:add:android

# Sync web code to native
npm run cap:sync

# Open in Android Studio
npm run cap:open:android

# In Android Studio:
# 1. Build → Generate Signed APK/Bundle
# 2. Create keystore (keep this safe — you need it for every update)
# 3. Build Release AAB
# 4. Upload to Google Play Console
```

---

## Free APK (No Google Play) — Android Only
```bash
npm install
npm run cap:add:android
npm run cap:sync
npm run cap:open:android
# Build → Build APK → Share the APK file directly
# Users enable "Install from unknown sources" and install
```

---

## App Icons Needed
- iOS: 1024×1024 PNG (no rounded corners, Apple adds them)
- Android: 512×512 PNG (with safe zone margins)
- Recommend: Use https://appicon.co — upload one 1024×1024 image, get all sizes

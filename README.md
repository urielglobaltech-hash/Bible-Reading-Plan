# Bible Reading Plan

A Flutter Android application wrapping the Bible Reading Plan 2027 daily reading experience.

- **Display name:** Bible Reading Plan
- **Android application ID:** `com.biblereadingplan.app`
- **Launcher icon:** `assets/app_icon.png`
- **Web app:** `assets/www/index.html` (self-contained HTML with both cover images and the complete 365-day schedule)
- **Build pipeline:** Codemagic (`codemagic.yaml`)

## Build with Codemagic
1. Push this project to a GitHub repository.
2. Connect the repository in Codemagic.
3. Select the `bible-reading-plan-android` workflow from `codemagic.yaml`.
4. Start the build.
5. Download `app-release.apk` to install on Android, or `app-release.aab` for Play Console.

The workflow generates the Android platform files, sets the display name and internet permission, generates the launcher icon, and builds the APK and AAB.

## Local Android build
Install Flutter stable and the Android SDK, then run:

```bash
flutter create --platforms=android --org com.biblereadingplan --project-name bible_reading_plan --no-pub .
python3 tool/prepare_android.py
flutter pub get
dart run flutter_launcher_icons
flutter build apk --release
```

## Scripture and offline behaviour
The reading schedule and cover images are bundled in the app. The first time a KJV passage is opened, the app retrieves it from bible-api.com; successfully retrieved passages may be cached by the WebView on that device for later offline access. The complete Bible text is not bundled for fully offline first-time reading.

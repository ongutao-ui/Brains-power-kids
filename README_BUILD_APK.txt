BRAIN POWER KIDS — ANDROID STUDIO PROJECT V6.2.1 (OFFLINE-FIRST)
School: Success Kings and Queens Schools
Application ID: ke.co.successkings.brainpowerkids

OFFLINE OPERATION
- Learner activities, logo and application screens are bundled in app/src/main/assets.
- The Android manifest does not request INTERNET permission.
- No server, account service, network connection or cloud sync is used.
- Teacher registration and login use a teacher-created username and password.
- Learner profiles and scores are saved locally on the same device using WebView local storage.
- Local records are not backed up or automatically transferred to another phone.

IMPORTANT SECURITY LIMITATION
This is a classroom prototype. Teacher passwords are stored in local app storage and are not securely hashed. Use a unique, non-sensitive test password. Do not store sensitive learner information or treat local login as secure identity verification. A secure authentication and school data backend is required for production deployment.

OPTION A — BUILD ON WINDOWS
1. Install Android Studio and Android SDK Platform 35 (Build Tools 35.0.0 or newer compatible 35.x).
2. Install/use JDK 17 (Android Studio's bundled JDK is suitable).
3. Open this project folder (the folder containing settings.gradle) in Android Studio.
4. Allow Gradle sync. The project uses Android Gradle Plugin 8.7.3 and Gradle 8.9.
5. Select Build > Build Bundle(s) / APK(s) > Build APK(s).
6. The debug APK is normally app/build/outputs/apk/debug/app-debug.apk.

If Gradle 8.9 is installed and on PATH, you can instead double-click BUILD_APK_ON_WINDOWS.bat.

OPTION B — HOSTED BUILD (NO LOCAL ANDROID SDK REQUIRED)
1. Create a GitHub repository and upload the contents of this project folder to its main branch.
2. In the repository, open the Actions tab and enable GitHub Actions if prompted.
3. Select “Build Brain Power Kids APK” and choose “Run workflow”. (A push to main/master also starts a build.)
4. When the workflow finishes, open the successful run and download the artifact named “Brain-Power-Kids-debug-APK”.
5. Extract the artifact; it contains app-debug.apk.
The workflow builds an unsigned-by-you Android debug APK that is debug-signed automatically by Android's build tools. It is suitable for testing, not Play Store production release.

SIGNED RELEASE APK
A release APK should be signed with a private keystore controlled by the school. Do not upload or share the keystore or its passwords. Use Android Studio > Build > Generate Signed Bundle / APK > APK. Keep secure backups of the keystore. The hosted workflow intentionally does not create a school-owned release signing key.

DEVICE TESTING
After obtaining the APK, copy it to an Android phone, allow installation from the file manager when prompted, install, then test: app launch, offline activities, teacher username login, learner records and score persistence. This source package has not yet been compiled, installed or physically tested in this environment.

PROJECT CONFIGURATION
- Android Gradle Plugin 8.7.3; Kotlin 2.0.21; compile/target SDK 35; minimum SDK 23.
- Android WebView loads the bundled local index.html.
- No Gradle wrapper is included; the GitHub workflow provisions Gradle 8.9, and Android Studio can manage Gradle locally.

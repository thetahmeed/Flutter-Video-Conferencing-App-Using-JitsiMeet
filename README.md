# Flutter Video Calling App With Jitsi Meet
### A video conferencing platform that can be used through a computer desktop or android app

- Screenshots
  - [Web](https://github.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet#screenshots-web-)
  - [Android](https://github.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet#screenshots-android-)
  - [iOS](https://github.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet#screenshots-iOS-)
- [Package used](https://github.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet#package-used)
- [Do before production](https://github.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet#do-before-production-)
  - [Anroid](https://github.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet#android)
  - [iOS](https://github.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet#ios)
  - [Web](https://github.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet#ios)
- [Pros](https://github.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet#pros)
- [Cons](https://github.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet#cons)

## Screenshots (Web) : 
![Web-demo](https://raw.githubusercontent.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet/main/web-demo.png)

## Screenshots (Android) : 
<img src="https://raw.githubusercontent.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet/main/android-demo%20(0).jpg" height="400">   <img src="https://raw.githubusercontent.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet/main/android-demo%20(2).jpg" height="400">   <img src="https://raw.githubusercontent.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet/main/android-demo%20(1).jpg" height="400">   <img src="https://raw.githubusercontent.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet/main/android-demo%20(3).jpg" height="400">   <img src="https://raw.githubusercontent.com/thetahmeed/Flutter-Video-Conferencing-App-Using-JitsiMeet/main/android-demo%20(4).jpg" height="400">

## Screenshots (iOS) : 
:slightly_smiling_face::slightly_smiling_face::slightly_smiling_face:

## Package used:
[Jitsi Meet 4.0.0](https://pub.dev/packages/jitsi_meet/example)

## Do before production :
### Android
Ensure the following permission is present in your Android Manifest file, located in `<project root>/android/app/src/main/AndroidManifest.xml`
```
<uses-feature android:name="android.hardware.camera" />
<uses-feature android:name="android.hardware.camera.autofocus" />
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.RECORD_AUDIO" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.CHANGE_NETWORK_STATE" />
<uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS" />
```
Make sure you added `Proguard`.
Learn [How](https://articles.wesionary.team/use-of-proguard-in-the-flutter-app-289cd7b31a18) </br>
Make sure your minimum sdk version to `24` in `android/app/build.gradle` and target sdk version `28`
```
defaultConfig {
    applicationId "com.tahmeed.vc"
    minSdkVersion 24 
    targetSdkVersion 28
    versionCode flutterVersionCode.toInteger()
    versionName flutterVersionName
}
```

### iOS
Ensure in your `Podfile` you have an entry like below declaring platform of 11.0 or above and disable BITCODE
```
platform :ios, '11.0'

...


post_install do |installer|
  installer.pods_project.targets.each do |target|
     flutter_additional_ios_build_settings(target)
       # Required by jitsi
     target.build_configurations.each do |config|
     config.build_settings['ENABLE_BITCODE'] = 'NO'
         config.build_settings["EXCLUDED_ARCHS[sdk=iphonesimulator*]"] = "arm64"
    end
 end
end
```
Add NSCameraUsageDescription and NSMicrophoneUsageDescription to your `Info.plist`
```
<key>NSCameraUsageDescription</key>
<string>$(PRODUCT_NAME) MyApp needs access to your camera for meetings.</string>
<key>NSMicrophoneUsageDescription</key>
<string>$(PRODUCT_NAME) MyApp needs access to your microphone for meetings.</string>
```
### Web
Make sure you implemented include Jitsi Js library in the `index.html` of web section
```
<script src="https://meet.jit.si/external_api.js" type="application/javascript"></script>
```

### Pros
Everything is readymade :drooling_face:
### Cons
Everything is readymade :unamused:

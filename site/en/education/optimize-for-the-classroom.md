---
title: Optimize Your App for the Classroom
metadesc: Learn the best practices to get your application installed in classrooms.
date: 2022-06-15
weight: -3
tags:
  - web
---

When targeting your application for a classroom environment, there are a number of steps that can be taken to make your application accessible to students and more likely to be adopted by a school district as a preferred application. These are the most common optimizations we recommend.

## Streamline identity and provisioning

Students are already signed into Chrome OS with Google accounts which helps enable them to quickly log in to sites. You can leverage that existing user profile information by prompting a user to use it to sign into your site with the [Sign in with Google API](https://developers.google.com/identity/gsi/web). Teachers have limited class time. Having a unified login experience via single sign on removes their burden of needing to remember passwords and usernames for each student and allows students to get up and running with your application faster.

## Add support for multiple cameras

Chromebooks can have more than one camera. Like a cell phone, they can have both a regular webcam and a world facing camera. To help users switch between them, add the ability to quickly cycle through the available cameras. This can be done using <code>[navigator.mediaDevices.enumerateDevices](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/enumerateDevices)</code> to check if there is more than one media input on the device. If there is, show a button or dropdown that allows users to switch between them. If you are developing an Android app, be sure to use <code><span style="text-decoration:underline;">android.hardware.camera.any</span></code> instead of <code>android.hardware.camera</code> in your <code>AndroidManifest.xml </code>file and add the <code>required=false<strong> </strong></code>tag to make sure your app is available on devices with only front facing cameras.

## Ensure touch and stylus inputs work

Many Chromebooks have the capability to go from a traditional laptop form factor to a tablet form factor and back again seamlessly. This requires that web developers targeting education users switch from the traditional event handlers like mouse up and touch start to [pointer events](https://developer.mozilla.org/en-US/docs/Web/API/Pointer_events). Pointer events are events that are designed for a multitude of pointing devices (stylus, finger, and mouse) and can help transition your users as they [move between different form factors and input methods](/{{locale.code}}/web/desktop-progressive-web-apps#make-it-touchable).

## Support large screen Android devices

ChromeOS devices are not limited to web applications; many devices have support for Android as well. When optimizing your application to work on ChromeOS, it's important to understand that users interact with laptops and phones differently. Many Android apps should consider preparing for [windowed mode](/{{locale.code}}/android/window-management) with a [responsive layout](/{{locale.code}}/android/optimizing#make-your-layouts-responsive) since users may interact with your application not only in fullscreen mode, but also side by side with other applications. Additionally, enabling hardware keyboards with shortcuts enables devices without touchscreens to adopt your app, opening up a range of additional devices available to your application. Small updates to the layout and overall look and feel may make your application feel that it was designed with ChromeOS in mind and give it a better experience for your users as well. We have a large document of [optimization guidelines](/{{locale.code}}/android/optimizing) that can help create great experiences for your users.

## Consider compliance needs

There are many regulatory compliance requirements that vary from school district to school district helping ensure student safety online. Make sure your application meets those requirements and works well with applications that help enforce those requirements. While not a comprehensive list, these suggestions can help you meet education compliance requirements.

### Use Google Drive for storage

Storing your application's user data in the users' Google Drive is largely preferred in an education environment. This is because there are not separate terms of service that need to be approved by school districts for education users. If you’re building for the US market, using Google Drive for storage, provided it’s approved by the school district, can be used in compliance with [FERPA](https://cloud.google.com/security/compliance/ferpa) and [COPPA](https://cloud.google.com/security/compliance/coppa).

### Improve WebView compatibility

There are a lot of content filtering solutions that are implemented within Chrome browser extensions on Chrome OS. These solutions are not able to capture embedded WebViews within Chrome apps or Android apps. [Improve how your app handles WebViews](/{{locale.code}}/education/improving-webview-compatibility) to make sure they work with content filtering solutions, and to help ensure FERPA and COPPA compliance.

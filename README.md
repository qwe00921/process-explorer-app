What is it?
===========

Process Explorer enables you to view the processes running on your device and,
in the case of Dalvik-based apps, their corresponding logcat output without
cluttering your device's main display. Instead, Process Explorer runs a
node.js-based process in the background that listens to a socket connection. By
pointing your computer's web browser to that socket on the device -- say using
"adb forward" -- you can see all the processes running in real-time along with
CPU and memory usage graphs. Basic controls allow you to control filtering and
refresh rates.

Process Explorer is also available on [Google Play](https://play.google.com/store/apps/details?id=com.opersys.processexplorer).

Installation
============

Required assets
---------------

In order to function, this project needs the following assets found in the
[process-explorer-web](https://github.com/opersys/process-explorer-web) project:

* app/src/main/assets/process-explorer.zip
* app/src/main/assets/process-explorer.zip.md5sum

This application won't function properly without these assets.

Building an APK
---------------

This project uses `gradle` in order to build and package this application.

Simply run the following in the `process-explorer-app` root directory:

> ./gradlew build

And you will find the build artefacts in `app/build/outputs/apk/`.

Installing
----------

Use `adb` to install the application in Android:

> adb install app/build/outputs/apk/app-debug.apk

>>>>>>> origin/master
Logcat fix
----------

The `READ_LOGS` permission is not automatically granted to applications
even when the application requires it. It needs to be manually granted to the
application right in the shell using the following command:

> adb shell pm grant com.opersys.processexplorer android.permission.READ_LOGS

Using Process Explorer
======================

Once it has been installed on your device, you should simply probably forward
TCP/3000 to be able to browse the nodejs app.

> adb forward tcp:3000 tcp:3000

Then simply browse to [http://localhost:3000](http://localhost:3000) !

Licensing
=========

See the `NOTICE` file.

Contributors
============

* François-Denis Gonthier <francois-denis.gonthier@opersys.com> -- main developer and maintaier
* Karim Yaghmour <karim.yaghmour@opersys.com> -- ideas and other forms of entertainment
* Benjamin Vanheuverzwijn <benjamin.vanheuverzwijn@opersys.com> -- contributor

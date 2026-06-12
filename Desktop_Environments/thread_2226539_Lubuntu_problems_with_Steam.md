---
title: "Lubuntu problems with Steam"
date: 2014-05-27
forum: Desktop Environments
---

### Post by Blix775 on 2014-05-27
Hi! I just installed Lubuntu 14.04 on my desktop which has a Radeon HD 6790 graphics card and 4GB of ram and it is running the desktop GUI quite slow. I installed the Ati Drivers from software and updates and ever since, when I minimize a window, it does this slow removal of the image from the top to the bottom, little by little. Also, steam just will not run. I downloaded it from the website and ran the .deb like I normally did in previous versions. I tried running it from the console with the command steam and this is the output: 

> Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140527210846_1.dmp
/home/blix/.local/share/Steam/steam.sh: line 755:  3408 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat ‘/home/blix/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/blix/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-a5066ad9-2010-498a-a6f5-5f6b72140527
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/blix/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140527210848_1.dmp
/home/blix/.local/share/Steam/steam.sh: line 755:  3534 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-6beb8c13-9712-480f-b23a-c8f532140527



I wonder if there's a problem with the graphics drivers or something. Any help will be appreciated.

---

### Post by Blix775 on 2014-05-27
I just realized the driver is having problems with youtube videos. Playing a 720p video in full screen will make the video play at like 1 frame every 3 seconds, really.

---


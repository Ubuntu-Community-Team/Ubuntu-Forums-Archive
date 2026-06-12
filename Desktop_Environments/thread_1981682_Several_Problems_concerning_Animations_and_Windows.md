---
title: "Several Problems concerning Animations and Windows"
date: 2012-05-17
forum: Desktop Environments
---

### Post by buggy12 on 2012-05-17
Hi, when i installed ubuntu 12.04 for the first time, i could grab a window, move it to a side and it automatically filled half of the screen. Furthermore i had nice animations when i changend from desktop 1 to 2 and so on. and i coul resize the icons in the sidebar without having to install any further programs. 
now i reinstalled ubuntu and none of the mentioned things work.

does anybody know this problem?

tahnke

---

### Post by ckop64 on 2012-05-17
> **buggy12 said:**
> Hi, when i installed ubuntu 12.04 for the first time, i could grab a window, move it to a side and it automatically filled half of the screen. Furthermore i had nice animations when i changend from desktop 1 to 2 and so on. and i coul resize the icons in the sidebar without having to install any further programs. 
now i reinstalled ubuntu and none of the mentioned things work.

does anybody know this problem?

tahnke

Are you using Unity3D? Didn't you forget to install your drivers?

---

### Post by buggy12 on 2012-05-17
hmmm i didnt install any drivers, since im a newbiee.. how kann i install them?

---

### Post by buggy12 on 2012-05-17
anyone a hint?

---

### Post by Frogs Hair on 2012-05-17
To find out if unity 3D will run on your system paste the following command in your terminal and press enter.```
/usr/lib/nux/unity_support_test -p
``` 

If you need or want a graphics driver open additional drivers from dash and the jockey will search for drivers. Select the recommend driver if the option is presented and select activate.

---

### Post by buggy12 on 2012-05-18
alright. when i try to install the drivers, i get an error. here's the jockey.log file:
[SIZE="1"]> 
2012-05-18 13:41:08,478 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x20a9680> about HardwareID('modalias', 'input:b0003v04D9p0499e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-05-18 13:41:08,478 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x20a9680> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,BF,CA,CB,E3,ED,EE,F0,ram4,lsfw')
2012-05-18 13:41:08,478 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x20a9680> about HardwareID('modalias', 'pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc02sc80i00')
2012-05-18 13:41:08,478 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x20a9680> about HardwareID('modalias', 'wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997')
2012-05-18 13:41:08,478 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x20a9680> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-05-18 13:41:08,536 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-18 13:41:08,536 DEBUG: fglrx_updates is not the alternative in use
2012-05-18 13:41:08,617 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-18 13:41:08,617 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-18 13:41:08,808 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-18 13:41:08,809 DEBUG: fglrx_updates is not the alternative in use
2012-05-18 13:41:08,856 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-18 13:41:08,857 DEBUG: fglrx_updates is not the alternative in use
2012-05-18 13:41:08,889 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-18 13:41:08,890 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-18 13:41:27,270 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-18 13:41:27,270 DEBUG: fglrx_updates is not the alternative in use
2012-05-18 13:41:29,980 DEBUG: Installing package: fglrx-updates
2012-05-18 13:41:32,342 DEBUG: install progress dpkg-exec 0.000000
2012-05-18 13:41:32,443 DEBUG: dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

2012-05-18 13:41:32,443 ERROR: Package failed to install:
dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

2012-05-18 13:41:32,588 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-18 13:41:32,588 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-05-18 13:41:32,588 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-05-18 13:42:08,973 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-18 13:42:08,973 DEBUG: fglrx_updates is not the alternative in use[/SIZE]

---

### Post by buggy12 on 2012-05-19
Ok here is something strange.
I uninstalled ubuntu and reinstalled it. Everything worked fine, all the effects were there again. 
However, ubuntu adviced me to update several things, and so i did. To complete the update i had to reboot ubuntu and voila, all the effects are gone again >.<

what the .. went wrong?

---

### Post by buggy12 on 2012-05-20
anyone an idea?

---

### Post by buggy12 on 2012-05-20
please help. this really sucks this problem

---

### Post by buggy12 on 2012-05-20
ok, im now pretty sure that the problem is unity3d
it wont work since my driver ati/amd fglrx seems to make trouble. does anyone know this problem?

---

### Post by nll on 2012-05-20
If I'm not mistaken, the ATI proprietary video drivers don't play very nice with Unity. When you reinstalled and updated your system, did you manage to install the proprietary drivers for your ATI card too? If you did, you could exclude (or confirm) them as the source of your problem by removing them (I don't know how to do that, but try searching in the forums) or reinstalling Ubuntu once again and then updating but sticking to the open source graphics drivers.

---

### Post by goaliedude3919 on 2012-05-23
You seem to be having the same problem that I had. I don't know what  computer you're using, but the CPU in my laptop has a built in GPU that  messing things up and putting my session into Unity2D as opposed to  Unity3D. What I had to do was I had to disable that built in GPU.

The way to do that is through the BIOS. When you boot up your computer, you should see somewhere either on the bottom of the screen or the top right that tells you to hit usually either F2, F8, F10, or F12. Hit the appropriate key and the BIOS should open. There should be an option for Optimus. This is the built in GPU. Simply click on the option to disable Optimus. There's actually even a description there that says Optimus isn't meant for OS's other than Windows.

Hopefully this is what is causing your problem and you can now enjoy the full awesomeness of Ubuntu :)

---


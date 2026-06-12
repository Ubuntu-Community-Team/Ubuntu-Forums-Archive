---
title: "How do you install a patch?"
date: 2009-01-14
forum: General Help
---

### Post by moosehadley on 2009-01-14
I have a patch here for a GPS program called QLandkarte.

Heres the patch: 

```
Only in QLandkarte_0.7.3.new: Makefile
Only in QLandkarte_0.7.3.new: bin
Only in QLandkarte_0.7.3.new: common
Only in QLandkarte_0.7.3.new: config.h
Only in QLandkarte_0.7.3.new: config.log
Only in QLandkarte_0.7.3.new: config.status
Only in QLandkarte_0.7.3.new/src: .tmp
Only in QLandkarte_0.7.3.new/src: Makefile
Only in QLandkarte_0.7.3.new/src/device: .tmp
diff -ru QLandkarte_0.7.3/src/device/CSerial.cpp 
QLandkarte_0.7.3.new/src/device/CSerial.cpp
--- QLandkarte_0.7.3/src/device/CSerial.cpp     2008-06-26 11:53:34.000000000 
-0700
+++ QLandkarte_0.7.3.new/src/device/CSerial.cpp 2008-07-24 18:32:11.000000000 
-0700
@@ -307,7 +307,7 @@
      }

      //wait 100 millisecs here (like GPSexplorer does)
-    usleep(100000);
+    usleep(500000);

      if (tcgetattr(port_fd, &tty) < 0) {
          // throw "Failed to get parameters for serial port";
Only in QLandkarte_0.7.3.new/src/device/Emap: .tmp
Only in QLandkarte_0.7.3.new/src/device/Emap: Makefile
Only in QLandkarte_0.7.3.new/src/device/EtrexH/.tmp: CDevice.o
Only in QLandkarte_0.7.3.new/src/device/EtrexH/.tmp: EHSerial.o
Only in QLandkarte_0.7.3.new/src/device/EtrexH/.tmp: loader.o
Only in QLandkarte_0.7.3.new/src/device/EtrexH: Makefile
Only in QLandkarte_0.7.3.new/src/device/EtrexLegend: .tmp
diff -ru QLandkarte_0.7.3/src/device/EtrexLegend/CDevice.cpp 
QLandkarte_0.7.3.new/src/device/EtrexLegend/CDevice.cpp
--- QLandkarte_0.7.3/src/device/EtrexLegend/CDevice.cpp 2008-04-13 
22:58:31.000000000 -0700
+++ QLandkarte_0.7.3.new/src/device/EtrexLegend/CDevice.cpp     2008-07-24 
18:35:30.000000000 -0700
@@ -171,6 +171,8 @@
      *(uint16_t*)command.payload = 0x000A;
      serial->write(command);

+    sleep(10);
+
      ready= 0;
      while(!ready && serial->read(response) > 0) {
          if(response.id == 74) {
Only in QLandkarte_0.7.3.new/src/device/EtrexLegend: Makefile
Only in QLandkarte_0.7.3.new/src/device/EtrexLegendC: .tmp
Only in QLandkarte_0.7.3.new/src/device/EtrexLegendC: Makefile
Only in QLandkarte_0.7.3.new/src/device/EtrexLegendCx: .tmp
Only in QLandkarte_0.7.3.new/src/device/EtrexLegendCx: Makefile
Only in QLandkarte_0.7.3.new/src/device/GPSMap60CSx: .tmp
Only in QLandkarte_0.7.3.new/src/device/GPSMap60CSx: Makefile
Only in QLandkarte_0.7.3.new/src/device/GPSMap76: .tmp
Only in QLandkarte_0.7.3.new/src/device/GPSMap76: Makefile
Only in QLandkarte_0.7.3.new/src/device: Makefile
Only in QLandkarte_0.7.3.new/src/device/NMEA/.tmp: CDevice.o
Only in QLandkarte_0.7.3.new/src/device/NMEA/.tmp: loader.o
Only in QLandkarte_0.7.3.new/src/device/NMEA: Makefile
Only in QLandkarte_0.7.3.new/src/device/NMEATcp/.tmp: CDevice.o
Only in QLandkarte_0.7.3.new/src/device/NMEATcp/.tmp: loader.o
Only in QLandkarte_0.7.3.new/src/device/NMEATcp: Makefile
Only in QLandkarte_0.7.3.new/src/device: libgarmin.a
Only in QLandkarte_0.7.3.new/src/device/whatGarmin: .tmp
Only in QLandkarte_0.7.3.new/src/device/whatGarmin: Makefile
Only in QLandkarte_0.7.3.new/src/device/whatGarminSerial: .tmp
Only in QLandkarte_0.7.3.new/src/device/whatGarminSerial: Makefile
Only in QLandkarte_0.7.3.new/src: qrc_binincludes.cpp
Only in QLandkarte_0.7.3.new/src: ui_ICopyright.h
Only in QLandkarte_0.7.3.new/src: ui_ICopyrightMaps.h
Only in QLandkarte_0.7.3.new/src: ui_IDetailDetail.h
Only in QLandkarte_0.7.3.new/src: ui_IDetailStatus.h
Only in QLandkarte_0.7.3.new/src: ui_IDlgConfig.h
Only in QLandkarte_0.7.3.new/src: ui_IDlgCustomIcons.h
Only in QLandkarte_0.7.3.new/src: ui_IDlgDeleteWpt.h
Only in QLandkarte_0.7.3.new/src: ui_IDlgDevice.h
Only in QLandkarte_0.7.3.new/src: ui_IDlgDeviceNag.h
Only in QLandkarte_0.7.3.new/src: ui_IDlgEditRoute.h
Only in QLandkarte_0.7.3.new/src: ui_IDlgScreenshot.h
Only in QLandkarte_0.7.3.new/src: ui_IDlgSetupWpt.h
Only in QLandkarte_0.7.3.new/src: ui_IToolViewDist.h
Only in QLandkarte_0.7.3.new/src: ui_IToolViewGoogle.h
Only in QLandkarte_0.7.3.new/src: ui_IToolViewLog.h
Only in QLandkarte_0.7.3.new/src: ui_IToolViewMap.h
Only in QLandkarte_0.7.3.new/src: ui_IToolViewRoute.h
Only in QLandkarte_0.7.3.new/src: ui_IToolViewTrack.h
Only in QLandkarte_0.7.3.new/src: ui_IToolViewTrackInfo.h
Only in QLandkarte_0.7.3.new/src: ui_IToolViewWpt.h

```





What am I supposed to do with it?

---

### Post by adam.ec on 2009-01-14
This is weird because I though QLandKarte was for Linux but that patch appears to have something to do with Windows software (I thought .cpp was a Borland extension).

What is this patch supposed to do? Can you not just down the latest version of QLandKarte from the website. Let me know what the patch is for and I'll see if I can find a solution for it.

---

### Post by Titan8990 on 2009-01-14
.cpp stands for C plus plus. C++ is multi-platform and can exist on all OSes.


I personally don't know how to do what you are trying to do but I can point you in the correct direction:



man patch



Also, not certain but I think you usually have to patch prior to compiling.

---

### Post by moosehadley on 2009-01-14
When you upload a map to the GPS, QLandkarte says that there was an error, and the screen on the GPS unit is left saying "Transfering data".

This patch is supposed to correct that.
The GPS unit connects over serial.




Edit: Heres where I got the patch from: [http://www.mail-archive.com/qlandkarte-users@lists.sourceforge.net/msg00132.html](http://www.mail-archive.com/qlandkarte-users@lists.sourceforge.net/msg00132.html)


The error is listed there.

---

### Post by Titan8990 on 2009-01-14
Was there no documentation that came with the patch???

---

### Post by moosehadley on 2009-01-14
None at all

---

### Post by Titan8990 on 2009-01-14
Where did you get it?

---

### Post by moosehadley on 2009-01-14
See my edit on the first post. theres a link

---

### Post by Titan8990 on 2009-01-14
Still don't know exactly the command you will use for patching but I can tell you that you have to remove that program from synaptic and use that patch prior to compiling the program from source.

---

### Post by heindsight on 2009-01-14
> **Titan8990 said:**
> Still don't know exactly the command you will use for patching but I can tell you that you have to remove that program from synaptic and use that patch prior to compiling the program from source.

Yes, if you want to apply the patch, you'll have to download and extract the source code for the program, then apply the patch using the patch command (have a look at the man page to see how) and then compile and install the program.

EDIT: I can't remember whether patch is installed by default. if it's not, just do
```
sudo aptitude install patch
```

---

### Post by phenest on 2009-02-03
The patch you have needs to be put into a .diff file. Use a text editor and save as patch.diff. Then use patch to apply it. First you need the source code of the app you want to patch. Place the folder with the source code in and the .diff file in a new folder and apply the patch using
```
patch -p1 < patch.diff
```
Then you need to compile the patched source code, et voila!

---


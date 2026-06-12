---
title: "Problems Starting Programs"
date: 2009-01-28
forum: General Help
---

### Post by JadenRosen on 2009-01-28
Hi,

I am currently using a computer with 392 RAM, and a 900Mhz Processor. My current release is Intrepid Ibex. But before I upgraded I had the same troubles with Hardy Heron.

When I try to open any kind of large program, for example Google Earth, it starts, but then black lines run all across the screen and then it quits.

Any help would really help because I really need Google Earth...

Thanks!

---

### Post by mb_webguy on 2009-01-28
Start one of these programs from the terminal and see what error messages you get.

---

### Post by JadenRosen on 2009-01-29
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x1e8) [0x8057fb4]
  ./googleearth-bin [0x8058399]
  [0xb7f55400]
  ./libbase.so(_ZN5earth8SpinLock4lockEj+0x22) [0xb7ef53fc]
  ./libbase.so(_ZN5earth9LockGuardC1ERNS_8SpinLockE+0x1f) [0xb7edb27f]
  ./libnet.so(_ZN5earth3net18CurlHttpConnection13removeRequestEPNS0_15CurlHttpRequestE+0x25) [0xb7a7845b]
  ./libnet.so(_ZN5earth3net15CurlHttpRequest4stopEv+0x20) [0xb7a784aa]
  ./libnet.so(_ZN5earth3net15CurlHttpRequestD0Ev+0x25) [0xb7a784d7]
  ./libnet.so(_ZN5earth3net11HttpRequest5unrefEv+0x35) [0xb7a70701]
  ./libnet.so(_ZN5earth6RefPtrINS_3net11HttpRequestEED1Ev+0x1e) [0xb7a679c2]
  ./libnet.so(_ZN5earth3net14NetworkRequestD0Ev+0x28) [0xb7a68a70]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xb7ed04fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xb7ef71d5]
  ./libnet.so(_ZN5earth3net7FetcherD0Ev+0x42) [0xb7a6c332]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xb7ed04fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xb7ef71d5]
  ./libwmsbase.so(_ZN5earth6RefPtrINS_3net7FetcherEEaSEPS2_+0x27) [0xb7acc055]
  /opt/google-earth/libevll.so(_ZN5earth4evll7Texture12ProcessWorkQEd+0xec) [0xb23438e6]
  /opt/google-earth/libevll.so(_ZN5earth4evll7Texture8endFrameEd+0x1a) [0xb2351c60]
  /opt/google-earth/libevll.so(_ZN5earth4evll13VisualContext8endFrameEv+0x148) [0xb234fa94]
  /opt/google-earth/libevll.so(_ZN5earth4evll13VisualContext4drawEbb+0xb2) [0xb23519f8]
  /opt/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl4drawEv+0xa1) [0xb230bb51]
  ./librender.so(_ZN12RenderWidget10paintEventEP11QPaintEvent+0x24) [0xb62697d0]
  ./librender.so(_ZN5earth6render11RenderTimer4fireEv+0x14) [0xb625660c]
  ./libbase.so(_ZN5earth5Timer10timerEventEP11QTimerEvent+0x31) [0xb7ed09bb]
  ./libqt-mt.so.3(_ZN7QObject5eventEP6QEvent+0x82) [0xb6d45fc2]
  ./libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xb6cda9a1]
  ./libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xef) [0xb6cdb4af]
  ./libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x1ed) [0xb6cce43d]
  ./libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x57b) [0xb6c8024b]
  ./libqt-mt.so.3(_ZN10QEventLoop13processEventsEji+0x5a) [0xb6cf45ea]
  ./libqt-mt.so.3(_ZN12QApplication13processEventsEi+0x2c) [0xb6cda33c]
  ./libqt-mt.so.3(_ZN12QApplication13processEventsEv+0x26) [0xb6cda376]
  /opt/google-earth/liblayer.so(_ZN5earth5layer11LayerWindow12onFirstEarthERKNS_4evll11UpdateEventE+0x8e) [0xafd0a1ea]
  /opt/google-earth/libevll.so(_ZN5earth7EmitterINS_4evll14UpdateObserverENS1_11UpdateEventENS_19EmitterDefaultTraitIS2_S3_EEE8doNotifyEMS2_FvRKS3_ES8_+0xa7) [0xb2314ed3]
  /opt/google-earth/libevll.so(_ZN5earth7EmitterINS_4evll14UpdateObserverENS1_11UpdateEventENS_19EmitterDefaultTraitIS2_S3_EEE6notifyEMS2_FvRKS3_ES8_b+0x3e) [0xb2314f58]
  /opt/google-earth/libevll.so [0xb230e31a]
  ./libbase.so(_ZN5earth5Timer10timerEventEP11QTimerEvent+0x31) [0xb7ed09bb]
  ./libqt-mt.so.3(_ZN7QObject5eventEP6QEvent+0x82) [0xb6d45fc2]
  ./libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xb6cda9a1]
  ./libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xef) [0xb6cdb4af]
  ./libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x1ed) [0xb6cce43d]
  ./libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x57b) [0xb6c8024b]
  ./libqt-mt.so.3(_ZN10QEventLoop9enterLoopEv+0xa9) [0xb6cf44e9]
  ./libqt-mt.so.3(_ZN10QEventLoop4execEv+0x26) [0xb6cf43e6]
  ./libqt-mt.so.3(_ZN12QApplication4execEv+0x1f) [0xb6cda39f]
  ./libgoogleearth.so(_ZN5earth6client11Application3runEv+0x24f) [0xb7679821]
  ./googleearth-bin(main+0x11f) [0x8058817]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb6005685]
  ./googleearth-bin(__gxx_personality_v0+0x75) [0x8057e41]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/jaden/.googleearth/crashlogs/crashlog-F1115AA9.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

This is what it says...

It does this with every program even SuperTux! I don't know why but it's like the lines are what make up the image, they are just assembled wrong.

---

### Post by saranam on 2009-01-29
My guess is that you don't have a large enough swap file, so it fails because of insufficient memory.  Unlike Windows, Ubuntu will not automatically enlarge your swap (page) file when necessary.  In fact, the only way I know how to enlarge it is to reinstall ubuntu with the alternate ed, so you can manually select  the size of your swap file.  I would make it at least 768 to 1024MB.  Good luck!

---


---
title: "google earth crash after starting"
date: 2009-03-28
forum: General Help
---

### Post by El Viejo Lobo on 2009-03-28
I downloaded from [http://earth.google.com/intl/es/](http://earth.google.com/intl/es/) and installed using  "./GoogleEarthLinux.bin / GoogleEarthLinux.bin Google Earth" 
It is carashing right after starting.
I am installing GE on Ubuntu 9.04  clean install, for the moment 9.04 is OK except that G.E is giving more problem then ever.

---

### Post by jmszr on 2009-03-28
El Viejo Lobo,

              This might help you, at the end of the post there is a fix for the crash.:[http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)

---

### Post by El Viejo Lobo on 2009-03-30
I made it with googleearth 5 it did not crash  - but it is so slooowwww on my HP pavilion dv5000 that I went back to GE 4.2 that now is crashing after starting. 
I started from Terminal and here is the output of it.
I hope that there is some workaround or fix for this.



lobo@lobo-laptop:~$ googleearth
get fences failed: -1
param: 6, val: 0
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
Google Earth has caught signal 11.

Stacktrace from glibc:
  /usr/lib/googleearth/googleearth-bin(__gxx_personality_v0+0x1e8) [0x8057fb4]
  /usr/lib/googleearth/googleearth-bin [0x8058399]
  [0xb7f50400]


lobo@lobo-laptop:~$ googleearth
get fences failed: -1
param: 6, val: 0
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
Google Earth has caught signal 11.

Stacktrace from glibc:
  /usr/lib/googleearth/googleearth-bin(__gxx_personality_v0+0x1e8) [0x8057fb4]
  /usr/lib/googleearth/googleearth-bin [0x8058399]
  [0xb7f5c400]
  ./libbase.so(_ZN5earth8SpinLock4lockEj+0x22) [0xb7f163fc]
  ./libbase.so(_ZN5earth9LockGuardC1ERNS_8SpinLockE+0x1f) [0xb7efc27f]
  ./libnet.so(_ZN5earth3net18CurlHttpConnection13removeRequestEPNS0_15CurlHttpRequestE+0x25) [0xb7a9945b]
  ./libnet.so(_ZN5earth3net15CurlHttpRequest4stopEv+0x20) [0xb7a994aa]
  ./libnet.so(_ZN5earth3net15CurlHttpRequestD0Ev+0x25) [0xb7a994d7]
  ./libnet.so(_ZN5earth3net11HttpRequest5unrefEv+0x35) [0xb7a91701]
  ./libnet.so(_ZN5earth6RefPtrINS_3net11HttpRequestEED1Ev+0x1e) [0xb7a889c2]
  ./libnet.so(_ZN5earth3net14NetworkRequestD0Ev+0x28) [0xb7a89a70]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xb7ef14fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xb7f181d5]
  ./libnet.so(_ZN5earth3net7FetcherD0Ev+0x42) [0xb7a8d332]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xb7ef14fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xb7f181d5]
  ./libwmsbase.so(_ZN5earth6RefPtrINS_3net7FetcherEEaSEPS2_+0x27) [0xb7aed055]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll18NetworkLinkFetcher9fetchDoneEv+0x890) [0xb2297486]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll18NetworkLinkFetcher12ProcessWorkQEd+0x38) [0xb229756a]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll18GeobaseContextImpl8endFrameEd+0x1a) [0xb229760c]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll13VisualContext8endFrameEv+0x19b) [0xb2394ae7]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll13VisualContext4drawEbb+0xb2) [0xb23969f8]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll17RenderContextImpl4drawEv+0xa1) [0xb2350b51]
  ./librender.so(_ZN12RenderWidget10paintEventEP11QPaintEvent+0x24) [0xb628a7d0]
  ./librender.so(_ZN5earth6render11RenderTimer4fireEv+0x14) [0xb627760c]
  ./libbase.so(_ZN5earth5Timer10timerEventEP11QTimerEvent+0x31) [0xb7ef19bb]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN7QObject5eventEP6QEvent+0x82) [0xb6d65fc2]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xb6cfa9a1]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xef) [0xb6cfb4af]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x1ed) [0xb6cee43d]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x57b) [0xb6ca024b]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop13processEventsEji+0x5a) [0xb6d145ea]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication13processEventsEi+0x2c) [0xb6cfa33c]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication13processEventsEv+0x26) [0xb6cfa376]
  /usr/lib/googleearth/liblayer.so(_ZN5earth5layer11LayerWindow12onFirstEarthERKNS_4evll11UpdateEventE+0x8e) [0xafd4f1ea]
  /usr/lib/googleearth/libevll.so(_ZN5earth7EmitterINS_4evll14UpdateObserverENS1_11UpdateEventENS_19EmitterDefaultTraitIS2_S3_EEE8doNotifyEMS2_FvRKS3_ES8_+0xa7) [0xb2359ed3]
  /usr/lib/googleearth/libevll.so(_ZN5earth7EmitterINS_4evll14UpdateObserverENS1_11UpdateEventENS_19EmitterDefaultTraitIS2_S3_EEE6notifyEMS2_FvRKS3_ES8_b+0x3e) [0xb2359f58]
  /usr/lib/googleearth/libevll.so [0xb235331a]
  ./libbase.so(_ZN5earth5Timer10timerEventEP11QTimerEvent+0x31) [0xb7ef19bb]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN7QObject5eventEP6QEvent+0x82) [0xb6d65fc2]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xb6cfa9a1]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xef) [0xb6cfb4af]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x1ed) [0xb6cee43d]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x57b) [0xb6ca024b]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop9enterLoopEv+0xc3) [0xb6d14503]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop4execEv+0x26) [0xb6d143e6]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication4execEv+0x1f) [0xb6cfa39f]
  ./libgoogleearth.so(_ZN5earth6client11Application3runEv+0x24f) [0xb7699821]
  /usr/lib/googleearth/googleearth-bin(main+0x11f) [0x8058817]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb6020775]
  /usr/lib/googleearth/googleearth-bin(__gxx_personality_v0+0x75) [0x8057e41]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/lobo/.googleearth/crashlogs/crashlog-F2292680.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

lobo@lobo-laptop:~$

---


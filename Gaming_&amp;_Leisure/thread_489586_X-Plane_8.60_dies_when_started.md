---
title: "X-Plane 8.60 dies when started??"
date: 2007-07-01
forum: Gaming &amp; Leisure
---

### Post by Rollinco on 2007-07-01
I have tried and tried to get X-Plane running on my Ubuntu rig and it will start, I can select language, it will load for a second and then drops to desktop with the following error. I have an ATI 9600XT video card which worked fine with X-Plane in Windows!! Any help would be appreciated!!


*** glibc detected *** ./X-Plane-i586: free(): invalid pointer: 0x0e374278 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7be87cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7bebe30]
./X-Plane-i586(_ZdlPv+0x1c)[0x86947d0]
/usr/local/games/X-Plane/Resources/plugins/XPLM.so(_ZN9__gnu_cxx13new_allocatorISsE10deallocateEPSsj+0x1d)[0xa77b27e3]
/usr/local/games/X-Plane/Resources/plugins/XPLM.so(_ZNSt12_Vector_baseISsSaISsEE13_M_deallocateEPSsj+0x33)[0xa77b281d]
/usr/local/games/X-Plane/Resources/plugins/XPLM.so(_ZNSt12_Vector_baseISsSaISsEED2Ev+0x42)[0xa77b5b60]
/usr/local/games/X-Plane/Resources/plugins/XPLM.so(_ZNSt6vectorISsSaISsEED1Ev+0x67)[0xa77b5bd9]
/usr/local/games/X-Plane/Resources/plugins/XPLM.so(_Z22XPLMFindAndLoadPluginsPKc+0x50f)[0xa77b4c1f]
/usr/local/games/X-Plane/Resources/plugins/XPLM.so(XPLMInitializePlugins+0x107)[0xa77b35a9]
./X-Plane-i586[0x8268f3b]
./X-Plane-i586[0x8161c0d]
./X-Plane-i586[0x8058e27]
./X-Plane-i586[0x8059a9c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7b96ebc]
./X-Plane-i586[0x804e4c1]
======= Memory map: ========
08048000-08799000 r-xp 00000000 03:41 14303238 /usr/local/games/X-Plane/X-Plane-i586
08799000-087ae000 rw-p 00751000 03:41 14303238 /usr/local/games/X-Plane/X-Plane-i586
087ae000-0e699000 rw-p 087ae000 00:00 0 [heap]
a7500000-a7521000 rw-p a7500000 00:00 0 
a7521000-a7600000 ---p a7521000 00:00 0 
a76df000-a76f5000 r-xp 00000000 03:41 13582416 /usr/local/games/X-Plane/Resources/plugins/PluginAdminLin.xpl
a76f5000-a76f8000 rw-p 00015000 03:41 13582416 /usr/local/games/X-Plane/Resources/plugins/PluginAdminLin.xpl
a76f8000-a76fc000 rw-p a76f8000 00:00 0 
a76fc000-a7772000 r-xp 00000000 03:41 13582418 /usr/local/games/X-Plane/Resources/plugins/XPWidgets.so
a7772000-a777b000 rw-p 00076000 03:41 13582418 /usr/local/games/X-Plane/Resources/plugins/XPWidgets.so
a777b000-a7782000 rw-p a777b000 00:00 0 
a7782000-a77d1000 r-xp 00000000 03:41 13582417 /usr/local/games/X-Plane/Resources/plugins/XPLM.so
a77d1000-a77d3000 rw-p 0004f000 03:41 13582417 /usr/local/games/X-Plane/Resources/plugins/XPLM.so
a77d3000-a77d9000 rw-p a77d3000 00:00 0 
a77d9000-a77da000 ---p a77d9000 00:00 0 
a77da000-a7fda000 rwxp a77da000 00:00 0 
a7fda000-a80da000 rw-s 00000000 00:12 81279 /dev/shm/ATISHM00
a80e8000-a8b51000 rw-p a80e8000 00:00 0 
a8b51000-a9051000 rw-s 0000b000 00:0d 16293 /dev/dri/card0
a9051000-a9551000 rw-s 0000a000 00:0d 16293 /dev/dri/card0
a9551000-a96b6000 rw-p a9551000 00:00 0 
a96bf000-a96d6000 rw-p a96ff000 00:00 0 
a96e8000-a96e9000 rw-p a96e8000 00:00 0 
a96f2000-a96fc000 rw-p a96f2000 00:00 0 
a96fc000-a96ff000 rw-s 00020000 00:0d 16293 /dev/dri/card0
a9703000-a9745000 rw-p a9703000 00:00 0 
a9745000-a9885000 rw-s 0001d000 00:0d 16293 /dev/dri/card0
a9885000-a9ec5000 rw-s 00007000 00:0d 16293 /dev/dri/card0
a9ec5000-a9fc5000 rw-s 00006000 00:0d 16293 /dev/dri/card0
a9fc5000-a9fd5000 rw-s 00004000 00:0d 16293 /dev/dri/card0
a9fd5000-b1fd5000 rw-s 00003000 00:0d 16293 /dev/dri/card0
b1fd5000-b1fdc000 r-xp 00000000 03:01 511234 /lib/tls/i686/cmov/librt-2.5.so
b1fdc000-b1fde000 rw-p 00006000 03:01 511234 /lib/tls/i686/cmov/librt-2.5.so
b1fde000-b208e000 r-xp 00000000 03:41 3212139 /usr/lib/libstdc++.so.5.0.7
b208e000-b2093000 rw-p 000af000 03:41 3212139 /usr/lib/libstdc++.so.5.0.7
b2093000-b2098000 rw-p b2093000 00:00 0 
b2098000-b28f5000 r-xp 00000000 03:41 3212970 /usr/lib/dri/fglrx_dri.so
b28f5000-b293f000 rw-p 0085d000 03:41 3212970 /usr/lib/dri/fglrx_dri.so
b293f000-b29c9000 rw-p b293f000 00:00 0 
b29c9000-b29ca000 ---p b29c9000 00:00 0 
b29ca000-b31ca000 rwxp b29ca000 00:00 0 
b31ca000-b7a8e000 rw-p b31ca000 00:00 0 
b7a8e000-b7a92000 r-xp 00000000 03:41 3211461 /usr/lib/libXdmcp.so.6.0.0
b7a92000-b7a93000 rw-p 00003000 03:41 3211461 /usr/lib/libXdmcp.so.6.0.0
b7a93000-b7a95000 r-xp 00000000 03:41 3211450 /usr/lib/libXau.so.6.0.0
b7a95000-b7a96000 rw-p 00001000 03:41 3211450 /usr/lib/libXau.so.6.0.0
b7a96000-b7a970Aborted (core dumped)

---

### Post by Rollinco on 2007-10-15
Went to Nvidia and problem solved!!

---


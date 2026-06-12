---
title: "ZSNES won't run!"
date: 2008-12-19
forum: Gaming &amp; Leisure
---

### Post by travnewmatic on 2008-12-19
it looks like file permission issues, but...
travnewmatic@optiplex:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d42558]
/lib/tls/i686/cmov/libc.so.6[0xb7d40680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:01 25439577   /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:01 25439577   /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:01 25439577   /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
08beb000-08c35000 rw-p 08beb000 00:00 0          [heap]
b6c0a000-b7739000 rw-p b6c0a000 00:00 0 
b7739000-b7787000 r-xp 00000000 08:01 25436569   /usr/lib/libpulse.so.0.4.1
b7787000-b7788000 r--p 0004d000 08:01 25436569   /usr/lib/libpulse.so.0.4.1
b7788000-b7789000 rw-p 0004e000 08:01 25436569   /usr/lib/libpulse.so.0.4.1
b7789000-b7795000 r-xp 00000000 08:01 25436912   /usr/lib/libpulse-simple.so.0.0.1
b7795000-b7796000 r--p 0000b000 08:01 25436912   /usr/lib/libpulse-simple.so.0.0.1
b7796000-b7797000 rw-p 0000c000 08:01 25436912   /usr/lib/libpulse-simple.so.0.0.1
b7797000-b77b9000 r-xp 00000000 08:01 25437792   /usr/lib/libaudiofile.so.0.0.2
b77b9000-b77bc000 rw-p 00021000 08:01 25437792   /usr/lib/libaudiofile.so.0.0.2
b77bc000-b77c5000 r-xp 00000000 08:01 25437949   /usr/lib/libesd.so.0.2.39
b77c5000-b77c6000 r--p 00008000 08:01 25437949   /usr/lib/libesd.so.0.2.39
b77c6000-b77c7000 rw-p 00009000 08:01 25437949   /usr/lib/libesd.so.0.2.39
b77d7000-b77ff000 r-xp 00000000 08:01 28295281   /lib/libpcre.so.3.12.1
b77ff000-b7800000 r--p 00027000 08:01 28295281   /lib/libpcre.so.3.12.1
b7800000-b7801000 rw-p 00028000 08:01 28295281   /lib/libpcre.so.3.12.1
b7801000-b78b6000 r-xp 00000000 08:01 25436874   /usr/lib/libglib-2.0.so.0.1800.2
b78b6000-b78b7000 r--p 000b4000 08:01 25436874   /usr/lib/libglib-2.0.so.0.1800.2
b78b7000-b78b8000 rw-p 000b5000 08:01 25436874   /usr/lib/libglib-2.0.so.0.1800.2
b78b8000-b78bc000 r-xp 00000000 08:01 25436877   /usr/lib/libgthread-2.0.so.0.1800.2
b78bc000-b78bd000 r--p 00003000 08:01 25436877   /usr/lib/libgthread-2.0.so.0.1800.2
b78bd000-b78be000 rw-p 00004000 08:01 25436877   /usr/lib/libgthread-2.0.so.0.1800.2
b78be000-b78c3000 r-xp 00000000 08:01 25439254   /usr/lib/libartsc.so.0.0.0
b78c3000-b78c4000 r--p 00004000 08:01 25439254   /usr/lib/libartsc.so.0.0.0
b78c4000-b78c5000 rw-p 00005000 08:01 25439254   /usr/lib/libartsc.so.0.0.0
b78c5000-b78da000 r-xp 00000000 08:01 25437667   /usr/lib/libICE.so.6.3.0
b78da000-b78db000 rw-p 00014000 08:01 25437667   /usr/lib/libICE.so.6.3.0
b78db000-b78dd000 rw-p b78db000 00:00 0 
b78dd000-b78e4000 r-xp 00000000 08:01 25437696   /usr/lib/libSM.so.6.0.0
b78e4000-b78e5000 r--p 00006000 08:01 25437696   /usr/lib/libSM.so.6.0.0
b78e5000-b78e6000 rw-p 00007000 08:01 25437696   /usr/lib/libSM.so.6.0.0
b78e6000-b7933000 r-xp 00000000 08:01 25437749   /usr/lib/libXt.so.6.0.0
b7933000-b7937000 rw-p 0004c000 08:01 25437749   /usr/lib/libXt.so.6.0.0
b7937000-b794d000 r-xp 00000000 08:01 25439192   /usr/lib/libaudio.so.2.4
b794d000-b794e000 r--p 00015000 08:01 25439192   /usr/lib/libaudio.so.2.4
b794e000-b794f000 rw-p 00016000 08:01 25439192   /usr/lib/libaudio.so.2.4
b794f000-b7950000 rw-p b794f000 00:00 0 
b7950000-b7953000 r-xp 00000000 08:01 28295210   /lib/libcap.so.1.10
b7953000-b7954000 rw-p 00002000 08:01 28295210   /lib/libcap.so.1.10
b7954000-b7956000 r-xp 00000000 08:01 25461107   /usr/lib/ao/plugins-2/libpulse.so
b7956000-b7958000 rw-p 00001000 08:01 25461107   /usr/lib/ao/plugins-2/libpulse.so
b7958000-b7959000 r-xp 00000000 08:01 25461104   /usr/lib/ao/plugins-2/libesd.so
b7959000-b795b000 rw-p 00000000 08:01 25461104   /usr/lib/ao/plugins-2/libesd.so
b795b000-b795d000 r-xp 00000000 08:01 25461106   /usr/lib/ao/plugins-2/liboss.so
b795d000-b795f000 rw-p 00001000 08:01 25461106   /usr/lib/ao/plugins-2/liboss.so
b795f000-b7969000 r-xp 00000000 08:01 28312737   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7969000-b796a000 r--p 00009000 08:01 28312737   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b796a000-b796b000 rw-p 0000a000 08:01 28312737   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b796b000-b7974000 r-xp 00000000 08:01 28312741   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7974000-b7975000 r--p 00008000 08:01 28312741   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7975000-b7976000 rw-p 00009000 08:01 28312741   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7976000-b798b000 r-xp 00000000 08:01 28312731   /lib/tls/i686/cmov/libnsl-2.8.90.so
b798b000-b798c000 r--p 00014000 08:01 28312731   /lib/tls/i686/cmov/libnsl-2.8.90.so
b798c000-b798d000 rw-p 00015000 08:01 28312731   /lib/tls/i686/cmov/libnsl-2.8.90.so
b798d000-b798f000 rw-p b798d000 00:00 0 
b798f000-b7996000 r-xp 00000000 08:01 28312733   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7996000-b7997000 r--p 00006000 08:01 28312733   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7997000-b7998000 rw-p 00007000 08:01 28312733   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7998000-b799a000 rw-p b7998000 00:00 0 
b799a000-b799e000 r-xp 00000000 08:01 25437719   /usr/lib/libXdmcp.so.6.0.0
b799e000-b799f000 rw-p 00003000 08:01 25437719   /usr/lib/libXdmcp.so.6.0.0
b799f000-b79a1000 r-xp 00000000 08:01 25437708   /usr/lib/libXau.so.6.0.0
b79a1000-b79a2000 rw-p 00001000 08:01 25437708   /usr/lib/libXau.so.6.0.0
b79a2000-b79a3000 rw-p b79a2000 00:00 0 
b79a3000-b79ba000 r-xp 00000000 08:01 25438654   /usr/lib/libxcb.so.1.0.0
b79ba000-b79bb000 r--p 00016000 08:01 25438654   /usr/lib/libxcb.so.1.0.0
b79bb000-b79bc000 rw-p 00017000 08:01 25438654   /usr/lib/libxcb.so.1.0.0
b79bc000-b79bd000 r-xp 00000000 08:01 25438652   /usr/lib/libxcb-xlib.so.0.0.0
b79bd000-b79be000 r--p 00000000 08:01 25438652   /usr/lib/libxcb-xlib.so.0.0.0
b79be000-b79bf000 rw-p 00001000 08:01 25438652   /usr/lib/libxcb-xlib.so.0.0.0
b79bf000-b79c6000 r-xp 00000000 08:01 28312750   /lib/tls/i686/cmov/librt-2.8.90.so
b79c6000-b79c7000 r--p 00007000 08:01 28312750   /lib/tls/i686/cmov/librt-2.8.90.so
b79c7000-b79c8000 rw-p 00008000 08:01 28312750   /lib/tls/i686/cmov/librt-2.8.90.so
b79c8000-b79cf000 r-xp 00000000 08:01 25437919   /usr/lib/libdrm.so.2.3.1
b79cf000-b79d0000 r--p 00006000 08:01 25437919   /usr/lib/libdrm.so.2.3.1
b79d0000-b79d1000 rw-p 00007000 08:01 25437919   /usr/lib/libdrm.so.2.3.1
b79d1000-b79d5000 r-xp 00000000 08:01 25437725   /usr/lib/libXfixes.so.3.1.0
b79d5000-b79d6000 rw-p 00003000 08:01 25437725   /usr/lib/libXfixes.so.3.1.0
b79d6000-b79d7000 rw-p b79d6000 00:00 0 
b79d7000-b79d9000 r-xp 00000000 08:01 25437717   /usr/lib/libXdamage.so.1.1.0
b79d9000-b79da000 rw-p 00001000 08:01 25437717   /usr/lib/libXdamage.so.1.1.0
b79da000-b79de000 r-xp 00000000 08:01 25437759   /usr/lib/libXxf86vm.so.1.0.0
b79de000-b79df000 r--p 00003000 08:01 25437759   /usr/lib/libXxf86vm.so.1.0.0
b79df000-b79e0000 rw-p 00004000 08:01 25437759   /usr/lib/libXxf86vm.so.1.0.0
b79e0000-b79ed000 r-xp 00000000 08:01 25437723   /usr/lib/libXext.so.6.4.0
b79ed000-b79ef000 rw-p 0000c000 08:01 25437723   /usr/lib/libXext.so.6.4.0
b79ef000-b7ada000 r-xp 00000000 08:01 25436277   /usr/lib/libX11.so.6.2.0
b7ada000-b7adb000 r--p 000ea000 08:01 25436277   /usr/lib/libX11.so.6.2.0
b7adb000-b7add000 rw-p 000eb000 08:01 25436277   /usr/lib/libX11.so.6.2.0
b7add000-b7ade000 rw-p b7add000 00:00 0 
b7ade000-b7af1000 r-xp 00000000 08:01 25437905   /usr/lib/libdirect-1.0.so.0.1.0
b7af1000-b7af2000 r--p 00012000 08:01 25437905   /usr/lib/libdirect-1.0.so.0.1.0
b7af2000-b7af3000 rw-p 00013000 08:01 25437905   /usr/lib/libdirect-1.0.so.0.1.0
b7af3000-b7afa000 r-xp 00000000 08:01 25437983   /usr/lib/libfusion-1.0.so.0.1.0
b7afa000-b7afb000 r--p 00006000 08:01 25437983   /usr/lib/libfusion-1.0.so.0.1.0
b7afb000-b7afc000 rw-p 00007000 08:01 25437983   /usr/lib/libfusion-1.0.so.0.1.0
b7afc000-b7afd000 rw-p b7afc000 00:00 0 
b7afd000-b7b61000 r-xp 00000000 08:01 25437907   /usr/lib/libdirectfb-1.0.so.0.1.0
b7b61000-b7b62000 r--p 00063000 08:01 25437907   /usr/lib/libdirectfb-1.0.so.0.1.0
b7b62000-b7b63000 rw-p 00064000 08:01 25437907   /usr/lib/libdirectfb-1.0.so.0.1.0
b7b63000-b7b65000 r-xp 00000000 08:01 28312726   /lib/tls/i686/cmov/libdl-2.8.90.so
b7b65000-b7b66000 r--p 00001000 08:01 28312726   /lib/tls/i686/cmov/libdl-2.8.90.so
b7b66000-b7b67000 rw-p 00002000 08:01 28312726   /lib/tls/i686/cmov/libdl-2.8.90.so
b7b67000-b7c2a000 r-xp 00000000 08:01 25438076   /usr/lib/libasound.so.2.0.0
b7c2a000-b7c2c000 r--p 00Aborted
travnewmatic@optiplex:~$ 

Let me know what else yall need!

Thanks in advance!

---

### Post by dfreer on 2008-12-19
It doesn't have anything to do with file permissions. There's a ton of threads about this already, have you even tried a search either in this forum or in the ZSNES forum?

Short Answer: You need to use a binary (preferably of 1.51b) that is not compiled using Ubuntu 8.10's GCC 4.3.2

---

### Post by travnewmatic on 2008-12-19
sorry about that, i did do a bit of searching but i didnt see anything at the time...  when i get home i'll try your method that you have in your signature.  thanks man :D

---


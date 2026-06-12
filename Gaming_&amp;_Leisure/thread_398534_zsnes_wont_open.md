---
title: "zsnes wont open"
date: 2007-04-01
forum: Gaming &amp; Leisure
---

### Post by Nolander on 2007-04-01
Hi all,

install zsnes when i click on the icon it does nothin. when i open it in the terminal i get```

ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

*** glibc detected *** zsnes: munmap_chunk(): invalid pointer: 0xbf923eab ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x18a)[0xb7c54b4a]
zsnes[0x80dd746]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7c038cc]
zsnes(__gxx_personality_v0+0xcd)[0x804b9f1]
======= Memory map: ========
08048000-082f7000 r-xp 00000000 03:01 365881     /usr/bin/zsnes
082f7000-0834a000 rwxp 002ae000 03:01 365881     /usr/bin/zsnes
0834a000-085d7000 rwxp 0834a000 00:00 0          [heap]
b79e4000-b79e6000 rwxp b79e4000 00:00 0 
b79e6000-b79ea000 r-xp 00000000 03:01 362594     /usr/lib/libXdmcp.so.6.0.0
b79ea000-b79eb000 rwxp 00003000 03:01 362594     /usr/lib/libXdmcp.so.6.0.0
b79eb000-b79ed000 r-xp 00000000 03:01 362592     /usr/lib/libXau.so.6.0.0
b79ed000-b79ee000 rwxp 00001000 03:01 362592     /usr/lib/libXau.so.6.0.0
b79ee000-b79ef000 rwxp b79ee000 00:00 0 
b79ef000-b79f5000 r-xp 00000000 03:01 362666     /usr/lib/libdrm.so.2.0.0
b79f5000-b79f6000 rwxp 00005000 03:01 362666     /usr/lib/libdrm.so.2.0.0
b79f6000-b79fa000 r-xp 00000000 03:01 362708     /usr/lib/libXxf86vm.so.1.0.0
b79fa000-b79fb000 rwxp 00003000 03:01 362708     /usr/lib/libXxf86vm.so.1.0.0
b79fb000-b7a07000 r-xp 00000000 03:01 362598     /usr/lib/libXext.so.6.4.0
b7a07000-b7a08000 rwxp 0000c000 03:01 362598     /usr/lib/libXext.so.6.4.0
b7a08000-b7ace000 r-xp 00000000 03:01 362596     /usr/lib/libX11.so.6.2.0
b7ace000-b7ad1000 rwxp 000c5000 03:01 362596     /usr/lib/libX11.so.6.2.0
b7ad1000-b7ad3000 r-xp 00000000 03:01 407356     /lib/tls/i686/cmov/libdl-2.4.so
b7ad3000-b7ad5000 rwxp 00001000 03:01 407356     /lib/tls/i686/cmov/libdl-2.4.so
b7ad5000-b7ae1000 r-xp 00000000 03:01 364089     /usr/lib/libdirect-0.9.so.24.0.0
b7ae1000-b7ae2000 rwxp 0000c000 03:01 364089     /usr/lib/libdirect-0.9.so.24.0.0
b7ae2000-b7ae3000 rwxp b7ae2000 00:00 0 
b7ae3000-b7ae7000 r-xp 00000000 03:01 364091     /usr/lib/libfusion-0.9.so.24.0.0
b7ae7000-b7ae8000 rwxp 00003000 03:01 364091     /usr/lib/libfusion-0.9.so.24.0.0
b7ae8000-b7b34000 r-xp 00000000 03:01 364090     /usr/lib/libdirectfb-0.9.so.24.0.0
b7b34000-b7b36000 rwxp 0004b000 03:01 364090     /usr/lib/libdirectfb-0.9.so.24.0.0
b7b36000-b7be9000 r-xp 00000000 03:01 360700     /usr/lib/libasound.so.2.0.0
b7be9000-b7bee000 rwxp 000b2000 03:01 360700     /usr/lib/libasound.so.2.0.0
b7bee000-b7d1b000 r-xp 00000000 03:01 407352     /lib/tls/i686/cmov/libc-2.4.so
b7d1b000-b7d1d000 r-xp 0012c000 03:01 407352     /lib/tls/i686/cmov/libc-2.4.so
b7d1d000-b7d1f000 rwxp 0012e000 03:01 407352     /lib/tls/i686/cmov/libc-2.4.so
b7d1f000-b7d22000 rwxp b7d1f000 00:00 0 
b7d22000-b7d2c000 r-xp 00000000 03:01 407216     /lib/libgcc_s.so.1
b7d2c000-b7d2d000 rwxp 00009000 03:01 407216     /lib/libgcc_s.so.1
b7d2d000-b7d51000 r-xp 00000000 03:01 407357     /lib/tls/i686/cmov/libm-2.4.so
b7d51000-b7d53000 rwxp 00023000 03:01 407357     /lib/tls/i686/cmov/libm-2.4.so
b7d53000-b7d54000 rwxp b7d53000 00:00 0 
b7d54000-b7e28000 r-xp 00000000 03:01 361022     /usr/lib/libstdc++.so.6.0.8
b7e28000-b7e2b000 r-xp 000d4000 03:01 361022     /usr/lib/libstdc++.so.6.0.8
b7e2b000-b7e2d000 rwxp 000d7000 03:01 361022     /usr/lib/libstdc++.so.6.0.8
b7e2d000-b7e33000 rwxp b7e2d000 00:00 0 
b7e33000-b7e9b000 r-xp 00000000 03:01 362760     /usr/lib/libGL.so.1.2
b7e9b000-b7ea1000 rwxp 00067000 03:01 362760     /usr/lib/libGL.so.1.2
b7ea1000-b7ea2000 rwxp b7ea1000 00:00 0 
b7ea2000-b7ec4000 r-xp 00000000 03:01 362823     /usr/lib/libpng12.so.0.1.2.8
b7ec4000-b7ec5000 rwxp 00021000 03:01 362823     /usr/lib/libpng12.so.0.1.2.8
b7ec5000-b7ed4000 r-xp 00000000 03:01 407370     /lib/tls/i686/cmov/libpthread-2.4.so
b7ed4000-b7ed6000 rwxp 0000f000 03:01 407370     /lib/tls/i686/cmov/libpthread-2.4.so
b7ed6000-b7ed8000 rwxp b7ed6000 00:00 0 
b7ed8000-b7f3c000 r-xp 00000000 03:01 364097     /usr/lib/libSDL-1.2.so.0.7.3
b7f3c000-b7f3e000 rwxp 00064000 03:01 364097     /usr/lib/libSDL-1.2.so.0.7.3
b7f3e000-b7f66000 rwxp b7f3e000 00:00 0 
b7f66000-b7f79000 r-xp 00000000 03:01 360587     /usr/lib/libz.so.1.2.3
b7f79000-b7f7a000 rwxp 00012000 03:01 360587     /usr/lib/libz.so.1.2.3
b7f7a000-b7f7b000 rwxp b7f7a000 00:00 0 
b7f84000-b7f86000 rwxp b7f84000 00:00 0 
b7f86000-b7f9f000 r-xp 00000000 03:01 407217     /lib/ld-2.4.so
b7f9f000-b7fa1000 rwxp 00018000 03:01 407217     /lib/ld-2.4.so
bf90f000-bf925000 rwxp bf90f000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

help plz!

Nolander.

---

### Post by Perfect Storm on 2007-04-01
Try with this howto (You'll get the latest zsnes, just remember to uninstall the previous version first and delete **./zsnes** i home folder to wipe out previous settings).): [http://gaming.gwos.org/e107_plugins/content/content.php?content.38](http://gaming.gwos.org/e107_plugins/content/content.php?content.38)

---


---
title: "is zsnes version 1.5 deb download anywhere?"
date: 2010-01-16
forum: Gaming &amp; Leisure
---

### Post by gypsumwolf on 2010-01-16
is zsnes version 1.5 deb download anywhere? I upgraded to the newest version 1.51 and it states my saved state is too old. So I completely removed zsnes. I would like a link to a deb or something to install 1.50 on my system so the saved state will work. Thanks!

(I have tried compiling from source and ran into too many errors.)

---

### Post by hikaricore on 2010-01-16
You can try the dapper version - zsnes (1.420-0.1ubuntu2)
[http://packages.ubuntu.com/dapper/zsnes](http://packages.ubuntu.com/dapper/zsnes)

Worth a shot, it's not 1.5 but it may work.

---

### Post by gypsumwolf on 2010-01-20
That is still the source pakage. I got further in the compile but it came up with an error.

---

### Post by hikaricore on 2010-01-21
That's not a source package.

---

### Post by gypsumwolf on 2010-01-21
> **hikaricore said:**
> That's not a source package.

When I click on show list of files at the bottom it gives me this 

"
Error

No such package in this suite on this architecture."

There is a link on the side that gives me the source code to compile.

Edit:
OOps, should have clicked on i386. Thanks!!

---

### Post by gypsumwolf on 2010-01-21
When I tried to run it, this is what happened:

```
# zsnes

ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

*** glibc detected *** zsnes: munmap_chunk(): invalid pointer: 0xbfb49f35 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x730ff1]
/lib/tls/i686/cmov/libc.so.6[0x7321f5]
zsnes[0x80dd746]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x6dcb56]
zsnes(__gxx_personality_v0+0xcd)[0x804b9f1]
======= Memory map: ========
00110000-0017d000 r-xp 00000000 08:01 182972     /usr/lib/libSDL-1.2.so.0.11.2
0017d000-0017e000 r-xp 0006c000 08:01 182972     /usr/lib/libSDL-1.2.so.0.11.2
0017e000-0017f000 rwxp 0006d000 08:01 182972     /usr/lib/libSDL-1.2.so.0.11.2
0017f000-001aa000 rwxp 00000000 00:00 0 
001aa000-001bf000 r-xp 00000000 08:01 132303     /lib/tls/i686/cmov/libpthread-2.10.1.so
001bf000-001c0000 r-xp 00014000 08:01 132303     /lib/tls/i686/cmov/libpthread-2.10.1.so
001c0000-001c1000 rwxp 00015000 08:01 132303     /lib/tls/i686/cmov/libpthread-2.10.1.so
001c1000-001c3000 rwxp 00000000 00:00 0 
001c3000-001e9000 r-xp 00000000 08:01 164229     /usr/lib/libpng12.so.0.37.0
001e9000-001ea000 r-xp 00025000 08:01 164229     /usr/lib/libpng12.so.0.37.0
001ea000-001eb000 rwxp 00026000 08:01 164229     /usr/lib/libpng12.so.0.37.0
001eb000-001f3000 r-xp 00000000 08:01 164390     /usr/lib/libfusion-1.2.so.0.7.0
001f3000-001f4000 r-xp 00007000 08:01 164390     /usr/lib/libfusion-1.2.so.0.7.0
001f4000-001f5000 rwxp 00008000 08:01 164390     /usr/lib/libfusion-1.2.so.0.7.0
001f5000-001f6000 rwxp 00000000 00:00 0 
001f6000-00204000 r-xp 00000000 08:01 158434     /usr/lib/libXext.so.6.4.0
00204000-00205000 r-xp 0000d000 08:01 158434     /usr/lib/libXext.so.6.4.0
00205000-00206000 rwxp 0000e000 08:01 158434     /usr/lib/libXext.so.6.4.0
00206000-0020a000 r-xp 00000000 08:01 169621     /usr/lib/libXxf86vm.so.1.0.0
0020a000-0020b000 r-xp 00003000 08:01 169621     /usr/lib/libXxf86vm.so.1.0.0
0020b000-0020c000 rwxp 00004000 08:01 169621     /usr/lib/libXxf86vm.so.1.0.0
0020c000-0020e000 r-xp 00000000 08:01 164911     /usr/lib/libXdamage.so.1.1.0
0020e000-0020f000 rwxp 00001000 08:01 164911     /usr/lib/libXdamage.so.1.1.0
0020f000-00210000 rwxp 00000000 00:00 0 
00210000-00214000 r-xp 00000000 08:01 162663     /usr/lib/libXfixes.so.3.1.0
00214000-00215000 r-xp 00003000 08:01 162663     /usr/lib/libXfixes.so.3.1.0
00215000-00216000 rwxp 00004000 08:01 162663     /usr/lib/libXfixes.so.3.1.0
00216000-0021e000 r-xp 00000000 08:01 169615     /usr/lib/libdrm.so.2.4.0
0021e000-0021f000 r-xp 00007000 08:01 169615     /usr/lib/libdrm.so.2.4.0
0021f000-00220000 rwxp 00008000 08:01 169615     /usr/lib/libdrm.so.2.4.0
00220000-0023c000 r-xp 00000000 08:01 158160     /usr/lib/libxcb.so.1.1.0
0023c000-0023d000 r-xp 0001c000 08:01 158160     /usr/lib/libxcb.so.1.1.0
0023d000-0023e000 rwxp 0001d000 08:01 158160     /usr/lib/libxcb.so.1.1.0
0023e000-0023f000 rwxp 00000000 00:00 0 
0025b000-0027f000 r-xp 00000000 08:01 131588     /lib/tls/i686/cmov/libm-2.10.1.so
0027f000-00280000 r-xp 00023000 08:01 131588     /lib/tls/i686/cmov/libm-2.10.1.so
00280000-00281000 rwxp 00024000 08:01 131588     /lib/tls/i686/cmov/libm-2.10.1.so
0031c000-0031d000 rwxp 00000000 00:00 0 
003af000-003b0000 r-xp 00000000 00:00 0          [vdso]
003b0000-00472000 r-xp 00000000 08:01 136589     /usr/lib/libasound.so.2.0.0
00472000-00476000 r-xp 000c1000 08:01 136589     /usr/lib/libasound.so.2.0.0
00476000-00477000 rwxp 000c5000 08:01 136589     /usr/lib/libasound.so.2.0.0
004e9000-004f0000 r-xp 00000000 08:01 132305     /lib/tls/i686/cmov/librt-2.10.1.so
004f0000-004f1000 r-xp 00006000 08:01 132305     /lib/tls/i686/cmov/librt-2.10.1.so
004f1000-004f2000 rwxp 00007000 08:01 132305     /lib/tls/i686/cmov/librt-2.10.1.so
00519000-00572000 r-xp 00000000 08:01 169627     /usr/lib/libGL.so.1.2
00572000-00577000 r-xp 00059000 08:01 169627     /usr/lib/libGL.so.1.2
00577000-0057c000 rwxp 0005e000 08:01 169627     /usr/lib/libGL.so.1.2
0057c000-0057d000 rwxp 00000000 00:00 0 
005f5000-005f7000 r-xp 00000000 08:01 131587     /lib/tls/i686/cmov/libdl-2.10.1.so
005f7000-005f8000 r-xp 00001000 08:01 131587     /lib/tls/i686/cmov/libdl-2.10.1.so
005f8000-005f9000 rwxp 00002000 08:01 131587     /lib/tls/i686/cmov/libdl-2.10.1.so
006b0000-006c4000 r-xp 00000000 08:01 133124     /lib/libz.so.1.2.3.3
006c4000-006c5000 r-xp 00013000 08:01 133124     /lib/libz.so.1.2.3.3
006c5000-006c6000 rwxp 00014000 08:01 133124     /lib/libz.so.1.2.3.3
006c6000-00804000 r-xp 00000000 08:01 131584     /lib/tls/i686/cmov/libc-2.10.1.so
00804000-00805000 ---p 0013e000 08:01 131584     /lib/tls/i686/cmov/libc-2.10.1.so
00805000-00807000 r-xp 0013e000 08:01 131584     /lib/tls/i686/cmov/libc-2.10.1.so
00807000-00808000 rwxp 00140000 08:01 131584     /lib/tls/i686/cmov/libc-2.10.1.so
00808000-0080b000 rwxp 00000000 00:00 0 
00827000-0089d000 r-xp 00000000 08:01 164389     /usr/lib/libdirectfb-1.2.so.0.7.0
0089d000-0089e000 ---p 00076000 08:01 164389     /usr/lib/libdirectfb-1.2.so.0.7.0
0089e000-0089f000 r-xp 00076000 08:01 164389     /usr/lib/libdirectfb-1.2.so.0.7.0
0089f000-008a0000 rwxp 00077000 08:01 164389     /usr/lib/libdirectfb-1.2.so.0.7.0
008a0000-008a1000 rwxp 00000000 00:00 0 
0091d000-0091f000 r-xp 00000000 08:01 158143     /usr/lib/libXau.so.6.0.0
0091f000-00920000 r-xp 00001000 08:01 158143     /usr/lib/libXau.so.6.0.0
00920000-00921000 rwxp 00002000 08:01 158143     /usr/lib/libXau.so.6.0.0
00970000-00971000 rwxp 00000000 00:00 0 
009af000-009c5000 r-xp 00000000 08:01 164388     /usr/lib/libdirect-1.2.so.0.7.0
009c5000-009c6000 r-xp 00015000 08:01 164388     /usr/lib/libdirect-1.2.so.0.7.0
009c6000-009c7000 rwxp 00016000 08:01 164388     /usr/lib/libdirect-1.2.so.0.7.0
009ff000-00a1b000 r-xp 00000000 08:01 131580     /lib/libgcc_s.so.1
00a1b000-00a1c000 r-xp 0001b000 08:01 131580     /lib/libgcc_s.so.1
00a1c000-00a1d000 rwxp 0001c000 08:01 131580     /lib/libgcc_s.so.1
00a8b000-00a8f000 r-xp 00000000 08:01 158153     /usr/lib/libXdmcp.so.6.0.0
00a8f000-00a90000 rwxp 00003000 08:01 158153     /usr/lib/libXdmcp.so.6.0.0
00ac1000-00ac2000 rwxp 00000000 00:00 0 
00b51000-00c37000 r-xp 00000000 08:01 131778     /usr/lib/libstdc++.so.6.0.13
00c37000-00c3b000 r-xp 000e6000 08:01 131778     /usr/lib/libstdc++.so.6.0.13
00c3b000-00c3c000 rwxp 000ea000 08:01 131778     /usr/lib/libstdc++.so.6.0.13
00c3c000-00c43000 rwxp 00000000 00:00 0 
00c43000-00d6d000 r-xp 00000000 08:01 158424     /usr/lib/libX11.so.6.2.0
00d6d000-00d6e000 ---p 0012a000 08:01 158424     /usr/lib/libX11.so.6.2.0
00d6e000-00d6f000 r-xp 0012a000 08:01 158424     /usr/lib/libX11.so.6.2.0
00d6f000-00d71000 rwxp 0012b000 08:01 158424     /usr/lib/libX11.so.6.2.0
00d71000-00d72000 rwxp 00000000 00:00 0 Aborted

```

---


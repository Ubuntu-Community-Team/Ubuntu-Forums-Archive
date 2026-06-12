---
title: "zsnes 1.42"
date: 2009-08-12
forum: Gaming &amp; Leisure
---

### Post by Kaninepete on 2009-08-12
I'm trying to get zsnes 1.42 because it has internet functionality that 1.51 does not.
I can't find it on the list of programs to install, so I downloaded a .deb from 
[http://ftp.handhelds.org/mirror/debi...420-1_i386.deb]("http://ftp.handhelds.org/mirror/debian/pool/main/z/zsnes/zsnes_1.420-1_i386.deb")

and installed it.
it didn't show up in the program list, so I typed zsnes is in a terminal, and it returned:
ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.
Please report crashes to [EMAIL="zsnes-devel@lists.sourceforge.net"]zsnes-devel@lists.sourceforge.net[/EMAIL].

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

*** glibc detected *** zsnes: munmap_chunk(): invalid pointer: 0xbfbf5e5d ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d5e604]
zsnes[0x80de151]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d05775]
zsnes(__gxx_personality_v0+0xd1)[0x804ba31]
======= Memory map: ========
08048000-082f8000 r-xp 00000000 08:05 1082538    /usr/bin/zsnes
082f8000-0834b000 rwxp 002b0000 08:05 1082538    /usr/bin/zsnes
0834b000-085b7000 rwxp 0834b000 00:00 0 
0910c000-0912d000 rwxp 0910c000 00:00 0          [heap]
b7a57000-b7a59000 rwxp b7a57000 00:00 0 
b7a59000-b7a5d000 r-xp 00000000 08:05 1080827    /usr/lib/libXdmcp.so.6.0.0
b7a5d000-b7a5e000 rwxp 00003000 08:05 1080827    /usr/lib/libXdmcp.so.6.0.0
b7a5e000-b7a60000 r-xp 00000000 08:05 1080816    /usr/lib/libXau.so.6.0.0
b7a60000-b7a61000 r-xp 00001000 08:05 1080816    /usr/lib/libXau.so.6.0.0
b7a61000-b7a62000 rwxp 00002000 08:05 1080816    /usr/lib/libXau.so.6.0.0
b7a62000-b7a7a000 r-xp 00000000 08:05 1081400    /usr/lib/libxcb.so.1.1.0
b7a7a000-b7a7b000 r-xp 00017000 08:05 1081400    /usr/lib/libxcb.so.1.1.0
b7a7b000-b7a7c000 rwxp 00018000 08:05 1081400    /usr/lib/libxcb.so.1.1.0
b7a7c000-b7a7d000 rwxp b7a7c000 00:00 0 
b7a7d000-b7a84000 r-xp 00000000 08:05 990567     /lib/tls/i686/cmov/librt-2.9.so
b7a84000-b7a85000 r-xp 00006000 08:05 990567     /lib/tls/i686/cmov/librt-2.9.so
b7a85000-b7a86000 rwxp 00007000 08:05 990567     /lib/tls/i686/cmov/librt-2.9.so
b7a86000-b7a8e000 r-xp 00000000 08:05 1081027    /usr/lib/libdrm.so.2.4.0
b7a8e000-b7a8f000 r-xp 00007000 08:05 1081027    /usr/lib/libdrm.so.2.4.0
b7a8f000-b7a90000 rwxp 00008000 08:05 1081027    /usr/lib/libdrm.so.2.4.0
b7a90000-b7a94000 r-xp 00000000 08:05 1080831    /usr/lib/libXfixes.so.3.1.0
b7a94000-b7a95000 rwxp 00003000 08:05 1080831    /usr/lib/libXfixes.so.3.1.0
b7a95000-b7a97000 r-xp 00000000 08:05 1080825    /usr/lib/libXdamage.so.1.1.0
b7a97000-b7a98000 rwxp 00001000 08:05 1080825    /usr/lib/libXdamage.so.1.1.0
b7a98000-b7a9c000 r-xp 00000000 08:05 1080869    /usr/lib/libXxf86vm.so.1.0.0
b7a9c000-b7a9d000 r-xp 00003000 08:05 1080869    /usr/lib/libXxf86vm.so.1.0.0
b7a9d000-b7a9e000 rwxp 00004000 08:05 1080869    /usr/lib/libXxf86vm.so.1.0.0
b7a9e000-b7a9f000 rwxp b7a9e000 00:00 0 
b7a9f000-b7aad000 r-xp 00000000 08:05 1080829    /usr/lib/libXext.so.6.4.0
b7aad000-b7aae000 r-xp 0000d000 08:05 1080829    /usr/lib/libXext.so.6.4.0
b7aae000-b7aaf000 rwxp 0000e000 08:05 1080829    /usr/lib/libXext.so.6.4.0
b7aaf000-b7b99000 r-xp 00000000 08:05 1080810    /usr/lib/libX11.so.6.2.0
b7b99000-b7b9a000 ---p 000ea000 08:05 1080810    /usr/lib/libX11.so.6.2.0
b7b9a000-b7b9b000 r-xp 000ea000 08:05 1080810    /usr/lib/libX11.so.6.2.0
b7b9b000-b7b9d000 rwxp 000eb000 08:05 1080810    /usr/lib/libX11.so.6.2.0
b7b9d000-b7b9e000 rwxp b7b9d000 00:00 0 
b7b9e000-b7bb1000 r-xp 00000000 08:05 1081013    /usr/lib/libdirect-1.0.so.0.1.0
b7bb1000-b7bb2000 r-xp 00012000 08:05 1081013    /usr/lib/libdirect-1.0.so.0.1.0
b7bb2000-b7bb3000 rwxp 00013000 08:05 1081013    /usr/lib/libdirect-1.0.so.0.1.0
b7bb3000-b7bba000 r-xp 00000000 08:05 1081095    /usr/lib/libfusion-1.0.so.0.1.0
b7bba000-b7bbb000 r-xp 00006000 08:05 1081095    /usr/lib/libfusion-1.0.so.0.1.0
b7bbb000-b7bbc000 rwxp 00007000 08:05 1081095    /usr/lib/libfusion-1.0.so.0.1.0
b7bbc000-b7c20000 r-xp 00000000 08:05 1081015    /usr/lib/libdirectfb-1.0.so.0.1.0
b7c20000-b7c21000 r-xp 00063000 08:05 1081015    /usr/lib/libdirectfb-1.0.so.0.1.0
b7c21000-b7c22000 rwxp 00064000 08:05 1081015    /usr/lib/libdirectfb-1.0.so.0.1.0
b7c22000-b7c23000 rwxp b7c22000 00:00 0 
b7c23000-b7c25000 r-xp 00000000 08:05 990543     /lib/tls/i686/cmov/libdl-2.9.so
b7c25000-b7c26000 r-xp 00001000 08:05 990543     /lib/tls/i686/cmov/libdl-2.9.so
b7c26000-b7c27000 rwxp 00002000 08:05 990543     /lib/tls/i686/cmov/libdl-2.9.so
b7c27000-b7cea000 r-xp 00000000 08:05 1080890    /usr/lib/libasound.so.2.0.0
b7cea000-b7cec000 r-xp 000c2000 08:05 1080890    /usr/lib/libasound.so.2.0.0
b7cec000-b7cef000 rwxp 000c4000 08:05 1080890    /usr/lib/libasound.so.2.0.0
b7cef000-b7e4b000 r-xp 00000000 08:05 990537   Aborted
 
what should be my next step?

---

### Post by BigSilly on 2009-08-12
Are you using 64 bit, because ZSNES needs 32 bit compatibility libraries to work on it. You'll need ia32-libs from Synaptic if that's the case. Otherwise it's hard to say.Version 1.42 is pretty old now...

---

### Post by BigSilly on 2009-08-12
You could try this package I've attached that was built for Dapper Drake. I take no responsibility for your system if it messes up though! :D

---

### Post by khelben1979 on 2009-08-12
Why not go with [Snes9x]("http://en.wikipedia.org/wiki/Snes9x")?

---

### Post by ShadowTek on 2009-08-12
> **Kaninepete said:**
> I can't find it on the list of programs to install...

They couldn't get the package for 9.04 to upload properly. Anyway, you can just download the one for 8.10 from the repository and install it manually.

---

### Post by hvymtlsteve on 2009-11-04
> **khelben1979 said:**
> Why not go with [Snes9x]("http://en.wikipedia.org/wiki/Snes9x")?

snes9x online play is also disabled..

---


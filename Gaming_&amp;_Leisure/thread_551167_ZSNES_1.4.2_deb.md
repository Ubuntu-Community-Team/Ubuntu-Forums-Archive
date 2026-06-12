---
title: "ZSNES 1.4.2 deb?"
date: 2007-09-14
forum: Gaming &amp; Leisure
---

### Post by Tylerofl on 2007-09-14
I know 1.5.1 is out, but for some reason they disabled netplay, which is what I want. I got all the dependencies, was able to ./configure it, but upon make...

```
g++ -o zsnes chips/sfxproc.o chips/fxemu2.o chips/dsp1proc.o chips/fxemu2b.o chips/fxemu2c.o chips/fxtable.o chips/sa1proc.o chips/sa1regs.o chips/dsp1emu.o chips/st10proc.o chips/seta10.o chips/dsp2proc.o chips/sdd1emu.o cpu/addrni.o cpu/dma.o cpu/dsp.o cpu/dspproc.o cpu/execute.o cpu/executec.o cpu/irq.o cpu/memory.o cpu/spc700.o cpu/stable.o cpu/table.o cpu/tableb.o cpu/tablec.o linux/copyvwin.o linux/sdlintrf.o linux/sdllink.o linux/sw_draw.o linux/zloaderw.o linux/ztcp.o linux/zipxw.o linux/zfilew.o dos/debug.o dos/joy.o dos/modemrtn.o dos/vesa2.o dos/initvid.o dos/sw.o dos/gppro.o dos/vesa12.o gui/gui.o gui/menu.o video/makev16b.o video/makev16t.o video/makevid.o video/mode716.o video/mode716b.o video/mode716d.o video/mode716e.o video/mode716t.o video/mode7.o video/mode7ext.o video/mv16tms.o video/newg162.o video/newgfx16.o video/newgfx2.o video/newgfx.o video/m716text.o video/2xsaiw.o video/procvid.o video/sw_draw.o video/hq2x16.o video/hq2x32.o video/hq3x16.o video/hq3x32.o video/hq4x16.o video/hq4x32.o cfgload.o endmem.o init.o initc.o uic.o patch.o ui.o vcache.o version.o zip/unzip.o zip/zpng.o effects/burn.o effects/water.o effects/smoke.o jma/7zlzma.o jma/crc32.o jma/iiostrm.o jma/inbyte.o jma/jma.o jma/lzma.o jma/lzmadec.o jma/winout.o jma/zsnesjma.o -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__ -I/usr/include/SDL -D_REENTRANT -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -L/usr/local/lib -L/usr/lib -lz -L/usr/lib -lSDL -lpthread -lpng -lm -L
g++: argument to '-L' missing 
```

There's an executable there now for some reason (maybe it compiled at some point, i've tried so many things), and when I run the executable...

```
*** glibc detected *** /home/tyler/zsnes/zsnes: munmap_chunk(): invalid pointer: 0xbfbf1e8d ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7bfef5b]
/home/tyler/zsnes/zsnes[0x80dde82]
======= Memory map: ========
08048000-082f9000 r-xp 00000000 08:01 11552674   /home/tyler/zsnes/zsnes
082f9000-0834d000 rwxp 002b0000 08:01 11552674   /home/tyler/zsnes/zsnes
0834d000-085d9000 rwxp 0834d000 00:00 0          [heap]
b7051000-b70b6000 rwxp b7051000 00:00 0 
b70b6000-b70ba000 r-xp 00000000 08:01 7374085    /usr/lib/libXdmcp.so.6.0.0
b70ba000-b70bb000 rwxp 00003000 08:01 7374085    /usr/lib/libXdmcp.so.6.0.0
b70bb000-b70bc000 rwxp b70bb000 00:00 0 
b70bc000-b70be000 r-xp 00000000 08:01 7374074    /usr/lib/libXau.so.6.0.0
b70be000-b70bf000 rwxp 00001000 08:01 7374074    /usr/lib/libXau.so.6.0.0
b70bf000-b71ac000 r-xp 00000000 08:01 7374068    /usr/lib/libX11.so.6.2.0
b71ac000-b71b0000 rwxp 000ed000 08:01 7374068    /usr/lib/libX11.so.6.2.0
b71b0000-b71bd000 r-xp 00000000 08:01 7374089    /usr/lib/libXext.so.6.4.0
b71bd000-b71be000 rwxp 0000d000 08:01 7374089    /usr/lib/libXext.so.6.4.0
b71be000-b71bf000 r-xp 00000000 08:01 7438873    /usr/lib/tls/libnvidia-tls.so.1.0.9631
b71bf000-b71c0000 rwxp 00000000 08:01 7438873    /usr/lib/tls/libnvidia-tls.so.1.0.9631
b71c0000-b7a0d000 r-xp 00000000 08:01 7373531    /usr/lib/libGLcore.so.1.0.9631
b7a0d000-b7a42000 rwxp 0084d000 08:01 7373531    /usr/lib/libGLcore.so.1.0.9631
b7a42000-b7a47000 rwxp b7a42000 00:00 0 
b7a47000-b7a5a000 r-xp 00000000 08:01 17679644   /lib/tls/i686/cmov/libpthread-2.5.so
b7a5a000-b7a5c000 rwxp 00013000 08:01 17679644   /lib/tls/i686/cmov/libpthread-2.5.so
b7a5c000-b7a5e000 rwxp b7a5c000 00:00 0 
b7a5e000-b7a6c000 r-xp 00000000 08:01 7374224    /usr/lib/libdirect-0.9.so.25.0.0
b7a6c000-b7a6d000 rwxp 0000e000 08:01 7374224    /usr/lib/libdirect-0.9.so.25.0.0
b7a6d000-b7a72000 r-xp 00000000 08:01 7374292    /usr/lib/libfusion-0.9.so.25.0.0
b7a72000-b7a73000 rwxp 00004000 08:01 7374292    /usr/lib/libfusion-0.9.so.25.0.0
b7a73000-b7ac8000 r-xp 00000000 08:01 7374226    /usr/lib/libdirectfb-0.9.so.25.0.0
b7ac8000-b7aca000 rwxp 00055000 08:01 7374226    /usr/lib/libdirectfb-0.9.so.25.0.0
b7aca000-b7acc000 r-xp 00000000 08:01 17679624   /lib/tls/i686/cmov/libdl-2.5.so
b7acc000-b7ace000 rwxp 00001000 08:01 17679624   /lib/tls/i686/cmov/libdl-2.5.so
b7ace000-b7acf000 rwxp b7ace000 00:00 0 
b7acf000-b7b8f000 r-xp 00000000 08:01 7374139    /usr/lib/libasound.so.2.0.0
b7b8f000-b7b94000 rwxp 000bf000 08:01 7374139    /usr/lib/libasound.so.2.0.0
b7b94000-b7ccf000 r-xp 00000000 08:01 17679618   /lib/tls/i686/cmov/libc-2.5.so
b7ccf000-b7cd0000 r-xp 0013b000 08:01 17679618   /lib/tls/i686/cmov/libc-2.5.so
b7cd0000-b7cd2000 rwxp 0013c000 08:01 17679618   /lib/tls/i686/cmov/libc-2.5.so
b7cd2000-b7cd5000 rwxp b7cd2000 00:00 0 
b7cd5000-b7ce0000 r-xp 00000000 08:01 17645632   /lib/libgcc_s.so.1
b7ce0000-b7ce1000 rwxp 0000a000 08:01 17645632   /lib/libgcc_s.so.1
b7ce1000-b7d06000 r-xp 00000000 08:01 17679626   /lib/tls/i686/cmov/libm-2.5.so
b7d06000-b7d08000 rwxp 00024000 08:01 17679626   /lib/tls/i686/cmov/libm-2.5.so
b7d08000-b7de7000 r-xp 00000000 08:01 7374765    /usr/lib/libstdc++.so.6.0.8
b7de7000-b7dea000 r-xp 000de000 08:01 7374765    /usr/lib/libstdc++.so.6.0.8
b7dea000-b7dec000 rwxp 000e1000 08:01 7374765    /usr/lib/libstdc++.so.6.0.8
b7dec000-b7df2000 rwxp b7dec000 00:00 0 
b7df2000-b7e63000 r-xp 00000000 08:01 7373530    /usr/lib/libGL.so.1.0.9631
b7e63000-b7e7d000 rwxp 00070000 08:01 7373530    /usr/lib/libGL.so.1.0.9631
b7e7d000-b7e7e000 rwxp b7e7d000 00:00 0 
b7e7e000-b7ea0000 r-xp 00000000 08:01 7374285    /usr/lib/libpng12.so.0.15.0
b7ea0000-b7ea1000 rwxp 00021000 08:01 7374285    /usr/lib/libpng12.so.0.15.0
b7ea1000-b7ea2000 rwxp b7ea1000 00:00 0 
b7ea2000-b7f07000 r-xp 00000000 08:01 7374062    /usr/lib/libSDL-1.2.so.0.11.0
b7f07000-b7f09000 rwxp 00065000 08:01 7374062    /usr/lib/libSDL-1.2.so.0.11.0
b7f09000-b7f31000 rwxp b7f09000 00:00 0 
b7f31000-b7f44000 r-xp 00000000 08:01 7374829    /usr/lib/libz.so.1.2.3
b7f44000-b7f45000 rwxp 00012000 08:01 7374829    /usr/lib/libz.so.1.2.3
b7f53000-b7f54000 rwxp b7f53000 00:00 0 
b7f54000-b7f56000 rwxp 00000000 00:0d 2611       /dev/zero
b7f56000-b7f58000 rwxp b7f56000 00:00 0 
b7f58000-b7f71000 r-xp 00000000 08:01 17645589   /lib/ld-2.5.so
b7f71000-b7f73000 rwxp 00019000 08:01 17645589   /lib/ld-2.5.so
bfbdd000-bfbf3000 rwxp bfbdd000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

This is all really frustrating and over my head, I was just wondering if any of you guys have a deb for version 1.4.2.

---

### Post by aidanr on 2007-09-14
[http://ftp.handhelds.org/mirror/debian/pool/main/z/zsnes/zsnes_1.420-1_i386.deb](http://ftp.handhelds.org/mirror/debian/pool/main/z/zsnes/zsnes_1.420-1_i386.deb)

---

### Post by acoustibop on 2007-09-15
No need for that, even.  ZSNES 1.42 is in the repositories.

---

### Post by disturbedite on 2007-09-15
yeah, in synaptic, just go to force version and pick 1.42.

---

### Post by MaindotC on 2007-11-12
Wow what is up with 1.51 removing netplay?? I tried downloading it in Synaptics but it won't give me the option to force version.  I downloaded and installed the .deb but if I click the icon installed in the games menu, it won't start (haven't checked ps) and if I run it in command line, it just displays a bunch of lines starting with:

*** glibc detected *** zsnes: munmap_chunk(): invalid pointer: 0xbfb27e47 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7bf892b]
zsnes[0x80de151]

Sorry I don't know how to implement code tags.  Any help would be appreciated.

Oh sorry now I see the post below - let's see what that says...

---

### Post by acoustibop on 2007-11-13
I would presume you're running Gutsy, then, strAlan.  All the previous posts in this thread were made in September, before Gutsy's final release.  ZSNES 1.42 was the repository version for Feisty; now, in Gutsy, it's 1.51.

Very possibly, the .deb you're trying is a Feisty .deb, too, and is broken in Gutsy - I would suspect any ZSNES 1.42 .deb you find will be.  You could try compiling from the [source]("http://www.zsnes.com/index.php?page=files") - I did the opposite, compiling 1.51 for Feisty a while back, and AIR it went very easily.

---

### Post by MaindotC on 2007-11-13
You are correct, Acousti.  I was actually trying to follow the aircrack tutorial and had several issues with Gusty (lost my wlan interface after installing the ipwraw driver) and Zsnes 1.51 was the last straw.  I reinstalled 7.04.  I'll hold off on Gusty till it's a little smoother.  Thanks for your reply :)

---

### Post by Kaninepete on 2009-08-11
I installed the .deb from the link up there^ and It didn't show up on the program list.
I typed zsnes in a terminal and it returned:
ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.
Please report crashes to [email]zsnes-devel@lists.sourceforge.net[/email].

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

### Post by overdrank on 2009-08-11
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---


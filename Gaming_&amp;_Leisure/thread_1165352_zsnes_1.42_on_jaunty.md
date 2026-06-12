---
title: "zsnes 1.42 on jaunty"
date: 2009-05-20
forum: Gaming &amp; Leisure
---

### Post by Luiggipro on 2009-05-20
hi guys, I have zbattle.net working but I need zsnes 1.42 to enable netplay. I installed the deb from ubuntu packages website (dapper was the only 1.42, the rest was 1.51 but it hasnt netplay support) but when I tried to launch it I got several errors (terminal), I tried compiling it but got the same errors:
```
luiggi@luiggi-desktop:~$ zsnes

ZSNES vPre 1.43, (c) 1997-2005, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7bf3da8]
/lib/tls/i686/cmov/libc.so.6[0xb7bf1eb0]
zsnes[0x82e58fa]
zsnes[0x804c361]
======= Memory map: ========
08048000-0830d000 r-xp 00000000 08:01 115523     /usr/local/bin/zsnes
0830d000-0830e000 r-xp 002c4000 08:01 115523     /usr/local/bin/zsnes
0830e000-08364000 rwxp 002c5000 08:01 115523     /usr/local/bin/zsnes
08364000-08dcb000 rwxp 08364000 00:00 0 
0a5d1000-0a5f2000 rwxp 0a5d1000 00:00 0          [heap]
b6da6000-b785f000 rwxp b6da6000 00:00 0 
b785f000-b7863000 r-xp 00000000 08:01 9375       /usr/lib/libXdmcp.so.6.0.0
b7863000-b7864000 rwxp 00003000 08:01 9375       /usr/lib/libXdmcp.so.6.0.0
b7864000-b787c000 r-xp 00000000 08:01 10332      /usr/lib/libxcb.so.1.1.0
b787c000-b787d000 r-xp 00017000 08:01 10332      /usr/lib/libxcb.so.1.1.0
b787d000-b787e000 rwxp 00018000 08:01 10332      /usr/lib/libxcb.so.1.1.0
b787e000-b787f000 rwxp b787e000 00:00 0 
b787f000-b7881000 r-xp 00000000 08:01 9364       /usr/lib/libXau.so.6.0.0
b7881000-b7882000 r-xp 00001000 08:01 9364       /usr/lib/libXau.so.6.0.0
b7882000-b7883000 rwxp 00002000 08:01 9364       /usr/lib/libXau.so.6.0.0
b7883000-b796d000 r-xp 00000000 08:01 9358       /usr/lib/libX11.so.6.2.0
b796d000-b796e000 ---p 000ea000 08:01 9358       /usr/lib/libX11.so.6.2.0
b796e000-b796f000 r-xp 000ea000 08:01 9358       /usr/lib/libX11.so.6.2.0
b796f000-b7971000 rwxp 000eb000 08:01 9358       /usr/lib/libX11.so.6.2.0
b7971000-b7972000 rwxp b7971000 00:00 0 
b7972000-b7979000 r-xp 00000000 08:01 6210       /lib/tls/i686/cmov/librt-2.9.so
b7979000-b797a000 r-xp 00006000 08:01 6210       /lib/tls/i686/cmov/librt-2.9.so
b797a000-b797b000 rwxp 00007000 08:01 6210       /lib/tls/i686/cmov/librt-2.9.so
b797b000-b7989000 r-xp 00000000 08:01 9377       /usr/lib/libXext.so.6.4.0
b7989000-b798a000 r-xp 0000d000 08:01 9377       /usr/lib/libXext.so.6.4.0
b798a000-b798b000 rwxp 0000e000 08:01 9377       /usr/lib/libXext.so.6.4.0
b798b000-b799e000 r-xp 00000000 08:01 9561       /usr/lib/libdirect-1.0.so.0.1.0
b799e000-b799f000 r-xp 00012000 08:01 9561       /usr/lib/libdirect-1.0.so.0.1.0
b799f000-b79a0000 rwxp 00013000 08:01 9561       /usr/lib/libdirect-1.0.so.0.1.0
b79a0000-b79a1000 rwxp b79a0000 00:00 0 
b79a1000-b79a8000 r-xp 00000000 08:01 9643       /usr/lib/libfusion-1.0.so.0.1.0
b79a8000-b79a9000 r-xp 00006000 08:01 9643       /usr/lib/libfusion-1.0.so.0.1.0
b79a9000-b79aa000 rwxp 00007000 08:01 9643       /usr/lib/libfusion-1.0.so.0.1.0
b79aa000-b7a0e000 r-xp 00000000 08:01 9563       /usr/lib/libdirectfb-1.0.so.0.1.0
b7a0e000-b7a0f000 r-xp 00063000 08:01 9563       /usr/lib/libdirectfb-1.0.so.0.1.0
b7a0f000-b7a10000 rwxp 00064000 08:01 9563       /usr/lib/libdirectfb-1.0.so.0.1.0
b7a10000-b7a12000 r-xp 00000000 08:01 6186       /lib/tls/i686/cmov/libdl-2.9.so
b7a12000-b7a13000 r-xp 00001000 08:01 6186       /lib/tls/i686/cmov/libdl-2.9.so
b7a13000-b7a14000 rwxp 00002000 08:01 6186       /lib/tls/i686/cmov/libdl-2.9.so
b7a14000-b7ad7000 r-xp 00000000 08:01 9438       /usr/lib/libasound.so.2.0.0
b7ad7000-b7ad9000 r-xp 000c2000 08:01 9438       /usr/lib/libasound.so.2.0.0
b7ad9000-b7adc000 rwxp 000c4000 08:01 9438       /usr/lib/libasound.so.2.0.0
b7adc000-b7af1000 r-xp 00000000 08:01 6206       /lib/tls/i686/cmov/libpthread-2.9.so
b7af1000-b7af2000 r-xp 00014000 08:01 6206       /lib/tls/i686/cmov/libpthread-2.9.so
b7af2000-b7af3000 rwxp 00015000 08:01 6206       /lib/tls/i686/cmov/libpthread-2.9.so
b7af3000-b7af6000 rwxp b7af3000 00:0Cancelado
```

---

### Post by Luiggipro on 2009-05-22
any ideas? :confused: this is getting very frustrating...

---

### Post by Ramage on 2009-05-23
1.42n is a few years old it might use older libraries which are not compatible with the current libs in jaunty. If you are running ubuntu 64 bit that can cause problems too, zsnes needs the compatibility libraries as it uses the 32 bit libraries to compile.

If you are using 64 bit install the 32 bit compatibility dev libraries for ubuntu they are some where in this forum.

If you are already using 32 bit, try to find which libs are failing by reading your error messages and try using older versions of them to compile it (its a long shot and fairly complicated but it may work).

Best thing would be to find a precompiled linux binary of 1.42n that works with debian and use it.

---

### Post by dli8ilb on 2009-08-23
i'm having the same trouble as you, Luiggipro.  let me know if you have found a solution.  one thing i am considering is downloading the windows version of 1.42 and running it though wine.  not sure how well that will work, but it's worth a shot.  

it would also be nice if jaunty had this 1.42 version in it's repos.

---


---
title: "Torcs doesn't start up"
date: 2009-12-31
forum: Gaming &amp; Leisure
---

### Post by echoforever on 2009-12-31
Hi,

This is the first time I am trying to play a game on Ubuntu.

I have installed Torc and when I click on the launcher nothing happens. It seems to crash due to a segmentation fault.

Can anyone help me solve the problem.

```
$ torcs -l
	linux-gate.so.1 =>  (0xb7f45000)
	libalut.so.0 => /usr/lib/libalut.so.0 (0xb7f29000)
	libracescreens.so => /usr/lib/torcs/lib/libracescreens.so (0xb7f1a000)
	librobottools.so => /usr/lib/torcs/lib/librobottools.so (0xb7f14000)
	libclient.so => /usr/lib/torcs/lib/libclient.so (0xb7f10000)
	libconfscreens.so => /usr/lib/torcs/lib/libconfscreens.so (0xb7f02000)
	libtgf.so => /usr/lib/torcs/lib/libtgf.so (0xb7ef7000)
	libtgfclient.so => /usr/lib/torcs/lib/libtgfclient.so (0xb7edf000)
	libtxml.so => /usr/lib/torcs/lib/libtxml.so (0xb7ec0000)
	libplibul.so.1 => /usr/lib/libplibul.so.1 (0xb7eba000)
	libraceengine.so => /usr/lib/torcs/lib/libraceengine.so (0xb7ea7000)
	liblearning.so => /usr/lib/torcs/lib/liblearning.so (0xb7e93000)
	libplibssgaux.so.1 => /usr/lib/libplibssgaux.so.1 (0xb7e61000)
	libplibssg.so.1 => /usr/lib/libplibssg.so.1 (0xb7afb000)
	libplibsm.so.1 => /usr/lib/libplibsm.so.1 (0xb7af7000)
	libplibsl.so.1 => /usr/lib/libplibsl.so.1 (0xb7ad6000)
	libplibsg.so.1 => /usr/lib/libplibsg.so.1 (0xb7ac3000)
	libglut.so.3 => /usr/lib/libglut.so.3 (0xb7a90000)
	libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7a1e000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0xb79b8000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb7992000)
	libz.so.1 => /lib/libz.so.1 (0xb797c000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7978000)
	libopenal.so.1 => /usr/lib/libopenal.so.1 (0xb7635000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb762d000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7622000)
	libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0xb761c000)
	libXmu.so.6 => /usr/lib/libXmu.so.6 (0xb7606000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb75fc000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0xb75a9000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb75a0000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb7587000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7577000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7488000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7399000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7373000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7364000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7200000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb71e7000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb71e4000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb71de000)
	libdrm.so.2 => /usr/lib/libdrm.so.2 (0xb71d4000)
	/lib/ld-linux.so.2 (0xb7f46000)
	libuuid.so.1 => /lib/libuuid.so.1 (0xb71cf000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb71cb000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb71b1000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb71a7000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb71a2000)

```

```
torcs -d
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb) Starting program: /usr/lib/torcs/torcs-bin -l /home/echo/.torcs -L /usr/lib/torcs -D /usr/share/games/torcs
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
Visual Properties Report
------------------------
Compatibility mode, properties unknown.
[New Thread 0xb71f1710 (LWP 14026)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb71f1710 (LWP 14026)]
0x00000000 in ?? ()
(gdb) quit
The program is running.  Exit anyway? (y or n) [answered Y; input not from terminal]
```

```
$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82865G Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

```
$ ps -eaf | grep meta
echo     12360 12261  0 18:35 ?        00:00:02 metacity
```

---

### Post by echoforever on 2010-01-01
The problem is not just restricted to torcs. I have installed racer and ppracer and they too do not function. 

Any idea if this is related to xserver-xorg-video-intel-2.4?
I went back to using v2.4 drivers after X refused to start up.
I don't remember the error now, ](*,) but a lot of user facing that problem fixed it by reverting back to v2.4 as explained in this guide:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by echoforever on 2010-01-05
I have removed xserver-xorg-video-intel-2.4 and installed latest xserver-xorg-video-intel package. I am able to start the games at last. I ma bale to play the games, but torcs is damn slow.

---


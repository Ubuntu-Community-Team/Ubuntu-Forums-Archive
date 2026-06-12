---
title: "X fails with Signal 11 (SEGV), using Nvidia Drivers"
date: 2009-03-09
forum: General Help
---

### Post by armon_d on 2009-03-09
I use Ubuntu Server 8.04, and my use of a graphical display is limited to starting xinit and then xbmc.
However, I can no longer launch xbmc (or boxee) because every time I attempt to do so, I get the following:

Backtrace:
0: X(xf86SigHandler+0x6a) [0x48402a]
1: /lib/libc.so.6 [0x7fe9f1464100]
2: /lib/libc.so.6(memcpy+0x67) [0x7fe9f14aed57]
3: /usr/lib/xorg/modules//libfb.so(fbBlt+0x9e4) [0x7fe9ee80ddb4]
4: /usr/lib/xorg/modules//libfb.so(fbOddTile+0x14c) [0x7fe9ee81997c]
5: /usr/lib/xorg/modules//libfb.so(fbFillRegionTiled+0x1db) [0x7fe9ee81a0fb]
6: /usr/lib/xorg/modules/drivers//nvidia_drv.so(_nv000764X+0xe6) [0x7fe9eef03216]

Fatal server error:
Caught signal 11.  Server aborting

Kernel:
Linux 2.6.24-23-server #1 SMP Mon Jan 26 01:36:05 UTC 2009 x86_64 GNU/Linux

armon@armon:/var/log$ dpkg --list | grep nvidia
ii  nvidia-glx-new                             169.12+2.6.24.16-23.56                                     NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu8                                          NVIDIA binary kernel module common files
ii  nvidia-settings                            1.0+20080304-0ubuntu1.1                                    Tool of configuring the NVIDIA graphics driver

Any thoughts? I ran boxee once, and it crashed X but after a reboot it seems that xbmc no longer works either. Launching firefox or glxgears in xinit works fine however. Any help would be appreciated.

---


---
title: "problem with the last kernel"
date: 2006-08-23
forum: Desktop Environments
---

### Post by dids22 on 2006-08-23
when i  boot from the last kernel (2.6.15-26-386)
i get eror about my xserver(faild start x server..... it's likly that it's not set correcly), the  output of  the log "xorg.0.log" is:
```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux chch-desktop 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 23 14:28:34 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 0000,0000 rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1458,0c11 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1458,0c11 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1458,5004 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 1458,e000 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:06:0: chip 10de,00ea card 1458,a002 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1458,5002 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1458,b002 rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,00f1 card 1682,2119 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:0b:0: chip 11ab,4320 card 1458,e000 rev 13 class 02,00,00 hdr 00
(II) PCI: 02:0d:0: chip 1095,3512 card 1095,6512 rev 01 class 01,04,00 hdr 00
(II) PCI: 02:0e:0: chip 104c,8025 card 1458,1000 rev 01 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfaffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
	[4] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[5] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[6] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[7] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfb000000 - 0xfcffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] rev 162, Mem @ 0xf8000000/24, 0xe0000000/28, 0xf9000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfc004000 - 0xfc007fff (0x4000) MX[B]
	[1] -1	0	0xfc008000 - 0xfc0087ff (0x800) MX[B]
	[2] -1	0	0xfc009000 - 0xfc0091ff (0x200) MX[B]
	[3] -1	0	0xfc000000 - 0xfc003fff (0x4000) MX[B]
	[4] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[5] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[6] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[7] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[8] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[15] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[16] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[17] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[18] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[29] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[30] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfc004000 - 0xfc007fff (0x4000) MX[B]
	[1] -1	0	0xfc008000 - 0xfc0087ff (0x800) MX[B]
	[2] -1	0	0xfc009000 - 0xfc0091ff (0x200) MX[B]
	[3] -1	0	0xfc000000 - 0xfc003fff (0x4000) MX[B]
	[4] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[5] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[6] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[7] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[8] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[15] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[16] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[17] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[18] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[29] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[30] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfc004000 - 0xfc007fff (0x4000) MX[B]
	[5] -1	0	0xfc008000 - 0xfc0087ff (0x800) MX[B]
	[6] -1	0	0xfc009000 - 0xfc0091ff (0x200) MX[B]
	[7] -1	0	0xfc000000 - 0xfc003fff (0x4000) MX[B]
	[8] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[9] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[10] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[11] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[12] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[13] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[14] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[21] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[22] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[23] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[24] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[33] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[34] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[35] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[36] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[37] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfc004000 - 0xfc007fff (0x4000) MX[B]
	[5] -1	0	0xfc008000 - 0xfc0087ff (0x800) MX[B]
	[6] -1	0	0xfc009000 - 0xfc0091ff (0x200) MX[B]
	[7] -1	0	0xfc000000 - 0xfc003fff (0x4000) MX[B]
	[8] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[9] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[10] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[11] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[12] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[13] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[14] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[21] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[22] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[23] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[24] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[33] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[34] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[35] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[36] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[37] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfc004000 - 0xfc007fff (0x4000) MX[B]
	[5] -1	0	0xfc008000 - 0xfc0087ff (0x800) MX[B]
	[6] -1	0	0xfc009000 - 0xfc0091ff (0x200) MX[B]
	[7] -1	0	0xfc000000 - 0xfc003fff (0x4000) MX[B]
	[8] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[9] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[10] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[11] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[12] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[13] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[14] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[24] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[25] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[26] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[27] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[29] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[30] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[31] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[32] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[33] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[34] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[35] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[36] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[37] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[38] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[39] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[40] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[41] 0	0	0xfa0003b0 - 0xfa0003bb (0xc) IS[B]
	[42] 0	0	0xfa0003c0 - 0xfa0003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

on the other virsion i dont get this problem(now i'am working on kernel 2.6.15-25-386)

u know how can i fix the problem?

btw
i use nvidia driver
sry about my english(how is she?:rolleyes: )

thnks

---

### Post by dids22 on 2006-08-23
someone?

---

### Post by dids22 on 2006-08-27
just if someone get this problem:
reinstall the module for your kernel

---

### Post by Ramses de Norre on 2006-08-27
You wont have this problem if you install linux-amd64-k8.

---

### Post by christhemonkey on 2006-08-27
You need to change the graphics driver in your xorg.conf from nvidia to nv as you need to reinstall the nvidia driver for each individual kernel you install.
```
sudo vi /etc/X11/xorg.conf 
```
Then find the line saying:
```
driver   "nvidia" 
```
And change it to:
```
driver   "nv" 
```
Then type "ZZ" (without quotes) to save and quit.
Then restart your X server to login:
```
sudo /etc/init.d/gdm restart 
```#
You can reinstall the offical nvidia drivers later if you desire 3D acceleration.

A meta-package like linux-amd64-k8 will automatically reinstall the resticted-modules package that you need every time you upgrade your kernel.

---


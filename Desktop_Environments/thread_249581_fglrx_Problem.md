---
title: "fglrx Problem"
date: 2006-09-02
forum: Desktop Environments
---

### Post by burty89 on 2006-09-02
For some reason fglrx randomly crashes the X server (I'm using Xgl), leaving me at a command prompt and unable to restart Xgl or even regular X.

In my xorg.94.log.old file (.old because I'm looking at it after restarting) I see that fglrx has managed to cause a signal 11 (segfault I think).

Here is my xorg.94.log.old file:

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux paul-laptop 2.6.17.11 #1 Fri Sep 1 13:38:02 BST 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.94.log", Time: Sun Sep  3 00:05:33 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
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
(II) PCI: 00:00:0: chip 1002,5950 card 103c,30ae rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 1002,5a37 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:13:0: chip 1002,4374 card 1002,4374 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 1002,4375 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 1002,4373 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,30ae rev 11 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,30ae rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 0000,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 103c,30ae rev 02 class 04,01,00 hdr 80
(II) PCI: 00:14:6: chip 1002,4378 card 103c,30ae rev 02 class 07,03,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,5955 card 103c,30ae rev 00 class 03,00,00 hdr 00
(II) PCI: 06:02:0: chip 14e4,4318 card 103c,1356 rev 02 class 02,80,00 hdr 00
(II) PCI: 06:06:0: chip 10ec,8139 card 103c,30a4 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc0100000 - 0xc01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:5:0), (0,2,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:20:4), (0,6,7), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xc0200000 - 0xc02fffff (0x100000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE) rev 0, Mem @ 0xc8000000/27, 0xc0100000/16, I/O @ 0x9000/8
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
(II) Active PCI resource ranges:
	[0] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[1] -1	0	0xc0200000 - 0xc0201fff (0x2000) MX[B]
	[2] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[3] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[4] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[5] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[6] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[8] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[11] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[12] -1	0	0x00008420 - 0x00008420 (0x1) IX[B]
	[13] -1	0	0x00008428 - 0x00008428 (0x1) IX[B]
	[14] -1	0	0x00008424 - 0x00008424 (0x1) IX[B]
	[15] -1	0	0x00008430 - 0x00008430 (0x1) IX[B]
	[16] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[17] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[1] -1	0	0xc0200000 - 0xc0201fff (0x2000) MX[B]
	[2] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[3] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[4] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[5] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[6] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[8] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[11] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[12] -1	0	0x00008420 - 0x00008420 (0x1) IX[B]
	[13] -1	0	0x00008428 - 0x00008428 (0x1) IX[B]
	[14] -1	0	0x00008424 - 0x00008424 (0x1) IX[B]
	[15] -1	0	0x00008430 - 0x00008430 (0x1) IX[B]
	[16] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[17] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
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
	[4] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[5] -1	0	0xc0200000 - 0xc0201fff (0x2000) MX[B]
	[6] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[7] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[8] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[9] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[10] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[18] -1	0	0x00008420 - 0x00008420 (0x1) IX[B]
	[19] -1	0	0x00008428 - 0x00008428 (0x1) IX[B]
	[20] -1	0	0x00008424 - 0x00008424 (0x1) IX[B]
	[21] -1	0	0x00008430 - 0x00008430 (0x1) IX[B]
	[22] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.28.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
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
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9250/9200 Series (RV280 5961),
	RADEON 9250/9200 Series (RV280 5962),
	RADEON 9250/9200 Series (RV280 5964), FireMV 2200 PCI (RV280 5965),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
	RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
	RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300/X550 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
	MOBILITY RADEON X600 SE (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600/X550 Series (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 GTO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), FireGL V7200 (R480 5D50),
	RADEON X850 XT (R480 5D52), RADEON X850 (R481 4B48),
	RADEON X850 XT (R481 4B49), RADEON X850 SE (R481 4B4A),
	RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), RADEON X700 XT (RV410 5E4A),
	RADEON X700 PRO (RV410 5E4B), RADEON X700 SE (RV410 5E4C),
	RADEON X700 (RV410 5E4D), RADEON X700/X550 Series (RV410 5E4F),
	MOBILITY RADEON X700 (M26 5652), MOBILITY RADEON X700 (M26 5653),
	MOBILITY RADEON X700 XL (M26-XC 564F),
	RADEON 9000/9100 IGP Series (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000 IGP (RL300MB 7835),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 XT (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
	FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
	MOBILITY FireGL V7100 (M58 7106), RADEON X1800 Series (R520 7108),
	RADEON X1800 Series (R520 7109), RADEON X1800 Series (R520 710A),
	RADEON X1800 Series (R520 710B), RADEON X1800 Series (R520 710C),
	FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1600 Series (RV515 7140), RADEON X1300 Series (RV515 7142),
	MOBILITY FireGL (M54 GL 7144), MOBILITY RADEON X1400 (M54 7145),
	RADEON X1300 Series (RV515 7146), MOBILITY RADEON X1300 (M52 7149),
	MOBILITY RADEON X1300 (M52 714A), RADEON X1300 Series (RV515 714D),
	RADEON X1300 Series (RV515 714E), FireGL V3300 (RV515 7152),
	RADEON X1300 Series (RV515 715E), RADEON X1300 (RV516 7180),
	RADEON X1600 Series (RV516 7181), RADEON X1300 (RV516 7183),
	MOBILITY RADEON X1450 (M64P 7186), RADEON X1300 (RV516 7187),
	MOBILITY RADEON X1350 (M62P 718B),
	MOBILITY RADEON X1350 (M62CSP 718C),
	MOBILITY RADEON X1450 (M64CSP 718D),
	MOBILITY RADEON X1350 (M62S 7196), RADEON X1900 (R580 7240),
	RADEON X1900 (R580 7243), RADEON X1900 (R580 7244),
	RADEON X1900 (R580 7245), RADEON X1900 (R580 7246),
	RADEON X1900 (R580 7247), RADEON X1900 (R580 7248),
	RADEON X1900 (R580 7249), RADEON X1900 (R580 724A),
	RADEON X1900 (R580 724B), RADEON X1900 (R580 724C),
	RADEON X1900 (R580 724D), FireStream 2U (R580 724E),
	FireStream 2U (R580 724F), RADEON X1600 Series (RV530 71C0),
	RADEON X1600 Series (RV530 71C2), MOBILITY FireGL V5200 (M56 71C4),
	MOBILITY RADEON X1600 (M56 71C5),
	RADEON X1600 Series (RV530 LE 71C6),
	RADEON X1600 Series (RV530 VE 71CE), FireGL V3400 (RV530 71D2),
	MOBILITY RADEON X1700 (M66-XT 71D6), FireGL V5200 (RV530 71DA),
	RADEON X1600 Series (RV530 SE 71DE), RADEON X1600 XT (RV535 XT 71C1),
	MOBILITY FireGL V5250 (M66GL 71D4),
	MOBILITY RADEON X1700 (M66-P 71D5), RADEON Xpress 1200 (RS600 7941),
	RADEON Xpress 1200 (RS600 7942)
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.28.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.28g1                           
(II) ATI Proprietary Linux Driver Build Date: Aug 17 2006 09:26:25
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.28.1.1.2.3-driver-lnx-x86-x86_64-287161
(--) Assigning device section with no busID to primary device
(--) Chipset RADEON XPRESS 200M (RS480 5955) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[5] -1	0	0xc0200000 - 0xc0201fff (0x2000) MX[B]
	[6] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[7] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[8] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[9] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[10] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[18] -1	0	0x00008420 - 0x00008420 (0x1) IX[B]
	[19] -1	0	0x00008428 - 0x00008428 (0x1) IX[B]
	[20] -1	0	0x00008424 - 0x00008424 (0x1) IX[B]
	[21] -1	0	0x00008430 - 0x00008430 (0x1) IX[B]
	[22] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81dbad0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[5] -1	0	0xc0200000 - 0xc0201fff (0x2000) MX[B]
	[6] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[7] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[8] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[9] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[10] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[20] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[21] -1	0	0x00008420 - 0x00008420 (0x1) IX[B]
	[22] -1	0	0x00008428 - 0x00008428 (0x1) IX[B]
	[23] -1	0	0x00008424 - 0x00008424 (0x1) IX[B]
	[24] -1	0	0x00008430 - 0x00008430 (0x1) IX[B]
	[25] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[26] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[27] 0	0	0xc01203b0 - 0xc01203bb (0xc) IS[B]
	[28] 0	0	0xc01203c0 - 0xc01203df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "NoAccel" "no"
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): Option "Capabilities" "0x00000000"
(**) fglrx(0): Option "CapabilitiesEx" "0x00000000"
(**) fglrx(0): Option "KernelModuleParm" "agplock=0"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DesktopSetup" "Single"
(**) fglrx(0): Option "ScreenOverlap" "0"
(**) fglrx(0): Option "UseInternalAGPGART" "no"
(**) fglrx(0): Option "Stereo" "off"
(**) fglrx(0): Option "StereoSyncEnable" "1"
(**) fglrx(0): Option "UseFastTLS" "0"
(**) fglrx(0): Option "BlockSignalsOnLock" "on"
(**) fglrx(0): Option "ForceGenericCPU" "no"
(**) fglrx(0): Option "CenterMode" "off"
(**) fglrx(0): Option "FSAAScale" "1"
(**) fglrx(0): Option "FSAAEnable" "no"
(**) fglrx(0): Option "FSAADisableGamma" "no"
(**) fglrx(0): Option "FSAACustomizeMSPos" "no"
(**) fglrx(0): Option "FSAAMSPosX0" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY0" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX1" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY1" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX2" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY2" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX3" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY3" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX4" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY4" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX5" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY5" "0.000000"
(**) fglrx(0): Option "PseudoColorVisuals" "off"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Option "mtrr" "on"
(--) fglrx(0): Chipset: "RADEON XPRESS 200M (RS480 5955)" (Chipset = 0x5955)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x30ae)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc8000000
(--) fglrx(0): MMIO registers at 0xc0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(EE) fglrx(0): vm86() syscall generated signal 11.
(II) fglrx(0): EAX=0x00004f00, EBX=0x00000000, ECX=0x00000000, EDX=0x00000000
(II) fglrx(0): ESP=0x00000ffa, EBP=0x00000000, ESI=0x00000000, EDI=0x00002000
(II) fglrx(0): CS=0xfff6, SS=0x0100, DS=0x0040, ES=0x0000, FS=0x0000, GS=0x0000
(II) fglrx(0): EIP=0x0000f6f6, EFLAGS=0x00033202
(II) fglrx(0): code at 0x0010f656:

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/Xorg(xf86SigHandler+0x86) [0x80b4ab6]
1: [0xffffe420]
2: /usr/lib/xorg/modules/libint10.so(dump_code+0x74) [0xb7a54f82]
3: /usr/lib/xorg/modules/libint10.so(xf86ExecX86int10+0xf2) [0xb7a56b87]
4: /usr/lib/xorg/modules/libvbe.so(VBEExtendedInit+0xa7) [0xb7a4e347]
5: /usr/lib/xorg/modules/libvbe.so(VBEInit+0x2c) [0xb7a4e725]
6: /usr/lib/xorg/modules/drivers/fglrx_drv.so [0xb733af8e]
7: /usr/lib/xorg/modules/drivers/fglrx_drv.so [0xb73419eb]
8: /usr/lib/xorg/modules/drivers/fglrx_drv.so(R200PreInit+0x62d) [0xb733b7ad]
9: /usr/bin/Xorg(InitOutput+0x9b8) [0x809e3f8]
10: /usr/bin/Xorg(main+0x292) [0x806deee]
11: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7ddeea2]
12: /usr/bin/Xorg(FontFileCompleteXLFD+0x85) [0x806d641]

Fatal server error:
Caught signal 11.  Server aborting

```

The whole system works fine until this happens after its been running for a while. The only other problem I have (which I doubt is related), is that if I take a screenshot whilst compiz is running it ends up distorted as a bunch of seemingly random pixels. The same happens to the screen when I click shutdown or need to enter the admin password (essentially when the screen is dimmed), I assume that the dimming works by taking a screenshot and then dimming that...

---

### Post by Anduu on 2006-09-03
XGL is still considered testing/unstable...there are bound to be problems.

---


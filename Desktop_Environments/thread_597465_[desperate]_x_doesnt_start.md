---
title: "[desperate] x doesnt start"
date: 2007-10-30
forum: Desktop Environments
---

### Post by j0sh78 on 2007-10-30
hi all
i upgraded to 7.10 some days ago
all right but today x dont start... i didnt make modifications or next installations

my xorg log

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 30 19:28:43 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc M24 1P [Radeon Mobility X600]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2590 card 1025,0066 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2591 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 04 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2662 card 0000,0000 rev 04 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,2664 card 0000,0000 rev 04 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 1025,0066 rev 04 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1025,0066 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1025,0066 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1025,0066 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1025,0066 rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev d4 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,266e card 1025,0066 rev 04 class 04,01,00 hdr 00
(II) PCI: 00:1e:3: chip 8086,266d card 1025,0066 rev 04 class 07,03,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,2641 card 1025,0066 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 1025,0066 rev 04 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 1025,0066 rev 04 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,3150 card 1025,0066 rev 00 class 03,00,00 hdr 00
(II) PCI: 06:01:0: chip 104c,8031 card 4000,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 06:01:2: chip 104c,8032 card 1025,0066 rev 00 class 0c,00,10 hdr 80
(II) PCI: 06:01:3: chip 104c,8033 card 1025,0066 rev 00 class 01,80,00 hdr 80
(II) PCI: 06:03:0: chip 8086,4220 card 8086,2701 rev 05 class 02,80,00 hdr 00
(II) PCI: 06:08:0: chip 14e4,4401 card 1025,0066 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,10), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc8100000 - 0xc81fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 9: bridge is at (0:28:0), (0,9,9), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 10: bridge is at (0:28:1), (0,10,10), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:2), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,8), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xc8200000 - 0xc82fffff (0x100000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x8bffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (6:1:0), (6,7,8), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 7 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x8bffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc M24 1P [Radeon Mobility X600] rev 0, Mem @ 0xd0000000/27, 0xc8100000/16, I/O @ 0x3000/8
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
	[0] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[1] -1	0	0xc820b000 - 0xc820bfff (0x1000) MX[B]
	[2] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[3] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[4] -1	0	0xc8209000 - 0xc82097ff (0x800) MX[B]
	[5] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[6] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[7] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[8] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[11] -1	0	0x000018c0 - 0x000018cf (0x10) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[17] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[18] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[19] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[20] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[24] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[1] -1	0	0xc820b000 - 0xc820bfff (0x1000) MX[B]
	[2] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[3] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[4] -1	0	0xc8209000 - 0xc82097ff (0x800) MX[B]
	[5] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[6] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[7] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[8] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[11] -1	0	0x000018c0 - 0x000018cf (0x10) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[17] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[18] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[19] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[20] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[24] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
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
	[4] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[5] -1	0	0xc820b000 - 0xc820bfff (0x1000) MX[B]
	[6] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[7] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[8] -1	0	0xc8209000 - 0xc82097ff (0x800) MX[B]
	[9] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[10] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[11] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[12] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[17] -1	0	0x000018c0 - 0x000018cf (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[23] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[24] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[25] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[30] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 01:00:0
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(--) Chipset ATI Radeon Mobility X600 (M24) 3150 (PCIE) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[5] -1	0	0xc820b000 - 0xc820bfff (0x1000) MX[B]
	[6] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[7] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[8] -1	0	0xc8209000 - 0xc82097ff (0x800) MX[B]
	[9] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[10] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[11] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[12] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[17] -1	0	0x000018c0 - 0x000018cf (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[23] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[24] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[25] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[30] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[5] -1	0	0xc820b000 - 0xc820bfff (0x1000) MX[B]
	[6] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[7] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[8] -1	0	0xc8209000 - 0xc82097ff (0x800) MX[B]
	[9] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[10] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[11] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[12] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[20] -1	0	0x000018c0 - 0x000018cf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[26] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[27] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[28] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[33] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xc8100000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon Mobility X600 (M24) 3150 (PCIE)" (ChipID = 0x3150)
(--) RADEON(0): Linear framebuffer at 0xd0000000
(II) RADEON(0): PCIE card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.27.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=65536K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2560x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(0): PLL parameters: rf=2700 rd=6 min=20000 max=40000; xclk=25000
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-3, DACType-0, TMDSType-0, ConnectorType-2
(II) RADEON(0): Port1: DDCType-2, DACType-0, TMDSType-0, ConnectorType-4
(II) RADEON(0): Port4: DDCType-0, DACType-2, TMDSType-2, ConnectorType-1
(II) RADEON(0): Port5: DDCType-0, DACType-1, TMDSType-2, ConnectorType-6
(II) RADEON(0): Output VGA-0 using monitor section Generic Monitor
(II) RADEON(0): I2C bus "VGA_DDC" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI_DDC" initialized.
(II) RADEON(0): DFP table revision: 4
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Panel ID string: LGP                     
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1024, YRes: 768, DotClock: 65000
HBlank: 320, HOverPlus: 24, HSyncWidth: 136
VBlank: 38, VOverPlus: 3, VSyncWidth: 6
(II) RADEON(0): Using LVDS Native Mode
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- VGA_DDC
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-D
 DAC Type  -- None
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- Proprietary/LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- None
(II) RADEON(0): Port3:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- None
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
finished output detect: 1
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
finished output detect: 2
finished output detect: 3
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
(II) RADEON(0): Output LVDS connected
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x768" (exceeds panel dimensions)
(II) RADEON(0): Not using default mode "1280x800" (exceeds panel dimensions)
(II) RADEON(0): Not using default mode "1152x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "1920x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output LVDS using initial mode 1024x768
after xf86InitialConfiguration
(++) RADEON(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc8100000 - 0xc810ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[7] -1	0	0xc820b000 - 0xc820bfff (0x1000) MX[B]
	[8] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[9] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[10] -1	0	0xc8209000 - 0xc82097ff (0x800) MX[B]
	[11] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[12] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[13] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[14] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[23] -1	0	0x000018c0 - 0x000018cf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[29] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[30] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[31] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[32] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[33] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[34] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[35] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[36] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xd0000000,0x4000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(II) RADEON(0): Dynamic Clock Scaling Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,1024) to (1024,1026)
(II) RADEON(0): Largest offscreen area available: 1024 x 7165
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x1100000
(II) RADEON(0): Will use depth buffer at offset 0x1500000
(II) RADEON(0): Will use 32 kb for PCI GART table at offset 0x3ff8000
(II) RADEON(0): Will use 39936 kb for textures at offset 0x1900000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] DRM interface version 1.3
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xf8ad2000
(II) RADEON(0): [drm] mapped SAREA 0xf8ad2000 to 0xb7b1b000
(II) RADEON(0): [drm] framebuffer handle = 0xd0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [pci] 8192 kB allocated with handle 0xf8d4b000
(II) RADEON(0): [pci] ring handle = 0xf8d4b000
(II) RADEON(0): [pci] Ring mapped at 0xb7a1a000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xf8e4c000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb7a19000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf8e4d000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xb3745000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xf904d000
(II) RADEON(0): [pci] GART Texture map mapped at 0xb3265000
(II) RADEON(0): [drm] register handle = 0xc8100000
(II) RADEON(0): [dri] Visual configs initialized
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 2
(==) RADEON(0): Backing store disabled
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1026)
(II) RADEON(0): Largest offscreen area available: 1024 x 7161
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 260 x 195
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
enable montype: 2
disable montype: 2
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xf8ad2000 at 0xb7b1b000
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
```

my xorg.conf

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

please help me...

---

### Post by DaGrimReefah on 2007-10-30
Have you tried:
```
sudo-dpkg reconfigure-xorg
```?

---

### Post by j0sh78 on 2007-10-30
yes... don't work... :(

after reconfigure this is the xorg log

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 30 19:27:09 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc M24 1P [Radeon Mobility X600]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2590 card 1025,0066 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2591 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 04 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2662 card 0000,0000 rev 04 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,2664 card 0000,0000 rev 04 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 1025,0066 rev 04 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1025,0066 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1025,0066 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1025,0066 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1025,0066 rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev d4 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,266e card 1025,0066 rev 04 class 04,01,00 hdr 00
(II) PCI: 00:1e:3: chip 8086,266d card 1025,0066 rev 04 class 07,03,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,2641 card 1025,0066 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 1025,0066 rev 04 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 1025,0066 rev 04 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,3150 card 1025,0066 rev 00 class 03,00,00 hdr 00
(II) PCI: 06:01:0: chip 104c,8031 card 4000,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 06:01:2: chip 104c,8032 card 1025,0066 rev 00 class 0c,00,10 hdr 80
(II) PCI: 06:01:3: chip 104c,8033 card 1025,0066 rev 00 class 01,80,00 hdr 80
(II) PCI: 06:03:0: chip 8086,4220 card 8086,2701 rev 05 class 02,80,00 hdr 00
(II) PCI: 06:08:0: chip 14e4,4401 card 1025,0066 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,10), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc8100000 - 0xc81fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 9: bridge is at (0:28:0), (0,9,9), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 10: bridge is at (0:28:1), (0,10,10), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:2), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,8), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xc8200000 - 0xc82fffff (0x100000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x8bffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (6:1:0), (6,7,8), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 7 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x8bffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc M24 1P [Radeon Mobility X600] rev 0, Mem @ 0xd0000000/27, 0xc8100000/16, I/O @ 0x3000/8
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
	[0] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[1] -1	0	0xc820b000 - 0xc820bfff (0x1000) MX[B]
	[2] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[3] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[4] -1	0	0xc8209000 - 0xc82097ff (0x800) MX[B]
	[5] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[6] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[7] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[8] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[11] -1	0	0x000018c0 - 0x000018cf (0x10) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[17] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[18] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[19] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[20] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[24] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[1] -1	0	0xc820b000 - 0xc820bfff (0x1000) MX[B]
	[2] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[3] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[4] -1	0	0xc8209000 - 0xc82097ff (0x800) MX[B]
	[5] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[6] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[7] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[8] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[11] -1	0	0x000018c0 - 0x000018cf (0x10) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[17] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[18] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[19] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[20] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[24] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
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
	[4] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[5] -1	0	0xc820b000 - 0xc820bfff (0x1000) MX[B]
	[6] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[7] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[8] -1	0	0xc8209000 - 0xc82097ff (0x800) MX[B]
	[9] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[10] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[11] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[12] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[17] -1	0	0x000018c0 - 0x000018cf (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[23] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[24] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[25] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[30] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 01:00:0
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(--) Chipset ATI Radeon Mobility X600 (M24) 3150 (PCIE) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[5] -1	0	0xc820b000 - 0xc820bfff (0x1000) MX[B]
	[6] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[7] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[8] -1	0	0xc8209000 - 0xc82097ff (0x800) MX[B]
	[9] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[10] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[11] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[12] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[17] -1	0	0x000018c0 - 0x000018cf (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[23] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[24] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[25] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[30] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[5] -1	0	0xc820b000 - 0xc820bfff (0x1000) MX[B]
	[6] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[7] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[8] -1	0	0xc8209000 - 0xc82097ff (0x800) MX[B]
	[9] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[10] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[11] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[12] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[20] -1	0	0x000018c0 - 0x000018cf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[26] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[27] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[28] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[33] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xc8100000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon Mobility X600 (M24) 3150 (PCIE)" (ChipID = 0x3150)
(--) RADEON(0): Linear framebuffer at 0xd0000000
(II) RADEON(0): PCIE card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.27.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=65536K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2560x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(0): PLL parameters: rf=2700 rd=6 min=20000 max=40000; xclk=25000
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-3, DACType-0, TMDSType-0, ConnectorType-2
(II) RADEON(0): Port1: DDCType-2, DACType-0, TMDSType-0, ConnectorType-4
(II) RADEON(0): Port4: DDCType-0, DACType-2, TMDSType-2, ConnectorType-1
(II) RADEON(0): Port5: DDCType-0, DACType-1, TMDSType-2, ConnectorType-6
(II) RADEON(0): Output VGA-0 using monitor section Generic Monitor
(II) RADEON(0): I2C bus "VGA_DDC" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI_DDC" initialized.
(II) RADEON(0): DFP table revision: 4
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Panel ID string: LGP                     
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1024, YRes: 768, DotClock: 65000
HBlank: 320, HOverPlus: 24, HSyncWidth: 136
VBlank: 38, VOverPlus: 3, VSyncWidth: 6
(II) RADEON(0): Using LVDS Native Mode
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- VGA_DDC
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-D
 DAC Type  -- None
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- Proprietary/LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- None
(II) RADEON(0): Port3:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- None
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
finished output detect: 1
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
finished output detect: 2
finished output detect: 3
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
(II) RADEON(0): Output LVDS connected
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x768" (exceeds panel dimensions)
(II) RADEON(0): Not using default mode "1280x800" (exceeds panel dimensions)
(II) RADEON(0): Not using default mode "1152x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "1920x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output LVDS using initial mode 1024x768
after xf86InitialConfiguration
(++) RADEON(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc8100000 - 0xc810ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[7] -1	0	0xc820b000 - 0xc820bfff (0x1000) MX[B]
	[8] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[9] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[10] -1	0	0xc8209000 - 0xc82097ff (0x800) MX[B]
	[11] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[12] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[13] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[14] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[23] -1	0	0x000018c0 - 0x000018cf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[29] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[30] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[31] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[32] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[33] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[34] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[35] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[36] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xd0000000,0x4000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(II) RADEON(0): Dynamic Clock Scaling Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,1024) to (1024,1026)
(II) RADEON(0): Largest offscreen area available: 1024 x 7165
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x1100000
(II) RADEON(0): Will use depth buffer at offset 0x1500000
(II) RADEON(0): Will use 32 kb for PCI GART table at offset 0x3ff8000
(II) RADEON(0): Will use 39936 kb for textures at offset 0x1900000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] DRM interface version 1.3
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xf8ad2000
(II) RADEON(0): [drm] mapped SAREA 0xf8ad2000 to 0xb7b8a000
(II) RADEON(0): [drm] framebuffer handle = 0xd0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [pci] 8192 kB allocated with handle 0xf8d4b000
(II) RADEON(0): [pci] ring handle = 0xf8d4b000
(II) RADEON(0): [pci] Ring mapped at 0xb7a89000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xf8e4c000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb7a88000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf8e4d000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xb37b4000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xf904d000
(II) RADEON(0): [pci] GART Texture map mapped at 0xb32d4000
(II) RADEON(0): [drm] register handle = 0xc8100000
(II) RADEON(0): [dri] Visual configs initialized
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 2
(==) RADEON(0): Backing store disabled
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1026)
(II) RADEON(0): Largest offscreen area available: 1024 x 7161
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 260 x 195
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
enable montype: 2
disable montype: 2
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xf8ad2000 at 0xb7b8a000
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
```

---

### Post by DaGrimReefah on 2007-10-30
What is the error message you get when you try to start x?

---

### Post by j0sh78 on 2007-10-30
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

---


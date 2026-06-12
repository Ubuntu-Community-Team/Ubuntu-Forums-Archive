---
title: "Login stop"
date: 2007-11-03
forum: Desktop Environments
---

### Post by PoeticCapybara on 2007-11-03
I can't login because the login screen just stops before the username prompt. I'm using Gutsy. The timer keeps rotating just a quarter and then starts again and keeps like that forever. I can move it so it's not a freeze but it doesn't evolve...
If I look in the Xorg.0.log it keeps writing Synaptics DeviceOn called at the end for as long as I keep it like that.

Any suggestions?

---

### Post by Happy_Man on 2007-11-03
Are you using a touchpad? If so, something may be screwing it up. Try plugging in a mouse and seeing if that works.

---

### Post by PoeticCapybara on 2007-11-03
I'm using a laptop so there is a touchpad, sorry for missing that. Tried that but it doesn't change anything. It still has the same problem. I tried to comment the synaptics part in xorg.conf but it doesn't work, although it does stop writing all the Synaptics DeviceOn called.

---

### Post by PoeticCapybara on 2007-11-03
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux poeticcapybara 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  3 15:47:25 2007
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
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
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
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
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
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3580 card 1025,0064 rev 02 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 8086,3584 card 1025,0064 rev 02 class 08,80,00 hdr 00
(II) PCI: 00:00:3: chip 8086,3585 card 1025,0064 rev 02 class 08,80,00 hdr 80
(II) PCI: 00:01:0: chip 8086,3581 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1025,0064 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1025,0064 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1025,0064 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1025,0064 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 83 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 1025,0064 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1025,0064 rev 03 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1025,0064 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1025,0064 rev 03 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e50 card 1025,0064 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:02:0: chip 14e4,4401 card 1025,0064 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 8086,4220 card 8086,2701 rev 05 class 02,80,00 hdr 00
(II) PCI: 02:06:0: chip 104c,8031 card 4000,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 02:06:2: chip 104c,8032 card 1025,0064 rev 00 class 0c,00,10 hdr 80
(II) PCI: 02:06:3: chip 104c,8033 card 1025,0064 rev 00 class 01,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
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
	[0] -1	0	0xd0100000 - 0xd01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd0200000 - 0xd05fffff (0x400000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x35ffffff (0x6000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:6:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x33ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] rev 0, Mem @ 0xd8000000/27, 0xd0100000/16, I/O @ 0x3000/8
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xd0206000 - 0xd0207fff (0x2000) MX[B]
	[1] -1	0	0xd0200000 - 0xd0203fff (0x4000) MX[B]
	[2] -1	0	0xd020a000 - 0xd020a7ff (0x800) MX[B]
	[3] -1	0	0xd0208000 - 0xd0208fff (0x1000) MX[B]
	[4] -1	0	0xd0204000 - 0xd0205fff (0x2000) MX[B]
	[5] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[6] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[7] -1	0	0x36000000 - 0x360003ff (0x400) MX[B]
	[8] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[13] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[14] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[15] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[16] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[17] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[23] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[24] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[25] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0206000 - 0xd0207fff (0x2000) MX[B]
	[1] -1	0	0xd0200000 - 0xd0203fff (0x4000) MX[B]
	[2] -1	0	0xd020a000 - 0xd020a7ff (0x800) MX[B]
	[3] -1	0	0xd0208000 - 0xd0208fff (0x1000) MX[B]
	[4] -1	0	0xd0204000 - 0xd0205fff (0x2000) MX[B]
	[5] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[6] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[7] -1	0	0x36000000 - 0x360003ff (0x400) MX[B]
	[8] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[13] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[14] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[15] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[16] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[17] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[23] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[24] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[25] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x35ffffff (0x35f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x35ffffff (0x35f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0206000 - 0xd0207fff (0x2000) MX[B]
	[5] -1	0	0xd0200000 - 0xd0203fff (0x4000) MX[B]
	[6] -1	0	0xd020a000 - 0xd020a7ff (0x800) MX[B]
	[7] -1	0	0xd0208000 - 0xd0208fff (0x1000) MX[B]
	[8] -1	0	0xd0204000 - 0xd0205fff (0x2000) MX[B]
	[9] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[10] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[11] -1	0	0x36000000 - 0x360003ff (0x400) MX[B]
	[12] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[15] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[19] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[20] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[21] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[22] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[23] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[29] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[30] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[31] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.37.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.37g1                           
(II) ATI Proprietary Linux Driver Build Date: May 25 2007 14:25:03
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.37.1.1.2.3-driver-lnx-x86-x86_64-346145
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x4E50) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x35ffffff (0x35f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0206000 - 0xd0207fff (0x2000) MX[B]
	[5] -1	0	0xd0200000 - 0xd0203fff (0x4000) MX[B]
	[6] -1	0	0xd020a000 - 0xd020a7ff (0x800) MX[B]
	[7] -1	0	0xd0208000 - 0xd0208fff (0x1000) MX[B]
	[8] -1	0	0xd0204000 - 0xd0205fff (0x2000) MX[B]
	[9] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[10] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[11] -1	0	0x36000000 - 0x360003ff (0x400) MX[B]
	[12] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[15] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[19] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[20] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[21] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[22] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[23] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[29] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[30] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[31] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8208bb8
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x35ffffff (0x35f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0206000 - 0xd0207fff (0x2000) MX[B]
	[5] -1	0	0xd0200000 - 0xd0203fff (0x4000) MX[B]
	[6] -1	0	0xd020a000 - 0xd020a7ff (0x800) MX[B]
	[7] -1	0	0xd0208000 - 0xd0208fff (0x1000) MX[B]
	[8] -1	0	0xd0204000 - 0xd0205fff (0x2000) MX[B]
	[9] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[10] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[11] -1	0	0x36000000 - 0x360003ff (0x400) MX[B]
	[12] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[15] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[22] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[23] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[24] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[25] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[26] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[32] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[33] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[34] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI MOBILITY RADEON 9600/9700 Series" (Chipset = 0x4e50)
(--) fglrx(0): (PciSubVendor = 0x1025, PciSubDevice = 0x0064)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd8000000
(--) fglrx(0): MMIO registers at 0xd0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 65536 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON 9600   
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: P11 
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 65536 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0): Derived EDID from BIOS and internal tables for Display1:
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: MS_  Model: 0  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 68.9 MHz   Image Size:  0 x 0 mm
(II) fglrx(0): h_active: 1280  h_sync: 1296  h_sync_end 1328 h_blank_end 1408 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 816 v_border: 0
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00367f000000000000
(II) fglrx(0): 	0000010380281e00f200000000000000
(II) fglrx(0): 	00000021080031404540614000000000
(II) fglrx(0): 	000000000000ea1a0080502010301020
(II) fglrx(0): 	44000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	0000000000000000000000000000002d
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  2 power states available:
(II) fglrx(0):   1. 452/209MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 105/105MHz @ 60Hz [low voltage, enable sleep]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 13 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   68.90  1280 1296 1328 1408  800 804 808 816
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   68.90  1024 1168 1200 1408  768 788 792 816
(**) fglrx(0): *Mode "848x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   68.90  848 1080 1112 1408  480 644 648 816
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   68.90  800 1056 1088 1408  600 704 708 816
(**) fglrx(0): *Mode "720x576": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   68.90  720 1016 1048 1408  576 692 696 816
(**) fglrx(0): *Mode "720x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   68.90  720 1016 1048 1408  480 644 648 816
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   68.90  640 976 1008 1408  480 644 648 816
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   68.90  640 976 1008 1408  400 604 608 816
(**) fglrx(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   68.90  640 976 1008 1408  350 579 583 816
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   68.90  512 912 944 1408  384 596 600 816
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   68.90  400 856 888 1408  300 704 708 816 doublescan
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   68.90  320 816 848 1408  240 644 648 816 doublescan
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   68.90  320 816 848 1408  200 604 608 816 doublescan
(--) fglrx(0): Display dimensions: (400, 300) mm
(--) fglrx(0): DPI set to (81, 67)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   68.90  1280 1296 1328 1408  800 804 808 816
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   68.90  1024 1168 1200 1408  768 788 792 816
(**) fglrx(0): *Mode "848x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   68.90  848 1080 1112 1408  480 644 648 816
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   68.90  800 1056 1088 1408  600 704 708 816
(**) fglrx(0): *Mode "720x576": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   68.90  720 1016 1048 1408  576 692 696 816
(**) fglrx(0): *Mode "720x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   68.90  720 1016 1048 1408  480 644 648 816
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   68.90  640 976 1008 1408  480 644 648 816
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   68.90  640 976 1008 1408  400 604 608 816
(**) fglrx(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   68.90  640 976 1008 1408  350 579 583 816
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   68.90  512 912 944 1408  384 596 600 816
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   68.90  400 856 888 1408  300 704 708 816 doublescan
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   68.90  320 816 848 1408  240 644 648 816 doublescan
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   68.90  320 816 848 1408  200 604 608 816 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) LoadModule: "glesx.so" (glesx)
(WW) LoadModule: given non-canonical module name "glesx.so"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0100000 - 0xd010ffff (0x10000) MX[B]
	[1] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x35ffffff (0x35f00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd0206000 - 0xd0207fff (0x2000) MX[B]
	[7] -1	0	0xd0200000 - 0xd0203fff (0x4000) MX[B]
	[8] -1	0	0xd020a000 - 0xd020a7ff (0x800) MX[B]
	[9] -1	0	0xd0208000 - 0xd0208fff (0x1000) MX[B]
	[10] -1	0	0xd0204000 - 0xd0205fff (0x2000) MX[B]
	[11] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[12] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[13] -1	0	0x36000000 - 0x360003ff (0x400) MX[B]
	[14] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[15] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[16] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[17] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[25] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[26] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[27] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[28] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[29] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[35] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[36] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[37] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb78b7000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.37.6
(II) fglrx(0):     Date: May 25 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 6.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] Mode=0x1f000217 bridge: 0x8086/0x3580
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000314
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xe0000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000314)
(II) fglrx(0): [agp] graphics chipset has AGP v2.0
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd8000000 FBMappedSize: 0x005e9000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1210)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): GLESX enableFlags = 0
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
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
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
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
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Synaptics DeviceOff called
Synaptics DeviceOn called
Synaptics DeviceOn called
Synaptics DeviceOn called
Synaptics DeviceOn called
 and so on with Synaptics DeviceOn called

```

---

### Post by Happy_Man on 2007-11-03
Try booting into safe mode and see if that works. If it doesn't, we'll know it's not the GUI that's screwing up. If it does boot into it fine, post back and we'll work from there.

---

### Post by chudder on 2008-01-06
I just developed a similar problem today.  I boot the laptop and it seems fine and then it gets to the login screen and the mouse can be moved but when I type it takes about 30 seconds to a minute for the letters to appear.  The password prompt can be quick or slow at random.  A week ago I enabled the synaptics touchpad scroll and disabling it when key strokes are being typed.  I turned off the start process for that and still had the problem.  I have a Toshiba Satellite A-105.  

Thank you for any help.

Chudder

---


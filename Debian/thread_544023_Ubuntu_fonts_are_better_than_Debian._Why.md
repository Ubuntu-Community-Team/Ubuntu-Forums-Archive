---
title: "Ubuntu fonts are better than Debian. Why?"
date: 2007-09-05
forum: Debian
---

### Post by hrod beraht on 2007-09-05
I just installed Debian Etch.
I've been a Ubuntu user for quite a while and wanted to check out the mothership distro from which Ubuntu sprang.

Long story short, the biggest difference I noticed was that the default Debian fonts didn't seem to be nearly as nice as with Ubuntu. They were often small and quite blocky (not a sub-pixel rendering problem, I don't believe - CRT).

I looked at all of the conf files I could think of, but couldn't really see a difference for fonts between Debian and Ubuntu.

What is it that makes them look better in Ubuntu?!?
I love Etch other than that. I hope you can help me figure it out.

Bob

---

### Post by kerry_s on 2007-09-05
there is no difference, there the same fonts from the same source. have you checked your /var/log/xorg.0.log for errors(EE) it should be free of errors.

mine, just installed about 4 hours ago->

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Debian (xorg-server 2:1.3.0.0.dfsg-12)
Current Operating System: Linux debian 2.6.21-2-686 #1 SMP Wed Jul 11 03:53:02 UTC 2007 i686
Build Date: 09 August 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep  5 14:52:57 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "AIGLX" "off"
(==) FontPath set to:
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
(II) Loader magic: 0x81e5140
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
(--) using VT number 3

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7190 card 104d,806f rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7191 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 8086,7110 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:07:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 8086,7113 card 0000,0000 rev 03 class 06,80,00 hdr 00
(II) PCI: 00:08:0: chip 104d,8039 card 104d,8071 rev 02 class 0c,00,10 hdr 00
(II) PCI: 00:09:0: chip 1073,0010 card 104d,8072 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:0a:0: chip 127a,2005 card 104d,8074 rev 01 class 07,08,00 hdr 00
(II) PCI: 00:0c:0: chip 1180,0478 card 1400,0000 rev 80 class 06,07,00 hdr 82
(II) PCI: 00:0c:1: chip 1180,0478 card 1c00,0000 rev 80 class 06,07,00 hdr 82
(II) PCI: 01:00:0: chip 10c8,0005 card 104d,8070 rev 20 class 03,00,00 hdr 00
(II) PCI: 06:00:0: chip 1113,1216 card 111a,1012 rev 11 class 02,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x008c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfecfffff (0x500000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:12:0), (0,2,5), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[1] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x24000000 - 0x27ffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x23ffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 6: bridge is at (0:12:1), (0,6,9), BCTRL: 0x0500 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[1] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0x2c000000 - 0x2fffffff (0x4000000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x28000000 - 0x2bffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) Neomagic Corporation NM2200 [MagicGraph 256AV] rev 32, Mem @ 0xfd000000/24, 0xfe800000/22, 0xfec00000/20
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
(II) PCI Memory resource overlap reduced 0x40000000 from 0x40ffffff to 0x3fffffff
(II) Active PCI resource ranges:
	[0] -1	0	0x2c000000 - 0x2c0003ff (0x400) MX[B]
	[1] -1	0	0xfede0000 - 0xfedeffff (0x10000) MX[B]
	[2] -1	0	0xfedf8000 - 0xfedfffff (0x8000) MX[B]
	[3] -1	0	0xfedf7c00 - 0xfedf7dff (0x200) MX[B]
	[4] -1	0	0xfedf7000 - 0xfedf77ff (0x800) MX[B]
	[5] -1	0	0x40000000 - 0x3fffffff (0x0) MX[B]O
	[6] -1	0	0xfec00000 - 0xfecfffff (0x100000) MX[B](B)
	[7] -1	0	0xfe800000 - 0xfebfffff (0x400000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[10] -1	0	0x0000fc78 - 0x0000fc7f (0x8) IX[B]
	[11] -1	0	0x0000fc8c - 0x0000fc8f (0x4) IX[B]
	[12] -1	0	0x0000fcc0 - 0x0000fcff (0x40) IX[B]
	[13] -1	0	0x0000fca0 - 0x0000fcbf (0x20) IX[B]
	[14] -1	0	0x0000fc90 - 0x0000fc9f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x2c000000 - 0x2c0003ff (0x400) MX[B]
	[1] -1	0	0xfede0000 - 0xfedeffff (0x10000) MX[B]
	[2] -1	0	0xfedf8000 - 0xfedfffff (0x8000) MX[B]
	[3] -1	0	0xfedf7c00 - 0xfedf7dff (0x200) MX[B]
	[4] -1	0	0xfedf7000 - 0xfedf77ff (0x800) MX[B]
	[5] -1	0	0x40000000 - 0x3fffffff (0x0) MX[B]O
	[6] -1	0	0xfec00000 - 0xfecfffff (0x100000) MX[B](B)
	[7] -1	0	0xfe800000 - 0xfebfffff (0x400000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[10] -1	0	0x0000fc78 - 0x0000fc7f (0x8) IX[B]
	[11] -1	0	0x0000fc8c - 0x0000fc8f (0x4) IX[B]
	[12] -1	0	0x0000fcc0 - 0x0000fcff (0x40) IX[B]
	[13] -1	0	0x0000fca0 - 0x0000fcbf (0x20) IX[B]
	[14] -1	0	0x0000fc90 - 0x0000fc9f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x2bffffff (0x2bf00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x2bffffff (0x2bf00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x2c000000 - 0x2c0003ff (0x400) MX[B]
	[5] -1	0	0xfede0000 - 0xfedeffff (0x10000) MX[B]
	[6] -1	0	0xfedf8000 - 0xfedfffff (0x8000) MX[B]
	[7] -1	0	0xfedf7c00 - 0xfedf7dff (0x200) MX[B]
	[8] -1	0	0xfedf7000 - 0xfedf77ff (0x800) MX[B]
	[9] -1	0	0x40000000 - 0x3fffffff (0x0) MX[B]O
	[10] -1	0	0xfec00000 - 0xfecfffff (0x100000) MX[B](B)
	[11] -1	0	0xfe800000 - 0xfebfffff (0x400000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[16] -1	0	0x0000fc78 - 0x0000fc7f (0x8) IX[B]
	[17] -1	0	0x0000fc8c - 0x0000fc8f (0x4) IX[B]
	[18] -1	0	0x0000fcc0 - 0x0000fcff (0x40) IX[B]
	[19] -1	0	0x0000fca0 - 0x0000fcbf (0x20) IX[B]
	[20] -1	0	0x0000fc90 - 0x0000fc9f (0x10) IX[B]
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
(**) AIGLX disabled
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
(II) LoadModule: "neomagic"
(II) Loading /usr/lib/xorg/modules/drivers//neomagic_drv.so
(II) Module neomagic: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
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
	compiled for 1.3.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NEOMAGIC: Driver for Neomagic chipsets: neo2070, neo2090, neo2093,
	neo2097, neo2160, neo2200, neo2230, neo2360, neo2380
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset neo2200 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x2bffffff (0x2bf00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x2c000000 - 0x2c0003ff (0x400) MX[B]
	[5] -1	0	0xfede0000 - 0xfedeffff (0x10000) MX[B]
	[6] -1	0	0xfedf8000 - 0xfedfffff (0x8000) MX[B]
	[7] -1	0	0xfedf7c00 - 0xfedf7dff (0x200) MX[B]
	[8] -1	0	0xfedf7000 - 0xfedf77ff (0x800) MX[B]
	[9] -1	0	0x40000000 - 0x3fffffff (0x0) MX[B]O
	[10] -1	0	0xfec00000 - 0xfecfffff (0x100000) MX[B](B)
	[11] -1	0	0xfe800000 - 0xfebfffff (0x400000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[16] -1	0	0x0000fc78 - 0x0000fc7f (0x8) IX[B]
	[17] -1	0	0x0000fc8c - 0x0000fc8f (0x4) IX[B]
	[18] -1	0	0x0000fcc0 - 0x0000fcff (0x40) IX[B]
	[19] -1	0	0x0000fca0 - 0x0000fcbf (0x20) IX[B]
	[20] -1	0	0x0000fc90 - 0x0000fc9f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x2bffffff (0x2bf00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x2c000000 - 0x2c0003ff (0x400) MX[B]
	[5] -1	0	0xfede0000 - 0xfedeffff (0x10000) MX[B]
	[6] -1	0	0xfedf8000 - 0xfedfffff (0x8000) MX[B]
	[7] -1	0	0xfedf7c00 - 0xfedf7dff (0x200) MX[B]
	[8] -1	0	0xfedf7000 - 0xfedf77ff (0x800) MX[B]
	[9] -1	0	0x40000000 - 0x3fffffff (0x0) MX[B]O
	[10] -1	0	0xfec00000 - 0xfecfffff (0x100000) MX[B](B)
	[11] -1	0	0xfe800000 - 0xfebfffff (0x400000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[19] -1	0	0x0000fc78 - 0x0000fc7f (0x8) IX[B]
	[20] -1	0	0x0000fc8c - 0x0000fc8f (0x4) IX[B]
	[21] -1	0	0x0000fcc0 - 0x0000fcff (0x40) IX[B]
	[22] -1	0	0x0000fca0 - 0x0000fcbf (0x20) IX[B]
	[23] -1	0	0x0000fc90 - 0x0000fc9f (0x10) IX[B]
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) NEOMAGIC(0): Chipset is a MagicMedia 256AV (NM2200)
(II) NEOMAGIC(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) NEOMAGIC(0): Panel is a 1024x768 color TFT display
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) NEOMAGIC(0): initializing int10
(II) NEOMAGIC(0): Primary V_BIOS segment is: 0xc000
(II) NEOMAGIC(0): VESA BIOS detected
(II) NEOMAGIC(0): VESA VBE Version 2.0
(II) NEOMAGIC(0): VESA VBE Total Mem: 2496 kB
(II) NEOMAGIC(0): VESA VBE OEM: MagicMedia 256AV  48K
(II) NEOMAGIC(0): VESA VBE OEM Software Rev: 2.3
(II) NEOMAGIC(0): VESA VBE OEM Vendor: NeoMagic
(II) NEOMAGIC(0): VESA VBE OEM Product: MagicMedia 256AV 
(II) NEOMAGIC(0): VESA VBE OEM Product Rev: 01.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) NEOMAGIC(0): VESA VBE DDC supported
(II) NEOMAGIC(0): VESA VBE DDC Level none
(II) NEOMAGIC(0): VESA VBE DDC transfer in appr. 0 sec.
(II) NEOMAGIC(0): VESA VBE DDC read failed
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) NEOMAGIC(0): I2C bus "I2C bus" initialized.
(II) NEOMAGIC(0): I2C device "I2C bus:ddc2" registered at address 0xA0.
(II) NEOMAGIC(0): I2C device "I2C bus:ddc2" removed.
(--) NEOMAGIC(0): No DDC signal
(**) NEOMAGIC(0): Depth 16, (--) framebuffer bpp 16
(==) NEOMAGIC(0): RGB weight 565
(==) NEOMAGIC(0): Default visual is TrueColor
(==) NEOMAGIC(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NEOMAGIC(0): Internal LCD only display mode
(==) NEOMAGIC(0): using linear mode
(**) NEOMAGIC(0): using PCI Burst mode
(**) NEOMAGIC(0): Option StrangeLockups set: disabling some acceleration
(--) NEOMAGIC(0): FB base address is set at 0xFD000000.
(--) NEOMAGIC(0): MMIO base address is set at 0xFE800000.
(--) NEOMAGIC(0): MMIO base address2 is set at 0xFEC00000.
(--) NEOMAGIC(0): VideoRAM: 2560 kByte
(--) NEOMAGIC(0): Max Clock: 110000 kHz
(II) NEOMAGIC(0): Generic Monitor: Using hsync range of 28.00-51.00 kHz
(II) NEOMAGIC(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) NEOMAGIC(0): Clock range:  11.00 to 110.00 MHz
(II) NEOMAGIC(0): Removing mode (640x350) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "640x350" (unknown reason)
(II) NEOMAGIC(0): Removing mode (320x175) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "320x175" (unknown reason)
(II) NEOMAGIC(0): Removing mode (640x400) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "640x400" (unknown reason)
(II) NEOMAGIC(0): Removing mode (320x200) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "320x200" (unknown reason)
(II) NEOMAGIC(0): Removing mode (720x400) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "720x400" (unknown reason)
(II) NEOMAGIC(0): Removing mode (360x200) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "360x200" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "640x480" (vrefresh out of range)
(II) NEOMAGIC(0): Not using default mode "320x240" (vrefresh out of range)
(II) NEOMAGIC(0): Not using default mode "640x480" (vrefresh out of range)
(II) NEOMAGIC(0): Not using default mode "320x240" (vrefresh out of range)
(II) NEOMAGIC(0): Not using default mode "640x480" (vrefresh out of range)
(II) NEOMAGIC(0): Not using default mode "320x240" (vrefresh out of range)
(II) NEOMAGIC(0): Removing mode (400x300) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "400x300" (unknown reason)
(II) NEOMAGIC(0): Removing mode (400x300) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "400x300" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "800x600" (vrefresh out of range)
(II) NEOMAGIC(0): Removing mode (400x300) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "400x300" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "800x600" (vrefresh out of range)
(II) NEOMAGIC(0): Removing mode (400x300) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "400x300" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "800x600" (hsync out of range)
(II) NEOMAGIC(0): Removing mode (400x300) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "400x300" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (512x384) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "512x384" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1024x768" (hsync out of range)
(II) NEOMAGIC(0): Removing mode (512x384) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "512x384" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1024x768" (hsync out of range)
(II) NEOMAGIC(0): Removing mode (512x384) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "512x384" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1024x768" (hsync out of range)
(II) NEOMAGIC(0): Removing mode (512x384) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "512x384" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1152x864) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "1152x864" (unknown reason)
(II) NEOMAGIC(0): Removing mode (576x432) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "576x432" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1280x960) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "1280x960" (unknown reason)
(II) NEOMAGIC(0): Removing mode (640x480) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "640x480" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (640x480) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "640x480" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1280x1024) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "1280x1024" (unknown reason)
(II) NEOMAGIC(0): Removing mode (640x512) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "640x512" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (640x512) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "640x512" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (640x512) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "640x512" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "800x600" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "800x600" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "800x600" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "800x600" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "896x672" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "928x696" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (832x624) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "832x624" (unknown reason)
(II) NEOMAGIC(0): Removing mode (416x312) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "416x312" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1280x768) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "1280x768" (unknown reason)
(II) NEOMAGIC(0): Removing mode (640x384) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "640x384" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1280x800) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "1280x800" (unknown reason)
(II) NEOMAGIC(0): Removing mode (640x400) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "640x400" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1152x768) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "1152x768" (unknown reason)
(II) NEOMAGIC(0): Removing mode (576x384) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "576x384" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (576x432) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "576x432" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "700x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "700x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "700x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "700x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1440x900" (width requires unsupported line pitch)
(II) NEOMAGIC(0): Removing mode (720x450) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "720x450" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) NEOMAGIC(0): Removing mode (800x512) larger than the LCD panel (1024x768)
(II) NEOMAGIC(0): Not using default mode "800x512" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "840x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "960x600" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) NEOMAGIC(0): Virtual size is 1024x768 (pitch 1024)
(**) NEOMAGIC(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NEOMAGIC(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NEOMAGIC(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NEOMAGIC(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NEOMAGIC(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NEOMAGIC(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NEOMAGIC(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NEOMAGIC(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NEOMAGIC(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NEOMAGIC(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(++) NEOMAGIC(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfec00000 - 0xfecfffff (0x100000) MX[B]
	[1] 0	0	0xfe800000 - 0xfebfffff (0x400000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x2bffffff (0x2bf00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x2c000000 - 0x2c0003ff (0x400) MX[B]
	[8] -1	0	0xfede0000 - 0xfedeffff (0x10000) MX[B]
	[9] -1	0	0xfedf8000 - 0xfedfffff (0x8000) MX[B]
	[10] -1	0	0xfedf7c00 - 0xfedf7dff (0x200) MX[B]
	[11] -1	0	0xfedf7000 - 0xfedf77ff (0x800) MX[B]
	[12] -1	0	0x40000000 - 0x3fffffff (0x0) MX[B]O
	[13] -1	0	0xfec00000 - 0xfecfffff (0x100000) MX[B](B)
	[14] -1	0	0xfe800000 - 0xfebfffff (0x400000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[22] -1	0	0x0000fc78 - 0x0000fc7f (0x8) IX[B]
	[23] -1	0	0x0000fc8c - 0x0000fc8f (0x4) IX[B]
	[24] -1	0	0x0000fcc0 - 0x0000fcff (0x40) IX[B]
	[25] -1	0	0x0000fca0 - 0x0000fcbf (0x20) IX[B]
	[26] -1	0	0x0000fc90 - 0x0000fc9f (0x10) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(==) NEOMAGIC(0): Write-combining range (0xfd000000,0x400000)
(II) NEOMAGIC(0): Stretching disabled
(II) NEOMAGIC(0): Using linear framebuffer at: 0xFD000000
(--) NEOMAGIC(0): 1048576 bytes off-screen memory available
(II) NEOMAGIC(0): Using H/W Cursor.
(II) NEOMAGIC(0): Using 256 scanlines of offscreen memory 
(II) NEOMAGIC(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
(II) NEOMAGIC(0): Acceleration  Initialized
(==) NEOMAGIC(0): Backing store disabled
(==) NEOMAGIC(0): Silken mouse enabled
(**) Option "dpms"
(**) NEOMAGIC(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
No matching visual for __GLcontextMode with visual class = 3 (32772), nplanes = 16
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 16
No matching visual for __GLcontextMode with visual class = 2 (32773), nplanes = 16
No matching visual for __GLcontextMode with visual class = 0 (32775), nplanes = 16
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
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
```

---

### Post by Bachstelze on 2007-09-06
Examples of ugly-looking fonts ? In which app ? A little screenshot, maybe ?

We can't really help you with so little information... The reason you don't get as nice fonts as in Ubuntu by default is that Ubuntu does the job of configuring it for you. Debian does not and lets you do it for yourself.

---

### Post by hrod beraht on 2007-09-06
> **HymnToLife said:**
> The reason you don't get as nice fonts as in Ubuntu by default is that Ubuntu does the job of configuring it for you. Debian does not and lets you do it for yourself.

What I would really like is to have a good understanding about how fonts are globally controlled.
Debian and Ubuntu seem to be referencing the same fonts under System --> Preferences --> Font (from Fonts:///, I presume). So where are they different?
Is the Ubuntu configuring difference something in /etc/fonts/fonts.conf or in /etc/X11/xorg.conf or somewhere else I'm missing?

Thanks for any info,
Bob

---

### Post by kerry_s on 2007-09-06
check the xorg version, mines  1:7.2-5, i'm running etch/lenny(stable/testing).
you might want to try running> **sudo dpkg-reconfigure -phigh xserver-xorg** <to rest it
use su then dpkg-reconfigure -phigh xserver-xorg, if you haven't turned on sudo.

```

deb http://ftp.debian.org/debian/ etch main contrib non-free
deb http://ftp.debian.org/debian/ lenny main contrib non-free
deb http://www.debian-multimedia.org lenny main

# su
# gpg --keyserver subkeys.pgp.net --recv-key 6A423791
# gpg --armor --export  6A423791| apt-key add -
deb http://deb.opera.com/opera/ lenny non-free

deb http://security.debian.org/ etch/updates main contrib non-free
deb http://security.debian.org/ lenny/updates main contrib non-free

#deb-src http://ftp.debian.org/debian/ etch main contrib non-free
#deb-src http://security.debian.org/ etch/updates main contrib non-free
#deb-src http://ftp.debian.org/debian/ lenny main contrib non-free
#deb-src http://security.debian.org/ lenny/updates main contrib non-free


```

---

### Post by Bachstelze on 2007-09-06
Actually, I think that Ubuntu does not install the low-quality version of some fonts (e.g. Helvetica) that most other distros install. For example, here's what the fonts directories section in my fonts.conf looks like in Gentoo :

```
        <dir>/usr/share/fonts/corefonts</dir>
        <dir>/usr/share/fonts/default</dir>
        <dir>/usr/share/fonts/dejavu</dir>
        <dir>/usr/share/fonts/misc</dir>
        <dir>/usr/share/fonts/ttf-bitstream-vera</dir>
        <dir>/usr/share/fonts/Type1</dir>
        <dir>/data/mfb/software/fonts</dir>
        <dir>/usr/local/share/fonts</dir>
        <dir>/usr/X11R6/lib/X11/fonts</dir>
        <dir>~/.fonts</dir>

```

Notice that I left out the 100dpi/ and 75dpi/ directories that contain the low-quality fonts. That way, when a website looks for e.g. Helvetica, the low quality Helvetica will not be found and my default font will be used instead :

[http://fkraiem.no-ip.org/stuff/fonts_good.png](http://fkraiem.no-ip.org/stuff/fonts_good.png)

However, if I put the 100dpi/ and 75dpi/ dirs back in my fonts.conf :

[http://fkraiem.no-ip.org/stuff/fonts_ugly.png](http://fkraiem.no-ip.org/stuff/fonts_ugly.png)

---

### Post by kerry_s on 2007-09-06
> **HymnToLife said:**
> Actually, I think that Ubuntu does not install the low-quality version of some fonts (e.g. Helvetica) that most other distros install. For example, here's what the fonts directories section in my fonts.conf looks like in Gentoo :

```
        <dir>/usr/share/fonts/corefonts</dir>
        <dir>/usr/share/fonts/default</dir>
        <dir>/usr/share/fonts/dejavu</dir>
        <dir>/usr/share/fonts/misc</dir>
        <dir>/usr/share/fonts/ttf-bitstream-vera</dir>
        <dir>/usr/share/fonts/Type1</dir>
        <dir>/data/mfb/software/fonts</dir>
        <dir>/usr/local/share/fonts</dir>
        <dir>/usr/X11R6/lib/X11/fonts</dir>
        <dir>~/.fonts</dir>

```

Notice that I left out the 100dpi/ and 75dpi/ directories that contain the low-quality fonts. That way, when a website looks for e.g. Helvetica, the low quality Helvetica will not be found and my default font will be used instead :

[http://fkraiem.no-ip.org/stuff/fonts_good.png](http://fkraiem.no-ip.org/stuff/fonts_good.png)

However, if I put the 100dpi/ and 75dpi/ dirs back in my fonts.conf :

[http://fkraiem.no-ip.org/stuff/fonts_ugly.png](http://fkraiem.no-ip.org/stuff/fonts_ugly.png)


i have my browser set to use my fonts, not the websites choose.

---

### Post by Bachstelze on 2007-09-06
Then all fonts look the same, I don't like that. Diversity is the spice of life :D

---

### Post by bradthebuyer on 2007-09-18
You probably need to disable bitmapped fonts. Debian doesn't do this by default and they don't scale well. Run **sudo dpkg-reconfigure fontconfig-config**. I recommend choosing Native for the tuning method, Automatic for subpixel rendering and the important bit is to  answer No when asked if you want to enable bitmapped fonts.

 I would also install some nice truetype fonts. **sudo aptitude install ttf-dejavu ttf-bitstream-vera** is a good start.

---


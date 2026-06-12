---
title: "Dual Head - i810 - Intel 82852/855GM"
date: 2006-05-29
forum: Desktop Environments
---

### Post by torf on 2006-05-29
I realize there are dozens of dual head threads, however the i810 ones I have found haven't been much help.  I'm using a Thinkpad R51 and would like to increase my productivity by using two screens (my LCD on the laptop and an external monitor.)  On the R51 there is a fn+f7 key that allows me to switch between LCD only, external monitory only and clone.  (No dual display).  So far the best resource I've found and been following is here:
[http://lists.debian.org/debian-laptop/2005/06/msg00213.html]("http://lists.debian.org/debian-laptop/2005/06/msg00213.html")

When I follow this and apply the relevant parts to my xorg.conf my monitor light turns green when X starts up, showing that it is getting some signal.  However, X crashes and I get the following errors:
(EE) I810(0): vm86() syscall generated signal 4.
(EE) I810(0): VBE initialization failed.
(EE) I810(0): vm86() syscall generated signal 4.
(EE) I810(1): VBE initialization failed.
(EE) Screen(s) found, but none have a usable configuration.

I've attached my failing xorg.conf and the original xorg.conf for comparison.  Since my Xorg.0.log is too big to attach, I've included it below.  Sorry for such a large post. Thank you for any assistance.

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77.1 20060503192905 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.12 i686 [ELF] 
Current Operating System: Linux entropy 2.6.12-10-386 #1 Fri Apr 28 13:13:44 UTC 2006 i686
Build Date: 03 May 2006
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Fri Apr 28 13:13:44 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 29 10:27:11 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Dual"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel Corporation 82852/855GM Integrated Graphics Device"
(**) |-->Screen "AMW Screen" (1)
(**) |   |-->Monitor "AMW Monitor"
(**) |   |-->Device "Intel Corporation 82852/855GM Integrated Graphics Device [2]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(**) Option "Xinerama" "1"
(**) Xinerama: enabled
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3580 card 1014,055c rev 02 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 8086,3584 card 1014,055d rev 02 class 08,80,00 hdr 00
(II) PCI: 00:00:3: chip 8086,3585 card 1014,055e rev 02 class 08,80,00 hdr 80
(II) PCI: 00:02:0: chip 8086,3582 card 1014,0557 rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,3582 card 1014,0557 rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1d:0: chip 8086,24c2 card 1014,052d rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1014,052d rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1014,052d rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1014,052e rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 1014,052d rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1014,052d rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1014,0554 rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1014,0559 rev 01 class 07,03,00 hdr 00
(II) PCI: 02:00:0: chip 104c,ac56 card 4000,0000 rev 00 class 06,07,00 hdr 02
(II) PCI: 02:02:0: chip 8086,4220 card 8086,2711 rev 05 class 02,80,00 hdr 00
(II) PCI: 02:08:0: chip 8086,103d card 1014,0522 rev 81 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
	[4] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[5] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[6] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[7] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
	[8] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[9] -1	0	0x00005400 - 0x000054ff (0x100) IX[B]
	[10] -1	0	0x00005800 - 0x000058ff (0x100) IX[B]
	[11] -1	0	0x00005c00 - 0x00005cff (0x100) IX[B]
	[12] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[13] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
	[14] -1	0	0x00006800 - 0x000068ff (0x100) IX[B]
	[15] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B]
	[16] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[17] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[18] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[19] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd0200000 - 0xdfffffff (0xfe00000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:0:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
(--) PCI:*(0:2:0) Intel Corp. 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xe0000000/27, 0xd0000000/19, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corp. 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xe8000000/27, 0xd0080000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[1] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[2] -1	0	0xd0100800 - 0xd01008ff (0x100) MX[B]
	[3] -1	0	0xd0100c00 - 0xd0100dff (0x200) MX[B]
	[4] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[5] -1	0	0xd0100000 - 0xd01003ff (0x400) MX[B]
	[6] -1	0	0xd0080000 - 0xd00fffff (0x80000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00007000 - 0x0000703f (0x40) IX[B]
	[11] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[12] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[13] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[14] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[15] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[16] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[17] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[18] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[19] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[20] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[1] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[2] -1	0	0xd0100800 - 0xd01008ff (0x100) MX[B]
	[3] -1	0	0xd0100c00 - 0xd0100dff (0x200) MX[B]
	[4] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[5] -1	0	0xd0100000 - 0xd01003ff (0x400) MX[B]
	[6] -1	0	0xd0080000 - 0xd00fffff (0x80000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00007000 - 0x0000703f (0x40) IX[B]
	[11] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[12] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[13] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[14] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[15] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[16] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[17] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[18] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[19] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[20] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[6] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[7] -1	0	0xd0100800 - 0xd01008ff (0x100) MX[B]
	[8] -1	0	0xd0100c00 - 0xd0100dff (0x200) MX[B]
	[9] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[10] -1	0	0xd0100000 - 0xd01003ff (0x400) MX[B]
	[11] -1	0	0xd0080000 - 0xd00fffff (0x80000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00007000 - 0x0000703f (0x40) IX[B]
	[18] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[19] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[20] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[21] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[22] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[23] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[24] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "i810"
(II) Loading /usr/X11R6/lib/modules/drivers/i810_drv.o
(II) Module i810: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.4.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G
(II) Primary Device is: PCI 00:02:0
(--) Chipset 852GM/855GM found
(--) Chipset 852GM/855GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[6] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[7] -1	0	0xd0100800 - 0xd01008ff (0x100) MX[B]
	[8] -1	0	0xd0100c00 - 0xd0100dff (0x200) MX[B]
	[9] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[10] -1	0	0xd0100000 - 0xd01003ff (0x400) MX[B]
	[11] -1	0	0xd0080000 - 0xd00fffff (0x80000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00007000 - 0x0000703f (0x40) IX[B]
	[18] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[19] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[20] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[21] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[22] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[23] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[24] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[6] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[7] -1	0	0xd0100800 - 0xd01008ff (0x100) MX[B]
	[8] -1	0	0xd0100c00 - 0xd0100dff (0x200) MX[B]
	[9] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[10] -1	0	0xd0100000 - 0xd01003ff (0x400) MX[B]
	[11] -1	0	0xd0080000 - 0xd00fffff (0x80000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00007000 - 0x0000703f (0x40) IX[B]
	[21] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[22] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[23] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[24] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[25] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[26] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[27] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[28] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[29] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[30] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[31] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(**) I810(0): Option "MonitorLayout" "CRT, CRT+LFP"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(EE) I810(0): vm86() syscall generated signal 4.
(II) I810(0): EAX=0xc0000fdc, EBX=0x00000000, ECX=0x0000007d, EDX=0x0000ff00
(II) I810(0): ESP=0x00000fb2, EBP=0x00000fdc, ESI=0x00000000, EDI=0x0000200e
(II) I810(0): CS=0xc000, SS=0x0100, DS=0x0000, ES=0x0000, FS=0x0000, GS=0x0000
(II) I810(0): EIP=0x0000303d, EFLAGS=0x00033282
(II) I810(0): code at 0x000c303d:
 c6 08 f6 c3 10 75 f2 80 fb 40 72 ea eb 1a bf 33
 06 be 13 06 57 56 e8 be 00 5e 5f e8 b9 00 f6 c3
(II) stack at 0x00001fb2:
 84 52 c6 0c 00 00 00 00 0e 20 22 69 00 00 00 00
 74 68 d6 69 7d 00 00 00 00 20 67 69 d7 1e 00 00
 03 50 10 00 01 00 05 00 00 0d 40 00 00 00 00 00
 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 00 00 00 00 00 4f 00 00 00 06 00 00 00 32
(II) I810(0): VESA BIOS not detected
(EE) I810(0): VBE initialization failed.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/X11R6/lib/modules/libvgahw.a
(**) I810(1): Depth 24, (--) framebuffer bpp 32
(==) I810(1): RGB weight 888
(==) I810(1): Default visual is TrueColor
(**) I810(1): Option "DevicePresence" "yes"
(**) I810(1): Option "MonitorLayout" "CRT. CRT+LFP"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(EE) I810(0): vm86() syscall generated signal 4.
(II) I810(0): EAX=0xc0000fdc, EBX=0x00000000, ECX=0x0000007d, EDX=0x0000ff00
(II) I810(0): ESP=0x00000fb2, EBP=0x00000fdc, ESI=0x00000000, EDI=0x0000200e
(II) I810(0): CS=0xc000, SS=0x0100, DS=0x0000, ES=0x0000, FS=0x0000, GS=0x0000
(II) I810(0): EIP=0x0000303d, EFLAGS=0x00033282
(II) I810(0): code at 0x000c303d:
 c6 08 f6 c3 10 75 f2 80 fb 40 72 ea eb 1a bf 33
 06 be 13 06 57 56 e8 be 00 5e 5f e8 b9 00 f6 c3
(II) stack at 0x00001fb2:
 84 52 c6 0c 00 00 00 00 0e 20 22 69 00 00 00 00
 74 68 d6 69 7d 00 00 00 00 20 67 69 d7 1e 00 00
 03 50 10 00 01 00 05 00 00 0d 40 00 00 00 00 00
 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 00 00 00 00 00 4f 00 00 00 06 00 00 00 32
(II) I810(0): VESA BIOS not detected
(EE) I810(1): VBE initialization failed.
(II) UnloadModule: "i810"
(II) UnloadModule: "int10"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) UnloadModule: "vbe"
(II) UnloadModule: "int10"
(II) UnloadModule: "i810"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/X11R6/lib/modules/libvgahw.a
(II) UnloadModule: "vbe"
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.


```

---

### Post by halfvolle melk on 2006-05-29
You might find a solution in here:
[http://www.ubuntuforums.org/showthread.php?t=155762](http://www.ubuntuforums.org/showthread.php?t=155762)

---

### Post by torf on 2006-05-29
Ah darn, I don't believe I missed that thread after searching through i810 threads all night.  Thanks, that looks like it can help.  I've encountered a few problems, but I will take care of them in that thread.

---


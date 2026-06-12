---
title: "ATI Radeon X850XT AGP Error"
date: 2005-12-05
forum: Desktop Environments
---

### Post by m0unds on 2005-12-05
Hi everyone, I just followed the revised *new* ATI setup instructions for ATI's newest driverset, which included module-assist, etc. I'm still receiving the same error message I've gotten since I first installed this card. Output from xorg.log is as follows:
```
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux m0undsbox 2.6.12-10-686-smp #1 SMP Fri Nov 18 12:27:41 UTC 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-686-smp (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 SMP Fri Nov 18 12:27:41 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec  5 15:34:18 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig Screen 0" (0)
(**) |   |-->Monitor "aticonfig Monitor 0"
(**) |   |-->Device "ATI Graphics Adapter 0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) PCI: 00:00:0: chip 8086,2578 card 1695,4003 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2579 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1695,4003 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1695,4003 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1695,4003 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1695,4003 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1695,4003 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1695,4003 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1695,4003 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4b4c card 1002,0312 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4b6c card 1002,0313 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:00:0: chip 1103,0008 card 1103,0001 rev 07 class 01,04,00 hdr 80
(II) PCI: 02:00:1: chip 1103,0008 card 1103,0001 rev 07 class 01,04,00 hdr 80
(II) PCI: 02:01:0: chip 14e4,1653 card 1695,9013 rev 03 class 02,00,00 hdr 00
(II) PCI: 02:07:0: chip 13f6,0111 card 584d,3731 rev 10 class 04,01,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x4b4c) rev 0, Mem @ 0xe0000000/27, 0xf1000000/16, I/O @ 0xc000/8
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x4b6c) rev 0, Mem @ 0xe8000000/27, 0xf1010000/16
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xdfffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf3000000 - 0xf300ffff (0x10000) MX[B]
	[1] -1	0	0x80000000 - 0x800003ff (0x400) MX[B]
	[2] -1	0	0xf4000000 - 0xf40003ff (0x400) MX[B]
	[3] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[4] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[5] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[6] -1	0	0x0000da00 - 0x0000daff (0x100) IX[B]
	[7] -1	0	0x0000d900 - 0x0000d9ff (0x100) IX[B]
	[8] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[9] -1	0	0x0000d700 - 0x0000d707 (0x8) IX[B]
	[10] -1	0	0x0000d600 - 0x0000d603 (0x4) IX[B]
	[11] -1	0	0x0000d500 - 0x0000d507 (0x8) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[13] -1	0	0x0000d300 - 0x0000d303 (0x4) IX[B]
	[14] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[15] -1	0	0x0000d100 - 0x0000d103 (0x4) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[17] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[20] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[22] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[1] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf3000000 - 0xf300ffff (0x10000) MX[B]
	[1] -1	0	0x80000000 - 0x800003ff (0x400) MX[B]
	[2] -1	0	0xf4000000 - 0xf40003ff (0x400) MX[B]
	[3] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[4] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[5] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[6] -1	0	0x0000da00 - 0x0000daff (0x100) IX[B]
	[7] -1	0	0x0000d900 - 0x0000d9ff (0x100) IX[B]
	[8] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[9] -1	0	0x0000d700 - 0x0000d707 (0x8) IX[B]
	[10] -1	0	0x0000d600 - 0x0000d603 (0x4) IX[B]
	[11] -1	0	0x0000d500 - 0x0000d507 (0x8) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[13] -1	0	0x0000d300 - 0x0000d303 (0x4) IX[B]
	[14] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[15] -1	0	0x0000d100 - 0x0000d103 (0x4) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[17] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[20] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[22] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[1] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
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
	[5] -1	0	0xf3000000 - 0xf300ffff (0x10000) MX[B]
	[6] -1	0	0x80000000 - 0x800003ff (0x400) MX[B]
	[7] -1	0	0xf4000000 - 0xf40003ff (0x400) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000da00 - 0x0000daff (0x100) IX[B]
	[16] -1	0	0x0000d900 - 0x0000d9ff (0x100) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[18] -1	0	0x0000d700 - 0x0000d707 (0x8) IX[B]
	[19] -1	0	0x0000d600 - 0x0000d603 (0x4) IX[B]
	[20] -1	0	0x0000d500 - 0x0000d507 (0x8) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000d300 - 0x0000d303 (0x4) IX[B]
	[23] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[24] -1	0	0x0000d100 - 0x0000d103 (0x4) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[26] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[28] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[29] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[31] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
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
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.19.10
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
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9200 (RV280 5961), RADEON 9200 SE (RV280 5964),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9550 (M12 4E56), RADEON 9500 (R300 4144),
	RADEON 9600 TX (R300 4146), FireGL Z1 (R300 4147),
	RADEON 9700 PRO (R300 4E44), RADEON 9500 PRO/9700 (R300 4E45),
	RADEON 9600 TX (R300 4E46), FireGL X1 (R300 4E47),
	RADEON 9800 SE (R350 4148), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9800 PRO (R350 4E48),
	RADEON 9800 (R350 4E49), RADEON 9800 XT (R360 4E4A),
	FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600 (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 XT Platinum Edition (R420 4A50), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 SE (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	RADEON X800 XL (R430 554D), RADEON X800 (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X850 PRO (R480 5D4F), RADEON X850 XT (R480 5D52),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), FireGL V3300 (RV410 5E49),
	RADEON X700 XT (RV410 5E4A), RADEON X700 PRO (RV410 5E4B),
	RADEON X700 SE (RV410 5E4C), RADEON X700 (RV410 5E4D),
	RADEON X700 (RV410 5E4F), MOBILITY RADEON X700 (M26 5652),
	MOBILITY RADEON X700 (M26 5653), MOBILITY RADEON X700 XL,
	RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.19.10
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.19g1                           
(II) ATI Proprietary Linux Driver Build Date: Nov  9 2005 17:51:16
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.19.1-driver-lnx-226030
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found
```

---

### Post by m0unds on 2005-12-05
the PCI device ID that's listed in the configuration is the same one that's used in the working config.

the broken config looks like this:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X850 XT PE (R481)"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon X850 XT PE (R481)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

### Post by m0unds on 2005-12-06
i tried using another driver revision after removing the newest one, with the same results. any insight?

---

### Post by b5mC on 2006-01-16
Yeah bro, Im having the same problems with my videocard(X850xtPE AGP).  Correct me if Im wrong but I believe this card is not supported with the driver.

---

### Post by sanzo on 2006-01-16
in /etc/X11/xorg.conf

search: Section "Device" and write 

Driver "radeon" instead Driver "ati"

It works for me.

---

### Post by m0unds on 2006-01-27
there's an issue with FGLRX that ATI didn't include the PCI Device ID's for the X850 AGP series; there's a thread at [http://www.rage3d.com](http://www.rage3d.com) that explains a fix for it-- hex editing the src

---


---
title: "Xorg, intel 82845 do not work."
date: 2005-07-25
forum: Desktop Environments
---

### Post by majikstreet on 2005-07-25
[SIZE=6]Update below!![/SIZE]

**disregard this post. please see my last post on tuesday july 26th.**
Hello,
I installed Ubuntu on my computer. I was able to get into Gnome, but only in a very low resolution. So I ran xorgconfig and configured my system and rebooted. X said that it couldn't work. I set up my xorg.conf following the instructions at [http://www.ubuntuforums.org/showpost.php?p=151596&postcount=4](http://www.ubuntuforums.org/showpost.php?p=151596&postcount=4)

Here is my Xorg.0.log file in case it can be of help: warning, it's very long
```


X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux oreo 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 25 17:46:57 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Simple Layout"
(**) |-->Screen "Screen 1" (0)
(**) |   |-->Monitor "My Monitor"
(**) |   |-->Device "My Video Card"
(**) |-->Input Device "Mouse1"
(**) |-->Input Device "Keyboard1"
(**) FontPath set to "/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/"
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
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
(II) PCI: 00:00:0: chip 8086,2560 card 1028,0147 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2562 card 1028,0147 rev 03 class 03,00,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24c2 card 1028,0147 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1028,0147 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1028,0147 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1028,0147 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 1028,0147 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1028,0147 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1028,0147 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:05:0: chip 17fe,2120 card 1737,0020 rev 00 class 02,00,00 hdr 00
(II) PCI: 01:06:0: chip 14f1,2702 card 1028,8d88 rev 01 class 07,80,00 hdr 00
(II) PCI: 01:09:0: chip 14e4,4401 card 1028,8127 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corp. 82845G/GL [Brookdale-G] Chipset Integrated Graphics Device rev 3, Mem @ 0xe0000000/27, 0xee000000/19
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
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xebffffff to 0xe7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xed010000 - 0xed011fff (0x2000) MX[B]
	[1] -1	0	0xed000000 - 0xed00ffff (0x10000) MX[B]
	[2] -1	0	0xed012000 - 0xed0127ff (0x800) MX[B]
	[3] -1	0	0xee082000 - 0xee0820ff (0x100) MX[B]
	[4] -1	0	0xee081000 - 0xee0811ff (0x200) MX[B]
	[5] -1	0	0x10000000 - 0x100003ff (0x400) MX[B]
	[6] -1	0	0xee080000 - 0xee0803ff (0x400) MX[B]
	[7] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[8] -1	0	0xee000000 - 0xee07ffff (0x80000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e43f (0x40) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[13] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xed010000 - 0xed011fff (0x2000) MX[B]
	[1] -1	0	0xed000000 - 0xed00ffff (0x10000) MX[B]
	[2] -1	0	0xed012000 - 0xed0127ff (0x800) MX[B]
	[3] -1	0	0xee082000 - 0xee0820ff (0x100) MX[B]
	[4] -1	0	0xee081000 - 0xee0811ff (0x200) MX[B]
	[5] -1	0	0x10000000 - 0x100003ff (0x400) MX[B]
	[6] -1	0	0xee080000 - 0xee0803ff (0x400) MX[B]
	[7] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[8] -1	0	0xee000000 - 0xee07ffff (0x80000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e43f (0x40) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[13] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x0fffffff (0xff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x0fffffff (0xff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xed010000 - 0xed011fff (0x2000) MX[B]
	[6] -1	0	0xed000000 - 0xed00ffff (0x10000) MX[B]
	[7] -1	0	0xed012000 - 0xed0127ff (0x800) MX[B]
	[8] -1	0	0xee082000 - 0xee0820ff (0x100) MX[B]
	[9] -1	0	0xee081000 - 0xee0811ff (0x200) MX[B]
	[10] -1	0	0x10000000 - 0x100003ff (0x400) MX[B]
	[11] -1	0	0xee080000 - 0xee0803ff (0x400) MX[B]
	[12] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[13] -1	0	0xee000000 - 0xee07ffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e43f (0x40) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[20] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
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
(II) Loading extension DPMS
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "vga"
(II) Loading /usr/X11R6/lib/modules/drivers/vga_drv.o
(II) Module vga: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 4.0.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) VGA: Generic VGA driver (version 4.0) for chipsets: generic
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset generic found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x0fffffff (0xff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xed010000 - 0xed011fff (0x2000) MX[B]
	[6] -1	0	0xed000000 - 0xed00ffff (0x10000) MX[B]
	[7] -1	0	0xed012000 - 0xed0127ff (0x800) MX[B]
	[8] -1	0	0xee082000 - 0xee0820ff (0x100) MX[B]
	[9] -1	0	0xee081000 - 0xee0811ff (0x200) MX[B]
	[10] -1	0	0x10000000 - 0x100003ff (0x400) MX[B]
	[11] -1	0	0xee080000 - 0xee0803ff (0x400) MX[B]
	[12] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[13] -1	0	0xee000000 - 0xee07ffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e43f (0x40) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[20] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x0fffffff (0xff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xed010000 - 0xed011fff (0x2000) MX[B]
	[6] -1	0	0xed000000 - 0xed00ffff (0x10000) MX[B]
	[7] -1	0	0xed012000 - 0xed0127ff (0x800) MX[B]
	[8] -1	0	0xee082000 - 0xee0820ff (0x100) MX[B]
	[9] -1	0	0xee081000 - 0xee0811ff (0x200) MX[B]
	[10] -1	0	0x10000000 - 0x100003ff (0x400) MX[B]
	[11] -1	0	0xee080000 - 0xee0803ff (0x400) MX[B]
	[12] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[13] -1	0	0xee000000 - 0xee07ffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e43f (0x40) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[23] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) VGA(0): initializing int10.
(WW) VGA(0): Bad V_BIOS checksum
(II) VGA(0): Primary V_BIOS segment is: 0xc000
(EE) VGA(0): Driver can't support depth 24
(II) UnloadModule: "vga"
(II) UnloadModule: "int10"
(II) Unloading /usr/X11R6/lib/modules/linux/libint10.a
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```

Hope someone can help!

majikstreet

---

### Post by dtfinch on 2005-07-26
Here's what my full xorg.conf looks like, minus some of the comments:

```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL E773c"
	Option		"DPMS"
	HorizSync 30-70
	VertRefresh 50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"DELL E773c"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

You'll at least have to change the monitor, unless we have the same.

---

### Post by majikstreet on 2005-07-26
I will try this later today.

Out of curiosity what computer do you have? I have a Dell Dimension 2350! It's not a bad computer, really. Linux doesn't seem to play too nicely with it, though -- well at least X doesn't!

---

### Post by majikstreet on 2005-07-26
I tried reconfigureing x with xorgconfig and specs I got from dell.....


doesn't work.

---

### Post by varunus on 2005-07-26
Some BIOSes have problems with Ubuntu's i810 driver; they don't report all the video modes possible, so Ubuntu has problems.

With Dells, one fix is to just update your BIOS.  Another fix that doesn't require a BIOS update, however, is to follow the following howto:
[http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

It will set up the 855resolution utility,, and you'll have all your resolutions back.   :) 

Enjoy.

---

### Post by dtfinch on 2005-07-26
I have a Dimension 2400.

---

### Post by majikstreet on 2005-07-26
> **varunus]Some BIOSes have problems with Ubuntu's i810 driver said:**
> http://ubuntuforums.org/showthread.php?t=27029[/url]

It will set up the 855resolution utility,, and you'll have all your resolutions back.   :) 

Enjoy.
 I tried this solution and voila! it doesn't work. 
I have a Dell Dimension 2350 with a Dell E151FPb monitor. 

I though Linux had no BSOD. It does if you have a POS Dell!

---


---
title: "X mysteriously stopped loading, and won't load"
date: 2008-05-06
forum: Desktop Environments
---

### Post by ejay563 on 2008-05-06
Hi,

I started up my computer, and for some unknown reason, it dropped me off at a command prompt login. Puzzled, but not overly concerned, I logged into my machine, and typed "startx" to get my GUI going. It started to load, then it died. I tried to look through the log file for an error or something, but I did not see anything. Heres my specs. 

Running Ubuntu 8.04lts/Windows XP Pro
Dell Inspiron 2200
1.2GB Ram
Intel Pentium M 1.60 Ghz
Graphics: Mobile Intel 915GM/GMS 910GML Express Chipset family

heres the x log file:


```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux onisogoma 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May  6 00:13:53 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL 1907FP"
(**) |   |-->Device "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2590 card 1028,01a4 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2592 card 1028,01a4 rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2792 card 1028,01a4 rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1d:0: chip 8086,2658 card 1028,01a4 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1028,01a4 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1028,01a4 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1028,01a4 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1028,01a4 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev d3 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,266e card 1028,01a4 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1e:3: chip 8086,266d card 14f1,5423 rev 03 class 07,03,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,2641 card 1028,01a4 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 1028,01a4 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 1028,01a4 rev 03 class 0c,05,00 hdr 00
(II) PCI: 02:01:0: chip 104c,ac56 card d000,0000 rev 00 class 06,07,00 hdr 02
(II) PCI: 02:03:0: chip 8086,4220 card 8086,2721 rev 05 class 02,80,00 hdr 00
(II) PCI: 02:08:0: chip 8086,1068 card 1028,01a6 rev 03 class 02,00,00 hdr 00
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
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,6), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfdfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:1:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
(--) PCI:*(0:2:0) Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 3, Mem @ 0xdff00000/19, 0xc0000000/28, 0xdfec0000/18, I/O @ 0xec38/3
(--) PCI: (0:2:1) Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 3, Mem @ 0xdff80000/19
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
	[0] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[1] -1	0	0xdfdfe000 - 0xdfdfefff (0x1000) MX[B]
	[2] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[3] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[4] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[5] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[6] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[9] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[10] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[11] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x0000ec80 - 0x0000ecff (0x80) IX[B]
	[17] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[18] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[19] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[20] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[21] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[22] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[23] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[24] -1	0	0x0000ec38 - 0x0000ec3f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[1] -1	0	0xdfdfe000 - 0xdfdfefff (0x1000) MX[B]
	[2] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[3] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[4] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[5] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[6] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[9] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[10] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[11] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x0000ec80 - 0x0000ecff (0x80) IX[B]
	[17] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[18] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[19] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[20] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[21] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[22] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[23] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[24] -1	0	0x0000ec38 - 0x0000ec3f (0x8) IX[B](B)
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
	[4] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[5] -1	0	0xdfdfe000 - 0xdfdfefff (0x1000) MX[B]
	[6] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[7] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[10] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[16] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[17] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000ec80 - 0x0000ecff (0x80) IX[B]
	[23] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[24] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[25] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[26] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[27] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[28] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[29] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[30] -1	0	0x0000ec38 - 0x0000ec3f (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 915GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[5] -1	0	0xdfdfe000 - 0xdfdfefff (0x1000) MX[B]
	[6] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[7] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[10] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[16] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[17] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000ec80 - 0x0000ecff (0x80) IX[B]
	[23] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[24] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[25] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[26] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[27] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[28] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[29] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[30] -1	0	0x0000ec38 - 0x0000ec3f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[5] -1	0	0xdfdfe000 - 0xdfdfefff (0x1000) MX[B]
	[6] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[7] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[10] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[19] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[20] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000ec80 - 0x0000ecff (0x80) IX[B]
	[26] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[27] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[28] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[29] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[30] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[31] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[32] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[33] -1	0	0x0000ec38 - 0x0000ec3f (0x8) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915GM
(--) intel(0): Chipset: "915GM"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xDFF00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section DELL 1907FP
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "QDS", prod id 18
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): EDID vendor "QDS", prod id 18
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1024x768
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x8000085e to 0x800010bb
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00012d2d to 0x00028283
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00009696 to 0x00014141
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfec0000 - 0xdfefffff (0x40000) MS[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MS[B]
	[2] 0	0	0xdff00000 - 0xdff7ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[8] -1	0	0xdfdfe000 - 0xdfdfefff (0x1000) MX[B]
	[9] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[10] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[11] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[12] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[13] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] 0	0	0x0000ec38 - 0x0000ec3f (0x8) IS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[23] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[24] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000ec80 - 0x0000ecff (0x80) IX[B]
	[30] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[31] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[32] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[33] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[34] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[35] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[36] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[37] -1	0	0x0000ec38 - 0x0000ec3f (0x8) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 301312 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1205244 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): [drm] Registers = 0xdff00000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] mapped front buffer at 0xc0800000, handle = 0xc0800000
(II) intel(0): [drm] mapped back buffer at 0xc1800000, handle = 0xc1800000
(II) intel(0): [drm] mapped depth buffer at 0xc1c00000, handle = 0xc1c00000
(II) intel(0): [drm] mapped classic textures at 0xc2000000, handle = 0xc2000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 12582912 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x00800000 (pgoffset 2048)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x00c00000 (pgoffset 3072)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01800000 (pgoffset 6144)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x01c00000 (pgoffset 7168)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x02000000 (pgoffset 8192)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000004f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000004fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000004fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000004fe33000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x00800000-0x00bfffff: front buffer (4096 kB) X tiled
(II) intel(0): 0x00c00000-0x017fffff: exa offscreen (12288 kB)
(II) intel(0): 0x01800000-0x01bfffff: back buffer (4096 kB) X tiled
(II) intel(0): 0x01c00000-0x01ffffff: depth buffer (4096 kB) X tiled
(II) intel(0): 0x02000000-0x03ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc enabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
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
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 304 x 228
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
[config/hal] couldn't initialise context: (null) ((null))
(II) intel(0): fbc disabled on plane a
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xf8d17000 at 0xb7b21000
(II) intel(0): [drm] Closed DRM master.
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

```

Anything else I need to post? Thank you very much in advance for your help

~ejay563

---

### Post by cubeist on 2008-05-06
one line that jumps out at me is:
(II) intel(0): Setting screen physical size to 304 x 228

that looks wrong.  I would suggest editing your xorg.conf file and set your monitor to vesa.  This should allow you to boot in graphically, and from there you can try to-reinstall the intel graphics driver.  I would guess that the minimum size supported by your monitor is 640x480 and this is why you can't load graphical X.

---

### Post by eternicode on 2008-05-06
When in doubt, backup your xorg.conf and run "sudo dpkg-reconfigure xserver-xorg"

And is it just me, or is everyone having X server problems after the hardy upgrade?

---

### Post by cubeist on 2008-05-06
> **eternicode said:**
> When in doubt, backup your xorg.conf and run "sudo dpkg-reconfigure xserver-xorg"

And is it just me, or is everyone having X server problems after the hardy upgrade?

Reading through other posts, I don't think "sudo dpkg-reconfigure xserver-xorg" works like it used to because it no longer probes for what resolution to configure.  I think resolution is now handled graphically in Monitor resolution application.

---

### Post by eternicode on 2008-05-06
> **cubeist said:**
> Reading through other posts, I don't think "sudo dpkg-reconfigure xserver-xorg" works like it used to because it no longer probes for what resolution to configure.  I think resolution is now handled graphically in Monitor resolution application.

I don't know about "probing", but every time I run it (about 5 times since my upgrade :D ), it asks for which resolutions I want to support.  Always defaults to 1440x900, the right size for my screen, but it does ask.

---

### Post by cubeist on 2008-05-06
> **eternicode said:**
> I don't know about "probing", but every time I run it (about 5 times since my upgrade :D ), it asks for which resolutions I want to support.  Always defaults to 1440x900, the right size for my screen, but it does ask.

huh! interesting... I think it will only ask if your monitor supplies the correct EDID (at least I think that is what it is called)

I saw a post (just today) where a user was having a similar problem and he changed is monitor to generic, then ran "sudo dpkg-reconfigure xserver-xorg" and it worked, set the correct resolution.

---

### Post by ejay563 on 2008-05-06
So, neither of those options worked, so i think I'm just going to bring back my 7.10 install form the image of it that I took a while back. I think it likes me a bit more that 8.04, and I'll give 8.04 a bit more time to come to terms with me. Thanks anyway. 

~ejay563

---

### Post by cubeist on 2008-05-06
> **ejay563 said:**
> So, neither of those options worked, so i think I'm just going to bring back my 7.10 install form the image of it that I took a while back. I think it likes me a bit more that 8.04, and I'll give 8.04 a bit more time to come to terms with me. Thanks anyway. 

~ejay563

So, just to confirm, you cannot boot into X even with the vesa driver?

---

### Post by ejay563 on 2008-05-07
> **cubeist said:**
> So, just to confirm, you cannot boot into X even with the vesa driver?
No, the vesa driver didn't have any effect. I've loaded my 7.10 image, and am back up an running again. I'll stick with good old gusty until more bugs are worked out with hardy. Thanks for the attempt! :-)

---

### Post by cubeist on 2008-05-07
> **ejay563 said:**
> No, the vesa driver didn't have any effect. I've loaded my 7.10 image, and am back up an running again. I'll stick with good old gusty until more bugs are worked out with hardy. Thanks for the attempt! :-)

Search launchpad for similar bugs, if one does not exist, make sure to file a bug report so the problem can be diagnosed...

---

### Post by ejay563 on 2008-05-07
> **cubeist said:**
> Search launchpad for similar bugs, if one does not exist, make sure to file a bug report so the problem can be diagnosed...
posted a bug report. Thanks again!

---


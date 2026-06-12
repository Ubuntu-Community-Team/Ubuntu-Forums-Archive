---
title: "Login page in endless loop :("
date: 2007-11-13
forum: Dell  Ubuntu Support
---

### Post by shushu on 2007-11-13
Hi,

I have a strange issue (OS is Kubuntu base on Ubuntu704, On Dell D410):
- when starting the laptop when its docked all is fine, when detaching is all is fine also meaning I am able to view the desktop on the laptop.
- when starting the laptop undocked I get to the login page and then when pressing the login (after filling the user and password) the system tries to start but returning back to the login page.

I must say that I can enter in safe mode and login into it just fine.

Please help.
Thanks

---

### Post by Triptol on 2007-11-13
Might be helpful if you post your /var/log/Xorg.0.log file (or the relevant part about the crash) here.

---

### Post by shushu on 2007-11-14
Thanks for the quick reply.
Here is the file contents, the file is after a successful login when the machine is docked (as mentioned above I cannot login when not docked):


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux shushu-kubuntu 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 14 09:08:37 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "i810"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2590 card 1028,018f rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2592 card 1028,018f rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2792 card 1028,018f rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 1028,018f rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1028,018f rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1028,018f rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1028,018f rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1028,018f rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev d3 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,266e card 1028,018f rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,2641 card 1028,018f rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 1028,018f rev 03 class 01,01,8a hdr 00
(II) PCI: 01:00:0: chip 14e4,1677 card 1028,018f rev 01 class 02,00,00 hdr 00
(II) PCI: 02:01:0: chip 104c,8036 card 1400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 02:01:5: chip 104c,8038 card 1028,018f rev 00 class 07,80,00 hdr 80
(II) PCI: 02:03:0: chip 8086,4220 card 8086,2722 rev 05 class 02,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfdfffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,6), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfcfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:1:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
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
	[0] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[1] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B]
	[2] -1	0	0xdfcfd000 - 0xdfcfdfff (0x1000) MX[B]
	[3] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[4] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[5] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[6] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[7] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[8] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[11] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[17] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[18] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[19] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[20] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[21] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[22] -1	0	0x0000ec38 - 0x0000ec3f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[1] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B]
	[2] -1	0	0xdfcfd000 - 0xdfcfdfff (0x1000) MX[B]
	[3] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[4] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[5] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[6] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[7] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[8] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[11] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[17] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[18] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[19] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[20] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[21] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[22] -1	0	0x0000ec38 - 0x0000ec3f (0x8) IX[B](B)
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
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B]
	[6] -1	0	0xdfcfd000 - 0xdfcfdfff (0x1000) MX[B]
	[7] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[8] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[9] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[10] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[11] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[12] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[23] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[24] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[25] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[26] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000ec38 - 0x0000ec3f (0x8) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
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
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 14.94.94
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ, 965GM
(II) Primary Device is: PCI 00:02:0
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 915GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B]
	[6] -1	0	0xdfcfd000 - 0xdfcfdfff (0x1000) MX[B]
	[7] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[8] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[9] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[10] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[11] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[12] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[23] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[24] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[25] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[26] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000ec38 - 0x0000ec3f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B]
	[6] -1	0	0xdfcfd000 - 0xdfcfdfff (0x1000) MX[B]
	[7] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[8] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[9] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[10] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[11] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[12] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[26] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[27] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[28] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[29] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[30] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[31] -1	0	0x0000ec38 - 0x0000ec3f (0x8) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915GM
(--) intel(0): Chipset: "915GM"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xDFF00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "SEC", prod id 19032
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) intel(0): I2C bus "SDVOB DDC Bus" initialized.
(II) intel(0): SDVO device VID/DID: 04:AA.02, clock range 25.0MHz - 165.0MHz, input 1: Y, input 2: N, output 1: Y, output 2: N
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Current clock rate multiplier: 8
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "SEC", prod id 19032
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID vendor "DEL", prod id 16405
(EE) intel(0): First SDVO output reported failure to sync
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) intel(0): Comparing regs from server start up to After PreInit
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
	[7] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[8] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B]
	[9] -1	0	0xdfcfd000 - 0xdfcfdfff (0x1000) MX[B]
	[10] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[11] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[12] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[13] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[14] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[15] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] 0	0	0x0000ec38 - 0x0000ec3f (0x8) IS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[30] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[31] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[32] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[33] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[34] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[35] -1	0	0x0000ec38 - 0x0000ec3f (0x8) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 4860 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00027fff: logical 3D context (32 kB)
(II) intel(0): 0x00028000-0x00037fff: xaa scratch (64 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x007bf000-0x007bffff: Core cursor (4 kB, 0x1fa94000 physical)
(II) intel(0): 0x007c0000-0x007c3fff: ARGB cursor (16 kB, 0x334dc000 physical)
(II) intel(0): 0x007c4000-0x007c4fff: Core cursor (4 kB, 0x1f953000 physical)
(II) intel(0): 0x007c5000-0x007c8fff: ARGB cursor (16 kB, 0x334f0000 physical)
(II) intel(0): 0x007c9000-0x007c9fff: overlay registers (4 kB, 0x348bf000 physical)
(II) intel(0): 0x007d0000-0x037c7fff: front buffer (49120 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (10240 kB)
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (10240 kB)
(II) intel(0): 0x06000000-0x07ffffff: DRI memory manager (32768 kB)
(II) intel(0): 0x08000000-0x09ffffff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] loaded kernel module for "i915" driver
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0xf8e65000
(II) intel(0): [drm] mapped SAREA 0xf8e65000 to 0xb7b19000
(II) intel(0): [drm] framebuffer handle = 0xc07d0000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): Unable to use TTM-based memory manager with DRM version 1.6
(II) intel(0): [drm] Registers = 0xdff00000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] init sarea width,height = 1280 x 1280 (pitch 2048)
(II) intel(0): [drm] Mapping front buffer
(II) intel(0): [drm] Front Buffer = 0x280fa000
(II) intel(0): [drm] Back Buffer = 0xc4000000
(II) intel(0): [drm] Depth Buffer = 0xc5000000
(II) intel(0): [drm] textures = 0xc8000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): Current clock rate multiplier: 8
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x007c0000 (pgoffset 1984)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007c4000 (pgoffset 1988)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x007c5000 (pgoffset 1989)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x007c9000 (pgoffset 1993)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x007d0000 (pgoffset 2000)
(II) intel(0): xf86BindGARTMemory: bind key 6 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 7 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 8 at 0x08000000 (pgoffset 32768)
(EE) intel(0): First SDVO output reported failure to sync
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TMDS-1 is connected to pipe A
(II) intel(0):   Output TV is connected to pipe none
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
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
(II) intel(0): Setting screen physical size to 246 x 184
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
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event5
(**) Option "Device" "/dev/input/event5"
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
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event5
(**) Option "Device" "/dev/input/event5"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): EDID vendor "SEC", prod id 19032
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID vendor "DEL", prod id 16405
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): EDID vendor "SEC", prod id 19032
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID vendor "DEL", prod id 16405
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): EDID vendor "SEC", prod id 19032
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID vendor "DEL", prod id 16405
(EE) intel(0): First SDVO output reported failure to sync
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): EDID vendor "SEC", prod id 19032
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID vendor "DEL", prod id 16405
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): EDID vendor "SEC", prod id 19032
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID vendor "DEL", prod id 16405
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): EDID vendor "SEC", prod id 19032
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID vendor "DEL", prod id 16405
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): EDID vendor "SEC", prod id 19032
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID vendor "DEL", prod id 16405
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): EDID vendor "SEC", prod id 19032
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID vendor "DEL", prod id 16405
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): EDID vendor "SEC", prod id 19032
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID vendor "DEL", prod id 16405

---

### Post by Triptol on 2007-11-15
Well you seem to have some errors there (marked (EE)).```
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID vendor "DEL", prod id 16405
(EE) intel(0): First SDVO output reported failure to sync
``` The errors about the wacom device just indicate that you don't have such a device and so they don't hurt. I did a little bit of googling on the errors above and came up with the following link (which might have an answer): [http://lists.debian.org/debian-user/2007/08/msg00414.html](http://lists.debian.org/debian-user/2007/08/msg00414.html)

On another thread some one indicated you might want to recompile the intel driver from source. The following commands should do that for you:
```
$ sudo aptitude install fakeroot dpkg-dev
$ sudo apt-get build-dep xserver-xorg-video-intel
$ mkdir xserver-xorg-video-intel
$ cd xserver-xorg-video-intel
$ apt-get source xserver-xorg-video-intel
$ cd xserver-xorg-video-intel-2.1.0/
$ dpkg-buildpackage -rfakeroot -b
$ cd ..
$ sudo dpkg -i xserver-xorg-video-intel_*.deb
```

I would only try recompiling as a last resort. I don't think it will do you an awful lot of good, but one might never know.

---


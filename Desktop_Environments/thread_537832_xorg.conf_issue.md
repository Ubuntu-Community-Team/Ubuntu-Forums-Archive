---
title: "xorg.conf issue"
date: 2007-08-29
forum: Desktop Environments
---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-08-29
I recently had this problem: [http://ubuntuforums.org/showthread.php?t=536904](http://ubuntuforums.org/showthread.php?t=536904)

I'm assuming it stems from the graphics card drivers that I recently installed. I'm using an NVidia GeForce Go 7400, if that helps. I've installed graphics card drivers from two places:

1) Envy, from this tutorial: [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

2) sudo apt-get install nvidia-glx-new from this tutorial: [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

I had to change "nvidia" to "nv" under "Devices" in order to fix the problem (the graphical Ubuntu desktop would not load). I have good reason to believe the latter is the source of the problem, as I recently uninstalled my Envy drivers, changed "nv" back to "nvidia" and the error persisted. Presumably it's desirable to be able to change "nv" back to "nvidia", and I do eventually want to get Compiz Fusion working, too.

Any help is appreciated.

---

### Post by cek on 2007-08-29
What is the output of /var/log/Xorg.0.log?

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-08-30
This file is enormous, so I'm assuming you want the tail end of it:

```
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
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
ProcXCloseDevice to close or not ?
```

---

### Post by kellemes on 2007-08-30
You need to post the hole /var/log/Xorg.0.log within [CODE]-tags

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-08-31
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux computer 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 30 08:50:36 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
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
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7a16e0
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
(II) PCI: 00:00:0: chip 8086,27a0 card 103c,30bb rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 103c,30bb rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 103c,30bb rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 103c,30bb rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 103c,30bb rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 103c,30bb rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 103c,30bb rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 103c,30bb rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 103c,30bb rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c5 card 103c,30bb rev 02 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 103c,30bb rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d8 card 103c,30bb rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 8086,4222 card 103c,135b rev 02 class 02,80,00 hdr 00
(II) PCI: 05:00:0: chip 8086,109a card 103c,30bb rev 00 class 02,00,00 hdr 00
(II) PCI: 07:05:0: chip 1180,0832 card 103c,30bb rev 00 class 0c,00,10 hdr 80
(II) PCI: 07:05:1: chip 1180,0822 card 103c,30bb rev 19 class 08,05,00 hdr 80
(II) PCI: 07:05:2: chip 1180,0843 card 103c,30bb rev 01 class 08,80,00 hdr 80
(II) PCI: 07:05:3: chip 1180,0592 card 103c,30bb rev 0a class 08,80,00 hdr 80
(II) PCI: 07:05:4: chip 1180,0852 card 103c,30bb rev 05 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0018 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xd9ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xd6000000 - 0xd7ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:2), (0,5,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xda000000 - 0xdbffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xd5ffffff (0x2000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:30:0), (0,7,7), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xde000000 - 0xde0fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce Go 7400 rev 161, Mem @ 0xdd000000/24, 0xc0000000/28, 0xdc000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xde000800 - 0xde0008ff (0x100) MX[B]
	[1] -1	0	0xde000000 - 0xde0007ff (0x800) MX[B]
	[2] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B]
	[3] -1	0	0xd8000000 - 0xd8000fff (0x1000) MX[B]
	[4] -1	0	0xde304400 - 0xde3047ff (0x400) MX[B]
	[5] -1	0	0xde304000 - 0xde3043ff (0x400) MX[B]
	[6] -1	0	0xde300000 - 0xde303fff (0x4000) MX[B]
	[7] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[10] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[11] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[12] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[13] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[14] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[15] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[16] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[17] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xde001400 - 0xde0014ff (0x100) MX[B]
	[1] -1	0	0xde001000 - 0xde0010ff (0x100) MX[B]
	[2] -1	0	0xde000c00 - 0xde000cff (0x100) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xde000800 - 0xde0008ff (0x100) MX[B]
	[1] -1	0	0xde000000 - 0xde0007ff (0x800) MX[B]
	[2] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B]
	[3] -1	0	0xd8000000 - 0xd8000fff (0x1000) MX[B]
	[4] -1	0	0xde304400 - 0xde3047ff (0x400) MX[B]
	[5] -1	0	0xde304000 - 0xde3043ff (0x400) MX[B]
	[6] -1	0	0xde300000 - 0xde303fff (0x4000) MX[B]
	[7] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[10] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[11] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[12] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[13] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[14] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[15] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[16] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[17] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xde001400 - 0xde0014ff (0x100) MX[B]
	[1] -1	0	0xde001000 - 0xde0010ff (0x100) MX[B]
	[2] -1	0	0xde000c00 - 0xde000cff (0x100) MX[B]
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
	[4] -1	0	0xde000800 - 0xde0008ff (0x100) MX[B]
	[5] -1	0	0xde000000 - 0xde0007ff (0x800) MX[B]
	[6] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B]
	[7] -1	0	0xd8000000 - 0xd8000fff (0x1000) MX[B]
	[8] -1	0	0xde304400 - 0xde3047ff (0x400) MX[B]
	[9] -1	0	0xde304000 - 0xde3043ff (0x400) MX[B]
	[10] -1	0	0xde300000 - 0xde303fff (0x4000) MX[B]
	[11] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xde001400 - 0xde0014ff (0x100) MX[B]
	[15] -1	0	0xde001000 - 0xde0010ff (0x100) MX[B]
	[16] -1	0	0xde000c00 - 0xde000cff (0x100) MX[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[20] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[21] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[22] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[23] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[24] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[25] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[26] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[32] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[33] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[34] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 2.0.0
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
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	Quadro FX 5600, Quadro FX 4600
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset GeForce Go 7400 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xde000800 - 0xde0008ff (0x100) MX[B]
	[5] -1	0	0xde000000 - 0xde0007ff (0x800) MX[B]
	[6] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B]
	[7] -1	0	0xd8000000 - 0xd8000fff (0x1000) MX[B]
	[8] -1	0	0xde304400 - 0xde3047ff (0x400) MX[B]
	[9] -1	0	0xde304000 - 0xde3043ff (0x400) MX[B]
	[10] -1	0	0xde300000 - 0xde303fff (0x4000) MX[B]
	[11] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xde001400 - 0xde0014ff (0x100) MX[B]
	[15] -1	0	0xde001000 - 0xde0010ff (0x100) MX[B]
	[16] -1	0	0xde000c00 - 0xde000cff (0x100) MX[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[20] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[21] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[22] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[23] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[24] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[25] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[26] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[32] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[33] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[34] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xde000800 - 0xde0008ff (0x100) MX[B]
	[5] -1	0	0xde000000 - 0xde0007ff (0x800) MX[B]
	[6] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B]
	[7] -1	0	0xd8000000 - 0xd8000fff (0x1000) MX[B]
	[8] -1	0	0xde304400 - 0xde3047ff (0x400) MX[B]
	[9] -1	0	0xde304000 - 0xde3043ff (0x400) MX[B]
	[10] -1	0	0xde300000 - 0xde303fff (0x4000) MX[B]
	[11] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xde001400 - 0xde0014ff (0x100) MX[B]
	[15] -1	0	0xde001000 - 0xde0010ff (0x100) MX[B]
	[16] -1	0	0xde000c00 - 0xde000cff (0x100) MX[B]
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[23] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[24] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[25] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[26] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[27] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[28] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[29] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[35] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[36] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[37] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce Go 7400"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xC0000000
(--) NV(0): MMIO registers at 0xDD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1280 x 800
(II) NV(0): Panel is LVDS
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Generic Monitor: Using hsync range of 28.00-64.00 kHz
(II) NV(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "832x624" (vrefresh out of range)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) NV(0): Virtual size is 1280x800 (pitch 1280)
(**) NV(0): *Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) NV(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) NV(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) NV(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(==) NV(0): DPI set to (75, 75)
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
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xde000800 - 0xde0008ff (0x100) MX[B]
	[8] -1	0	0xde000000 - 0xde0007ff (0x800) MX[B]
	[9] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B]
	[10] -1	0	0xd8000000 - 0xd8000fff (0x1000) MX[B]
	[11] -1	0	0xde304400 - 0xde3047ff (0x400) MX[B]
	[12] -1	0	0xde304000 - 0xde3043ff (0x400) MX[B]
	[13] -1	0	0xde300000 - 0xde303fff (0x4000) MX[B]
	[14] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[17] -1	0	0xde001400 - 0xde0014ff (0x100) MX[B]
	[18] -1	0	0xde001000 - 0xde0010ff (0x100) MX[B]
	[19] -1	0	0xde000c00 - 0xde000cff (0x100) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[26] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[27] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[28] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[29] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[30] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[31] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[32] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[38] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[39] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[40] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xc0000000,0x8000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
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
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(WW) NV(0): Option "NoLogo" is not used
(WW) NV(0): Option "AddARGBGLXVisuals" is not used
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
(EE) AIGLX: DRI module not loaded
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
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
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
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
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
ProcXCloseDevice to close or not ?
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

---

### Post by dumbbeatnix on 2007-08-31
Hello Everyone

Just a simple search found how people got NVidia to work for them.  There was this one guy Andrew Smith, he had a card similar to yours (in fact it is the same).

Dont believe me!!!!  Then follow this link:

[Andrew Smith]("http://http://ubuntuforums.org/showpost.php?p=1947135&postcount=127")

He said something about deleting some files, this is only advice I can give.  Maybe it works, maybe I'm a pizza.  Don't smell like mozarella to me.  Check it out it may work.

Cheers
dumbbeatnix :guitar:

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-01
Did that and it didn't work.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-01
bump

---

### Post by bruno666 on 2007-09-02
Check that you have linux-restricted-modules and nvidia-glx-new installed.

Maybe, you'll need to type the command :

sudo dpkg-reconfigure xserver-xorg

and answer the questions to reconfigure your X server.
 
You need to post the /var/log/Xorg0.log file when using nvidia driver, not nv which is working...

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-03
I don't know how I can do that when I can't access GNOME without "nv". If you give me instructions, I can try, though.

---

### Post by Happy_Man on 2007-09-03
Well, change it to nvidia, and log in. When it hangs, press ctrl-alt-f1 and log in as yourself. Then use the command there ```
cp /var/log/xorg.0.log ~/xorg.0.log
``` and then edit the xorg.conf back to nv with the command ```
sudo nano /etc/X11/xorg.conf
``` After you have changed it back, press ctrl-x to quit, pressing enter when it prompts you (should be twice you have to press it.) Press ctrl-alt-f7 to go back to the GUI, and press ctrl-alt-backspace to restart X. It should take you to the login screen. Then post the ~/xorg.0.log file here.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-10-27
Wow, I finally got around to tackling this problem again. I haven't had much free time for the past two months, lol.

I tried doing cp /var/log/xorg.0.log ~/xorg.0.log but it said that /var/log/xorg.0.log couldn't be found.

(Sorry for the ancient bump, but I feel it's better than posting an entirely new thread.)

P.S. I'm still using Feisty Fawn, I can't upgrade currently and I think that it's better to fix this issue before upgrading.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-10-31
Bump.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-11-07
bump. I recently tried changing "nv" to "nvidia" for Envy uninstallation and reinstallation, but neither worked, so I'm assuming it's the second set of drivers in the first post that's causing me trouble.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-11-08
bump.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-11-10
Uh, I tried to upgrade to 7.10 and it half-installed; now I *really* need help. ](*,)

---

### Post by Happy_Man on 2007-11-11
Honestly, at this point, I can only suggest burning a Gutsy CD and working from there.

---

### Post by zippy028 on 2007-11-11
If you get Gutsy installed you can try what I did to solve this problem.

[My Post]("http://ubuntuforums.org/showthread.php?t=594196")

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-11-11
> **zippy028 said:**
> If you get Gutsy installed you can try what I did to solve this problem.

[My Post]("http://ubuntuforums.org/showthread.php?t=594196")

The nvidia-glx-new drivers I installed from the link before are what's giving me trouble upgrading, I think.

---


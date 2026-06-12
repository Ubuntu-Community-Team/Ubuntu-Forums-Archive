---
title: "unichrome II problem"
date: 2005-11-01
forum: Desktop Environments
---

### Post by wammy on 2005-11-01
i have an intergrated unichrome II vga chip on my mobo and it gives me an headache.

although from different threads here i understand that it should work for desktop stuff it doesnt work for me.

i see the gnome login screen but as soon as i log in the screen goes.. ehhr.. brown.

i can still move the mouse around but the desktop never appears.

cant find anything that looks like an error in xorg.log or in dmesg or in messages...

so, is this fixable or maybe a work around?

somewhere i read to replace 'via' with 'vesa' in xorg.conf but there's no such entry...

oftopic,
why isnt there an init script for iptables in /.etc/rc.x
(i'm used to redhat....)

---

### Post by dcstar on 2005-11-02
[QUOTE=wammy]i have an intergrated unichrome II vga chip on my mobo and it gives me an headache.
........
somewhere i read to replace 'via' with 'vesa' in xorg.conf but there's no such entry...
........[/QUOTE]

Here's what my UniChrome xorg.conf entries look like:

------
Section "Device"
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection
-------
Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Monitor		"StudioWorks"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
(with more following........


You may want to run: sudo dpkg-reconfigure xserver-xorg

---

### Post by jvictor on 2005-11-02
[http://ubuntuforums.org/showthread.php?t=76037](http://ubuntuforums.org/showthread.php?t=76037)

---

### Post by wammy on 2005-11-02
i saw that thread... doesnt help me unfortunately.

the strange thing is that the x server does start correctly but only after loging in gnome doesnt seem to load so i'm not sure if this even is a video card problem...

btw,
i overlooked something in the conf file,
seems like the installer already choose for vesa mode.

i ran dpkg-reconfigure xserver-xorg and choose via option but that doesnt change much.

---

### Post by Teroedni on 2005-11-02
To get xorg.log write in gnome
sudo gedit /var/log/Xorg.0.log


if you in console(before x start)write
sudo nano /var/log/Xorg.0.log

i guess you have no possible to paste your x.org and x.log here, but if you can please do it.

---

### Post by wammy on 2005-11-07
the forum says that the text is to long so here is the log file but only a part of it:

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux localhost 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  7 18:13:22 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
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
(II) Open APM successful
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0204 card 1106,0204 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1204 card 1106,1204 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2204 card 1106,2204 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3204 card 1106,3204 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4204 card 1106,4204 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7204 card 1106,7204 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 1106,3149 card 1106,3149 rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1106,3038 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1106,3104 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1106,3227 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1019,aa01 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1106,3108 card 1106,0204 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:0:1), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:0:2), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:0:3), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:0:4), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:0:7), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfca00000 - 0xfeafffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf4900000 - 0xfc8fffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:0), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:1), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:2), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:3), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x3108) rev 1, Mem @ 0xf8000000/26, 0xfd000000/24, BIOS @ 0xfeaf0000/16
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd3ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[1] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[2] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[3] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[4] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[5] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[6] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[7] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[8] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[9] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[10] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[1] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[2] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[3] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[4] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[5] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[6] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[7] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[8] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[9] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[10] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
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
	[5] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[17] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
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
(II) LoadModule: "vesa"
(II) Loading /usr/X11R6/lib/modules/drivers/vesa_drv.o
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
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
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[17] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32768 kB
(II) VESA(0): VESA VBE OEM: VIA K8M800


(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: 
(II) VESA(0): VESA VBE OEM Product: 
(II) VESA(0): VESA VBE OEM Product Rev: 
(**) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 101 (640x480)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0006969
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 101
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xf8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 101
	LinNumberOfImagePages: 101
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0

<snip>

Mode: 102 (800x600)
	ModeAttributes: 0x1f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0006969
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0

(II) VESA(0): Total Memory: 512 64KB banks (32768kB)
(II) VESA(0): Generic Monitor: Using hsync range of 28.00-51.00 kHz
(II) VESA(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) VESA(0): Not using built-in mode "1280x800" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1280x768" (width too large for virtual size)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(++) VESA(0): DPI set to (100, 100)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/X11R6/lib/modules/libshadow.a
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfebff800 - 0xfebff8ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32768 kB
(II) VESA(0): VESA VBE OEM: VIA K8M800


(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: 
(II) VESA(0): VESA VBE OEM Product: 
(II) VESA(0): VESA VBE OEM Product Rev: 
(==) VESA(0): Write-combining range (0xf8000000,0x2000000)
(II) VESA(0): virtual address = 0xb5cea000,
	physical address = 0xf8000000, size = 33554432
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
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
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
(II) Open APM successful
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open APM successful
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open APM successful
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

---


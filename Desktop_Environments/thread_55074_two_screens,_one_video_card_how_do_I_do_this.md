---
title: "two screens, one video card: how do I do this?"
date: 2005-08-07
forum: Desktop Environments
---

### Post by ad noiseam on 2005-08-07
Hello,

I am really new to Linux, please bear with me... :/

I have a ATI Radeon 7500 card, with has two outputs, each of them going to a screen (simple, generic monitors).

I have look in these forums (both the english and french ones) for information about how to get a "wide" screen on Linux (rather than the same thing on each screen), but am having trboule with this.

Here is the Xorg.conf that I tried. When using this, Ubuntu boots OK, but I just have the same thing on each screen, it doesn't help a lot.

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 7500 (RV200 QW)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"leftscreen"
	Device		"ATI Technologies, Inc. Radeon 7500 (RV200 QW)"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"rightscreen"
	Device		"ATI Technologies, Inc. Radeon 7500 (RV200 QW)"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"leftscreen"
	Screen		"rightscreen" RightOf "leftscreen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

I have read everywhere about Xinerama, but I have no idea if I have it installed (I didn't install it, I am sure of this) or how to use it.

Any idea?

Nicolas

---

### Post by PeP on 2005-08-07
you might want to try the official but non-free ati drivers, look here:

[http://ubuntuforums.org/showthread.php?t=51408&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=51408&page=1&pp=10)

---

### Post by ad noiseam on 2005-08-08
Yes, I tried what you had written in this thread, and encounted the exact same problems as the original poster there.

So, I went and installed fglrx-control from Synaptic again, and modified my Xorg.conf to be what had worked for this user.

Here it is:
```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 7500 (RV200 QW)""
	Driver		"fglrx"
  	Option 		"VideoOverlay" 		"on"
  	Option 		"OpenGLOverlay" 	"off"
  	Option 		"UseInternalAGPGART" 	"no"
	BusID		"PCI:1:0:0
Option "DesktopSetup" "0x00000201"
Option "MonitorLayout" "AUTO, AUTO"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 7500 (RV200 QW)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480" "1x1"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

And it still doesn't work.

Also, if I go to a terminal and type "fireglcontrol", I get a window telling me:

> 
Driver does not provide the FireGL X11 extensions! Panel components will operate only partially


I click OK, get an ATI Control panel with some information and a panel called "TV out"... That's all. :(

---

### Post by PeP on 2005-08-08
ok, let's start from the beginning.

do you have errors in /var/log/gdm.log (or kdm.log or xdm.log) ?
do you have errors in /var/log/xorg.0.log ?

what is the output of 
% glxinfo |grep direct

what is your kernel version
% uname -a

are the corresponding restricted modules installed ?

---

### Post by ad noiseam on 2005-08-08
[QUOTE=PeP]ok, let's start from the beginning.

do you have errors in /var/log/gdm.log (or kdm.log or xdm.log) ?
[/QUOTE]

Not that I can find, no.

[QUOTE=PeP]do you have errors in /var/log/xorg.0.log ?[/QUOTE]

Yes, this log file is so big that I can't post it here, I will have to split it into several posts.

[QUOTE=PeP]what is your kernel version
% uname -a[/QUOTE]

Linux ubuntu 2.6.10-5-386

[QUOTE=PeP]are the corresponding restricted modules installed ?[/QUOTE]

Yes...

---

### Post by ad noiseam on 2005-08-08
Here is the first half of my xorg.0.log:

```


X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux nicolas 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@vernadsky) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Jun 24 16:53:01 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug  8 16:01:15 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon 7500 (RV200 QW)"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "de"
(**) XKB: layout: "de"
(**) Option "XkbOptions" "nodeadkeys"
(**) XKB: options: "nodeadkeys"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
(II) PCI: 00:00:0: chip 1039,0735 card 0000,0000 rev 01 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1039,0001 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0018 card 0000,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:2: chip 1039,7001 card 1019,0a14 rev 07 class 0c,03,10 hdr 00
(II) PCI: 00:02:3: chip 1039,7001 card 1019,0a14 rev 07 class 0c,03,10 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1039,5513 rev d0 class 01,01,80 hdr 80
(II) PCI: 00:03:0: chip 1039,0900 card 1019,0a14 rev 90 class 02,00,00 hdr 00
(II) PCI: 00:0b:0: chip 1102,0002 card 1102,8027 rev 07 class 04,01,00 hdr 80
(II) PCI: 00:0b:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: 00:0d:0: chip 10ec,8029 card 1259,2400 rev 00 class 02,00,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 00:0f:2: chip 1106,3104 card 1106,3104 rev 63 class 0c,03,20 hdr 80
(II) PCI: 00:0f:3: chip 1033,00e7 card 1033,00ce rev 01 class 0c,00,10 hdr 00
(II) PCI: 01:00:0: chip 1002,5157 card 1787,0f07 rev 00 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xcfe00000 - 0xcfefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbfc00000 - 0xcfcfffff (0x10100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon RV200 QW [Radeon 7500] rev 0, Mem @ 0xc0000000/27, 0xcfef0000/16, I/O @ 0x9800/8, BIOS @ 0xcfec0000/17
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
	[0] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[1] -1	0	0xcfffcf00 - 0xcfffcfff (0x100) MX[B]
	[2] -1	0	0xcffdd000 - 0xcffddfff (0x1000) MX[B]
	[3] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[4] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[7] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[10] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[15] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[16] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[17] -1	0	0x00009800 - 0x000098ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[1] -1	0	0xcfffcf00 - 0xcfffcfff (0x100) MX[B]
	[2] -1	0	0xcffdd000 - 0xcffddfff (0x1000) MX[B]
	[3] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[4] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[7] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[10] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[15] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[16] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[17] -1	0	0x00009800 - 0x000098ff (0x100) IX[B](B)
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
	[5] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[6] -1	0	0xcfffcf00 - 0xcfffcfff (0x100) MX[B]
	[7] -1	0	0xcffdd000 - 0xcffddfff (0x1000) MX[B]
	[8] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[9] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[12] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[23] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[24] -1	0	0x00009800 - 0x000098ff (0x100) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
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
(II) Loading extension FontCache
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
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
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
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 6.5.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) ATI: ATI driver (version 6.5.6) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
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
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9200PRO 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9700 NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI RADEON 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireGL D1100 (RV370) 5B65 (PCIE),
	ATI Radeon Mobility M300 (M22) 5460 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI FireGL V5000,
	ATI MOBILITY FireGL V5000, ATI MOBILITY FireGL V5000,
	ATI MOBILITY RADEON X700, ATI MOBILITY RADEON X700,
	ATI RADEON X700 PRO, ATI RADEON X700 XT, ATI RADEON X700,
	ATI RADEON X700 SE, ATI RADEON X700 SE,
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI RADEON X800 SE,
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V7200 (R423) UQ (PCIE), ATI FireGL V5100 (R423) UR (PCIE),
	ATI FireGL V7100 (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100,
	ATI MOBILITY FireGL V5100, ATI MOBILITY RADEON X800,
	ATI MOBILITY RADEON X800 XT, ATI RADEON X800, ATI RADEON X800 XL,
	ATI RADEON R430 SE, ATI RADEON R430 XTP, ATI RADEON R480 4P,
	ATI RADEON R480 GL 16P, ATI RADEON R480 SE, ATI RADEON X850 PRO,
	ATI RADEON X850 XT, ATI RADEON X850 XT Platinum Edition,
	ATI RADEON X850 PRO, ATI RADEON X850 SE, ATI RADEON X850 XT,
	ATI RADEON X850 XT Platinum Edition
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon 7500 (RV200 QW)".
(--) Chipset ATI Radeon 7500 QW (AGP/PCI) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[6] -1	0	0xcfffcf00 - 0xcfffcfff (0x100) MX[B]
	[7] -1	0	0xcffdd000 - 0xcffddfff (0x1000) MX[B]
	[8] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[9] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[12] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[23] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[24] -1	0	0x00009800 - 0x000098ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/X11R6/lib/modules/drivers/radeon_drv.o
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 4.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[6] -1	0	0xcfffcf00 - 0xcfffcfff (0x100) MX[B]
	[7] -1	0	0xcffdd000 - 0xcffddfff (0x1000) MX[B]
	[8] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[9] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[12] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[26] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[27] -1	0	0x00009800 - 0x000098ff (0x100) IX[B](B)
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xcfef0000
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 7500 QW (AGP/PCI)" (ChipID = 0x5157)
(--) RADEON(0): Linear framebuffer at 0xc0000000
(--) RADEON(0): BIOS at 0xcfec0000
(--) RADEON(0): VideoRAM: 65536 kByte (128 bit SDR SDRAM)
(II) RADEON(0): AGP card detected
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Type: 1
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 1
(II) RADEON(0): EDID data from the display on port 1 ----------------------
(II) RADEON(0): Manufacturer: VSN  Model: 1712  Serial#: 2123
(II) RADEON(0): Year: 2002  Week: 3
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.64
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.651 redY: 0.320   greenX: 0.280 greenY: 0.615
(II) RADEON(0): blueX: 0.141 blueY: 0.057   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 78.8 MHz   Image Size:  300 x 225 mm
(II) RADEON(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) RADEON(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 98 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: S98S
(II) RADEON(0): Serial No: CDID02102123
(II) RADEON(0): EDID data from the display on port 2-----------------------
(II) RADEON(0): Manufacturer: SNI  Model: ab0b  Serial#: 16544
(II) RADEON(0): Year: 1997  Week: 9
(II) RADEON(0): EDID Version: 1.0
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.714/0.286 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 31  vert.: 23
(II) RADEON(0): Gamma: 2.13
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.274 greenY: 0.604
(II) RADEON(0): blueX: 0.149 blueY: 0.064   whiteX: 0.282 whiteY: 0.298
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 800  vsize 600  refresh: 100  vid: 26693
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 100  vid: 26721
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 85  vid: 22897
(II) RADEON(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 40.5 MHz   Image Size:  300 x 225 mm
(II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 720 h_blank_end 800 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 481  v_sync_end 484 v_blanking: 506 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 67.5 MHz   Image Size:  300 x 225 mm
(II) RADEON(0): h_active: 800  h_sync: 832  h_sync_end 912 h_blank_end 1072 h_border: 0
(II) RADEON(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 633 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 112.5 MHz   Image Size:  300 x 225 mm
(II) RADEON(0): h_active: 1024  h_sync: 1056  h_sync_end 1216 h_blank_end 1392 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 773 v_blanking: 809 v_border: 0
(II) RADEON(0): 

```

---

### Post by ad noiseam on 2005-08-08
and here is the second half:

```


(II) RADEON(0): Primary:
 Monitor   -- CRT
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): Secondary:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=35000; xclk=16000
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(WW) RADEON(0): config file hsync range 28-49kHz not within DDC hsync ranges.
(WW) RADEON(0): config file vrefresh range 43-72Hz not within DDC vrefresh ranges.
(II) RADEON(0): Generic Monitor: Using hsync range of 28.00-49.00 kHz
(II) RADEON(0): Generic Monitor: Using vrefresh range of 43.00-72.00 Hz
(II) RADEON(0): Clock range:  20.00 to 350.00 MHz
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "832x624" (hsync out of range)
(II) RADEON(0): Not using default mode "416x312" (hsync out of range)
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (hsync out of range)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using mode "1x1" (no mode of this name)
(II) RADEON(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x768" (width too large for virtual size)
(II) RADEON(0): Validating CRTC2 modes for MergedFB ------------ 
(WW) RADEON(0): config file hsync range 28-49kHz not within DDC hsync ranges.
(WW) RADEON(0): config file vrefresh range 43-72Hz not within DDC vrefresh ranges.
(II) RADEON(0): CRT2 Monitor: Using hsync range of 28.00-49.00 kHz
(II) RADEON(0): CRT2 Monitor: Using vrefresh range of 43.00-72.00 Hz
(II) RADEON(0): Clock range:  20.00 to 350.00 MHz
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "832x624" (hsync out of range)
(II) RADEON(0): Not using default mode "416x312" (hsync out of range)
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (hsync out of range)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using mode "1x1" (no mode of this name)
(II) RADEON(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x768" (width too large for virtual size)
(II) RADEON(0): Total of 7 CRTC2 modes found for MergedFB------------ 
(II) RADEON(0): Modes for CRT1: ********************
(--) RADEON(0): Virtual size is 1024x768 (pitch 1024)
(**) RADEON(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) RADEON(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) RADEON(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) RADEON(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) RADEON(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(II) RADEON(0): Modes for CRT2: ********************
(--) RADEON(0): Virtual size is 1024x768 (pitch 1024)
(**) RADEON(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) RADEON(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) RADEON(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) RADEON(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) RADEON(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(II) RADEON(0): Generating MergedFB mode list
(II) RADEON(0): No MetaModes given, linking first modes by default
(II) RADEON(0): Merged 1024x768 and 1024x768 to 1024x768 (Clone)
(II) RADEON(0): Merged 800x600 and 800x600 to 800x600 (Clone)
(II) RADEON(0): Merged 640x480 and 640x480 to 640x480 (Clone)
(II) RADEON(0): Merged 800x600 and 800x600 to 800x600 (Clone)
(--) RADEON(0): MergedFB: Virtual width 1024
(--) RADEON(0): MergedFB: Virtual height 768
(--) RADEON(0): MergedFB: Display dimensions: (320, 240) mm
(--) RADEON(0): MergedFB: DPI set to (81, 81)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): AGP Fast Write disabled by default
(II) RADEON(0): Depth moves disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/X11R6/lib/modules/libshadowfb.a
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) RADEON(0): Page flipping disabled
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xcfffcf00 - 0xcfffcfff (0x100) MX[B]
	[9] -1	0	0xcffdd000 - 0xcffddfff (0x1000) MX[B]
	[10] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[11] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[14] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[28] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[29] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[30] -1	0	0x00009800 - 0x000098ff (0x100) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xc0000000,0x4000000)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] loaded kernel module for "radeon" driver
(II) RADEON(0): [drm] DRM interface version 1.2
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xe0c22000
(II) RADEON(0): [drm] mapped SAREA 0xe0c22000 to 0xb3d91000
(II) RADEON(0): [drm] framebuffer handle = 0xc0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [agp] Mode 0x1f000201 [AGP 0x1039/0x0735; Card 0x1002/0x5157]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xd0000000
(II) RADEON(0): [agp] Ring mapped at 0xb3c90000
(II) RADEON(0): [agp] ring read ptr handle = 0xd0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb3c8f000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xd0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb3a8f000
(II) RADEON(0): [agp] GART texture map handle = 0xd0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb35af000
(II) RADEON(0): [drm] register handle = 0xcfef0000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,768) to (1024,770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7421
(II) RADEON(0): Will use back buffer at offset 0xc00000
(II) RADEON(0): Will use depth buffer at offset 0xf00000
(II) RADEON(0): Will use 47104 kb for textures at offset 0x1200000
(II) RADEON(0): Render acceleration enabled
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
(==) RADEON(0): Backing store disabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7417
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(II) RADEON(0): Running MergedFB in Clone mode, Radeon Pseudo-Xinerama disabled
(II) RADEON(0): X context handle = 0x00000001
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 11
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(II) RADEON(0): Direct rendering enabled
(==) RandR enabled
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
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "de"
(**) Generic Keyboard: XkbLayout: "de"
(**) Option "XkbOptions" "nodeadkeys"
(**) Generic Keyboard: XkbOptions: "nodeadkeys"
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
Could not init font path element unix/:7100, removing from list!
AUDIT: Mon Aug  8 16:01:40 2005: 7232 X: client 5 rejected from local host
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xe0c22000 at 0xb3d91000

```

---

### Post by PeP on 2005-08-08
you didn't post the result of 
% glxinfo|grep direct

-> does 3d accel work?

since it doesn't load the gl libs, you might try to reinstall linux-restricted-modules
```
sudo apt-get install --reinstall --purge linux-restricted-modules-XXXXXXXX

```
shutdown X
ctrl alt f1
```
/etc/init.d/gdm stop

```
reload fglrx:
```
rmmod fglrx
modprobe fglrx

```
restart X:
```
/etc/init.d/gdm restart
```

---

### Post by ad noiseam on 2005-08-08
[QUOTE=PeP]you didn't post the result of 
% glxinfo|grep direct
[/quote]

root@nicolas:~ # glxinfo|grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

[QUOTE=PeP]
-> does 3d accel work?
[/quote]

How do I know this? Also, I am just looking for a way to use my two monitors. 3D is not really important to me.

> 
reload fglrx:
[CODE]rmmod fglrx
modprobe fglrx


I get:
"Module fglrx does not exist in proc/modules"
event though, according to Synaptic, the following two items are installed:
xorg-driver-fglrx
fglrx-control

---

### Post by ad noiseam on 2005-08-08
[QUOTE=ad noiseam]
"Module fglrx does not exist in proc/modules"[/QUOTE]

Also,
```
lsmod|grep fglrx
```

doesn't give me anything at all...

---

### Post by PeP on 2005-08-09
[QUOTE=ad noiseam]Also,
```
lsmod|grep fglrx
```

doesn't give me anything at all...[/QUOTE]

above: 
> 
 LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 6.5.6
	Module class: X.Org Video Driver


Strange it doesn't even try to load fglrx, going directly to ati driver from xorg.

try first to reinstall it if you cannot find it:
sudo apt-get install --reinstall --purge linux-restricted-modules-2.6.10-5-386

Then check you have modified /etc/X11/xorg.conf (no uppercase in xorg.conf) and not something else.

Then check you don't have a section in it refering to "ati":

```

Section "device"
[...]
Driver "ati"

```

if there is one comment it (add a '#' character at the beginning of each line of this section).

Then serach /etc/

---

### Post by ad noiseam on 2005-08-10
Actually, I solved this. I don't think I get 3D acceleration and so on, but it works by using the "Pseudo_Xinerama" part of the Radeon driver.

Here is my Xorg.conf, it works like a charm:

```

Section "Device"
	Identifier	"myvideocard"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
 Option "MergedFB" "True"
	Option		"Clone"	"off"
 Option "MetaModes" "1152x864-1152x864"
 Option "CRT2Position" "RightOf"
EndSection

Section "Monitor"
	Identifier	"myplainmonitor"
	Option		"DPMS"
	HorizSync	28-90
	VertRefresh	43-90
EndSection

Section "Screen"
	Identifier	"mybigscreen"
	Device		"myvideocard"
	Monitor		"myplainmonitor"
	DefaultDepth	24
	SubSection "Display"
	Depth		16
        Modes        "1152x864" "1024x768"
 Virtual 2304 864
	EndSubSection
EndSection

Section "ServerLayout"

	Identifier	"Multihead"

	Screen		"mybigscreen"

	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

---

### Post by Paul Chang on 2006-04-09
Hi [COLOR="Red"]ad noiseam[/COLOR],

Could you post the FINAL and WHOLE contents of your xorg.conf file? I have a ATI AIW 7500 card, try to get TV-out work, but never succeded. Thanks!

---


---
title: "(Almost) always falling back to Failsafe Mode / The Evil Black Bar On The Left Side"
date: 2008-03-20
forum: Desktop Environments
---

### Post by liquid circuit on 2008-03-20
First off, this may be information overload.... sorry, but I figure it is better to provide context if I want help.  I've broken the post into sections to try and make it easier to understand/skip the unimportant details;  I do tech support for a living, so I understand that sometimes too much information is REALLY too much information.

**Ubuntu Version:**
Ubuntu 7.10 (Gutsy) - clean install

**Hardware (that may matter):**
[LIST]
[*]*GFX Card*: Radeon 9200 (AGP)
[*]*Monitor*:  LG 194WTX (officially 194WTX-BF, but I guess the BF part means "Black Frame") connected via VGA cable [1440x900 LCD]
[*]*Keyboard*: Logitech MX5000 (Bluetooth)
[*]*Mouse*:  Logitech MX1000 (Bluetooth)
[*]*Bluetooth Dongle*:  the one included with the Logitech MX5000 / MX1000 bundle
[/LIST]

**Disclaimers:**
[LIST]
[*]First off, I only mention the keyboard/mouse because the mouse had some issues connecting at start-up in Feisty, thus causing X to crash... doesn't SEEM to be an issue now, but what do I know? (very little)
[*]I think I must be missing the log that would actually tell me what is going wrong.
[*]Me == Linux/Ubuntu noob
[/LIST]

**Background:**
So, I had to do some hacking of my xorg.conf to get my monitor working correctly.  Allowing anything to auto-configure it results in the 1440 horizontal width to be squished to the right 5/6 of the screen (I get a black bar about 3 inches wide down the left side of my screen).  I have *some* success by hacking my xorg.conf with a modeline, and have (seemingly randomly) been able to log in successfully in native resolution, fullscreen, with Compiz running smoothly.

I've also had to hack my xorg.conf to get my mouse working via Bluetooth with all buttons (all twelve of them) functioning.

**Issue:**
Now, I have been able to get into the desktop without falling back to failsafe mode, and have had Compiz running smoothly.  Once I get in, everything is golden, and is very reliable.  I can restart X (CTRL-ALT-F1), etc. with no problems.  However, if I have to reboot/crash for whatever reason, its very unpredictable whether I will be able to get back in without the failsafe mode kicking in.

Now, I must admit I had been doing some extra hacking trying to get the Ubuntu boot screen (with the progress bar) to display... it was originally causing my monitor to display (Out Of Range) and just show a black screen (now always displaying correctly).  Also, the GDM login screen was always being displayed in a non-native resolution, and I've been trying to fix that (to no avail: usplash.conf, menu.lst defoptions with VGA code, whatever I could find).  It seems I may have made things worse.  Its not that I was ever reliably able to get into X in native resolution AND full screen, but now its even worse.  I've logged in correctly maybe twice in the past 100 reboots.  I am writing this now with a big black bar down the left-hand side of my screen, but I have 1440x900 pixels in what seems like a 4:3 aspect ratio.

I'm not really sure where to look now to figure out what is causing the problem.  PLEASE HELP? Oh pleeeeeeeeeeease help!!! =)

**xorg.conf**
```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech Bluetooth Mouse"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"L194WTX"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-75

	Option		"DDC"		"false"
	Modeline 	"1440x900_60.00" 106.47  1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200]"
	Monitor		"L194WTX"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
        InputDevice     "Logitech MX1000" "CorePointer"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

**Xorg.0.log (probably no help?)**
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux ubuntu 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 20 23:43:24 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Failsafe Monitor"
(**) |   |-->Device "Failsafe Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) Loader magic: 0x81e9800
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
(II) PCI: 00:00:0: chip 1106,0314 card 1106,0314 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1314 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2314 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3208 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4314 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7314 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 1412,1712 card 1412,d634 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1462,7222 rev 80 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1462,7222 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1462,7222 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1462,7222 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1462,7222 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1462,7222 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1462,7222 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1106,3227 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:12:0: chip 1106,3065 card 1462,7222 rev 78 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5961 card 174b,7c11 rev 01 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,5941 card 174b,7c10 rev 01 class 03,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xf7ffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV280 [Radeon 9200] rev 1, Mem @ 0xf0000000/27, 0xfdef0000/16, I/O @ 0xbc00/8
(--) PCI: (1:0:1) ATI Technologies Inc RV280 [Radeon 9200] (Secondary) rev 1, Mem @ 0xe8000000/27, 0xfdee0000/16
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xdfffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfdffe000 - 0xfdffe0ff (0x100) MX[B]
	[1] -1	0	0xfdfff000 - 0xfdfff0ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[3] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[4] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[6] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[7] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[8] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[9] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[18] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[19] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfdee0000 - 0xfdeeffff (0x10000) MX[B](B)
	[1] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdffe000 - 0xfdffe0ff (0x100) MX[B]
	[1] -1	0	0xfdfff000 - 0xfdfff0ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[3] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[4] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[6] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[7] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[8] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[9] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[18] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[19] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdee0000 - 0xfdeeffff (0x10000) MX[B](B)
	[1] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
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
	[4] -1	0	0xfdffe000 - 0xfdffe0ff (0x100) MX[B]
	[5] -1	0	0xfdfff000 - 0xfdfff0ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfdee0000 - 0xfdeeffff (0x10000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[16] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[26] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[27] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
(WW) "dbe" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "vbe" will not be loaded unless you've specified it to be loaded elsewhere.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
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
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
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
(II) v4l driver for Video4Linux
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 01:00:0
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
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
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon 9200 5961 (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdffe000 - 0xfdffe0ff (0x100) MX[B]
	[5] -1	0	0xfdfff000 - 0xfdfff0ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfdee0000 - 0xfdeeffff (0x10000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[16] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[26] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[27] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdffe000 - 0xfdffe0ff (0x100) MX[B]
	[5] -1	0	0xfdfff000 - 0xfdfff0ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfdee0000 - 0xfdeeffff (0x10000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[28] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[29] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[30] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[32] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xfdef0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9200 5961 (AGP)" (ChipID = 0x5961)
(--) RADEON(0): Linear framebuffer at 0xf0000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 1920x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=18300
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-3, DACType-0, TMDSType-0, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0, DACType-1, TMDSType-2, ConnectorType-6
(II) RADEON(0): Output VGA-0 using monitor section Failsafe Monitor
(II) RADEON(0): I2C bus "VGA_DDC" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- VGA_DDC
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- None
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: GSM  Model: 4b1e  Serial#: 166593
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.643 redY: 0.325   greenX: 0.295 greenY: 0.616
(II) RADEON(0): blueX: 0.143 blueY: 0.081   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: L194WTX
(II) RADEON(0): Monitor name: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d1e4bc18a0200
(II) RADEON(0): 	031101036a291a78ea9bb6a4534b9d24
(II) RADEON(0): 	144f54a76f80950f81808140714f0101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384b1c
(II) RADEON(0): 	530e000a202020202020000000fc004c
(II) RADEON(0): 	3139345754580a2020202020000000fc
(II) RADEON(0): 	000a20202020202020202020202000b4
finished output detect: 0
finished output detect: 1
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: GSM  Model: 4b1e  Serial#: 166593
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.643 redY: 0.325   greenX: 0.295 greenY: 0.616
(II) RADEON(0): blueX: 0.143 blueY: 0.081   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: L194WTX
(II) RADEON(0): Monitor name: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d1e4bc18a0200
(II) RADEON(0): 	031101036a291a78ea9bb6a4534b9d24
(II) RADEON(0): 	144f54a76f80950f81808140714f0101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384b1c
(II) RADEON(0): 	530e000a202020202020000000fc004c
(II) RADEON(0): 	3139345754580a2020202020000000fc
(II) RADEON(0): 	000a20202020202020202020202000b4
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: GSM  Model: 4b1e  Serial#: 166593
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.643 redY: 0.325   greenX: 0.295 greenY: 0.616
(II) RADEON(0): blueX: 0.143 blueY: 0.081   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: L194WTX
(II) RADEON(0): Monitor name: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d1e4bc18a0200
(II) RADEON(0): 	031101036a291a78ea9bb6a4534b9d24
(II) RADEON(0): 	144f54a76f80950f81808140714f0101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384b1c
(II) RADEON(0): 	530e000a202020202020000000fc004c
(II) RADEON(0): 	3139345754580a2020202020000000fc
(II) RADEON(0): 	000a20202020202020202020202000b4
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) RADEON(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) RADEON(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) RADEON(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) RADEON(0): EDID vendor "GSM", prod id 19230
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
(II) RADEON(0): Modeline "1920x1200@60"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1680x1050@75"x75.0  188.07  1680 1800 1984 2288  1050 1051 1054 1096 -hsync +vsync (82.2 kHz)
(II) RADEON(0): Modeline "1680x1050@60"x60.0  147.14  1680 1784 1968 2256  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) RADEON(0): Modeline "1600x1024@60"x60.0  136.36  1600 1704 1872 2144  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900@75"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) RADEON(0): Modeline "1440x900@60"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1280x800@75"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 -hsync +vsync (62.6 kHz)
(II) RADEON(0): Modeline "1280x800@60"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 -hsync +vsync (49.7 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x768@75"x75.0  102.98  1280 1360 1496 1712  768 769 772 802 -hsync +vsync (60.2 kHz)
(II) RADEON(0): Modeline "1280x768@60"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1280x720@60"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600@72"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600@75"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600@60"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600@56"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1440x900
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (410, 260) mm
(**) RADEON(0): DPI set to (118, 117)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(**) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfdffe000 - 0xfdffe0ff (0x100) MX[B]
	[7] -1	0	0xfdfff000 - 0xfdfff0ff (0x100) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xfdee0000 - 0xfdeeffff (0x10000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[16] 0	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[32] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[33] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[34] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[35] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xf0000000,0x8000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xf7fff000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1920,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1920,1202)
(II) RADEON(0): Largest offscreen area available: 1920 x 6989
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xf7fff000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
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
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1202)
(II) RADEON(0): Largest offscreen area available: 1920 x 6986
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "MergedFB" is not used
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
(EE) AIGLX: DRI module not loaded
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 408 x 255
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
enable montype: 1
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: GSM  Model: 4b1e  Serial#: 166593
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.643 redY: 0.325   greenX: 0.295 greenY: 0.616
(II) RADEON(0): blueX: 0.143 blueY: 0.081   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: L194WTX
(II) RADEON(0): Monitor name: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d1e4bc18a0200
(II) RADEON(0): 	031101036a291a78ea9bb6a4534b9d24
(II) RADEON(0): 	144f54a76f80950f81808140714f0101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384b1c
(II) RADEON(0): 	530e000a202020202020000000fc004c
(II) RADEON(0): 	3139345754580a2020202020000000fc
(II) RADEON(0): 	000a20202020202020202020202000b4
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: GSM  Model: 4b1e  Serial#: 166593
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.643 redY: 0.325   greenX: 0.295 greenY: 0.616
(II) RADEON(0): blueX: 0.143 blueY: 0.081   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: L194WTX
(II) RADEON(0): Monitor name: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d1e4bc18a0200
(II) RADEON(0): 	031101036a291a78ea9bb6a4534b9d24
(II) RADEON(0): 	144f54a76f80950f81808140714f0101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384b1c
(II) RADEON(0): 	530e000a202020202020000000fc004c
(II) RADEON(0): 	3139345754580a2020202020000000fc
(II) RADEON(0): 	000a20202020202020202020202000b4
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) RADEON(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) RADEON(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) RADEON(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) RADEON(0): EDID vendor "GSM", prod id 19230
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
(II) RADEON(0): Modeline "1920x1200@60"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1680x1050@75"x75.0  188.07  1680 1800 1984 2288  1050 1051 1054 1096 -hsync +vsync (82.2 kHz)
(II) RADEON(0): Modeline "1680x1050@60"x60.0  147.14  1680 1784 1968 2256  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) RADEON(0): Modeline "1600x1024@60"x60.0  136.36  1600 1704 1872 2144  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900@75"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) RADEON(0): Modeline "1440x900@60"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1280x800@75"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 -hsync +vsync (62.6 kHz)
(II) RADEON(0): Modeline "1280x800@60"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 -hsync +vsync (49.7 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x768@75"x75.0  102.98  1280 1360 1496 1712  768 769 772 802 -hsync +vsync (60.2 kHz)
(II) RADEON(0): Modeline "1280x768@60"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1280x720@60"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600@72"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600@75"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600@60"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600@56"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: GSM  Model: 4b1e  Serial#: 166593
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.643 redY: 0.325   greenX: 0.295 greenY: 0.616
(II) RADEON(0): blueX: 0.143 blueY: 0.081   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: L194WTX
(II) RADEON(0): Monitor name: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d1e4bc18a0200
(II) RADEON(0): 	031101036a291a78ea9bb6a4534b9d24
(II) RADEON(0): 	144f54a76f80950f81808140714f0101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384b1c
(II) RADEON(0): 	530e000a202020202020000000fc004c
(II) RADEON(0): 	3139345754580a2020202020000000fc
(II) RADEON(0): 	000a20202020202020202020202000b4
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: GSM  Model: 4b1e  Serial#: 166593
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.643 redY: 0.325   greenX: 0.295 greenY: 0.616
(II) RADEON(0): blueX: 0.143 blueY: 0.081   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: L194WTX
(II) RADEON(0): Monitor name: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d1e4bc18a0200
(II) RADEON(0): 	031101036a291a78ea9bb6a4534b9d24
(II) RADEON(0): 	144f54a76f80950f81808140714f0101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384b1c
(II) RADEON(0): 	530e000a202020202020000000fc004c
(II) RADEON(0): 	3139345754580a2020202020000000fc
(II) RADEON(0): 	000a20202020202020202020202000b4
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) RADEON(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) RADEON(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) RADEON(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) RADEON(0): EDID vendor "GSM", prod id 19230
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
(II) RADEON(0): Modeline "1920x1200@60"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Modeline "1680x1050@75"x75.0  188.07  1680 1800 1984 2288  1050 1051 1054 1096 -hsync +vsync (82.2 kHz)
(II) RADEON(0): Modeline "1680x1050@60"x60.0  147.14  1680 1784 1968 2256  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) RADEON(0): Modeline "1600x1024@60"x60.0  136.36  1600 1704 1872 2144  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900@75"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) RADEON(0): Modeline "1440x900@60"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1280x800@75"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 -hsync +vsync (62.6 kHz)
(II) RADEON(0): Modeline "1280x800@60"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 -hsync +vsync (49.7 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x768@75"x75.0  102.98  1280 1360 1496 1712  768 769 772 802 -hsync +vsync (60.2 kHz)
(II) RADEON(0): Modeline "1280x768@60"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1280x720@60"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600@72"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600@75"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600@60"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600@56"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
```

**dmesg**
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f38c0
[    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524016
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524016
[    0.000000] On node 0 totalpages: 524016
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7820 checksum 0
[    0.000000] ACPI: RSDP 000F7820, 0014 (r0 P4M80P)
[    0.000000] ACPI: RSDT 7FEF3040, 002C (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEF3180, 5161 (r1 P4M80P AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FEF0000, 0040
[    0.000000] ACPI: APIC 7FEF8340, 0084 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:7ed00000)
[    0.000000] Built 1 zonelists.  Total pages: 519923
[    0.000000] Kernel command line: root=UUID=9aa0334d-4837-4b4e-a7da-d5d873931d1f ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3000.402 MHz processor.
[   21.580655] Console: colour VGA+ 80x25
[   21.581331] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.581890] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.678537] Memory: 2066592k/2096064k available (2015k kernel code, 28188k reserved, 915k data, 364k init, 1178560k highmem)
[   21.678547] virtual kernel memory layout:
[   21.678548]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   21.678549]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.678550]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   21.678551]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   21.678552]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   21.678554]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   21.678555]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   21.678558] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.678611] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   21.758573] Calibrating delay using timer specific routine.. 6007.66 BogoMIPS (lpj=12015325)
[   21.758611] Security Framework v1.0.0 initialized
[   21.758619] SELinux:  Disabled at boot.
[   21.758635] Mount-cache hash table entries: 512
[   21.758806] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000001
[   21.758815] monitor/mwait feature present.
[   21.758817] using mwait in idle threads.
[   21.758825] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   21.758828] CPU: L2 cache: 1024K
[   21.758830] CPU: Physical Processor ID: 0
[   21.758833] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000641d 00000000 00000001
[   21.758846] Compat vDSO mapped to ffffe000.
[   21.758865] Checking 'hlt' instruction... OK.
[   21.774714] SMP alternatives: switching to UP code
[   21.775345] Early unpacking initramfs... done
[   22.058585] ACPI: Core revision 20070126
[   22.058645] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.066140] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   22.066161] SMP alternatives: switching to SMP code
[   22.066259] Booting processor 1/1 eip 3000
[   22.076376] Initializing CPU#1
[   22.154206] Calibrating delay using timer specific routine.. 6000.51 BogoMIPS (lpj=12001038)
[   22.154216] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000001
[   22.154224] monitor/mwait feature present.
[   22.154231] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   22.154234] CPU: L2 cache: 1024K
[   22.154236] CPU: Physical Processor ID: 0
[   22.154239] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000641d 00000000 00000001
[   22.154615] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   22.154660] Total of 2 processors activated (12008.18 BogoMIPS).
[   22.155419] ENABLING IO-APIC IRQs
[   22.155740] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   22.302185] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   22.322184] Brought up 2 CPUs
[   22.480152] migration_cost=99
[   22.480333] Booting paravirtualized kernel on bare hardware
[   22.480427] Time: 23:40:21  Date: 02/20/108
[   22.480453] NET: Registered protocol family 16
[   22.480548] EISA bus registered
[   22.480553] ACPI: bus type pci registered
[   22.488518] PCI: PCI BIOS revision 2.10 entry at 0xf9f20, last bus=1
[   22.488521] PCI: Using configuration type 1
[   22.488523] Setting up standard PCI resources
[   22.496285] ACPI: EC: Look up EC in DSDT
[   22.502645] ACPI: Interpreter enabled
[   22.502651] ACPI: (supports S0 S1 S4 S5)
[   22.502674] ACPI: Using IOAPIC for interrupt routing
[   22.509554] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.509577] PCI: Probing PCI hardware (bus 00)
[   22.510786] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.552506] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   22.552689] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   22.552872] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[   22.553035] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   22.553194] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   22.553348] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   22.553502] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   22.553656] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   22.553846] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[   22.554030] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[   22.554203] ACPI: PCI Interrupt Link [ALKC] (IRQs *22), disabled.
[   22.554403] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[   22.554508] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.554520] pnp: PnP ACPI init
[   22.554533] ACPI: bus type pnp registered
[   22.557923] pnp: PnP ACPI: found 9 devices
[   22.557926] ACPI: ACPI bus type pnp unregistered
[   22.557932] PnPBIOS: Disabled by ACPI PNP
[   22.557998] PCI: Using ACPI for IRQ routing
[   22.558001] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.569054] NET: Registered protocol family 8
[   22.569057] NET: Registered protocol family 20
[   22.569130] pnp: 00:00: iomem range 0xcc000-0xcffff has been reserved
[   22.569133] pnp: 00:00: iomem range 0xd6000-0xd7fff has been reserved
[   22.569136] pnp: 00:00: iomem range 0xf0000-0xfbfff could not be reserved
[   22.569140] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   22.569146] pnp: 00:02: ioport range 0x400-0x47f has been reserved
[   22.569149] pnp: 00:02: ioport range 0x500-0x50f has been reserved
[   22.569854] Time: tsc clocksource has been installed.
[   22.599501] PCI: Bridge: 0000:00:01.0
[   22.599505]   IO window: b000-bfff
[   22.599511]   MEM window: fde00000-fdefffff
[   22.599516]   PREFETCH window: e8000000-f7ffffff
[   22.599536] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   22.599548] NET: Registered protocol family 2
[   22.638087] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.638231] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   22.639559] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   22.639929] TCP: Hash tables configured (established 131072 bind 65536)
[   22.639932] TCP reno registered
[   22.650287] checking if image is initramfs... it is
[   23.101571] Switched to high resolution mode on CPU 0
[   23.101659] Switched to high resolution mode on CPU 1
[   23.213644] Freeing initrd memory: 7067k freed
[   23.214279] audit: initializing netlink socket (disabled)
[   23.214297] audit(1206056421.272:1): initialized
[   23.214409] highmem bounce pool size: 64 pages
[   23.216765] VFS: Disk quotas dquot_6.5.1
[   23.216830] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.216934] io scheduler noop registered
[   23.216936] io scheduler anticipatory registered
[   23.216938] io scheduler deadline registered
[   23.216954] io scheduler cfq registered (default)
[   23.216977] PCI: VIA PCI bridge detected. Disabling DAC.
[   31.206066] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   31.206085] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   31.206093] Boot video device is 0000:01:00.0
[   31.206275] isapnp: Scanning for PnP cards...
[   31.557634] isapnp: No Plug & Play device found
[   31.584728] Real Time Clock Driver v1.12ac
[   31.584829] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.586104] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.586352] input: Macintosh mouse button emulation as /class/input/input0
[   31.586491] PNP: No PS/2 controller found. Probing ports directly.
[   31.586978] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.586986] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.587152] mice: PS/2 mouse device common for all mice
[   31.587277] EISA: Probing bus 0 at eisa.0
[   31.587320] EISA: Detected 0 cards.
[   31.587512] TCP cubic registered
[   31.587528] NET: Registered protocol family 1
[   31.587552] Using IPI No-Shortcut mode
[   31.587720]   Magic number: 0:59:707
[   31.588308] Freeing unused kernel memory: 364k freed
[   32.800338] AppArmor: AppArmor initialized<5>audit(1206056430.772:2):  type=1505 info="AppArmor initialized" pid=1194
[   32.807301] fuse init (API version 7.8)
[   32.812487] Failure registering capabilities with primary security module.
[   32.840512] ACPI: Fan [FAN] (on)
[   32.845413] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   32.845428] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   32.846922] ACPI: Thermal Zone [THRM] (55 C)
[   33.401979] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.401986] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.402833] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   33.403178] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   33.403187] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   33.403203] VP_IDE: chipset revision 6
[   33.403206] VP_IDE: not 100% native mode: will probe irqs later
[   33.403222] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   33.403231]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb:DMA
[   33.403245]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:DMA
[   33.403255] Probing IDE interface ide0...
[   33.429546] usbcore: registered new interface driver usbfs
[   33.429581] usbcore: registered new interface driver hub
[   33.429615] usbcore: registered new device driver usb
[   33.430869] USB Universal Host Controller Interface driver v3.0
[   33.455862] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   33.528523] SCSI subsystem initialized
[   33.588104] libata version 2.21 loaded.
[   33.615753] FDC 0 is a post-1991 82077
[   33.847806] hda: WDC WD200BB-75AUA1, ATA DISK drive
[   34.127556] hdb: WDC WD400EB-00CPF0, ATA DISK drive
[   34.186803] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   34.229079] Probing IDE interface ide1...
[   34.754974] hdc: HL-DT-STDVD-RAM GSA-H55N, ATAPI CD/DVD-ROM drive
[   35.034722] hdd: WDC WD153BA, ATA DISK drive
[   35.092382] ide1 at 0x170-0x177,0x376 on irq 15
[   35.111504] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   35.111513] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   35.111526] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   35.111814] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   35.111847] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000d000
[   35.112218] usb usb1: configuration #1 chosen from 1 choice
[   35.112361] hub 1-0:1.0: USB hub found
[   35.112370] hub 1-0:1.0: 2 ports detected
[   35.214598] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   35.214614] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   35.214649] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   35.214675] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000cc00
[   35.214822] usb usb2: configuration #1 chosen from 1 choice
[   35.214863] hub 2-0:1.0: USB hub found
[   35.214872] hub 2-0:1.0: 2 ports detected
[   35.318482] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   35.318498] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   35.318536] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   35.318562] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000c800
[   35.318703] usb usb3: configuration #1 chosen from 1 choice
[   35.318745] hub 3-0:1.0: USB hub found
[   35.318754] hub 3-0:1.0: 2 ports detected
[   35.422391] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   35.422406] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   35.422445] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   35.422471] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000c400
[   35.422609] usb usb4: configuration #1 chosen from 1 choice
[   35.422651] hub 4-0:1.0: USB hub found
[   35.422661] hub 4-0:1.0: 2 ports detected
[   35.526788] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[   35.526800] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 18
[   35.526929] eth0: VIA Rhine II at 0x1c000, 00:16:17:9d:7d:a2, IRQ 18.
[   35.527652] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[   35.530989] sata_via 0000:00:0f.0: version 2.2
[   35.531020] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   35.531073] sata_via 0000:00:0f.0: routed to hard irq line 11
[   35.531184] scsi0 : sata_via
[   35.531260] scsi1 : sata_via
[   35.531314] ata1: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e802 bmdma 0x0001dc00 irq 16
[   35.531322] ata2: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e002 bmdma 0x0001dc08 irq 16
[   35.559837] hda: max request size: 128KiB
[   35.568473] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[   35.568483] hda: cache flushes not supported
[   35.568542]  hda: hda1 hda2 hda3
[   35.608034] hdb: max request size: 128KiB
[   35.609105] hdb: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   35.609113] hdb: cache flushes not supported
[   35.609148]  hdb: hdb1
[   35.619961] hdd: max request size: 128KiB
[   35.620746] hdd: 30043440 sectors (15382 MB) w/2048KiB Cache, CHS=29805/16/63, UDMA(33)
[   35.620752] hdd: cache flushes not supported
[   35.620780]  hdd: hdd1
[   35.646073] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   35.646088] Uniform CD-ROM driver Revision: 3.20
[   35.710068] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   35.733997] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   35.890178] usb 2-1: configuration #1 chosen from 1 choice
[   35.893113] hub 2-1:1.0: USB hub found
[   35.896057] hub 2-1:1.0: 3 ports detected
[   35.945810] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   35.956309] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   35.956328] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   35.956379] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   35.956426] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfdfff000
[   35.956436] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   35.956567] usb usb5: configuration #1 chosen from 1 choice
[   35.956610] hub 5-0:1.0: USB hub found
[   35.956622] hub 5-0:1.0: 8 ports detected
[   35.979371] Attempting manual resume
[   35.979376] swsusp: Resume From Partition 3:2
[   35.979378] PM: Checking swsusp image.
[   35.979517] PM: Resume from disk failed.
[   36.000394] kjournald starting.  Commit interval 5 seconds
[   36.000408] EXT3-fs: mounted filesystem with ordered data mode.
[   36.641215] usb 2-1: USB disconnect, address 2
[   37.324578] usb 2-1: new full speed USB device using uhci_hcd and address 3
[   37.509571] usb 2-1: configuration #1 chosen from 1 choice
[   37.512504] hub 2-1:1.0: USB hub found
[   37.515474] hub 2-1:1.0: 3 ports detected
[   37.829170] usb 2-1.2: new full speed USB device using uhci_hcd and address 4
[   37.983112] usb 2-1.2: configuration #1 chosen from 1 choice
[   38.192814] usb 2-1.3: new full speed USB device using uhci_hcd and address 5
[   38.346736] usb 2-1.3: configuration #1 chosen from 1 choice
[   44.504217] Linux agpgart interface v0.102 (c) Dave Jones
[   44.515195] agpgart: Detected VIA VT3314 chipset
[   44.534651] agpgart: AGP aperture is 256M @ 0xd0000000
[   44.909735] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.163953] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.361385] input: PC Speaker as /class/input/input1
[   45.630871] usbcore: registered new interface driver hiddev
[   45.637978] input: Logitech Logitech BT Mini-Receiver as /class/input/input2
[   45.638226] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:10.1-1.2
[   45.646641] input: Logitech Logitech BT Mini-Receiver as /class/input/input3
[   45.646763] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:10.1-1.3
[   45.646786] usbcore: registered new interface driver usbhid
[   45.646791] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   46.034845] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 18 (level, low) -> IRQ 19
[   46.994311] lp: driver loaded but no devices found
[   47.066195] Bluetooth: Core ver 2.11
[   47.066263] NET: Registered protocol family 31
[   47.066266] Bluetooth: HCI device and connection manager initialized
[   47.066271] Bluetooth: HCI socket layer initialized
[   47.069820] Bluetooth: L2CAP ver 2.8
[   47.069824] Bluetooth: L2CAP socket layer initialized
[   47.079369] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   47.129197] Adding 498004k swap on /dev/hda2.  Priority:-1 extents:1 across:498004k
[   47.574723] EXT3 FS on hda3, internal journal
[   49.171004] input: Power Button (FF) as /class/input/input4
[   49.171031] ACPI: Power Button (FF) [PWRF]
[   49.171099] input: Power Button (CM) as /class/input/input5
[   49.171124] ACPI: Power Button (CM) [PWRB]
[   49.171173] input: Sleep Button (CM) as /class/input/input6
[   49.171203] ACPI: Sleep Button (CM) [SLPB]
[   49.271783] No dock devices found.
[   50.649876] ppdev: user-space parallel port driver
[   50.849517] audit(1206067249.696:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4844 profile="/usr/sbin/cupsd"
[   50.925491] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   50.954249] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   50.954256] apm: disabled - APM is not SMP safe.
[   51.446781] Failure registering capabilities with primary security module.
[   51.776267] Bluetooth: RFCOMM socket layer initialized
[   51.776451] Bluetooth: RFCOMM TTY layer initialized
[   51.776456] Bluetooth: RFCOMM ver 1.8
[   51.883614] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   51.883646]  [<f89d8628>] hid_output_report+0x2a8/0x320 [hid]
[   51.883727]  [<f89e14a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   51.883776]  [<f89e176b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   51.883812]  [<f89e3ea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   51.883841]  [<c01610f1>] filemap_nopage+0x181/0x340
[   51.883855]  [<f88c36ff>] usb_open+0x8f/0xf0 [usbcore]
[   51.883901]  [<c011fc6e>] kunmap_atomic+0x5e/0xa0
[   51.883907]  [<c011fc7a>] kunmap_atomic+0x6a/0xa0
[   51.883926]  [<c016ce38>] __handle_mm_fault+0x288/0xb00
[   51.883990]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.884011]  [<c018caf4>] do_ioctl+0x84/0xc0
[   51.884021]  [<c02f5ef9>] do_page_fault+0x389/0x690
[   51.884035]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.884057]  [<c018cb8c>] vfs_ioctl+0x5c/0x290
[   51.884106]  [<c018ce32>] sys_ioctl+0x72/0x90
[   51.884152]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   51.884185]  [<c02f0000>] clip_ioctl+0x3a0/0x510
[   51.884239]  =======================
[   51.884244] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   51.884256]  [<f89d8628>] hid_output_report+0x2a8/0x320 [hid]
[   51.884330]  [<f89e14a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   51.884376]  [<f89e176b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   51.884411]  [<f89e3ea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   51.884439]  [<c01610f1>] filemap_nopage+0x181/0x340
[   51.884449]  [<f88c36ff>] usb_open+0x8f/0xf0 [usbcore]
[   51.884492]  [<c011fc6e>] kunmap_atomic+0x5e/0xa0
[   51.884500]  [<c011fc7a>] kunmap_atomic+0x6a/0xa0
[   51.884518]  [<c016ce38>] __handle_mm_fault+0x288/0xb00
[   51.884581]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.884600]  [<c018caf4>] do_ioctl+0x84/0xc0
[   51.884610]  [<c02f5ef9>] do_page_fault+0x389/0x690
[   51.884621]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.884641]  [<c018cb8c>] vfs_ioctl+0x5c/0x290
[   51.884665]  [<c018ce32>] sys_ioctl+0x72/0x90
[   51.884686]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   51.884719]  [<c02f0000>] clip_ioctl+0x3a0/0x510
[   51.884748]  =======================
[   51.884752] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   51.884763]  [<f89d8628>] hid_output_report+0x2a8/0x320 [hid]
[   51.884837]  [<f89e14a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   51.884883]  [<f89e176b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   51.884942]  [<f89e3ea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   51.884994]  [<c01610f1>] filemap_nopage+0x181/0x340
[   51.885003]  [<f88c36ff>] usb_open+0x8f/0xf0 [usbcore]
[   51.885044]  [<c011fc6e>] kunmap_atomic+0x5e/0xa0
[   51.885050]  [<c011fc7a>] kunmap_atomic+0x6a/0xa0
[   51.885068]  [<c016ce38>] __handle_mm_fault+0x288/0xb00
[   51.885131]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.885150]  [<c018caf4>] do_ioctl+0x84/0xc0
[   51.885159]  [<c02f5ef9>] do_page_fault+0x389/0x690
[   51.885170]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.885192]  [<c018cb8c>] vfs_ioctl+0x5c/0x290
[   51.885216]  [<c018ce32>] sys_ioctl+0x72/0x90
[   51.885237]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   51.885269]  [<c02f0000>] clip_ioctl+0x3a0/0x510
[   51.885323]  =======================
[   51.886428] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   51.886439]  [<f89d8628>] hid_output_report+0x2a8/0x320 [hid]
[   51.886515]  [<f89e14a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   51.886526]  [<c0131470>] process_timeout+0x0/0x10
[   51.886564]  [<c02f2eb7>] schedule_timeout+0x47/0xd0
[   51.886580]  [<c013bead>] finish_wait+0x2d/0x70
[   51.886600]  [<f89e176b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   51.886613]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[   51.886639]  [<f89e3ea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   51.886667]  [<c01610f1>] filemap_nopage+0x181/0x340
[   51.886676]  [<f88c36ff>] usb_open+0x8f/0xf0 [usbcore]
[   51.886718]  [<c011fc6e>] kunmap_atomic+0x5e/0xa0
[   51.886725]  [<c011fc7a>] kunmap_atomic+0x6a/0xa0
[   51.886742]  [<c016ce38>] __handle_mm_fault+0x288/0xb00
[   51.886829]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.886849]  [<c018caf4>] do_ioctl+0x84/0xc0
[   51.886858]  [<c02f5ef9>] do_page_fault+0x389/0x690
[   51.886869]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.886891]  [<c018cb8c>] vfs_ioctl+0x5c/0x290
[   51.886915]  [<c018ce32>] sys_ioctl+0x72/0x90
[   51.886935]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   51.886967]  [<c02f0000>] clip_ioctl+0x3a0/0x510
[   51.886996]  =======================
[   51.887000] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   51.887011]  [<f89d8628>] hid_output_report+0x2a8/0x320 [hid]
[   51.887086]  [<f89e14a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   51.887096]  [<c0131470>] process_timeout+0x0/0x10
[   51.887108]  [<c02f2eb7>] schedule_timeout+0x47/0xd0
[   51.887123]  [<c013bead>] finish_wait+0x2d/0x70
[   51.887142]  [<f89e176b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   51.887155]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[   51.887180]  [<f89e3ea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   51.887207]  [<c01610f1>] filemap_nopage+0x181/0x340
[   51.887217]  [<f88c36ff>] usb_open+0x8f/0xf0 [usbcore]
[   51.887258]  [<c011fc6e>] kunmap_atomic+0x5e/0xa0
[   51.887265]  [<c011fc7a>] kunmap_atomic+0x6a/0xa0
[   51.887284]  [<c016ce38>] __handle_mm_fault+0x288/0xb00
[   51.887347]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.887366]  [<c018caf4>] do_ioctl+0x84/0xc0
[   51.887376]  [<c02f5ef9>] do_page_fault+0x389/0x690
[   51.887387]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.887409]  [<c018cb8c>] vfs_ioctl+0x5c/0x290
[   51.887432]  [<c018ce32>] sys_ioctl+0x72/0x90
[   51.887452]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   51.887485]  [<c02f0000>] clip_ioctl+0x3a0/0x510
[   51.887515]  =======================
[   51.888424] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   51.888436]  [<f89d8628>] hid_output_report+0x2a8/0x320 [hid]
[   51.888512]  [<f89e14a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   51.888522]  [<c0131470>] process_timeout+0x0/0x10
[   51.888535]  [<c02f2eb7>] schedule_timeout+0x47/0xd0
[   51.888551]  [<c013bead>] finish_wait+0x2d/0x70
[   51.888570]  [<f89e176b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   51.888583]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[   51.888633]  [<f89e3ea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   51.888660]  [<c01610f1>] filemap_nopage+0x181/0x340
[   51.888670]  [<f88c36ff>] usb_open+0x8f/0xf0 [usbcore]
[   51.888736]  [<c011fc6e>] kunmap_atomic+0x5e/0xa0
[   51.888743]  [<c011fc7a>] kunmap_atomic+0x6a/0xa0
[   51.888761]  [<c016ce38>] __handle_mm_fault+0x288/0xb00
[   51.888825]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.888844]  [<c018caf4>] do_ioctl+0x84/0xc0
[   51.888854]  [<c02f5ef9>] do_page_fault+0x389/0x690
[   51.888865]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.888886]  [<c018cb8c>] vfs_ioctl+0x5c/0x290
[   51.888909]  [<c018ce32>] sys_ioctl+0x72/0x90
[   51.888929]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   51.888962]  [<c02f0000>] clip_ioctl+0x3a0/0x510
[   51.888991]  =======================
[   51.888995] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   51.889005]  [<f89d8628>] hid_output_report+0x2a8/0x320 [hid]
[   51.889079]  [<f89e14a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   51.889088]  [<c0131470>] process_timeout+0x0/0x10
[   51.889100]  [<c02f2eb7>] schedule_timeout+0x47/0xd0
[   51.889115]  [<c013bead>] finish_wait+0x2d/0x70
[   51.889135]  [<f89e176b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   51.889148]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[   51.889198]  [<f89e3ea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   51.889251]  [<c01610f1>] filemap_nopage+0x181/0x340
[   51.889261]  [<f88c36ff>] usb_open+0x8f/0xf0 [usbcore]
[   51.889302]  [<c011fc6e>] kunmap_atomic+0x5e/0xa0
[   51.889309]  [<c011fc7a>] kunmap_atomic+0x6a/0xa0
[   51.889351]  [<c016ce38>] __handle_mm_fault+0x288/0xb00
[   51.889414]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.889432]  [<c018caf4>] do_ioctl+0x84/0xc0
[   51.889466]  [<c02f5ef9>] do_page_fault+0x389/0x690
[   51.889477]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.889499]  [<c018cb8c>] vfs_ioctl+0x5c/0x290
[   51.889523]  [<c018ce32>] sys_ioctl+0x72/0x90
[   51.889544]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   51.889577]  [<c02f0000>] clip_ioctl+0x3a0/0x510
[   51.889606]  =======================
[   51.889611] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   51.889621]  [<f89d8628>] hid_output_report+0x2a8/0x320 [hid]
[   51.889696]  [<f89e14a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   51.889706]  [<c0131470>] process_timeout+0x0/0x10
[   51.889718]  [<c02f2eb7>] schedule_timeout+0x47/0xd0
[   51.889758]  [<c013bead>] finish_wait+0x2d/0x70
[   51.889778]  [<f89e176b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   51.889790]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[   51.889816]  [<f89e3ea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   51.889868]  [<c01610f1>] filemap_nopage+0x181/0x340
[   51.889877]  [<f88c36ff>] usb_open+0x8f/0xf0 [usbcore]
[   51.889919]  [<c011fc6e>] kunmap_atomic+0x5e/0xa0
[   51.889925]  [<c011fc7a>] kunmap_atomic+0x6a/0xa0
[   51.889943]  [<c016ce38>] __handle_mm_fault+0x288/0xb00
[   51.890006]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.890026]  [<c018caf4>] do_ioctl+0x84/0xc0
[   51.890035]  [<c02f5ef9>] do_page_fault+0x389/0x690
[   51.890045]  [<f89e3a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   51.890067]  [<c018cb8c>] vfs_ioctl+0x5c/0x290
[   51.890091]  [<c018ce32>] sys_ioctl+0x72/0x90
[   51.890136]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   51.890193]  [<c02f0000>] clip_ioctl+0x3a0/0x510
[   51.890222]  =======================
[   52.105221] usb 2-1.1: new full speed USB device using uhci_hcd and address 6
[   52.241210] usb 2-1.1: configuration #1 chosen from 1 choice
[   52.340487] Bluetooth: HCI USB driver ver 2.9
[   52.346298] usbcore: registered new interface driver hci_usb
[   53.817936] [drm] Initialized drm 1.1.0 20060810
[   53.829574] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   53.830110] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   55.220056] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   55.220083] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   55.220168] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   55.576461] [drm] Setting GART location based on new memory map
[   55.576473] [drm] Loading R200 Microcode
[   55.576518] [drm] writeback test succeeded in 1 usecs
[   56.195659] NET: Registered protocol family 17
[   63.358463] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   63.358490] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   63.358575] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   63.711582] [drm] Setting GART location based on new memory map
[   63.711593] [drm] Loading R200 Microcode
[   63.711638] [drm] writeback test succeeded in 1 usecs
[   69.091083] NET: Registered protocol family 10
[   69.091587] lo: Disabled Privacy Extensions
[   71.017674] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   71.017702] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   71.017788] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   71.371177] [drm] Setting GART location based on new memory map
[   71.371188] [drm] Loading R200 Microcode
[   71.371233] [drm] writeback test succeeded in 1 usecs
[   79.911155] eth0: no IPv6 routers present
[   83.458629] input: Logitech MX1000 mouse as /class/input/input7
[  117.932847] input: Logitech MX5000 Keyboard as /class/input/input8
```

---

### Post by liquid circuit on 2008-03-23
**Update:**

I figured out what was going on.  First off, /var/log/Xorg.0.log is useless currently because it gets overwritten by the Failsafe mode, so you can't determine why X wouldn't run in the first place.  I managed to stop X from trying to load (I think I ran /etc/init.d/gdm restart from the console to start it, and then I ran /etc/init.d/gdm stop after the screen blinked the first time), and then I read through /var/log/Xorg.0.log or /var/log/Xorg.0.log.old to find the error.  Turns out that the issue was my mouse not initializing correctly... I had the same issue on Feisty, although there wasn't this issue with the Xorg.0.log getting overwritten, so it was easier to narrow down.

Anyways, I now know how to get around the issue; either set my mouse to SendCoreEvents rather than CorePointer, OR just move my mouse around during the entire boot process so it doesn't go into power-saving mode.  The SendCoreEvents option has its own drawbacks for some reason; my mouse is only being detected as having 9 buttons, but it should be detected with 20 buttons... and also after my computer idled all night, I came back to it and my mouse/keyboard weren't responding.  I had to reseat my Bluetooth dongle to get it to switch to USB emulation mode for anything to work...

I guess I'll just deal with wobbling my mouse around during reboots and stick with CorePointer.

---


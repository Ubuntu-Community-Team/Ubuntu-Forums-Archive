---
title: "Can't quite get xorg.conf right"
date: 2009-02-23
forum: General Help
---

### Post by e-a-c on 2009-02-23
I have been messing with this all day long, and I am so close to finally getting it right. I am trying to set up an extended desktop over two monitors.

I am running Ubuntu 8.04 (Hardy Heron), my video card is a Radeon HD 3200. I have two monitors - my main monitor is a Dell 20" LCD at 1600x1200 and my secondary monitor is a wide screen TV plugged into the VGA port at 1360x768.

After trying various things, Xinerama is what finally worked for me, but I have two problems left:
1) My login screen is on the wrong screen and I can't figure out how to switch it (I need it to be on my monitor, not the TV, in case the TV isn't on...)
2) Video on both screens is running very slowly (e.g. scrolling in firefox is painfully slow and choppy). I had to disable DRI because I was getting millions of "fglrx(1): [DRI] Unlocking inconsistency:" and "(EE) fglrx(1): [DRI] Locking deadlock." errors (I assume this is related).

Here is my xorg.conf:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device" # Dell monitor
	Identifier	"Video Device 0"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
	Option		"DRI"		"off"
	Option		"ForceMonitors"	"tmds2i,crt1"
	Screen		0
EndSection

Section "Monitor" # Dell monitor
	Identifier	"Monitor 0"
	ModeLine	"1600x1200" 161.0 1600 1704 1880 2160 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Screen" # Dell monitor
	Identifier	"Screen 0"
	Monitor		"Monitor 0"
	Device		"Video Device 0"
	DefaultDepth	24
	SubSection "Display"
		Modes	"1600x1200"
		Virtual	1600 1200
	EndSubSection
EndSection

Section "Device" # VGA (TV)
	Identifier	"Video Device 1"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
	Option		"DRI"		"off"
	Option		"ForceMonitors"	"tmds2i,crt1"
	Screen		1
EndSection

Section "Monitor" # VGA (TV)
	Identifier	"Monitor 1"
	Modeline	"1360x768"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
EndSection

Section "Screen" # VGA (TV)
	Identifier	"Screen 1"
	Monitor		"Monitor 1"
	Device		"Video Device 1"
	DefaultDepth	24
	SubSection "Display"
		Modes	"1360x768"
		Virtual	1360 768
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen 1"
	Screen		"Screen 0"	RightOf "Screen 1"
	Option		"Xinerama"	"true"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection

```

I tried the obvious, switching these lines in ServerLayout:
> 
	Screen		"Screen 1"
	Screen		"Screen 0"	RightOf "Screen 1"

to
> 
	Screen		"Screen 0"
	Screen		"Screen 1"	LeftOf "Screen 0"

But my login screen still showed up on my VGA monitor/TV, just now it was blurry and square and off center (I assume that is what it looks like when my TV tries to display 1600x1200), and my LCD monitor was stretched vertically, trying to display 1360x768 - so, basically, all of the settings were correct but it swapped the physical monitors.

I couldn't get anything similar working with aticonfig (no matter how hard I tried, I couldn't get the resolutions on the TV to change), but I would be willing to give it another shot if someone has advice.
The Catalyst Control Center is completely useless to me (can't change the resolution on the individual screens).

Here is my latest Xorg.0.log:
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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux elizabeth-desktop 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 23 18:34:37 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen 1" (0)
(**) |   |-->Monitor "Monitor 1"
(**) |   |-->Device "Video Device 1"
(**) |-->Screen "Screen 0" (1)
(**) |   |-->Monitor "Monitor 0"
(**) |   |-->Device "Video Device 0"
(**) Option "Xinerama" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
(==) No FontPath specified.  Using compiled-in default.
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
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
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
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1022,9600 card 1849,9600 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1849,9602 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0a:0: chip 1022,9609 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:11:0: chip 1002,4390 card 1849,4390 rev 00 class 01,06,01 hdr 00
(II) PCI: 00:12:0: chip 1002,4397 card 1849,4397 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:12:1: chip 1002,4398 card 1849,4398 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:12:2: chip 1002,4396 card 1849,4396 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:13:0: chip 1002,4397 card 1849,4397 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4398 card 1849,4398 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4396 card 1849,4396 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4385 card 1849,4385 rev 3a class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,439c card 1849,439c rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,4383 card 1849,0888 rev 00 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,439d card 1849,439d rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4384 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4399 card 1849,4399 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,9610 card 1849,9610 rev 00 class 03,00,00 hdr 80
(II) PCI: 02:00:0: chip 10ec,8168 card 1849,8168 rev 02 class 02,00,00 hdr 00
(II) PCI: 03:07:0: chip 1106,3044 card 1849,3044 rev c0 class 0c,00,10 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,2), BCTRL: 0x0007 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:20:4), (0,3,3), BCTRL: 0x0007 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[1] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[2] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[3] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc unknown chipset (0x9610) rev 0, Mem @ 0xd0000000/28, 0xfe9f0000/16, 0xfe800000/20, I/O @ 0xc000/8
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
	[0] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[1] -1	0	0xfdfe0000 - 0xfdfeffff (0x10000) MX[B]
	[2] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[3] -1	0	0xfe7fa000 - 0xfe7fafff (0x1000) MX[B]
	[4] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[5] -1	0	0xfe7ff400 - 0xfe7ff4ff (0x100) MX[B]
	[6] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[7] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[8] -1	0	0xfe7ff800 - 0xfe7ff8ff (0x100) MX[B]
	[9] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[10] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[11] -1	0	0xfe7ffc00 - 0xfe7fffff (0x400) MX[B]
	[12] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[13] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[23] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[24] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[1] -1	0	0xfdfe0000 - 0xfdfeffff (0x10000) MX[B]
	[2] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[3] -1	0	0xfe7fa000 - 0xfe7fafff (0x1000) MX[B]
	[4] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[5] -1	0	0xfe7ff400 - 0xfe7ff4ff (0x100) MX[B]
	[6] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[7] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[8] -1	0	0xfe7ff800 - 0xfe7ff8ff (0x100) MX[B]
	[9] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[10] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[11] -1	0	0xfe7ffc00 - 0xfe7fffff (0x400) MX[B]
	[12] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[13] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[23] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[24] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
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
	[4] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[5] -1	0	0xfdfe0000 - 0xfdfeffff (0x10000) MX[B]
	[6] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[7] -1	0	0xfe7fa000 - 0xfe7fafff (0x1000) MX[B]
	[8] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[9] -1	0	0xfe7ff400 - 0xfe7ff4ff (0x100) MX[B]
	[10] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[11] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[12] -1	0	0xfe7ff800 - 0xfe7ff8ff (0x100) MX[B]
	[13] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[14] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[15] -1	0	0xfe7ffc00 - 0xfe7fffff (0x400) MX[B]
	[16] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[17] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[29] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[30] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[33] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.47.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.471                    
(II) ATI Proprietary Linux Driver Build Date: Feb 25 2008 21:22:09
(--) Chipset Supported AMD Graphics Processor (0x9610) found
(--) Chipset Supported AMD Graphics Processor (0x9610) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[5] -1	0	0xfdfe0000 - 0xfdfeffff (0x10000) MX[B]
	[6] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[7] -1	0	0xfe7fa000 - 0xfe7fafff (0x1000) MX[B]
	[8] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[9] -1	0	0xfe7ff400 - 0xfe7ff4ff (0x100) MX[B]
	[10] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[11] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[12] -1	0	0xfe7ff800 - 0xfe7ff8ff (0x100) MX[B]
	[13] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[14] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[15] -1	0	0xfe7ffc00 - 0xfe7fffff (0x400) MX[B]
	[16] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[17] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[29] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[30] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[33] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x820eaa8
(II) fglrx(1): pEnt->device->identifier=0x820eaa8
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[5] -1	0	0xfdfe0000 - 0xfdfeffff (0x10000) MX[B]
	[6] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[7] -1	0	0xfe7fa000 - 0xfe7fafff (0x1000) MX[B]
	[8] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[9] -1	0	0xfe7ff400 - 0xfe7ff4ff (0x100) MX[B]
	[10] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[11] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[12] -1	0	0xfe7ff800 - 0xfe7ff8ff (0x100) MX[B]
	[13] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[14] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[15] -1	0	0xfe7ffc00 - 0xfe7fffff (0x400) MX[B]
	[16] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[17] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[32] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[33] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[34] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[35] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[36] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "dri" "off"
(**) fglrx(0): Option "ForceMonitors" "tmds2i,crt1"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x06419064
(**) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon HD 3200 Graphics" (Chipset = 0x9610)
(--) fglrx(0): (PciSubVendor = 0x1849, PciSubDevice = 0x9610)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfe9f0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.82
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS780
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:5.0.
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCI card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(**) fglrx(0): ForceMonitors Settings: 81
(WW) fglrx(0): Dual head is configured, DesktopSetup setting "horizontal,reverse" will not be used
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: XXX  Model: 3  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing not preferred mode in violation of standard!(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff006318030000000000
(II) fglrx(0): 	0000010300281e00f000000000000000
(II) fglrx(0): 	00000021080031404540614000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	0000000000000000000000000000008e
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Connected Display2: DFP on secondary TMDS [tmds2i]
(II) fglrx(0): Display2 EDID data ---------------------------
(II) fglrx(0): Manufacturer: XXX  Model: 3  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing not preferred mode in violation of standard!(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff006318030000000000
(II) fglrx(0): 	0000010380281e00f000000000000000
(II) fglrx(0): 	00000021080031404540614000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	0000000000000000000000000000000e
(II) fglrx(0): End of Display2 EDID data --------------------
(II) fglrx(0): Primary Controller - DFP on secondary TMDS
(II) fglrx(0): Secondary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(**) fglrx(0): Center Mode is enabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 12 modes found for primary display.
(--) fglrx(0): Virtual size is 1360x768 (pitch 0)
(**) fglrx(0): *Mode "1360x768": 84.7 MHz (scaled from 0.0 MHz), 47.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1360x768"x60.0   84.72  1360 1424 1568 1776  768 769 772 795 +vsync (47.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace +hsync (29.8 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (400, 300) mm
(--) fglrx(0): DPI set to (86, 65)
(--) fglrx(0): Virtual size is 1360x768 (pitch 1408)
(**) fglrx(0): *Mode "1360x768": 84.7 MHz (scaled from 0.0 MHz), 47.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1360x768"x60.0   84.72  1360 1424 1568 1776  768 769 772 795 +vsync (47.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace +hsync (29.8 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(EE) fglrx(0): The new pair mode should not have size bigger than 1360x768. Please try new setting.
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(**) fglrx(0): NoDRI = YES
(II) fglrx(0): Depth moves disabled by default
(**) fglrx(0): Capabilities: 0x00000800
(**) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pcie] 258048 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(1): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(II) fglrx(1): PCI bus 1 card 5 func 0
(**) fglrx(1): Depth 24, (--) framebuffer bpp 32
(II) fglrx(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(1): Default visual is TrueColor
(==) fglrx(1): RGB weight 888
(II) fglrx(1): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(1): Buffer Tiling is OFF (copy from primary)
(--) fglrx(1): Chipset: "ATI Radeon HD 3200 Graphics" (Chipset = 0x9610)
(--) fglrx(1): (PciSubVendor = 0x1849, PciSubDevice = 0x9610)
(--) fglrx(1): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(1): VideoRAM: 131072 kByte, Type: DDR2
(WW) fglrx(1): board is an unknown third party board, chipset is supported
(==) fglrx(1):  PseudoColor visuals disabled
(**) fglrx(1): Center Mode is enabled 
(==) fglrx(1): TMDS coherent mode is enabled 
(II) fglrx(1): Total of 9 modes found for primary display.
(--) fglrx(1): Virtual size is 1600x1200 (pitch 0)
(**) fglrx(1): *Mode "1600x1200": 161.0 MHz (scaled from 0.0 MHz), 74.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1600x1200"x60.0  161.00  1600 1704 1880 2160  1200 1201 1204 1242 +vsync (74.5 kHz)
(**) fglrx(1):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(1):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(1):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x480"x60.0   25.18  640 664 760 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(1):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(1):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(1):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(1):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(1):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(1): Display dimensions: (400, 300) mm
(--) fglrx(1): DPI set to (101, 101)
(--) fglrx(1): Virtual size is 1600x1200 (pitch 1600)
(**) fglrx(1): *Mode "1600x1200": 161.0 MHz (scaled from 0.0 MHz), 74.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1600x1200"x60.0  161.00  1600 1704 1880 2160  1200 1201 1204 1242 +vsync (74.5 kHz)
(**) fglrx(1):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(1):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(1): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(1):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x480"x60.0   25.18  640 664 760 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(1):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(1): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(1):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(1): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(1):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(1):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(1):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(1): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(EE) fglrx(1): The new pair mode should not have size bigger than 1600x1200. Please try new setting.
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(==) fglrx(1): NoAccel = NO (copy from primary screen)
(==) fglrx(1): bNoDRI = YES (copy from primary screen)
(==) fglrx(1): UseFastTLS=0
(==) fglrx(1): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 0	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
	[1] 0	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B]
	[2] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[3] 0	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
	[4] 0	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B]
	[5] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[6] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[7] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[8] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[9] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[10] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[11] -1	0	0xfdfe0000 - 0xfdfeffff (0x10000) MX[B]
	[12] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[13] -1	0	0xfe7fa000 - 0xfe7fafff (0x1000) MX[B]
	[14] -1	0	0xfe7f4000 - 0xfe7f7fff (0x4000) MX[B]
	[15] -1	0	0xfe7ff400 - 0xfe7ff4ff (0x100) MX[B]
	[16] -1	0	0xfe7fb000 - 0xfe7fbfff (0x1000) MX[B]
	[17] -1	0	0xfe7fc000 - 0xfe7fcfff (0x1000) MX[B]
	[18] -1	0	0xfe7ff800 - 0xfe7ff8ff (0x100) MX[B]
	[19] -1	0	0xfe7fd000 - 0xfe7fdfff (0x1000) MX[B]
	[20] -1	0	0xfe7fe000 - 0xfe7fefff (0x1000) MX[B]
	[21] -1	0	0xfe7ffc00 - 0xfe7fffff (0x400) MX[B]
	[22] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B](B)
	[23] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[24] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[25] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[26] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[27] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[28] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[29] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[33] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[34] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[40] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[41] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[42] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[43] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[44] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(WW) fglrx(0): ***********************************
(WW) fglrx(0): * DRI initialization disabled!    *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available    *
(WW) fglrx(0): ***********************************
(II) fglrx(0): FBADPhys: 0xc4700000 FBMappedSize: 0x08000000
(II) fglrx(0): Reserved 0x04700000 bytes of sideport memory for power saving
(II) fglrx(0): Splitting WC range: base: 0xd4700000, size: 0x8000000
(II) fglrx(0): Splitting WC range: base: 0xd4800000, size: 0x7f00000
(II) fglrx(0): Splitting WC range: base: 0xd5000000, size: 0x7700000
(II) fglrx(0): Splitting WC range: base: 0xd6000000, size: 0x6700000
(II) fglrx(0): Splitting WC range: base: 0xd8000000, size: 0x4700000
(II) fglrx(0): Splitting WC range: base: 0xdc000000, size: 0x700000
(II) fglrx(0): Splitting WC range: base: 0xdc400000, size: 0x300000
(==) fglrx(0): Write-combining range (0xdc600000,0x100000)
(==) fglrx(0): Write-combining range (0xdc400000,0x300000)
(==) fglrx(0): Write-combining range (0xdc000000,0x700000)
(==) fglrx(0): Write-combining range (0xd8000000,0x4700000)
(==) fglrx(0): Write-combining range (0xd6000000,0x6700000)
(WW) fglrx(0): Failed to set up write-combining range (0xd5000000,0x7700000)
(WW) fglrx(0): Failed to set up write-combining range (0xd4800000,0x7f00000)
(WW) fglrx(0): Failed to set up write-combining range (0xd4700000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1408,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1408,768) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1408 x 7423
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): DPMS enabled
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 10
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) fglrx(0): Finished Initialize PPLIB!
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(WW) fglrx(1): ***********************************
(WW) fglrx(1): * DRI initialization disabled!    *
(WW) fglrx(1): * 2D acceleraton available (MMIO) *
(WW) fglrx(1): * no 3D acceleration available    *
(WW) fglrx(1): ***********************************
(II) fglrx(1): FBADPhys: 0xca380000 FBMappedSize: 0x08000000
(II) fglrx(1): Reserved 0x04700000 bytes of sideport memory for power saving
(==) fglrx(1): Removed MMIO write-combining range (0xdc600000,0x100000)
(==) fglrx(1): Removed MMIO write-combining range (0xdc400000,0x200000)
(==) fglrx(1): Removed MMIO write-combining range (0xdc000000,0x400000)
(II) fglrx(1): Splitting WC range: base: 0xda380000, size: 0x8000000
(II) fglrx(1): Splitting WC range: base: 0xda400000, size: 0x7f80000
(II) fglrx(1): Splitting WC range: base: 0xda800000, size: 0x7b80000
(II) fglrx(1): Splitting WC range: base: 0xdb000000, size: 0x7380000
(II) fglrx(1): Splitting WC range: base: 0xdc000000, size: 0x6380000
(II) fglrx(1): Splitting WC range: base: 0xe0000000, size: 0x2380000
(II) fglrx(1): Splitting WC range: base: 0xe2000000, size: 0x380000
(II) fglrx(1): Splitting WC range: base: 0xe2200000, size: 0x180000
(==) fglrx(1): Write-combining range (0xe2300000,0x80000)
(==) fglrx(1): Write-combining range (0xe2200000,0x180000)
(==) fglrx(1): Write-combining range (0xe2000000,0x380000)
(WW) fglrx(1): Failed to set up write-combining range (0xe0000000,0x2380000)
(WW) fglrx(1): Failed to set up write-combining range (0xdc000000,0x6380000)
(==) fglrx(1): Write-combining range (0xdb000000,0x7380000)
(==) fglrx(1): Write-combining range (0xda800000,0x7b80000)
(==) fglrx(1): Write-combining range (0xda400000,0x7f80000)
(==) fglrx(1): Write-combining range (0xda380000,0x8000000)
(II) fglrx(1): FBMM initialized for area (0,0)-(1600,8191)
(II) fglrx(1): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(II) fglrx(1): Largest offscreen area available: 1600 x 6991
(==) fglrx(1): Backing store disabled
(II) fglrx(1): DPMS enabled
(WW) fglrx(1): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".
(II) fglrx(1): Acceleration enabled
(II) fglrx(1): Direct rendering disabled
(II) fglrx(1): Finished Initialize PPLIB!
(==) fglrx(1): Silken mouse enabled
(==) fglrx(1): Using hardware cursor
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) AIGLX: Screen 1 is not DRI capable
(II) GLX: Initialized MESA-PROXY GL provider for screen 1
(II) fglrx(0): Match for the recent mode (2880x1200@60Hz) not found
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
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
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.

```

Here is the what I get from fglrxinfo:
> 
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)


Any ideas/suggestions? I am pretty desperate, having already spent 8 hours working on this.

---

### Post by e-a-c on 2009-03-11
(bump)
I have not been able to resolve any of the problems above, and have spent several days on this. Because of this I have been forced to go back to using Windows for my home machine... please, someone, help! I'm begging!

---

### Post by GnuSense on 2009-03-12
I wish I had great insights to add, have you tried the Catalyst Control Center?  It works for some.

I got dual head working with the **radeonhd** driver, you might give that a shot.  No compiz fusion for me, as of yet, but I'd rather have dual monitors.  Send me a private message if you want my xorg.conf.

---


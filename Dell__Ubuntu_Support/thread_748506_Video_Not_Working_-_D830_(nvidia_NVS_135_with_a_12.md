---
title: "Video Not Working - D830 (nvidia NVS 135 with a 1280x800 WXGA screen) on Ubuntu 8.04"
date: 2008-04-07
forum: Dell  Ubuntu Support
---

### Post by uvray on 2008-04-07
Posted on the Dell.com Linux forum today and tried the steps [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) with no luck. Any suggestions here?
------------------------------------
Video Not Working - D830 (nvidia NVS 135 with a 1280x800 WXGA screen) on Ubuntu 8.04 (2.6.25-15-generic). Once I install the driver via EnvyNG and reboot, the screen is grey and horizontally lined and when you can hear the "login sound" complete, a black bar 2" thick appears on the right side, almost like it is off-centered.

 

Here is the xorg.conf file (minus comments) that gets generated with EnvyNG for driver 169.12

 
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "vmmouse"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "Defaultdepth"    "24"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
    Inputdevice    "Synaptics Touchpad"
EndSection
Section "Extensions"
    Option        "Composite"    "Enable"
EndSection

Feel free to be rude if I've missed something "n00bish", I've got thick skin(and skull lol).

---

### Post by win2456 on 2008-04-09
having the same problem with my D830.  I have the nvidia 140m.  currently using the default xorg.conf.  here's what it looks like:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by win2456 on 2008-04-09
the scrolling with the default drivers is extremely slow, graphics are choppy and compiz or any enhanced graphics are not working...
this is what we get for trying a beta! :)  hopefully problems will be fixed with the final release.  video worked right out of the box with gutsy

---

### Post by jecker on 2008-04-09
To help everyone help you, you should post the /var/log/Xorg.0.log logs. Posting these logs will help determine the problem.

---

### Post by uvray on 2008-04-09
Here is the log file as suggested
---------------------------------------------
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu6)
Current Operating System: Linux ubuntop 2.6.24-15-generic #1 SMP Fri Apr 4 03:48:31 UTC 2008 i686
Build Date: 30 March 2008  04:42:53PM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr  7 15:14:59 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Card0"
(==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "<default pointer>"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the default mouse configuration.
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
(II) PCI: 00:00:0: chip 8086,2a00 card 1028,01fe rev 0c class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2a01 card 0000,0000 rev 0c class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,01fe rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,01fe rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,01fe rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,01fe rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2845 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,2849 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,01fe rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,01fe rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,01fe rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,01fe rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2815 card 1028,01fe rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2850 card 1028,01fe rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2828 card 1028,01fe rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,01fe rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,042b card 1028,01fe rev a1 class 03,00,00 hdr 00
(II) PCI: 03:01:0: chip 1217,7135 card 1401,0000 rev 21 class 06,07,00 hdr 82
(II) PCI: 03:01:4: chip 1217,00f7 card 1028,01fe rev 02 class 0c,00,10 hdr 00
(II) PCI: 09:00:0: chip 14e4,1673 card 1028,01fe rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,12), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfeafffff (0x4b00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:0), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:3), (0,12,13), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xf9e00000 - 0xf9ffffff (0x200000) MX[B]
(II) Bus 12 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf01fffff (0x200000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 9: bridge is at (0:28:5), (0,9,9), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 9 non-prefetchable memory range:
	[0] -1	0	0xf9d00000 - 0xf9dfffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,7), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf9c00000 - 0xf9cfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 4: bridge is at (3:1:0), (3,4,7), BCTRL: 0x05c0 (VGA_EN is cleared)
(--) PCI:*(1:0:0) nVidia Corporation Quadro NVS 135M rev 161, Mem @ 0xfd000000/24, 0xe0000000/28, 0xfa000000/25, I/O @ 0xdf00/7
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
	[0] -1	0	0xf9df0000 - 0xf9dfffff (0x10000) MX[B]
	[1] -1	0	0xf9cfe800 - 0xf9cfefff (0x800) MX[B]
	[2] -1	0	0xf9cff000 - 0xf9cfffff (0x1000) MX[B]
	[3] -1	0	0xfebfbf00 - 0xfebfbfff (0x100) MX[B]
	[4] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[6] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
	[7] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[11] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[12] -1	0	0x00006ee0 - 0x00006eef (0x10) IX[B]
	[13] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[B]
	[14] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[B]
	[15] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[B]
	[16] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[B]
	[17] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[B]
	[23] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[B]
	[24] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[B]
	[25] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[B]
	[26] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[B]
	[27] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf9df0000 - 0xf9dfffff (0x10000) MX[B]
	[1] -1	0	0xf9cfe800 - 0xf9cfefff (0x800) MX[B]
	[2] -1	0	0xf9cff000 - 0xf9cfffff (0x1000) MX[B]
	[3] -1	0	0xfebfbf00 - 0xfebfbfff (0x100) MX[B]
	[4] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[6] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
	[7] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[11] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[12] -1	0	0x00006ee0 - 0x00006eef (0x10) IX[B]
	[13] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[B]
	[14] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[B]
	[15] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[B]
	[16] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[B]
	[17] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[B]
	[23] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[B]
	[24] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[B]
	[25] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[B]
	[26] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[B]
	[27] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
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
	[4] -1	0	0xf9df0000 - 0xf9dfffff (0x10000) MX[B]
	[5] -1	0	0xf9cfe800 - 0xf9cfefff (0x800) MX[B]
	[6] -1	0	0xf9cff000 - 0xf9cfffff (0x1000) MX[B]
	[7] -1	0	0xfebfbf00 - 0xfebfbfff (0x100) MX[B]
	[8] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
	[9] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[10] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
	[11] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[17] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[18] -1	0	0x00006ee0 - 0x00006eef (0x10) IX[B]
	[19] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[B]
	[20] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[B]
	[21] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[B]
	[22] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[B]
	[23] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[B]
	[29] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[B]
	[30] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[B]
	[31] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[B]
	[32] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[B]
	[33] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
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
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:55:38 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9df0000 - 0xf9dfffff (0x10000) MX[B]
	[5] -1	0	0xf9cfe800 - 0xf9cfefff (0x800) MX[B]
	[6] -1	0	0xf9cff000 - 0xf9cfffff (0x1000) MX[B]
	[7] -1	0	0xfebfbf00 - 0xfebfbfff (0x100) MX[B]
	[8] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
	[9] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[10] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
	[11] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[17] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[18] -1	0	0x00006ee0 - 0x00006eef (0x10) IX[B]
	[19] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[B]
	[20] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[B]
	[21] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[B]
	[22] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[B]
	[23] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[B]
	[29] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[B]
	[30] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[B]
	[31] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[B]
	[32] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[B]
	[33] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9df0000 - 0xf9dfffff (0x10000) MX[B]
	[5] -1	0	0xf9cfe800 - 0xf9cfefff (0x800) MX[B]
	[6] -1	0	0xf9cff000 - 0xf9cfffff (0x1000) MX[B]
	[7] -1	0	0xfebfbf00 - 0xfebfbfff (0x100) MX[B]
	[8] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
	[9] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[10] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
	[11] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[20] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[21] -1	0	0x00006ee0 - 0x00006eef (0x10) IX[B]
	[22] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[B]
	[23] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[B]
	[24] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[B]
	[25] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[B]
	[26] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[B]
	[32] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[B]
	[33] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[B]
	[34] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[B]
	[35] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[B]
	[36] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid: the
(WW) NVIDIA(GPU-0):     checksum for EDID version 1 is invalid.
(--) NVIDIA(GPU-0): 
(--) NVIDIA(GPU-0): Raw EDID bytes:
(--) NVIDIA(GPU-0): 
(--) NVIDIA(GPU-0):   00 ff ff ff ff ff ff 00  4c a3 58 33 00 00 00 00
(--) NVIDIA(GPU-0):   00 11 01 03 80 21 15 78  0a 87 f5 94 57 4f 8c 27
(--) NVIDIA(GPU-0):   27 50 54 00 00 00 01 01  01 01 01 01 01 01 01 01
(--) NVIDIA(GPU-0):   01 01 01 01 01 01 4c 1d  00 90 50 20 22 30 10 30
(--) NVIDIA(GPU-0):   13 00 4b cf 10 00 00 19  00 00 00 0f 00 00 00 00
(--) NVIDIA(GPU-0):   00 00 00 00 00 23 87 02  64 00 00 00 00 fe 00 43
(--) NVIDIA(GPU-0):   50 30 34 31 00 31 35 34  58 33 0a 20 00 00 00 fe
(--) NVIDIA(GPU-0):   00 26 36 40 47 6a 8f c6  ff 01 01 0a 20 20 00 a3
(--) NVIDIA(GPU-0): 
(II) NVIDIA(0): NVIDIA GPU Quadro NVS 135M (G86GL) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.47.00.01
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro NVS 135M at PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9df0000 - 0xf9dfffff (0x10000) MX[B]
	[5] -1	0	0xf9cfe800 - 0xf9cfefff (0x800) MX[B]
	[6] -1	0	0xf9cff000 - 0xf9cfffff (0x1000) MX[B]
	[7] -1	0	0xfebfbf00 - 0xfebfbfff (0x100) MX[B]
	[8] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
	[9] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[10] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
	[11] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[20] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[21] -1	0	0x00006ee0 - 0x00006eef (0x10) IX[B]
	[22] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[B]
	[23] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[B]
	[24] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[B]
	[25] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[B]
	[26] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[B]
	[32] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[B]
	[33] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[B]
	[34] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[B]
	[35] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[B]
	[36] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) Initializing extension GLX
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event11
(**) Option "Device" "/dev/input/event11"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "CorePointer"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(**) <default pointer>: Sensitivity: 1
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
(II) evaluating device (<default pointer>)
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event11
(**) Option "Device" "/dev/input/event11"
(--) Synaptics Touchpad touchpad found

---

### Post by jecker on 2008-04-10
The good thing is there are no errors. I may be wrong but it sounds like the frequency is incorrect.
run this command: sudo nvidia-xconfig

Also look at the website I posted at [http://ubuntuforums.org/showthread.php?t=698621&page=3](http://ubuntuforums.org/showthread.php?t=698621&page=3)
I am not sure if these options pertain to your video card, but they are options for the xorg.conf file that Nvidia supports.

---

### Post by win2456 on 2008-04-10
forgot to mention, i cannot run nvidia-settings.  it says that the system is not using nvidia drivers.  if i try to use nvidia drivers, it doesn't save the settings.  keeps reverting to VESA.  when I run nvidia-xconfig, i get the same results after a restart (white screen, thick grey patch down the middle)

---

### Post by artir on 2008-04-10
DO NOT NEVER use envy. Install drivers trought the official Restricted drivers manager

---

### Post by jecker on 2008-04-10
Have you tried to change the vertical refresh rate to 60?

---

### Post by uvray on 2008-04-10
> **artir said:**
> DO NOT NEVER use envy. Install drivers trought the official Restricted drivers manager

That's how I started off my little adventure. And it does the exact same thing if I use the built-in restricted drives, EnvyNG or manually installing the nVidia driver.

jecker - thanks for your input. I tried using - Option "UseDisplayDevice" "DFP" - but it still came up the same way.

 I'm thinking that you're right about the refresh rate, but I cannot find any hard documentation about the HorizSync and VertRefresh. Apparently the screen is a Samsung WXGA 15.4 LCD (part # XU105) but there is nothing concrete out there. It seems any range that I put in just comes back with the same garbled display. I tried using the modelines calculator at sourceforge but it messed it up too, just differently.

Any thoughts on how to get that information?

---

### Post by jecker on 2008-04-10
This website may be of some help:
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README)

---

### Post by uvray on 2008-04-11
Thanks again jecker, however, I simply get a "file not found" text string off of any link on the [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README) link you gave.

The search continues =^)

---

### Post by jecker on 2008-04-11
Wow I am sorry. My machine must have had it cached, because it worked fine for me before. Try this link: [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/part-03.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/part-03.html)
If this link does not work either try doing a Google search for Nvidia Appendix Linux, this will get you started.

---

### Post by doweller on 2008-04-27
My Dell D830 has a NVS140, too, and shows the same problems with nvidia as a driver (nv works fine). My Xorg.0.log says
> The EDID read for display device DFP-0 is invalid: the checksum for EDID version 1 is invalid.
Did you solve your problem somehow? Would you please post your solution if you did so? And if not: Any idea about how to configure xorg.conf so that the wrong display EDID doesn't get in the way (nvidia worked fine with Gutsy).

---

### Post by win2456 on 2008-04-27
I just got mine working yesterday.  I had to delete and uninstall all nvidia drivers (including the ones that hardy tries to install).  There is a write up on the net for a Thinkpad R61 on how to remove proprietary drivers and install nvidia ones off the website.  In addition to all this, I had to remove the nvidia-glx-new & nvidia-*.  I then downloaded the latest beta drivers from NVIDIA (173.xx) and it worked!

I'll try to find the links I used and post them here.

---

### Post by win2456 on 2008-04-27
I just got mine working yesterday.  I had to delete and uninstall all nvidia drivers (including the ones that hardy tries to install).  There is a write up on the net for a Thinkpad R61 on how to remove proprietary drivers and install nvidia ones off the website.  In addition to all this, I had to remove the nvidia-glx-new & nvidia-*.  I then downloaded the latest beta drivers from NVIDIA (173.xx) and it worked!

I'll try to find the links I used and post them here.

***double post, my bad***

---

### Post by win2456 on 2008-04-27
Okay, here is the link:
[http://ubuntuforums.org/showthread.php?t=712479&page=3](http://ubuntuforums.org/showthread.php?t=712479&page=3)

quick tip: make sure you do apt-get build-essential and install all the updates before changing any of this.

---

### Post by doweller on 2008-04-30
Juhu! It works! Thanks a lot!

But there are some "buts", too: When I plug in my beamer and (!) use a lot of desktop effects the driver dies on me, taking Hardy with it into the grave ... reboot. I will use it only without external monitors and see what happens then.

---

### Post by win2456 on 2008-05-01
aahh... I haven't tried it with an external monitor yet.  I remember in Gutsy, I tried to get external monitor and video out working properly, but I just ended up with a messed up xorg file.  So, I'm happy for now and hopefully video output issues will be resolved soon with better support :)

---

### Post by prock on 2008-05-07
[SIZE="4"]I have the same problem with the D830 and the nvidia driver.  I had the same hardware running fine with the driver in Guttsy AMD-64 but lost it when I upgraded to Hardy AMD-64.  

I think UVRAY may be on the right track with the resolutions and refresh rate idea.  Perhaps editing /etc/X11/xorg.conf with the correct ones will help.  

I have a support e-mail request into Dell for a list of Screen resolutions, sync and refresh rates.  If I get it I will post it.  I will keep looking for solutions on this thread.[/SIZE]

---

### Post by prock on 2008-05-09
[SIZE="3"]My Reply from Dell dose not tell me much.  I am not dual booting windows so I can froget the display tab.  
I may try the solution [here from Ubustew]("http://ubuntuforums.org/showthread.php?t=712479&page=4")
This is what dell said:[/SIZE]

Thank you for contacting Dell Warranty Support.

With regard to your query on the list of resolutions on supported by the part number gave, this will have to rely on the standard rate that the LCD is able to support. The maximum resolution for this 15.4-inch WXGA nonglare is 1280x800. Everything below this is supported varying on the video cards supported resolutions as well.

If you can pull up screen resolutions on the display tab, you can actually select the supported resolutions that the LCD supports.

As for documentation on this part, this is not available since manufacturing details would only indicate the LCD type, class and the maximum resolution. All other information will be displayed on the display tab.

I hope this has addressed your concern. Should you require further assistance from me, please feel free to reply to this email.

---


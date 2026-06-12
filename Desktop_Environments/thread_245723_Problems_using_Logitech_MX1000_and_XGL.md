---
title: "Problems using Logitech MX1000 and XGL"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Nojatron on 2006-08-28
When trying to use the evdev driver in a XGL session I get the following error:
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "noj"
/etc/gdm/Xsession: Beginning session setup...

(gnome-session:6458): Gtk-WARNING **: cannot open display: 

```

it works fine from what I can tell in a ordinary gnome, metacity session (haven't got around to mapping buttons etc because I want it in XGL/Compiz). Compiz also works fine using the standard mouse configuration.

Relevant xorg.conf parts:
```

Section "InputDevice"
	Identifier	"Logitech MX1000"
	Driver		"evdev"
	Option		"Name"				"Logitech USB Receiver"
	Option		"Device"			"/dev/input/event2"
	Option		"Emulate3Buttons"		"false"
	Option		"WHEELRelativeAxisButtons"	"4 5"
	Option		"HWHEELRelativeAxisButtons"	"7 6"
	Option		"SendCoreEvents"		"true"
EndSection

```

Relevant "cat /proc/bus/input/devices" readout:
```

I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-9/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse0 ts0 event2
B: EV=7
B: KEY=7fffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=143

```

XGL Session script:
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session

```

I have no idea what I'm doing so any help would be much appreciated.

---

### Post by Nojatron on 2006-08-28
Any ideas? I don't know enough about this to know what's going on.

---

### Post by zas on 2006-08-28
Hmm...I have an MX1000 under XGL also, and my xorg looks quite a bit different.  I used the instructions in the comdocs [here]("https://help.ubuntu.com/community/MX1000Mouse"), and all of my buttons(except the stupid app switcher) work fine in firefox and nautilus.  (Be careful that you *don't* do the steps in the **Breezy** section!) 

One thing that's not in that guide is that sometimes the horizontal scroll and cruise buttons will stop working (usually right after I boot out of XP.)  To fix it you need lmctl which you can get [here]("http://www.bedroomlan.org/~alexios/files/SOFTWARE/lmctl/lmctl_0.3.2_i386.deb").  Then just run it like this to turn SmartScroll back on:
[INDENT]sudo lmctl --sms[/INDENT]

Hope this helps!

---

### Post by Nojatron on 2006-08-29
I tried commenting out the lines that the guide did not include and the Xserver fails to load. It does appear to see the mouse though.

Xorg.0.log:
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux Nojatron-Ubuntu 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 29 19:51:31 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA GeForce 7800"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Logitech MX1000"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1458,5000 rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1458,0c11 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1458,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1458,5004 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1458,5004 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1458,ae01 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 1458,5002 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1458,b003 rev a3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1458,b003 rev a3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1458,e000 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:07:0: chip 168c,0013 card 1385,4d00 rev 01 class 02,00,00 hdr 00
(II) PCI: 01:08:0: chip 109e,036e card 1461,0771 rev 11 class 04,00,00 hdr 80
(II) PCI: 01:08:1: chip 109e,0878 card 1461,0771 rev 11 class 04,80,00 hdr 80
(II) PCI: 01:0a:0: chip 104c,8025 card 1458,1000 rev 01 class 0c,00,10 hdr 00
(II) PCI: 05:00:0: chip 10de,0091 card 107d,2a30 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:9:0), (0,1,1), BCTRL: 0x0200 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe3100000 - 0xe31fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00008000 - 0x00008fff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:13:0), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00007000 - 0x00007fff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:14:0), (0,5,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe2ffffff (0x3000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI: (1:8:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xe3100000/12
(--) PCI:*(5:0:0) nVidia Corporation GeForce 7800 GTX rev 161, Mem @ 0xe0000000/24, 0xd0000000/28, 0xe1000000/24, I/O @ 0xa000/7
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
	[0] -1	0	0xe3010000 - 0xe3013fff (0x4000) MX[B]
	[1] -1	0	0xe3014000 - 0xe30147ff (0x800) MX[B]
	[2] -1	0	0xe3101000 - 0xe3101fff (0x1000) MX[B]
	[3] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B]
	[4] -1	0	0xe3203000 - 0xe3203fff (0x1000) MX[B]
	[5] -1	0	0xe3200000 - 0xe3200fff (0x1000) MX[B]
	[6] -1	0	0xe3205000 - 0xe3205fff (0x1000) MX[B]
	[7] -1	0	0xe3204000 - 0xe3204fff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xe3201000 - 0xe3201fff (0x1000) MX[B]
	[10] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xe3100000 - 0xe3100fff (0x1000) MX[B](B)
	[14] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[16] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[17] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[18] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[19] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[28] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[29] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe3010000 - 0xe3013fff (0x4000) MX[B]
	[1] -1	0	0xe3014000 - 0xe30147ff (0x800) MX[B]
	[2] -1	0	0xe3101000 - 0xe3101fff (0x1000) MX[B]
	[3] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B]
	[4] -1	0	0xe3203000 - 0xe3203fff (0x1000) MX[B]
	[5] -1	0	0xe3200000 - 0xe3200fff (0x1000) MX[B]
	[6] -1	0	0xe3205000 - 0xe3205fff (0x1000) MX[B]
	[7] -1	0	0xe3204000 - 0xe3204fff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xe3201000 - 0xe3201fff (0x1000) MX[B]
	[10] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xe3100000 - 0xe3100fff (0x1000) MX[B](B)
	[14] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[16] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[17] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[18] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[19] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[28] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[29] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
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
	[4] -1	0	0xe3010000 - 0xe3013fff (0x4000) MX[B]
	[5] -1	0	0xe3014000 - 0xe30147ff (0x800) MX[B]
	[6] -1	0	0xe3101000 - 0xe3101fff (0x1000) MX[B]
	[7] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B]
	[8] -1	0	0xe3203000 - 0xe3203fff (0x1000) MX[B]
	[9] -1	0	0xe3200000 - 0xe3200fff (0x1000) MX[B]
	[10] -1	0	0xe3205000 - 0xe3205fff (0x1000) MX[B]
	[11] -1	0	0xe3204000 - 0xe3204fff (0x1000) MX[B]
	[12] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[13] -1	0	0xe3201000 - 0xe3201fff (0x1000) MX[B]
	[14] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xe3100000 - 0xe3100fff (0x1000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[33] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[34] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[35] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[37] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 0.0.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 05:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3010000 - 0xe3013fff (0x4000) MX[B]
	[5] -1	0	0xe3014000 - 0xe30147ff (0x800) MX[B]
	[6] -1	0	0xe3101000 - 0xe3101fff (0x1000) MX[B]
	[7] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B]
	[8] -1	0	0xe3203000 - 0xe3203fff (0x1000) MX[B]
	[9] -1	0	0xe3200000 - 0xe3200fff (0x1000) MX[B]
	[10] -1	0	0xe3205000 - 0xe3205fff (0x1000) MX[B]
	[11] -1	0	0xe3204000 - 0xe3204fff (0x1000) MX[B]
	[12] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[13] -1	0	0xe3201000 - 0xe3201fff (0x1000) MX[B]
	[14] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xe3100000 - 0xe3100fff (0x1000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[33] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[34] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[35] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[37] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3010000 - 0xe3013fff (0x4000) MX[B]
	[5] -1	0	0xe3014000 - 0xe30147ff (0x800) MX[B]
	[6] -1	0	0xe3101000 - 0xe3101fff (0x1000) MX[B]
	[7] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B]
	[8] -1	0	0xe3203000 - 0xe3203fff (0x1000) MX[B]
	[9] -1	0	0xe3200000 - 0xe3200fff (0x1000) MX[B]
	[10] -1	0	0xe3205000 - 0xe3205fff (0x1000) MX[B]
	[11] -1	0	0xe3204000 - 0xe3204fff (0x1000) MX[B]
	[12] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[13] -1	0	0xe3201000 - 0xe3201fff (0x1000) MX[B]
	[14] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xe3100000 - 0xe3100fff (0x1000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[25] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[26] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[27] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[28] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[30] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[31] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[32] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[33] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[34] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[35] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[36] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[37] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[38] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[39] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[40] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[41] 0	0	0xe20003b0 - 0xe20003bb (0xc) IS[B]
	[42] 0	0	0xe20003c0 - 0xe20003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce 7800 GTX at PCI:5:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.70.02.11.68
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7800 GTX at PCI:5:0:0:
(--) NVIDIA(0):     MEA 1998E (CRT-1)
(--) NVIDIA(0): MEA 1998E (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): No valid modes for "1280x854"; removing.
(WW) NVIDIA(0): No valid modes for "1200x800"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0):     "1280x768"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1152x768"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (92, 100); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe3010000 - 0xe3013fff (0x4000) MX[B]
	[8] -1	0	0xe3014000 - 0xe30147ff (0x800) MX[B]
	[9] -1	0	0xe3101000 - 0xe3101fff (0x1000) MX[B]
	[10] -1	0	0xe3000000 - 0xe300ffff (0x10000) MX[B]
	[11] -1	0	0xe3203000 - 0xe3203fff (0x1000) MX[B]
	[12] -1	0	0xe3200000 - 0xe3200fff (0x1000) MX[B]
	[13] -1	0	0xe3205000 - 0xe3205fff (0x1000) MX[B]
	[14] -1	0	0xe3204000 - 0xe3204fff (0x1000) MX[B]
	[15] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[16] -1	0	0xe3201000 - 0xe3201fff (0x1000) MX[B]
	[17] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xe3100000 - 0xe3100fff (0x1000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[24] 0	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[29] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[30] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[31] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[32] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[33] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[34] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[35] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[36] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[37] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[38] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[39] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[40] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[41] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[42] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[43] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[44] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[45] 0	0	0xe20003b0 - 0xe20003bb (0xc) IS[B]
	[46] 0	0	0xe20003c0 - 0xe20003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
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
(II) Initializing extension GLX
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
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Logitech MX1000-usb-0000:00:02.0-9/input0: Core Pointer
(**) Option "CorePointer"
(**) Logitech MX1000-usb-0000:00:02.0-9/input1: Core Pointer
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: Found 4 relative axes.
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: Configuring as pointer.
(**) Option "HWHEELRelativeAxisButtons" "7 6"
(**) Logitech MX1000-usb-0000:00:02.0-9/input1: HWHEELRelativeAxisButtons: 7 6.
(**) Logitech MX1000-usb-0000:00:02.0-9/input1: WHEELRelativeAxisButtons: 4 5.
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: Found 95 mouse buttons
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: Configured 99 mouse buttons
(II) XINPUT: Adding extended input device "Logitech MX1000-usb-0000:00:02.0-9/input1" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Logitech MX1000-usb-0000:00:02.0-9/input0" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Logitech MX1000-usb-0000:00:02.0-9/input0: Init
(**) Logitech MX1000-usb-0000:00:02.0-9/input1: 4 valuators.
(**) ../../src/evdev_btn.c (90): Registering 99 buttons.
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: Init
(II) evdev brain: Rescanning devices (2).
(II) Logitech MX1000-usb-0000:00:02.0-9/input0: On
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: On

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4ab6]
1: [0xffffe420]
2: /usr/bin/X(CreateConnectionBlock+0x4a) [0x806d7d2]
3: /usr/bin/X(main+0x5cf) [0x806e22b]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7dd7ea2]
5: /usr/bin/X(FontFileCompleteXLFD+0x85) [0x806d641]

Fatal server error:
Caught signal 11.  Server aborting

```

---

### Post by zas on 2006-08-29
It looks like your mouse is trying to load twice.  I have to admit though, that is just a guess.  I've only been using Ubuntu for about 2 weeks, and I honestly don't really know how to read that log.  

That being said, in comparing it to mine, I see double lines for the mouse loading.  Here are the last few lines of my Xorg.0.log:
```
(**) Option "CorePointer"
(**) Logitech MX1000-usb-0000:00:02.1-2/input0: Core Pointer
(II) Logitech MX1000-usb-0000:00:02.1-2/input0: Found 4 relative axes.
(II) Logitech MX1000-usb-0000:00:02.1-2/input0: Configuring as pointer.
(**) Option "HWHEELRelativeAxisButtons" "7 6"
(**) Logitech MX1000-usb-0000:00:02.1-2/input0: HWHEELRelativeAxisButtons: 7 6.
(**) Logitech MX1000-usb-0000:00:02.1-2/input0: WHEELRelativeAxisButtons: 4 5.
(II) Logitech MX1000-usb-0000:00:02.1-2/input0: Found 16 mouse buttons
(II) Logitech MX1000-usb-0000:00:02.1-2/input0: Configured 20 mouse buttons
(II) XINPUT: Adding extended input device "Logitech MX1000-usb-0000:00:02.1-2/input0" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Logitech MX1000-usb-0000:00:02.1-2/input0: 4 valuators.
(**) ../../src/evdev_btn.c (90): Registering 20 buttons.
(II) Logitech MX1000-usb-0000:00:02.1-2/input0: Init
(II) evdev brain: Rescanning devices (2).
(II) Logitech MX1000-usb-0000:00:02.1-2/input0: On
(II) NVIDIA(0): Setting mode "1600x1200"
```
You might want to double check that there aren't any duplicated sections in your xorg.conf.  If your still having problems, perhaps you should post your whole xorg.conf and maybe somebody a little more knowledgeable can take a look.

---

### Post by Nojatron on 2006-08-30
I think the issue is because mine is a combo pack (mx3100) after doing some more research. I changed my settings to load XGL by default rather then just the one session and got a slightly different error:

```

(II) evdev brain: Rescanning devices (1).
(**) Option "SendCoreEvents" "true"
(**) Logitech MX1000-usb-0000:00:02.0-9/input1: always reports core events
(**) Option "CorePointer"
(**) Logitech MX1000-usb-0000:00:02.0-9/input1: Core Pointer
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: Found 4 relative axes.
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: Configuring as pointer.
(**) Option "HWHEELRelativeAxisButtons" "7 6"
(**) Logitech MX1000-usb-0000:00:02.0-9/input1: HWHEELRelativeAxisButtons: 7 6.
(**) Option "WHEELRelativeAxisButtons" "4 5"
(**) Logitech MX1000-usb-0000:00:02.0-9/input1: WHEELRelativeAxisButtons: 4 5.
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: Found 95 mouse buttons
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: Configured 99 mouse buttons
(II) XINPUT: Adding extended input device "Logitech MX1000-usb-0000:00:02.0-9/input1" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Logitech MX1000-usb-0000:00:02.0-9/input1: 4 valuators.
(**) ../../src/evdev_btn.c (90): Registering 99 buttons.
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: Init
(II) evdev brain: Rescanning devices (2).
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: On
(II) Logitech MX1000-usb-0000:00:02.0-9/input1: Off

```

If you look at this post and my post before it looks like it is identifying it as a keyboard... and also if you look at my cat readout it has keyboard AND mouse under the handlers part. I could be completely wrong but either way I don't know if there's a way to work around it.

Anyway, thanks for trying to help out zas, much appreciated.

---

### Post by zas on 2006-08-30
Ah, I remember reading that the setup is different for the combos.  Have you seen [this]("http://www.ubuntuforums.org/showthread.php?p=1360560&highlight=mx3100#post1360560") post?  It's a mx3100 specific setup, and a couple people said it was working for them.

One tip in case you haven't noticed is that when you do a search in the forums it pulls up the entire thread that includes your search terms.  Once you open the thread then you can use the "Search this Thread" link (right below the page numbers) to narrow down the specific posts that contain your search term.

---

### Post by kayrune on 2006-08-30
It's an "old" bug, still not fixed it seems then....

[http://www.ubuntuforums.org/showthread.php?t=193946](http://www.ubuntuforums.org/showthread.php?t=193946)

---

### Post by Nojatron on 2006-08-31
Still didn't work. I don't think it matters whether I use a udev rule so long as I don't swap around usb devices frequently, which I don't.

I just had a look at the log for when I log in without using XGL and it still says keyboard. I set up the other buttons to see if it really is working and it went well, I can use all the buttons fine.

I've tried just about everything, I don't think there's anything else I can do other then buy a new mouse or wait for a update that fixes the problem.

Thanks again.

---

### Post by gils0040 on 2006-08-31
i am affected by this bug as well. im using an mx3100 (mx1000 and keyboard) combo. xgl from beerorkid repositories crashes on gdm start.

---


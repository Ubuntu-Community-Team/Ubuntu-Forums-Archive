---
title: "ctrl+alt+f1 disabled"
date: 2006-06-06
forum: Desktop Environments
---

### Post by subzero79 on 2006-06-06
I am having problems to switch to consoles in the login windows with Ctrl+alt+f1 - f6. When i login to Gnome i get back the ability to change to console mode with ctrl+alt

any ideas?

thanx

---

### Post by et2013 on 2006-06-06
You get any error messages ?
What does /var/log/Xorg.0.log say ?

---

### Post by ramcosca on 2006-06-06
Ok, I don't wanna thread jack, but what exactly does Ctrl + Alt + F1 do? Just open up a full-screen terminal? I, as a n00b to Linux, decided to investigate the use of those buttons and found no way of coming back into GNOME. How would I do that?

---

### Post by et2013 on 2006-06-06
CTRL+ALT+F<1-6> will open up a terminal session to tty<1-6>, it's something like a "full-screen terminal" in gnome. 

ctrl+alt+f7 will bring you back to gnome.

---

### Post by Dreaden on 2006-06-06
[QUOTE=subzero79]I am having problems to switch to consoles in the login windows with Ctrl+alt+f1 - f6. When i login to Gnome i get back the ability to change to console mode with ctrl+alt[/QUOTE]
I've got the reverse problem, while I'm in GDM, I can access my tty's, but once I'm in Gnome, it's disabled. (problem is located in my use of XGL, xgl-xserver started seperately after GDM)

[QUOTE=ramcosca]Ok, I don't wanna thread jack, but what exactly does Ctrl + Alt + F1 do? Just open up a full-screen terminal? I, as a n00b to Linux, decided to investigate the use of those buttons and found no way of coming back into GNOME. How would I do that?[/QUOTE]
you can go bach to gnome with ctrl+alt+F7 (or sometimes ctrl-alt-F8 ). 
You can use these virtual consoles if you've got problems with your X. (eg: the nvidia driver is broke, so you want to switch to 'nv').

---

### Post by subzero79 on 2006-06-06
[QUOTE=et2013]You get any error messages ?
What does /var/log/Xorg.0.log say ?[/QUOTE]

here goes Xorg.0.log

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux rbp 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  6 08:37:45 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "ViewSonic E7"
(**) |   |-->Device "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
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
(II) PCI: 00:00:0: chip 10de,005e card 1695,1011 rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1695,1011 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1695,1011 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1695,1011 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1695,1011 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1695,1011 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 1695,1011 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1695,1011 rev a3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 10de,cb84 rev a3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1695,1011 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:04:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:09:0: chip 1106,3044 card 0611,4430 rev 80 class 0c,00,10 hdr 00
(II) PCI: 05:00:0: chip 10de,0161 card 1043,81b3 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:9:0), (0,1,1), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:13:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[1] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[2] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[3] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfd900000 - 0xfd9fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xfd800000 - 0xfd8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:14:0), (0,5,5), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[1] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
	[2] -1	0	0x00006800 - 0x000068ff (0x100) IX[B]
	[3] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfcffffff (0x3000000) MX[B]
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
(--) PCI:*(5:0:0) nVidia Corporation GeForce 6200 TurboCache(TM) rev 161, Mem @ 0xfa000000/24, 0xd0000000/28, 0xfb000000/24
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
	[0] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[2] -1	0	0xfe029000 - 0xfe029fff (0x1000) MX[B]
	[3] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[4] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[8] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[12] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[13] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[15] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[16] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[17] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[18] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[27] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[28] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[2] -1	0	0xfe029000 - 0xfe029fff (0x1000) MX[B]
	[3] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[4] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[8] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[12] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[13] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[15] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[16] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[17] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[18] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[27] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[28] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
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
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[6] -1	0	0xfe029000 - 0xfe029fff (0x1000) MX[B]
	[7] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[8] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[33] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[34] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[35] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
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
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-8762  Mon May 15 13:08:07 PDT 2006
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
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[6] -1	0	0xfe029000 - 0xfe029fff (0x1000) MX[B]
	[7] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[8] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[33] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[34] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[35] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[6] -1	0	0xfe029000 - 0xfe029fff (0x1000) MX[B]
	[7] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[8] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[21] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[24] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[25] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[26] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[27] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[29] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[30] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[31] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[32] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[34] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[35] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[36] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[37] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[38] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[39] 0	0	0xfc0003b0 - 0xfc0003bb (0xc) IS[B]
	[40] 0	0	0xfc0003c0 - 0xfc0003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 TurboCache(TM) at PCI:5:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.02.11.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 TurboCache(TM) at
(--) NVIDIA(0):     PCI:5:0:0:
(--) NVIDIA(0):     ViewSonic E771-2 (CRT-0)
(--) NVIDIA(0): ViewSonic E771-2 (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): No size information available in CRT-0's EDID; cannot compute
(WW) NVIDIA(0):     DPI from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[8] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[9] -1	0	0xfe029000 - 0xfe029fff (0x1000) MX[B]
	[10] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[11] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[15] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[27] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[28] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[29] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[30] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[31] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[32] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[33] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[34] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[35] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[36] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[37] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[38] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[39] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[40] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[41] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[42] 0	0	0xfc0003b0 - 0xfc0003bb (0xc) IS[B]
	[43] 0	0	0xfc0003c0 - 0xfc0003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(**) NVIDIA(0): Option "BackingStore" "true"
(**) NVIDIA(0): Backing store enabled
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
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "es"
(**) Generic Keyboard: XkbLayout: "es"
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
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(WW) Couldn't load XKB keymap, falling back to pre-XKB keymap
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/X11/fonts/100dpi/:unscaled, removing from list!
Could not init font path element /usr/share/X11/fonts/75dpi/:unscaled, removing from list!
Could not init font path element /usr/share/X11/fonts/100dpi, removing from list!
Could not init font path element /usr/share/X11/fonts/75dpi, removing from list!
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!

```

at the end i see errors complaining about the font path

---

### Post by et2013 on 2006-06-06
[QUOTE=subzero79]here goes Xorg.0.log

Try to set the keyboard layout when you're in gnome : setxkbmap es if your keyboard is es ? And then hit ctrl+f1 and look at /var/log/messages to see if there's any error related to setkeycode or something like that.

---

### Post by ramcosca on 2006-06-06
[QUOTE=et2013]CTRL+ALT+F<1-6> will open up a terminal session to tty<1-6>, it's something like a "full-screen terminal" in gnome. 

ctrl+alt+f7 will bring you back to gnome.[/QUOTE]Thank you... [QUOTE=Dreaden]you can go bach to gnome with ctrl+alt+F7 (or sometimes ctrl-alt-F8 ). 
You can use these virtual consoles if you've got problems with your X. (eg: the nvidia driver is broke, so you want to switch to 'nv').[/QUOTE]And thank you... I love this community!

---

### Post by subzero79 on 2006-06-06
[QUOTE=et2013]

Try to set the keyboard layout when you're in gnome : setxkbmap es if your keyboard is es ? And then hit ctrl+f1 and look at /var/log/messages to see if there's any error related to setkeycode or something like that.[/QUOTE]

ok i'll see how it goes tonight (gmt -4). Currently i am not in my linux box.

thanx

PD: you mean ctrl+f1 or ctrl+alt+f1?

---

### Post by subzero79 on 2006-06-07
nope, i did't get any error.

any more ideas?

---

### Post by Joeb on 2006-06-07
Are you maybe using a logitech keyboard with extra functions mapped onto the function keys?  If so, I have found that you need to hit the special function lock key that is used to activate the special functions in Windows to get the regular functions to work in Linux.

---

### Post by subzero79 on 2006-06-07
[QUOTE=Joeb]Are you maybe using a logitech keyboard with extra functions mapped onto the function keys?  If so, I have found that you need to hit the special function lock key that is used to activate the special functions in Windows to get the regular functions to work in Linux.[/QUOTE]

nop, it is tipical generic keyboard, no more no less..

---

### Post by et2013 on 2006-06-08
[QUOTE=subzero79]I am having problems to switch to consoles in the login windows with Ctrl+alt+f1 - f6. When i login to Gnome i get back the ability to change to console mode with ctrl+alt

any ideas?

thanx[/QUOTE]

Do you mean you can't use ctrl+alt+f1 when you're at the (gdm)login screen and when you're logged in to gnome you can use the keys ?

Just wondering, but are you sure your keyboard layout is es and 105 keys ? Maybe try doing dpkg --recofigure xserver-xorg again and see what that does.

---

### Post by subzero79 on 2006-06-08
[QUOTE=et2013]Do you mean you can't use ctrl+alt+f1 when you're at the (gdm)login screen and when you're logged in to gnome you can use the keys ?[/QUOTE]

yes, that's right

[QUOTE=et2013]Just wondering, but are you sure your keyboard layout is es and 105 keys ? Maybe try doing dpkg --recofigure xserver-xorg again and see what that does.
[/QUOTE]

The thing is it worked everyday and suddenly it stopped worked. The xserver reconfigure didn't work at all.

---

### Post by et2013 on 2006-06-09
[QUOTE=subzero79]yes, that's right



The thing is it worked everyday and suddenly it stopped worked. The xserver reconfigure didn't work at all.[/QUOTE]

Found this while looking around : [http://wiki.archlinux.org/index.php/Xorg7#Keyboard_problems](http://wiki.archlinux.org/index.php/Xorg7#Keyboard_problems)
Do you have a file called .Xmodmap in your home dir ?

---

### Post by danderson3 on 2006-08-24
I cannot switch from X to a console with the ctrl+alt+fn combo;
I get a black full screen which does not respond.  This is true
for all six key combos.  ctrl+alt+f7 does return me to X.

I am running Dapper with a Matrox G450 video card and a Microsoft
Natural keyboard.  I have no Xmodmap file.

I see no relevant errors in syslog /var/log/messages.

any help debugging this would be appreciated...

thanks,
David

---

### Post by armware on 2006-09-10
> **danderson3 said:**
> I get a black full screen which does not respond.  This is true
for all six key combos.  ctrl+alt+f7 does return me to X.


i have the same issue, but i've been able to figure out a few things. it IS responsive, try logging in, and issuing the command sudo halt and type in your password. it'll shutdown your computer. basically this means it's a display issue, which may be related to the monitor settings. i assume this because when i plug in my crt (the machine is a laptop) i CAN get the terminal to show up. nothing changes, just the monitor. that's as far as i can get. any ideas to fix this?

---

### Post by LinuxRocks713 on 2008-05-04
> **et2013 said:**
> [QUOTE=subzero79]here goes Xorg.0.log

Try to set the keyboard layout when you're in gnome : setxkbmap es if your keyboard is es ? And then hit ctrl+f1 and look at /var/log/messages to see if there's any error related to setkeycode or something like that.

(not trying to thread bump...)

Thanks! that worked like a charm. I guess some buggy app decided to change the keyboard layout and cause the disablation.

---


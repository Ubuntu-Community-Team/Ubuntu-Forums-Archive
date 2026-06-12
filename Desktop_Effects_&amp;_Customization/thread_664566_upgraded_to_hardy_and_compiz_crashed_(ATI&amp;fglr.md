---
title: "upgraded to hardy and compiz crashed (ATI&amp;fglrx)"
date: 2008-01-11
forum: Desktop Effects &amp; Customization
---

### Post by hotgly on 2008-01-11
Just upgraded from Gusty to Hardy(alpha2 or alpha3? no idea, just from the deb source of hardy and no care) , and compiz is also upgraded to 0.6.99 &#65288;Compiz-fusion).
Ati Mobility Radeon 9600/9700 card with the latest fglrx driver in the Hardy repo (I think it's like the ATI Catalyst 7.11, and they work similarly).
Before upgrade, Gusty+ATI Catalyst 7.11, and compiz works well, every plugin can work.
After upgrade, Hardy+open source radeon driver, and compiz works well.
But:Hardy+ATI catalyst 7.11 or xorg-driver-fglrx 1:7.1.0-7-11 (similar as 7.11 and  support AIGLX), compiz effect unable to be enabled, and in the terminal run
```
compiz --replace
``` or
```
SKIP_CHECKS=yes compiz
```,same output:

```
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
......
[COLOR="Red"]/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0[/COLOR]
......

```
some more information

```
glxinfo | grep texture_from_pixmap 
```output:
```
GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap

```
 ```
cat /var/log/Xorg.0.log | grep AIGLX 
``` output:
```
(==) AIGLX enabled
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
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so

```

I think the problem is due to the three red line, but connot google up or figure out any resolution.Just even no idea it's a blame to fglrx or compiz,since both of them can do a good job in their specific environment. And besides compiz, no trouble with fglrx, and the full 3D acceleration (Googleearth) on fglrx is enjoyable.
Any idea? Thanks for any help.
:confused::confused::confused:

---

### Post by DavyDuke17 on 2008-01-11
Bump, I'm having the same problem.

---

### Post by SorinN on 2008-01-13
Exact the same problem.

Until Hardy upgrade  Compiz + FGLRX = OK

After Hardy Upgrade just FGLRX(7.11) 3D Acceleration OK, but no Compiz + ugly artifacts in the right bottom corner

After fglrx from AMD website (7.12) -> no ugly artifacts, no Compiz but 3D Acceleration

---

### Post by knewter on 2008-01-24
Bump.  Identical problem.  The output of my /var/log/Xorg.0.log:

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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080118-1ubuntu2)
Current Operating System: Linux john-galt 2.6.24-4-generic #1 SMP Mon Jan 14 18:19:11 UTC 2008 x86_64
Build Date: 19 January 2008  07:45:28PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 24 15:34:05 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
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
(II) Loader magic: 0x7bc660
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
(II) PCI: 00:00:0: chip 1002,7910 card 1179,ff10 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,7912 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 1002,7914 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 1002,7915 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 1002,7916 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4380 card 1179,ff10 rev 00 class 01,06,01 hdr 00
(II) PCI: 00:13:0: chip 1002,4387 card 1179,ff10 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4388 card 1179,ff10 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4389 card 1179,ff10 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:3: chip 1002,438a card 1179,ff10 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:4: chip 1002,438b card 1179,ff10 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:5: chip 1002,4386 card 1179,ff10 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4385 card 1179,ff10 rev 14 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,438c card 1179,ff10 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,4383 card 1179,ff0a rev 00 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,438d card 1179,ff10 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4384 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,791f card 1179,ff1a rev 00 class 03,00,00 hdr 00
(II) PCI: 08:00:0: chip 10ec,8136 card 1179,ff10 rev 01 class 02,00,00 hdr 00
(II) PCI: 14:06:0: chip 1180,0832 card 1179,ff10 rev 05 class 0c,00,10 hdr 80
(II) PCI: 14:06:1: chip 1180,0822 card 1179,ff10 rev 22 class 08,05,00 hdr 80
(II) PCI: 14:06:2: chip 1180,0592 card 1179,ff10 rev 12 class 08,80,00 hdr 80
(II) PCI: 14:06:3: chip 1180,0852 card 1179,ff10 rev 12 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,20), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf81fffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:4:0), (0,2,7), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 8: bridge is at (0:5:0), (0,8,13), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 8 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 8 non-prefetchable memory range:
	[0] -1	0	0xf8200000 - 0xf82fffff (0x100000) MX[B]
(II) Bus 8 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x880fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 14: bridge is at (0:6:0), (0,14,19), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 20: bridge is at (0:20:4), (0,20,25), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 20 non-prefetchable memory range:
	[0] -1	0	0xf8300000 - 0xf83fffff (0x100000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc Radeon X1200 Series rev 0, Mem @ 0xf0000000/27, 0xf8100000/16, 0xf8000000/20, I/O @ 0x9000/8
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
	[0] -1	0	0xf8301000 - 0xf83010ff (0x100) MX[B]
	[1] -1	0	0xf8300c00 - 0xf8300cff (0x100) MX[B]
	[2] -1	0	0xf8300800 - 0xf83008ff (0x100) MX[B]
	[3] -1	0	0xf8300000 - 0xf83007ff (0x800) MX[B]
	[4] -1	0	0xf8200000 - 0xf8200fff (0x1000) MX[B]
	[5] -1	0	0xf8600000 - 0xf8603fff (0x4000) MX[B]
	[6] -1	0	0xf8609400 - 0xf86094ff (0x100) MX[B]
	[7] -1	0	0xf8608000 - 0xf8608fff (0x1000) MX[B]
	[8] -1	0	0xf8607000 - 0xf8607fff (0x1000) MX[B]
	[9] -1	0	0xf8606000 - 0xf8606fff (0x1000) MX[B]
	[10] -1	0	0xf8605000 - 0xf8605fff (0x1000) MX[B]
	[11] -1	0	0xf8604000 - 0xf8604fff (0x1000) MX[B]
	[12] -1	0	0xf8609000 - 0xf86093ff (0x400) MX[B]
	[13] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B](B)
	[14] -1	0	0xf8100000 - 0xf810ffff (0x10000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[18] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[23] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[24] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[25] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[26] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[27] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[28] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf8301000 - 0xf83010ff (0x100) MX[B]
	[1] -1	0	0xf8300c00 - 0xf8300cff (0x100) MX[B]
	[2] -1	0	0xf8300800 - 0xf83008ff (0x100) MX[B]
	[3] -1	0	0xf8300000 - 0xf83007ff (0x800) MX[B]
	[4] -1	0	0xf8200000 - 0xf8200fff (0x1000) MX[B]
	[5] -1	0	0xf8600000 - 0xf8603fff (0x4000) MX[B]
	[6] -1	0	0xf8609400 - 0xf86094ff (0x100) MX[B]
	[7] -1	0	0xf8608000 - 0xf8608fff (0x1000) MX[B]
	[8] -1	0	0xf8607000 - 0xf8607fff (0x1000) MX[B]
	[9] -1	0	0xf8606000 - 0xf8606fff (0x1000) MX[B]
	[10] -1	0	0xf8605000 - 0xf8605fff (0x1000) MX[B]
	[11] -1	0	0xf8604000 - 0xf8604fff (0x1000) MX[B]
	[12] -1	0	0xf8609000 - 0xf86093ff (0x400) MX[B]
	[13] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B](B)
	[14] -1	0	0xf8100000 - 0xf810ffff (0x10000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[18] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[23] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[24] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[25] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[26] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[27] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[28] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
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
	[4] -1	0	0xf8301000 - 0xf83010ff (0x100) MX[B]
	[5] -1	0	0xf8300c00 - 0xf8300cff (0x100) MX[B]
	[6] -1	0	0xf8300800 - 0xf83008ff (0x100) MX[B]
	[7] -1	0	0xf8300000 - 0xf83007ff (0x800) MX[B]
	[8] -1	0	0xf8200000 - 0xf8200fff (0x1000) MX[B]
	[9] -1	0	0xf8600000 - 0xf8603fff (0x4000) MX[B]
	[10] -1	0	0xf8609400 - 0xf86094ff (0x100) MX[B]
	[11] -1	0	0xf8608000 - 0xf8608fff (0x1000) MX[B]
	[12] -1	0	0xf8607000 - 0xf8607fff (0x1000) MX[B]
	[13] -1	0	0xf8606000 - 0xf8606fff (0x1000) MX[B]
	[14] -1	0	0xf8605000 - 0xf8605fff (0x1000) MX[B]
	[15] -1	0	0xf8604000 - 0xf8604fff (0x1000) MX[B]
	[16] -1	0	0xf8609000 - 0xf86093ff (0x400) MX[B]
	[17] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B](B)
	[18] -1	0	0xf8100000 - 0xf810ffff (0x10000) MX[B](B)
	[19] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[24] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[29] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[30] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[31] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[32] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[33] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[34] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.45.4
	Module class: X.Org Video Driver
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
(II) v4l driver for Video4Linux
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.45.4
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.452.1                  
(II) ATI Proprietary Linux Driver Build Date: Jan 16 2008 10:43:31
(--) Chipset Supported AMD Graphics Processor (0x791F) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8301000 - 0xf83010ff (0x100) MX[B]
	[5] -1	0	0xf8300c00 - 0xf8300cff (0x100) MX[B]
	[6] -1	0	0xf8300800 - 0xf83008ff (0x100) MX[B]
	[7] -1	0	0xf8300000 - 0xf83007ff (0x800) MX[B]
	[8] -1	0	0xf8200000 - 0xf8200fff (0x1000) MX[B]
	[9] -1	0	0xf8600000 - 0xf8603fff (0x4000) MX[B]
	[10] -1	0	0xf8609400 - 0xf86094ff (0x100) MX[B]
	[11] -1	0	0xf8608000 - 0xf8608fff (0x1000) MX[B]
	[12] -1	0	0xf8607000 - 0xf8607fff (0x1000) MX[B]
	[13] -1	0	0xf8606000 - 0xf8606fff (0x1000) MX[B]
	[14] -1	0	0xf8605000 - 0xf8605fff (0x1000) MX[B]
	[15] -1	0	0xf8604000 - 0xf8604fff (0x1000) MX[B]
	[16] -1	0	0xf8609000 - 0xf86093ff (0x400) MX[B]
	[17] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B](B)
	[18] -1	0	0xf8100000 - 0xf810ffff (0x10000) MX[B](B)
	[19] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[24] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[29] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[30] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[31] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[32] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[33] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[34] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7f7a40
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8301000 - 0xf83010ff (0x100) MX[B]
	[5] -1	0	0xf8300c00 - 0xf8300cff (0x100) MX[B]
	[6] -1	0	0xf8300800 - 0xf83008ff (0x100) MX[B]
	[7] -1	0	0xf8300000 - 0xf83007ff (0x800) MX[B]
	[8] -1	0	0xf8200000 - 0xf8200fff (0x1000) MX[B]
	[9] -1	0	0xf8600000 - 0xf8603fff (0x4000) MX[B]
	[10] -1	0	0xf8609400 - 0xf86094ff (0x100) MX[B]
	[11] -1	0	0xf8608000 - 0xf8608fff (0x1000) MX[B]
	[12] -1	0	0xf8607000 - 0xf8607fff (0x1000) MX[B]
	[13] -1	0	0xf8606000 - 0xf8606fff (0x1000) MX[B]
	[14] -1	0	0xf8605000 - 0xf8605fff (0x1000) MX[B]
	[15] -1	0	0xf8604000 - 0xf8604fff (0x1000) MX[B]
	[16] -1	0	0xf8609000 - 0xf86093ff (0x400) MX[B]
	[17] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B](B)
	[18] -1	0	0xf8100000 - 0xf810ffff (0x10000) MX[B](B)
	[19] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[26] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[27] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[32] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[33] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[34] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[35] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[36] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[37] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 5 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "dri" "true"
(**) fglrx(0): Option "DPMS"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon X1200 Series" (Chipset = 0x791f)
(--) fglrx(0): (PciSubVendor = 0x1179, PciSubDevice = 0xff1a)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xf0000000
(--) fglrx(0): MMIO registers at 0xf8100000
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
(II) fglrx(0): VESA VBE OEM Software Rev: 10.55
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS690
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
	compiled for 7.1.0, module version = 8.45.4
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: PCI:1:5:0.
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(II) fglrx(0):  SAMSUNG
(II) fglrx(0):  LTN154X3-L06
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004ca3333600000000
(II) fglrx(0): 	000f0103802115780a87f594574f8c27
(II) fglrx(0): 	27505400000001010101010101010101
(II) fglrx(0): 	010101010101ee1a0080502010301030
(II) fglrx(0): 	13004bcf100000190000000f00000000
(II) fglrx(0): 	00000000002387026402000000fe0053
(II) fglrx(0): 	414d53554e470a2020202020000000fe
(II) fglrx(0): 	004c544e31353458332d4c30360a0070
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 10 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   68.94  1280 1296 1344 1408  768 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   68.94  1024 1296 1344 1408  768 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   68.94  800 1296 1344 1408  600 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   68.94  640 1296 1344 1408  480 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   68.94  640 1296 1344 1408  400 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   68.94  512 1296 1344 1408  384 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0   68.94  400 1296 1344 1408  300 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0   68.94  320 1296 1344 1408  240 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0   68.94  320 1296 1344 1408  200 801 804 816 +hsync +vsync (49.0 kHz)
(++) fglrx(0): DPI set to (100, 100)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   68.94  1280 1296 1344 1408  768 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   68.94  1024 1296 1344 1408  768 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   68.94  800 1296 1344 1408  600 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   68.94  640 1296 1344 1408  480 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   68.94  640 1296 1344 1408  400 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   68.94  512 1296 1344 1408  384 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0   68.94  400 1296 1344 1408  300 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0   68.94  320 1296 1344 1408  240 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0   68.94  320 1296 1344 1408  200 801 804 816 +hsync +vsync (49.0 kHz)
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
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pcie] 258048 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf8000000 - 0xf80fffff (0x100000) MX[B]
	[1] 0	0	0xf8100000 - 0xf810ffff (0x10000) MX[B]
	[2] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xf8301000 - 0xf83010ff (0x100) MX[B]
	[8] -1	0	0xf8300c00 - 0xf8300cff (0x100) MX[B]
	[9] -1	0	0xf8300800 - 0xf83008ff (0x100) MX[B]
	[10] -1	0	0xf8300000 - 0xf83007ff (0x800) MX[B]
	[11] -1	0	0xf8200000 - 0xf8200fff (0x1000) MX[B]
	[12] -1	0	0xf8600000 - 0xf8603fff (0x4000) MX[B]
	[13] -1	0	0xf8609400 - 0xf86094ff (0x100) MX[B]
	[14] -1	0	0xf8608000 - 0xf8608fff (0x1000) MX[B]
	[15] -1	0	0xf8607000 - 0xf8607fff (0x1000) MX[B]
	[16] -1	0	0xf8606000 - 0xf8606fff (0x1000) MX[B]
	[17] -1	0	0xf8605000 - 0xf8605fff (0x1000) MX[B]
	[18] -1	0	0xf8604000 - 0xf8604fff (0x1000) MX[B]
	[19] -1	0	0xf8609000 - 0xf86093ff (0x400) MX[B]
	[20] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B](B)
	[21] -1	0	0xf8100000 - 0xf810ffff (0x10000) MX[B](B)
	[22] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[26] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[29] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[30] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[31] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[32] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[33] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[36] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[37] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[38] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[39] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[40] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[41] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) [drm] DRM interface version 1.0
(II) [drm] DRM open master succeeded.
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [drm] installed DRM signal handler
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.45.4
(II) fglrx(0):     Date: Jan 16 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-4-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00005000
(II) fglrx(0): Interrupt handler installed at IRQ 18.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x78000000 FBMappedSize: 0x01004000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,3280)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 2480
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		19 256x256 slots
		5 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
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
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
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
Atom 4, CARD32 4, unsigned long 8
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
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
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

---

### Post by hardhu on 2008-01-24
I think this problem is due to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/173663](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/173663)

---

### Post by macaholic on 2008-01-24
It is because fglrx does not support the newer version of Xorg (1.4), which is in hardy. You can always check your Xorg version w/ Xorg -version.

---


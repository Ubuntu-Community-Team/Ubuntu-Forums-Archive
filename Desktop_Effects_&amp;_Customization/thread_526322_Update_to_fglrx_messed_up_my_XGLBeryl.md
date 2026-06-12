---
title: "Update to fglrx messed up my XGL/Beryl"
date: 2007-08-15
forum: Desktop Effects &amp; Customization
---

### Post by markdjones82 on 2007-08-15
Hi All,
  I am currently running Feisty Fawn with an ATI card using fglrx.  fglrx had an update last night that I ran and when I rebooted, it messed up video.  As soon as I login the screen has messed up horizontal lines over everything and it does not show up properly.

Now, if I choose gnome without xgl everything shows up fine.  Any suggestions what to check?

Also I used this guide to get my xgl and beryl working: [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

---

### Post by BucKao on 2007-08-15
The exact same thing happened to me when I installed the latest ATI proprietary driver from ATI's webpage.  I regressed to the version in the Ubuntu repositories, and now everything is fine again.  I would suggest you stick to the repository version, for now.

---

### Post by kellemes on 2007-08-15
Watch /var/log/Xorg.0.log for hints.

---

### Post by markdjones82 on 2007-08-16
> **BucKao said:**
> The exact same thing happened to me when I installed the latest ATI proprietary driver from ATI's webpage.  I regressed to the version in the Ubuntu repositories, and now everything is fine again.  I would suggest you stick to the repository version, for now.

I am not sure how to go back to the old driver exactly.  It was just in my software updates that needed to be done. And I believe it was from the repository.  I actually didn't get the driver from ATI

---

### Post by markdjones82 on 2007-08-17
This is what my xorg.log shows any help?

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux mark-ubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 17 17:31:52 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc ATI Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
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
(**) Extension "Composite" is disabled
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
(II) PCI: 00:00:0: chip 10de,03ea card 1043,8234 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,03e0 card 1043,8234 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,03eb card 1043,8234 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:01:2: chip 10de,03f5 card 1043,8234 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,03f1 card 1043,8234 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,03f2 card 1043,8234 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,03f3 card 0000,0000 rev a1 class 06,04,01 hdr 01
(II) PCI: 00:05:0: chip 10de,03f0 card 1043,8234 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:06:0: chip 10de,03ec card 1043,8234 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,03ef card 1043,8234 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:08:0: chip 10de,03f6 card 1043,8234 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:08:1: chip 10de,03f6 card 1043,8234 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:09:0: chip 10de,03e8 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 10de,03e9 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,03e9 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:0a:0: chip 14e4,4320 card 1737,0015 rev 03 class 02,80,00 hdr 00
(II) PCI: 02:00:0: chip 1002,71c1 card 174b,0840 rev 9e class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,71e1 card 174b,0841 rev 9e class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:4:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:9:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdff00000 - 0xdfffffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:11:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:12:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(2:0:0) ATI Technologies Inc unknown chipset (0x71c1) rev 158, Mem @ 0xc0000000/28, 0xdfff0000/16, I/O @ 0xe800/8, BIOS @ 0xdffc0000/17
(--) PCI: (2:0:1) ATI Technologies Inc unknown chipset (0x71e1) rev 158, Mem @ 0xdffe0000/16
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
	[0] -1	0	0xdfefe000 - 0xdfefffff (0x2000) MX[B]
	[1] -1	0	0xdfdf3000 - 0xdfdf3fff (0x1000) MX[B]
	[2] -1	0	0xdfdfc000 - 0xdfdfcfff (0x1000) MX[B]
	[3] -1	0	0xdfdfd000 - 0xdfdfdfff (0x1000) MX[B]
	[4] -1	0	0xdfdf8000 - 0xdfdfbfff (0x4000) MX[B]
	[5] -1	0	0xdfdfec00 - 0xdfdfecff (0x100) MX[B]
	[6] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[7] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[8] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[9] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[12] -1	0	0x0000c080 - 0x0000c083 (0x4) IX[B]
	[13] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[14] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[16] -1	0	0x0000c880 - 0x0000c88f (0x10) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[19] -1	0	0x0000d080 - 0x0000d083 (0x4) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[21] -1	0	0x0000d480 - 0x0000d487 (0x8) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[24] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfefe000 - 0xdfefffff (0x2000) MX[B]
	[1] -1	0	0xdfdf3000 - 0xdfdf3fff (0x1000) MX[B]
	[2] -1	0	0xdfdfc000 - 0xdfdfcfff (0x1000) MX[B]
	[3] -1	0	0xdfdfd000 - 0xdfdfdfff (0x1000) MX[B]
	[4] -1	0	0xdfdf8000 - 0xdfdfbfff (0x4000) MX[B]
	[5] -1	0	0xdfdfec00 - 0xdfdfecff (0x100) MX[B]
	[6] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[7] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[8] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[9] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[12] -1	0	0x0000c080 - 0x0000c083 (0x4) IX[B]
	[13] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[14] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[16] -1	0	0x0000c880 - 0x0000c88f (0x10) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[19] -1	0	0x0000d080 - 0x0000d083 (0x4) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[21] -1	0	0x0000d480 - 0x0000d487 (0x8) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[24] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B](B)
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
	[4] -1	0	0xdfefe000 - 0xdfefffff (0x2000) MX[B]
	[5] -1	0	0xdfdf3000 - 0xdfdf3fff (0x1000) MX[B]
	[6] -1	0	0xdfdfc000 - 0xdfdfcfff (0x1000) MX[B]
	[7] -1	0	0xdfdfd000 - 0xdfdfdfff (0x1000) MX[B]
	[8] -1	0	0xdfdf8000 - 0xdfdfbfff (0x4000) MX[B]
	[9] -1	0	0xdfdfec00 - 0xdfdfecff (0x100) MX[B]
	[10] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[11] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[12] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[13] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[18] -1	0	0x0000c080 - 0x0000c083 (0x4) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[20] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[22] -1	0	0x0000c880 - 0x0000c88f (0x10) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[25] -1	0	0x0000d080 - 0x0000d083 (0x4) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[27] -1	0	0x0000d480 - 0x0000d487 (0x8) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[30] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B](B)
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.33.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) ATI Radeon/FireGL: The following chipsets are supported:
	ATI MOBILITY RADEON X600 (M24 3150), ATI FireMV 2400 (M24 3151),
	ATI MOBILITY RADEON X300 (M22 (HP) 3152),
	ATI MOBILITY FireGL V3200 (M24 GL 3154),
	RADEON X600/X550 Series (RV380 3E50),
	ATI FireGL V3200 (RV380 GL 3E54), RADEON 9500 (RADEON 9500 4144),
	RADEON 9600TX (RADEON 9600TX 4146), ATI FireGL Z1 (FireGL Z1 4147),
	RADEON 9800 SE (RADEON 9800 SE 4148), RADEON 9500 (RADEON 9500 4149),
	ATI RADEON 9600 Series (RV350 4150),
	ATI RADEON 9600 Series (RV350 SE 4151),
	ATI RADEON 9600 Series (RV360 4152), ATI RADEON 9550 (RV350 LX 4153),
	ATI FireGL T2 (FireGL T2 4154),
	ATI RADEON 9600 Series (RV351 P 4155),
	RADEON X800 Series (R420 4A48 4A48),
	RADEON X800 PRO (R420 4A49 4A49), RADEON X800 Series (R420 SE 4A4A),
	RADEON X800 XT (R420 XT 4A4B), RADEON X800 Series (R420 4A4C 4A4C),
	ATI FireGL X3-256 (R420 GL 4A4D),
	ATI MOBILITY RADEON 9800 (M18-P 4A4E), RADEON X800 SE (R420 8P 4A4F),
	RADEON X800 XT Platinum Edition (R420 XT Platinum 4A50),
	RADEON X800 VE (R420 4P 4A54),
	ATI RADEON X850 Consumer (R481 4P 4B48),
	ATI RADEON X850 XT (R481 XT 4B49), ATI RADEON X850 SE (R481 SE 4B4A),
	ATI RADEON X850 PRO (R481 Pro 4B4B),
	ATI RADEON X850 XT Platinum Edition (R481 XT Platinum Edition 4B4C),
	RADEON 9700 PRO (RADEON 9700 PRO 4E44),
	RADEON 9500 PRO / 9700 (RADEON 9500 PRO / 9700 4E45),
	RADEON 9600 TX (RADEON 9600 4E46), ATI FireGL X1 (FireGL X1 4E47),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350LE 4E49),
	RADEON 9800 XT (R360 4E4A),
	ATI FireGL X2-256/X2-256t (FireGL X2 4E4B),
	ATI MOBILITY RADEON 9600/9700 Series (M10-P 4E50),
	ATI RADEON 9600 Series (RV350 LE 4E51),
	ATI MOBILITY RADEON 9500 (M11-CL 4E52),
	ATI MOBILITY FIRE GL T2/T2e (M10-GL 4E54),
	ATI MOBILITY RADEON 9550 (M12-P 4E56),
	ATI MOBILITY RADEON X300 (M22 5460),
	ATI MOBILITY RADEON X300 (M22T 5461),
	ATI MOBILITY RADEON X600 SE (M24-C 5462),
	ATI MOBILITY FireGL V3100 (M22 GL 5464),
	RADEON X800 Series (R423 5548), RADEON X800 GTO (R423 PRO 5549),
	RADEON X800 XT Platinum Edition (R423 XT Platinum 554A),
	RADEON X800 GT (R423 SE 554B), R430 XTP (R430 XTP 554C),
	ATI RADEON X800 XL (R430 XT 554D), ATI RADEON X800 GT (R430 SE 554E),
	RADEON X800 GTO (R430 PRO 554F), ATI FireGL V7100 (R423 GL XT 5550),
	ATI FireGL V5100 (R423 GL - PRO2 5551), R430 GL XT (R430 GL XT 5554),
	R430 GL PRO (R430 GL PRO 5555),
	ATI MOBILITY FireGL V5000 (M26-CSP128GL 564A),
	ATI MOBILITY FireGL V5000 (M26-GL 564B),
	Radeon X550/X700 Series (RV410 (564F) 564F),
	ATI MOBILITY RADEON X700 (M26-CSP128 5652),
	ATI MOBILITY RADEON X700 (M26-X 5653),
	Radeon X700 Series (RV410 (5657) 5657),
	ATI Radeon Xpress Series (RS480 5954 Generic 5954),
	ATI Radeon Xpress Series (RS480 5955 Generic 5955),
	ATI Radeon Xpress Series (RS482 5974 Generic 5974),
	ATI Radeon Xpress Series (RS482 5975 Generic 5975),
	ATI Radeon Xpress Series (RS400 5A41 Generic 5A41),
	ATI Radeon Xpress Series (RS400 5A42 Generic 5A42),
	ATI Radeon Xpress Series (RC410 5A61 Generic 5A61),
	ATI Radeon Xpress Series (RC410 5A62 Generic 5A62),
	RADEON X300/X550 Series (RV370 5B60),
	RADEON X600 Series (RV380 (X) 5B62), RADEON X550 (RV370 XT 5B63),
	ATI FireGL V3100 (RV370 GL V3100 5B64),
	ATI FireMV 2200 (RV370 FireMV 2200 5B65), RV370X (RV370X 5B66),
	ATI MOBILITY RADEON X800  XT (M28-XT 5D48),
	ATI MOBILITY FireGL V5100 (M28 GL 5D49),
	ATI MOBILITY RADEON X800 (M28-P 5D4A),
	R480 Consumer 4P (R480 Consumer 4P 5D4C),
	RADEON X850 XT Platinum Edition (R480 XTP 5D4D),
	RADEON X800 GTO (R480 PRO 5D4F), ATI FireGL V7200 (R480 GL 16P 5D50),
	R480 GL 12P (R480 GL 12P 5D51), RADEON X850 XT (R480 XT 5D52),
	RADEON X800 XT (R423 XT 5D57), ATI FireGL V5000 (RV410 GL - 8P 5E48),
	RADEON X700 XT (RV410 XT 5E4A), RADEON X700 PRO (RV410 PRO 5E4B),
	RADEON X700 SE (RV410 SE (5E4C) 5E4C), RADEON X700 (RV410 LE 5E4D),
	RADEON X700/X550 Series (RV410 SE (5E4F) 5E4F),
	Radeon X1800 Series (R520 7100),
	ATI Mobility Radeon X1800 XT (M58 16P 7101),
	ATI Mobility Radeon X1800 (M58 12P 7102),
	ATI MOBILITY FireGL V7200 (M58 GL 16P 7103),
	ATI FireGL V7200 (R520 GL 16P 7104),
	ATI FireGL V5300 (R520 GL 12P 7105),
	ATI MOBILITY FireGL V7100 (M58 GL 12P 7106),
	Radeon X1800 Series (R520 16P HiClk 7108),
	Radeon X1800 Series (R520 16P 7109),
	Radeon X1800 Series (R520 12P 710A),
	Radeon X1800 Series (R520 8P 710B),
	Radeon X1800 Series (R520 4P 710C),
	ATI FireGL V7300 (R520 GL 16P 528 MB 710E),
	ATI FireGL V7350 (R520 GL 16P 1 GB 710F),
	Radeon X1600 Series (RV515 XT 7140), RV505 (RV505 7141 7141),
	Radeon X1300 Series (RV515 PRO 7142),
	Radeon X1550 Series (RV505 7143 7143), M54-GL (M54-GL 7144),
	ATI Mobility Radeon X1400 (M54-P 7145),
	Radeon X1300 Series (RV515 LE 7146),
	Radeon X1550 64-bit (RV505 7147 7147),
	ATI Mobility Radeon X1300 (M52 7149),
	ATI Mobility Radeon X1300 (M52-T 714A),
	ATI Mobility Radeon X1300 (M52 714B 714B),
	ATI Mobility Radeon X1300 (M52 714C 714C),
	Radeon X1300 Series (RV515 714D 714D),
	Radeon X1300 Series (RV515LE PCI 714E), RV505 (RV505 714F 714F),
	RV505 (RV505 7151 7151), ATI FireGL V3300 (RV515 GL 7152),
	ATI FireGL V3350 (RV515 GL (7153) 7153),
	Radeon X1300 Series (RV515 VE 715E),
	Radeon X1550 64-bit (RV505 715F 715F),
	Radeon X1300 Series (RV516 7180 7180),
	Radeon X1600 Series (RV516 XT 7181),
	Radeon X1300 Series (RV516 7183 7183),
	ATI Mobility Radeon X1450 (M64P 7186),
	Radeon X1300 Series (RV516 7187 7187),
	ATI Mobility Radeon X2300 (M64S 7188),
	ATI Mobility Radeon X2300 (M64M 718A),
	ATI Mobility Radeon X1350 (M62P 718B),
	ATI Mobility Radeon X1350 (M62CSP64 718C),
	ATI Mobility Radeon X1450 (M64CSP128 718D),
	Radeon X1300 Series (RV516LE PCI 718F),
	Radeon X1550 Series (RV516 7193 7193),
	ATI Mobility Radeon X1350 (M62S 7196), ATI FireMV 2250 (RV516 719B),
	Radeon X1550 64-bit (RV516 719F 719F),
	Radeon X1600 Series (RV530 XT 71C0),
	Radeon X1650 Series (RV535 XT (71C1) 71C1),
	Radeon X1600 Series (RV530 PRO 71C2),
	Radeon X1600 Series (RV535 PRO (71C3) 71C3),
	ATI MOBILITY FireGL V5200 (M56 GL 71C4),
	ATI Mobility Radeon X1600 (M56-P 71C5),
	Radeon X1650 Series (RV530 XT2 71C6),
	Radeon X1650 Series (RV535 (71C7) 71C7),
	Radeon X1600 Series (RV530 71CD 71CD),
	Radeon X1300 Series (RV530 PRO2 71CE),
	ATI FireGL V3400 (RV530 GL 128 MB 71D2),
	ATI MOBILITY FireGL V5250 (M66 GL 71D4),
	ATI Mobility Radeon X1700 (M66-P 71D5),
	ATI Mobility Radeon X1700 XT (M66-XT 71D6),
	ATI FireGL V5200 (RV530 GL 256 MB 71DA),
	ATI Mobility Radeon X1700 (M66-M 71DE),
	Radeon X2300HD (RV550 7200 7200),
	Mobility Radeon X2300 HD (M71-M 7210),
	Mobility Radeon X2300 HD (M71-S 7211),
	Radeon X1950 Series (R580 7240 7240),
	Radeon X1900 Series (R580 7243 7243),
	Radeon X1950 Series (R580 7244 7244),
	Radeon X1900 Series (R580 7245 7245),
	Radeon X1900 Series (R580 7246 7246),
	Radeon X1900 Series (R580 7247 7247),
	Radeon X1900 Series (R580 7248 7248),
	Radeon X1900 Series (R580 7249 7249),
	Radeon X1900 Series (R580 724A 724A),
	Radeon X1900 Series (R580 724B 724B),
	Radeon X1900 Series (R580 724C 724C),
	Radeon X1900 Series (R580 724D 724D),
	ATI FireStream 2U (R580 724E 724E),
	Radeon X1900 Series (R580 724F 724F),
	Radeon X1950 Series (RV570 XT 7280),
	ATI Mobility Radeon X1900 (M68 7284), RV570 (RV570 7288 7288),
	RV570 (RV570 7289 7289), RV570 (RV570 728B 728B),
	ATI FireGL V7400 (RV570 GL 728C), RV560 (RV560 7290 7290),
	Radeon X1650 Series (RV560 XT 7291), RV560 (RV560 7293 7293),
	RV560 (RV560 7297 7297),
	ATI Radeon Xpress 1200 Series (RS600 7941 Generic 7941),
	ATI Radeon Xpress 1200 Series (RS600 7942 Generic 7942)
(II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.33.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.33g1                           
(II) ATI Proprietary Linux Driver Build Date: Jan  8 2007 23:27:29
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.33.2.1.2.3-driver-lnx-x86-x86_64-317595
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(--) Chipset Radeon X1650 Series (RV535 XT (71C1) 71C1) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfefe000 - 0xdfefffff (0x2000) MX[B]
	[5] -1	0	0xdfdf3000 - 0xdfdf3fff (0x1000) MX[B]
	[6] -1	0	0xdfdfc000 - 0xdfdfcfff (0x1000) MX[B]
	[7] -1	0	0xdfdfd000 - 0xdfdfdfff (0x1000) MX[B]
	[8] -1	0	0xdfdf8000 - 0xdfdfbfff (0x4000) MX[B]
	[9] -1	0	0xdfdfec00 - 0xdfdfecff (0x100) MX[B]
	[10] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[11] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[12] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[13] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[18] -1	0	0x0000c080 - 0x0000c083 (0x4) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[20] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[22] -1	0	0x0000c880 - 0x0000c88f (0x10) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[25] -1	0	0x0000d080 - 0x0000d083 (0x4) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[27] -1	0	0x0000d480 - 0x0000d487 (0x8) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[30] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e6550
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfefe000 - 0xdfefffff (0x2000) MX[B]
	[5] -1	0	0xdfdf3000 - 0xdfdf3fff (0x1000) MX[B]
	[6] -1	0	0xdfdfc000 - 0xdfdfcfff (0x1000) MX[B]
	[7] -1	0	0xdfdfd000 - 0xdfdfdfff (0x1000) MX[B]
	[8] -1	0	0xdfdf8000 - 0xdfdfbfff (0x4000) MX[B]
	[9] -1	0	0xdfdfec00 - 0xdfdfecff (0x100) MX[B]
	[10] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[11] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[12] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[13] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[21] -1	0	0x0000c080 - 0x0000c083 (0x4) IX[B]
	[22] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[23] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[25] -1	0	0x0000c880 - 0x0000c88f (0x10) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[28] -1	0	0x0000d080 - 0x0000d083 (0x4) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[30] -1	0	0x0000d480 - 0x0000d487 (0x8) IX[B]
	[31] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[32] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[33] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[35] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "Radeon X1650 Series (RV535 XT (71C1) 71C1)" (Chipset = 0x71c1)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x0840)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xdfff0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.13
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV535
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.33.6
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: CPQ  Model: 1349  Serial#: 1261647157
(II) fglrx(0): Year: 1998  Week: 49
(II) fglrx(0): EDID Version: 1.1
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 25
(II) fglrx(0): Gamma: 2.60
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): redX: 0.627 redY: 0.336   greenX: 0.279 greenY: 0.588
(II) fglrx(0): blueX: 0.143 blueY: 0.059   whiteX: 0.281 whiteY: 0.311
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 31.5 MHz   Image Size:  310 x 232 mm
(II) fglrx(0): h_active: 640  h_sync: 672  h_sync_end 736 h_blank_end 832 h_border: 0
(II) fglrx(0): v_active: 350  v_sync: 382  v_sync_end 385 v_blanking: 445 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz,
(II) fglrx(0): Serial No: 849CD34SK355
(II) fglrx(0): Monitor name: COMPAQ S700
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff000e1149133535334b
(II) fglrx(0): 	310801016c2119a0e88a82a056479624
(II) fglrx(0): 	0f484f256a0081806159455931590101
(II) fglrx(0): 	0101010101014e0c80c0205e5f102040
(II) fglrx(0): 	030836e81000001a000000fd0032a01e
(II) fglrx(0): 	46ff000a202020202020000000ff0038
(II) fglrx(0): 	343943443334534b3335350a000000fc
(II) fglrx(0): 	00434f4d50415120533730300a200019
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 594/395MHz @ 0Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 13 modes found for primary display.
(--) fglrx(0): Virtual size is 1024x768 (pitch 0)
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "720x576": 26.6 MHz (scaled from 0.0 MHz), 29.6 kHz, 50.0 Hz
(II) fglrx(0): Modeline "720x576"   26.56  720 736 808 896  576 577 580 593 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (330, 250) mm
(--) fglrx(0): DPI set to (78, 78)
(--) fglrx(0): Virtual size is 1024x768 (pitch 1024)
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "720x576": 26.6 MHz (scaled from 0.0 MHz), 29.6 kHz, 50.0 Hz
(II) fglrx(0): Modeline "720x576"   26.56  720 736 808 896  576 577 580 593 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfefe000 - 0xdfefffff (0x2000) MX[B]
	[7] -1	0	0xdfdf3000 - 0xdfdf3fff (0x1000) MX[B]
	[8] -1	0	0xdfdfc000 - 0xdfdfcfff (0x1000) MX[B]
	[9] -1	0	0xdfdfd000 - 0xdfdfdfff (0x1000) MX[B]
	[10] -1	0	0xdfdf8000 - 0xdfdfbfff (0x4000) MX[B]
	[11] -1	0	0xdfdfec00 - 0xdfdfecff (0x100) MX[B]
	[12] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[13] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[14] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[15] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[24] -1	0	0x0000c080 - 0x0000c083 (0x4) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[26] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[28] -1	0	0x0000c880 - 0x0000c88f (0x10) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[31] -1	0	0x0000d080 - 0x0000d083 (0x4) IX[B]
	[32] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[33] -1	0	0x0000d480 - 0x0000d487 (0x8) IX[B]
	[34] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[35] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[36] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[37] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[38] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:2:0:0
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
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7c3e000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7c3e000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x0ffe0000
(II) fglrx(0): Splitting WC range: base: 0xc0000000, size: 0xffe0000
(II) fglrx(0): Splitting WC range: base: 0xc8000000, size: 0x7fe0000
(II) fglrx(0): Splitting WC range: base: 0xcc000000, size: 0x3fe0000
(II) fglrx(0): Splitting WC range: base: 0xce000000, size: 0x1fe0000
(II) fglrx(0): Splitting WC range: base: 0xcf000000, size: 0xfe0000
(II) fglrx(0): Splitting WC range: base: 0xcf800000, size: 0x7e0000
(II) fglrx(0): Splitting WC range: base: 0xcfc00000, size: 0x3e0000
(II) fglrx(0): Splitting WC range: base: 0xcfe00000, size: 0x1e0000
(II) fglrx(0): Splitting WC range: base: 0xcff00000, size: 0xe0000
(II) fglrx(0): Splitting WC range: base: 0xcff80000, size: 0x60000
(==) fglrx(0): Write-combining range (0xcffc0000,0x20000)
(==) fglrx(0): Write-combining range (0xcff80000,0x60000)
(==) fglrx(0): Write-combining range (0xcff00000,0xe0000)
(==) fglrx(0): Write-combining range (0xcfe00000,0x1e0000)
(==) fglrx(0): Write-combining range (0xcfc00000,0x3e0000)
(==) fglrx(0): Write-combining range (0xcf800000,0x7e0000)
(==) fglrx(0): Write-combining range (0xcf000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xce000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xcc000000,0x3fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc8000000,0x7fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc0000000,0xffe0000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1024 x 7423
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(WW) fglrx(0): Textured Video not supported without DRI enabled.
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
(EE) AIGLX: Screen 0 is not DRI capable
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
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

---

### Post by markdjones82 on 2007-08-19
Anyone have a chance to look at my xorg.log and let me know why my XGL isn't working properly?  I copied that over after logging in without XGL if that effects anything.

I can get it to login, but the screen has horizontal lines all over the place and I can't make anything out.  This occured after an update to fglrx from the OS.

---

### Post by dgrafix on 2007-10-09
Im having the exact same on ati x2300 i created the xgl session and when i try and use it the screen is unreadable with lines everywhere.

> The exact same thing happened to me when I installed the latest ATI proprietary driver from ATI's webpage. I regressed to the version in the Ubuntu repositories, and now everything is fine again. I would suggest you stick to the repository version, for now.

How is this done??

---


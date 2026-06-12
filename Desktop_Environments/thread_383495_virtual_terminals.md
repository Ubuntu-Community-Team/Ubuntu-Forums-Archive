---
title: "virtual terminals"
date: 2007-03-13
forum: Desktop Environments
---

### Post by troughton on 2007-03-13
i did some updates a few days ago with no problem they were just standerd updates nothing big and just related to security of applications. they installed with no problem and did not require a restart.  when i restarted the computer the next day i booted into a blue screen saying my grahics had failed so i reinstalled the xorg-server and rebooted this got me back into ubunt grahics mode but i now have no vertuel terminals can anyone help ??/

---

### Post by daengbo on 2007-03-13
Please give some more information about your machine, including the output of uname -a and a tail of /var/log/Xorg.0.log

Just to be clear, is your problem that you can't switch to a VT using CTRL-ALT-F1 to F6 or that you get a blank screen when you do switch?

Thanks

---

### Post by troughton on 2007-03-14
when i press ALT-CTRL-F1 to F6 
the output from uname -a is Linux troughton-laptop 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux
the xorg.0.log is in attachment 
if you need to know anything else let me know its a compaq presario v6000 laptop

---

### Post by troughton on 2007-03-14
ok log not in attachment i will have to post it in two halfs as to meny charicters for 1 post and too big a file for an attachment 
log part 1 

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux troughton-laptop 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.[PHP]
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 14 15:05:22 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
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
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f0 card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 103c,30b7 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,0244 card 103c,30b7 rev a2 class 03,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0270 card 103c,30b7 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 103c,30b7 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 103c,30b7 rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:0a:3: chip 10de,0271 card 103c,30b7 rev a3 class 0b,40,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 103c,30b7 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 103c,30b7 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 103c,30b7 rev f1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 103c,30b7 rev f1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 103c,30b7 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 103c,30b7 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 03:00:0: chip 14e4,4312 card 103c,1361 rev 01 class 02,80,00 hdr 00
(II) PCI: 07:05:0: chip 1180,0832 card 103c,30b7 rev 00 class 0c,00,10 hdr 80
(II) PCI: 07:05:1: chip 1180,0822 card 103c,30b7 rev 19 class 08,05,00 hdr 80
(II) PCI: 07:05:2: chip 1180,0843 card 103c,30b7 rev 01 class 08,80,00 hdr 80
(II) PCI: 07:05:3: chip 1180,0592 card 103c,30b7 rev 0a class 08,80,00 hdr 80
(II) PCI: 07:05:4: chip 1180,0852 card 103c,30b7 rev 05 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xb3000000 - 0xb31fffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd01fffff (0x200000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:3:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xb3200000 - 0xb33fffff (0x200000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:16:0), (0,7,7), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xb3400000 - 0xb34fffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51 PCI Express Bridge rev 162, Mem @ 0xb2000000/24, 0xc0000000/28, 0xb1000000/24
(--) PCI: (0:10:3) nVidia Corporation MCP51 PMU rev 163, Mem @ 0xb0040000/18
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
	[0] -1	0	0xb3401400 - 0xb34014ff (0x100) MX[B]
	[1] -1	0	0xb3401000 - 0xb34010ff (0x100) MX[B]
	[2] -1	0	0xb3400c00 - 0xb3400cff (0x100) MX[B]
	[3] -1	0	0xb3400800 - 0xb34008ff (0x100) MX[B]
	[4] -1	0	0xb3400000 - 0xb34007ff (0x800) MX[B]
	[5] -1	0	0xb3200000 - 0xb3203fff (0x4000) MX[B]
	[6] -1	0	0xb0007000 - 0xb0007fff (0x1000) MX[B]
	[7] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[8] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[9] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[10] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[11] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[12] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[16] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[17] -1	0	0x000030a0 - 0x000030a3 (0x4) IX[B]
	[18] -1	0	0x000030a8 - 0x000030af (0x8) IX[B]
	[19] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[20] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[21] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[22] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[23] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[24] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xb3401400 - 0xb34014ff (0x100) MX[B]
	[1] -1	0	0xb3401000 - 0xb34010ff (0x100) MX[B]
	[2] -1	0	0xb3400c00 - 0xb3400cff (0x100) MX[B]
	[3] -1	0	0xb3400800 - 0xb34008ff (0x100) MX[B]
	[4] -1	0	0xb3400000 - 0xb34007ff (0x800) MX[B]
	[5] -1	0	0xb3200000 - 0xb3203fff (0x4000) MX[B]
	[6] -1	0	0xb0007000 - 0xb0007fff (0x1000) MX[B]
	[7] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[8] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[9] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[10] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[11] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[12] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[16] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[17] -1	0	0x000030a0 - 0x000030a3 (0x4) IX[B]
	[18] -1	0	0x000030a8 - 0x000030af (0x8) IX[B]
	[19] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[20] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[21] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[22] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[23] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[24] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
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
	[4] -1	0	0xb3401400 - 0xb34014ff (0x100) MX[B]
	[5] -1	0	0xb3401000 - 0xb34010ff (0x100) MX[B]
	[6] -1	0	0xb3400c00 - 0xb3400cff (0x100) MX[B]
	[7] -1	0	0xb3400800 - 0xb34008ff (0x100) MX[B]
	[8] -1	0	0xb3400000 - 0xb34007ff (0x800) MX[B]
	[9] -1	0	0xb3200000 - 0xb3203fff (0x4000) MX[B]
	[10] -1	0	0xb0007000 - 0xb0007fff (0x1000) MX[B]
	[11] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[12] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[13] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[14] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[15] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[16] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[22] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[23] -1	0	0x000030a0 - 0x000030a3 (0x4) IX[B]
	[24] -1	0	0x000030a8 - 0x000030af (0x8) IX[B]
	[25] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[26] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[27] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[28] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[29] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[30] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
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
	GeForce Go 6150, GeForce Go 6100[PHP][PHP][/PHP][/PHP][/PHP]

---

### Post by troughton on 2007-03-14
part 2
 [PHP](II) Primary Device is: PCI 00:05:0
(WW) NV: No matching Device section for instance (BusID PCI:0:10:3) found
(--) Chipset GeForce Go 6150 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb3401400 - 0xb34014ff (0x100) MX[B]
	[5] -1	0	0xb3401000 - 0xb34010ff (0x100) MX[B]
	[6] -1	0	0xb3400c00 - 0xb3400cff (0x100) MX[B]
	[7] -1	0	0xb3400800 - 0xb34008ff (0x100) MX[B]
	[8] -1	0	0xb3400000 - 0xb34007ff (0x800) MX[B]
	[9] -1	0	0xb3200000 - 0xb3203fff (0x4000) MX[B]
	[10] -1	0	0xb0007000 - 0xb0007fff (0x1000) MX[B]
	[11] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[12] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[13] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[14] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[15] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[16] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[22] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[23] -1	0	0x000030a0 - 0x000030a3 (0x4) IX[B]
	[24] -1	0	0x000030a8 - 0x000030af (0x8) IX[B]
	[25] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[26] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[27] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[28] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[29] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[30] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb3401400 - 0xb34014ff (0x100) MX[B]
	[5] -1	0	0xb3401000 - 0xb34010ff (0x100) MX[B]
	[6] -1	0	0xb3400c00 - 0xb3400cff (0x100) MX[B]
	[7] -1	0	0xb3400800 - 0xb34008ff (0x100) MX[B]
	[8] -1	0	0xb3400000 - 0xb34007ff (0x800) MX[B]
	[9] -1	0	0xb3200000 - 0xb3203fff (0x4000) MX[B]
	[10] -1	0	0xb0007000 - 0xb0007fff (0x1000) MX[B]
	[11] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[12] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[13] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[14] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[15] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[16] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[25] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[26] -1	0	0x000030a0 - 0x000030a3 (0x4) IX[B]
	[27] -1	0	0x000030a8 - 0x000030af (0x8) IX[B]
	[28] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[29] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[30] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[31] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[32] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[33] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce Go 6150"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xC0000000
(--) NV(0): MMIO registers at 0xB2000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
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
(--) NV(0): VideoRAM: 32768 kBytes
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
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(==) NV(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xb3401400 - 0xb34014ff (0x100) MX[B]
	[8] -1	0	0xb3401000 - 0xb34010ff (0x100) MX[B]
	[9] -1	0	0xb3400c00 - 0xb3400cff (0x100) MX[B]
	[10] -1	0	0xb3400800 - 0xb34008ff (0x100) MX[B]
	[11] -1	0	0xb3400000 - 0xb34007ff (0x800) MX[B]
	[12] -1	0	0xb3200000 - 0xb3203fff (0x4000) MX[B]
	[13] -1	0	0xb0007000 - 0xb0007fff (0x1000) MX[B]
	[14] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[15] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[16] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[17] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[18] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[19] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[28] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[29] -1	0	0x000030a0 - 0x000030a3 (0x4) IX[B]
	[30] -1	0	0x000030a8 - 0x000030af (0x8) IX[B]
	[31] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[32] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[33] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[34] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[35] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[36] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xc0000000,0x2000000)
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
(==) RandR enabled
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
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "uk"
(**) Generic Keyboard: XkbLayout: "uk"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
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
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
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
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+uk+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
ProcXCloseDevice to close or not ?
[/PHP]

---


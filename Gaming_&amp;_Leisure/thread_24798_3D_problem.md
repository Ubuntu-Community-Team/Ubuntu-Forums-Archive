---
title: "3D problem"
date: 2005-04-08
forum: Gaming &amp; Leisure
---

### Post by wxm505 on 2005-04-08
After I upgraded from Warty to hoary.Tuxracer ran bloody slowly.
And the CPU in use came to 100% one second after I ran the game.
It worked very well under Warty. What is the problem??
Any help?? Cheers

---

### Post by fackamato on 2005-04-08
[QUOTE=wxm505]After I upgraded from Warty to hoary.Tuxracer ran bloody slowly.
And the CPU in use came to 100% one second after I ran the game.
It worked very well under Warty. What is the problem??
Any help?? Cheers[/QUOTE]

check your gfx drivers.

---

### Post by wxm505 on 2005-04-08
[QUOTE=fackamato]check your gfx drivers.[/QUOTE]
Sorry I am quite new with ubuntu. How to do this??

---

### Post by p!=f on 2005-04-08
What's your graphic card?

---

### Post by wxm505 on 2005-04-08
[QUOTE=p!=f]What's your graphic card?[/QUOTE]
I am using a Toshiba laptop A30
the grapics card is intel 82852/855GM onboard card.
It share the memory with main memory.
It worked well under warty but hoary.

---

### Post by p!=f on 2005-04-08
Please take a look at /etc/X11/xorg.conf section "Device" and post it here.
i810 is the driver your card should be using.
There's also [Intel's driver](http://downloadfinder.intel.com/scripts-df/filter_results.asp?strOSs=39&strTypes=DRV%2CARC&ProductID=922&OSFullName=Linux*&submit=Go%21) but you will have to compile it yourself. Help available. :)

---

### Post by wxm505 on 2005-04-08
[QUOTE=p!=f]Please take a look at /etc/X11/xorg.conf section "Device" and post it here.
i810 is the driver your card should be using.
There's also [Intel's driver](http://downloadfinder.intel.com/scripts-df/filter_results.asp?strOSs=39&strTypes=DRV%2CARC&ProductID=922&OSFullName=Linux*&submit=Go%21) but you will have to compile it yourself. Help available. :)[/QUOTE]
I think the driver is all right though.

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

I guess that there is something wrong about the display setting of gnome
because when I ran some applications the display windows are much bigger
than they showed under warty.
E.g: Gaim is running well but the window of skype is twice bigger than the 
original one. The window and fonts of Kget is ugly too ,very big.
Any idea??
Thanks a lot mate :)

---

### Post by wxm505 on 2005-04-08
any help???

---

### Post by fackamato on 2005-04-08
Please post the xorg log in /var/log .

---

### Post by wxm505 on 2005-04-09
[QUOTE=fackamato]Please post the xorg log in /var/log .[/QUOTE]

X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.10-5-686 #1 Tue Apr 5 12:27:02 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-686 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:27:02 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr  9 10:39:19 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel Corporation 82852/855GM Integrated Graphics Device"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "gb"
(**) XKB: layout: "gb"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,
/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,
/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
(II) PCI: 00:00:0: chip 8086,3580 card 1179,ff00 rev 02 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 8086,3584 card 1179,ff00 rev 02 class 08,80,00 hdr 00
(II) PCI: 00:00:3: chip 8086,3585 card 1179,ff00 rev 02 class 08,80,00 hdr 80
(II) PCI: 00:02:0: chip 8086,3582 card 1179,ff00 rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,3582 card 1179,ff00 rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1d:0: chip 8086,24c2 card 1179,ff00 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1179,ff00 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1179,ff00 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1179,ff00 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 83 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 1179,ff00 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1179,ff00 rev 03 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1179,ff00 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1179,0001 rev 03 class 07,03,00 hdr 00
(II) PCI: 02:00:0: chip 1106,3044 card 1106,3044 rev 80 class 0c,00,10 hdr 00
(II) PCI: 02:01:0: chip 10ec,8139 card 1179,ff00 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1524,1410 card 4000,0000 rev 01 class 06,07,00 hdr 02
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
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe0200000 - 0xe02fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:4:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(--) PCI:*(0:2:0) Intel Corp. 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xe8000000/27, 0xe0000000/19, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corp. 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xf0000000/27, 0xe0080000/19
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
(II) Active PCI resource ranges:
	[0] -1	0	0xe0200800 - 0xe02008ff (0x100) MX[B]
	[1] -1	0	0xe0200000 - 0xe02007ff (0x800) MX[B]
	[2] -1	0	0xe0100800 - 0xe01008ff (0x100) MX[B]
	[3] -1	0	0xe0100c00 - 0xe0100dff (0x200) MX[B]
	[4] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[5] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[6] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[7] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[11] -1	0	0x00003400 - 0x0000347f (0x80) IX[B]
	[12] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[13] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[14] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[15] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[16] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[17] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[18] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[19] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[20] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[21] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe0200800 - 0xe02008ff (0x100) MX[B]
	[1] -1	0	0xe0200000 - 0xe02007ff (0x800) MX[B]
	[2] -1	0	0xe0100800 - 0xe01008ff (0x100) MX[B]
	[3] -1	0	0xe0100c00 - 0xe0100dff (0x200) MX[B]
	[4] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[5] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[6] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[7] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[11] -1	0	0x00003400 - 0x0000347f (0x80) IX[B]
	[12] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[13] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[14] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[15] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[16] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[17] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[18] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[19] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[20] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[21] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe0200800 - 0xe02008ff (0x100) MX[B]
	[6] -1	0	0xe0200000 - 0xe02007ff (0x800) MX[B]
	[7] -1	0	0xe0100800 - 0xe01008ff (0x100) MX[B]
	[8] -1	0	0xe0100c00 - 0xe0100dff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[11] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[14] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[18] -1	0	0x00003400 - 0x0000347f (0x80) IX[B]
	[19] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[20] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[21] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[23] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[24] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[25] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[26] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[27] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[28] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(WW) Ignoring request to load module GLcore
(WW) Ignoring request to load module speedo
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
(II) LoadModule: "v4l"
(II) Loading /usr/X11R6/lib/modules/drivers/linux/v4l_drv.o
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.0.1
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "i810"
(II) Loading /usr/X11R6/lib/modules/drivers/i810_drv.o
(II) Module i810: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.3.0
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
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) v4l driver for Video4Linux
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, 915GM
(II) Primary Device is: PCI 00:02:0
(--) Chipset 852GM/855GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe0200800 - 0xe02008ff (0x100) MX[B]
	[6] -1	0	0xe0200000 - 0xe02007ff (0x800) MX[B]
	[7] -1	0	0xe0100800 - 0xe01008ff (0x100) MX[B]
	[8] -1	0	0xe0100c00 - 0xe0100dff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[11] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[14] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[18] -1	0	0x00003400 - 0x0000347f (0x80) IX[B]
	[19] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[20] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[21] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[23] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[24] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[25] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[26] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[27] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[28] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe0200800 - 0xe02008ff (0x100) MX[B]
	[6] -1	0	0xe0200000 - 0xe02007ff (0x800) MX[B]
	[7] -1	0	0xe0100800 - 0xe01008ff (0x100) MX[B]
	[8] -1	0	0xe0100c00 - 0xe0100dff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[11] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[14] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[15] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[21] -1	0	0x00003400 - 0x0000347f (0x80) IX[B]
	[22] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[23] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[24] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[25] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[26] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[27] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[28] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[29] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[30] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[31] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[32] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 32576 kB
(II) I810(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 852GME
(--) I810(0): Chipset: "852GM/855GM"
(--) I810(0): Linear framebuffer at 0xE8000000
(--) I810(0): IO registers at addr 0xE0000000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 32636 kB stolen memory.
(II) I810(0): I830CheckAvailableMemory: 672764 kB available
(II) I810(0): Checking Lid status enabled
(--) I810(0): Pre-allocated VideoRAM: 32636 kByte
(==) I810(0): VideoRAM: 32768 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 2991
(==) I810(0): Device Presence: disabled.
(WW) I810(0): Primary Pipe is B, switching off second monitor (0x800)
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: TRUE, size: (800,600)
(II) I810(0): Display Info: TV: attached: FALSE, present: TRUE, size: (800,600)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1024,768)
(II) I810(0): Display Info: CRT2 (second CRT): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Size of device LFP (local flat panel) is 1024 x 768
(II) I810(0): No active displays on Pipe A.
(II) I810(0): Currently active displays on Pipe B:
(II) I810(0): 	LFP (local flat panel)
(II) I810(0): Lowest common panel size for pipe B is 1024 x 768
(==) I810(0): Display is using Pipe B
(--) I810(0): Maximum frambuffer space: 32600 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) I810(0): VESA VBE PanelID read successfully
(II) I810(0): PanelID returned panel resolution : 1024x768
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(--) I810(0): Maximum space available for video modes: 32576 kByte
Mode: 30 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
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
	NumberOfImages: 100
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 100
	LinNumberOfImagePages: 100
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 32 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 71
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 71
	LinNumberOfImagePages: 71
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 34 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 41
	LinNumberOfImagePages: 41
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 38 (1280x1024)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3a (1600x1200)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3c (1920x1440)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 1920
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1920
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 41 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 55
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 55
	LinNumberOfImagePages: 55
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000

---

### Post by wxm505 on 2005-04-09
Followed
Mode: 43 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 32
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 32
	LinNumberOfImagePages: 32
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 45 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 20
	LinNumberOfImagePages: 20
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 49 (1280x1024)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4b (1600x1200)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4d (1920x1440)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 50 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 25
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 25
	LinNumberOfImagePages: 25
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 52 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 54 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 58 (1280x1024)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 5a (1600x1200)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 5c (1920x1440)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 7680
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 7680
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 7c (1024x600)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 55
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 55
	LinNumberOfImagePages: 55
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 7d (1024x600)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 25
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 25
	LinNumberOfImagePages: 25
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 7e (1024x600)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007033
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
(II) I810(0): Generic Monitor: Using hsync range of 28.00-49.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 43.00-72.00 Hz
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(==) I810(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/X11R6/lib/modules/libshadow.a
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 1	0	0xe0000000 - 0xe007ffff (0x80000) MS[B]
	[1] 1	0	0xe8000000 - 0xefffffff (0x8000000) MS[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe0200800 - 0xe02008ff (0x100) MX[B]
	[8] -1	0	0xe0200000 - 0xe02007ff (0x800) MX[B]
	[9] -1	0	0xe0100800 - 0xe01008ff (0x100) MX[B]
	[10] -1	0	0xe0100c00 - 0xe0100dff (0x200) MX[B]
	[11] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[12] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[13] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[14] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[16] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[17] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] 1	0	0x00001800 - 0x00001807 (0x8) IS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[24] -1	0	0x00003400 - 0x0000347f (0x80) IX[B]
	[25] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[26] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[27] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[28] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[29] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[30] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[31] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[32] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[33] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[34] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[35] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 1	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 32576 kB
(II) I810(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(==) I810(0): Default visual is TrueColor
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 512 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 5120 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0x7fff000 (0x2b38a000)
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0x7ffb000 (0x2b3dc000)
(II) I810(0): Allocated 4 kB for Overlay registers at 0x7ffa000 (0x2b391000).
(II) I810(0): Allocated 64 kB for the scratch buffer at 0x7fea000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) I810(0): [drm] loaded kernel module for "i915" driver
(II) I810(0): [drm] DRM interface version 1.2
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [drm] added 8192 byte SAREA at 0xeeca4000
(II) I810(0): [drm] mapped SAREA 0xeeca4000 to 0xb7d6d000
(II) I810(0): [drm] framebuffer handle = 0xe8020000
(II) I810(0): [drm] added 1 reserved context for kernel
(II) I810(0): Allocated 8060 kB for the back buffer at 0xffc21000.
(II) I810(0): Allocated 4096 kB for the depth buffer at 0xff421000.
(II) I810(0): Allocated 32 kB for the logical context at 0x7fe2000.
(II) I810(0): Allocated 15232 kB for textures at 0xfe541000
(II) I810(0): Updated framebuffer allocation size from 5120 to 5132 kByte
(II) I810(0): Updated pixmap cache from 512 scanlines to 515 scanlines
(II) I810(0): 0x82e63e8: Memory at offset 0x00020000, size 5132 kBytes
(II) I810(0): 0x83c1a48: Memory at offset 0x07fff000, size 4 kBytes
(II) I810(0): 0x8616c90: Memory at offset 0x07ffb000, size 16 kBytes
(II) I810(0): 0x835e8a4: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x82e6428: Memory at offset 0x07fea000, size 64 kBytes
(II) I810(0): 0x8553a30: Memory at offset 0x07ffa000, size 4 kBytes
(II) I810(0): 0x82e6478: Memory at offset 0x01c03000, size 3964 kBytes
(II) I810(0): 0x82e6498: Memory at offset 0x01403000, size 4096 kBytes
(II) I810(0): 0x82e64d8: Memory at offset 0x07fe2000, size 32 kBytes
(II) I810(0): 0x82e64b8: Memory at offset 0x00523000, size 15232 kBytes
(--) SetFence: 0: start (0x01c03000) is not 512k aligned
(II) I810(0): Activating tiled memory for the back buffer.
(--) SetFence: 1: start (0x01403000) is not 512k aligned
(II) I810(0): Activating tiled memory for the depth buffer.
(II) I810(0): [drm] Registers = 0xe0000000
(II) I810(0): [drm] Back Buffer = 0xe9c03000
(II) I810(0): [drm] Depth Buffer = 0xe9403000
(II) I810(0): [drm] ring buffer = 0xe8000000
(II) I810(0): [drm] textures = 0xe8523000
(II) I810(0): [drm] dma control initialized, using IRQ 16
(II) I810(0): [drm] Initialized kernel agp heap manager, 15597568
(II) I810(0): [dri] visual configs initialized
(==) I810(0): Write-combining range (0xe8000000,0x8000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x01fdf000 (pgoffset 8159)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x07fff000 (pgoffset 32767)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x07ffb000 (pgoffset 32763)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x07fea000 (pgoffset 32746)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x07ffa000 (pgoffset 32762)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x07fe2000 (pgoffset 32738)
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): LFP compensation mode: 0x6
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): X context handle = 0x00000001
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
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
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
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
(II) Synaptics touchpad driver version 0.13.6
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
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

Any idea?? cheers

---

### Post by wxm505 on 2005-04-09
Any help ? Thanks a lot
Any idea??

---

### Post by wxm505 on 2005-04-20
any idea???

---


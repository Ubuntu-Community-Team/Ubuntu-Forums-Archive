---
title: "X will not start"
date: 2005-10-27
forum: Desktop Environments
---

### Post by Protostar on 2005-10-27
Hello all. I'm am having some problems with Ubuntu. I downloaded the final release version of Ubuntu and installed it. I had to install it using special parameters like VGA 771 and disabling ACPI/LACPI before the installation would continue. I finally got it installed and rebooted and X would not start. I got a whole bunch of errors and am trying to figure out what to do. I know you will need the output for these errors before you can help me, so I need to know the command sequence necessary to pipe the errors from the X server into a text file so I can post it. I had the same issue with Kubuntu and thought that it had something to do with KDE. I also had the prerelease version of Breezy installed and it worked fine. When I installed a bunch of updates, it gave me these errors. BTW, when I was installing Ubuntu I made the swap space bootable. Can this cause any problems? If so, how do I make it unbootable?

My Computer Specs:

HP Pavilion zd8000 laptop
2.8Ghz P4
512 MB DDR Ram
ATI X600 dedicated graphics chipset

Thanks in Advance,

Proto

---

### Post by Ampersand on 2005-10-27
Hi
The errors should be in /var/log/Xorg.0.log, if you look for the lines in that starting with (EE), it should say where the error is.

Generally with X problems, quite a few can be solved by running

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by DarthStygeon on 2005-10-27
Ive been having the same problem with this. I have sucessfully installed hoary on another desktop by luck i guess. im a noob to linux and need to get my dual boot machin up.:confused:

---

### Post by Ampersand on 2005-10-27
I'd suggest the same thing to start with. Try a 
```
sudo dpkg-reconfigure xserver-xorg
```
if you haven't already, and

```
cat /var/log/Xorg.0.log | less 
```

making note of any lines starting with (EE). You should be able to scroll through the output from the second command using the arrow keys.

---

### Post by Protostar on 2005-10-27
I tried the reconfigure Xserver command and it still won't work. I did however copy the X log to my external HD so I could post it. I have no idea what any of it means though.:confused: 

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux Protostar 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 27 21:30:44 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Mobility X600 (M24)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2580 card 103c,3082 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2581 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 103c,3082 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 103c,3082 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 103c,3082 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 103c,3082 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 103c,3082 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d3 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,266e card 103c,3082 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1e:3: chip 8086,266d card 103c,3082 rev 03 class 07,03,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,2640 card 103c,3082 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 103c,3082 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 103c,3082 rev 03 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,3150 card 103c,3082 rev 00 class 03,00,00 hdr 00
(II) PCI: 0b:00:0: chip 104c,8031 card 5400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 0b:00:2: chip 104c,8032 card 103c,3082 rev 00 class 0c,00,10 hdr 80
(II) PCI: 0b:00:3: chip 104c,8033 card 103c,3082 rev 00 class 01,80,00 hdr 80
(II) PCI: 0b:00:4: chip 104c,8034 card 103c,3082 rev 00 class 08,05,00 hdr 80
(II) PCI: 0b:02:0: chip 10ec,8139 card 103c,3082 rev 10 class 02,00,00 hdr 00
(II) PCI: 0b:03:0: chip 14e4,4320 card 103c,12f8 rev 03 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,12), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc8100000 - 0xc81fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:30:0), (0,11,13), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 11 I/O range:
	[0] -1	0	0x00005000 - 0x00005fff (0x1000) IX[B]
(II) Bus 11 non-prefetchable memory range:
	[0] -1	0	0xc8200000 - 0xc82fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 12: bridge is at (11:0:0), (11,12,15), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 12 I/O range:
	[0] -1	0	0x00005400 - 0x000054ff (0x100) IX[B]
	[1] -1	0	0x00005800 - 0x000058ff (0x100) IX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x3150) rev 0, Mem @ 0xd0000000/27, 0xc8100000/16, I/O @ 0x4000/8
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
	[0] -1	0	0xc8209400 - 0xc82094ff (0x100) MX[B]
	[1] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[2] -1	0	0xc8208000 - 0xc82087ff (0x800) MX[B]
	[3] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[4] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[5] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[6] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[9] -1	0	0x00003c20 - 0x00003c3f (0x20) IX[B]
	[10] -1	0	0x00003c40 - 0x00003c4f (0x10) IX[B]
	[11] -1	0	0x00003800 - 0x0000387f (0x80) IX[B]
	[12] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[13] -1	0	0x00003880 - 0x000038bf (0x40) IX[B]
	[14] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[15] -1	0	0x00003c00 - 0x00003c1f (0x20) IX[B]
	[16] -1	0	0x000038e0 - 0x000038ff (0x20) IX[B]
	[17] -1	0	0x000038c0 - 0x000038df (0x20) IX[B]
	[18] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[19] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[1] -1	0	0xc8208800 - 0xc82088ff (0x100) MX[B]
	[2] -1	0	0xc8208c00 - 0xc8208cff (0x100) MX[B]
	[3] -1	0	0xc8209000 - 0xc82090ff (0x100) MX[B]
	[4] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc8209400 - 0xc82094ff (0x100) MX[B]
	[1] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[2] -1	0	0xc8208000 - 0xc82087ff (0x800) MX[B]
	[3] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[4] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[5] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[6] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[9] -1	0	0x00003c20 - 0x00003c3f (0x20) IX[B]
	[10] -1	0	0x00003c40 - 0x00003c4f (0x10) IX[B]
	[11] -1	0	0x00003800 - 0x0000387f (0x80) IX[B]
	[12] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[13] -1	0	0x00003880 - 0x000038bf (0x40) IX[B]
	[14] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[15] -1	0	0x00003c00 - 0x00003c1f (0x20) IX[B]
	[16] -1	0	0x000038e0 - 0x000038ff (0x20) IX[B]
	[17] -1	0	0x000038c0 - 0x000038df (0x20) IX[B]
	[18] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[19] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[1] -1	0	0xc8208800 - 0xc82088ff (0x100) MX[B]
	[2] -1	0	0xc8208c00 - 0xc8208cff (0x100) MX[B]
	[3] -1	0	0xc8209000 - 0xc82090ff (0x100) MX[B]
	[4] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
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
	[5] -1	0	0xc8209400 - 0xc82094ff (0x100) MX[B]
	[6] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[7] -1	0	0xc8208000 - 0xc82087ff (0x800) MX[B]
	[8] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[9] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[10] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[11] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[14] -1	0	0xc8208800 - 0xc82088ff (0x100) MX[B]
	[15] -1	0	0xc8208c00 - 0xc8208cff (0x100) MX[B]
	[16] -1	0	0xc8209000 - 0xc82090ff (0x100) MX[B]
	[17] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[21] -1	0	0x00003c20 - 0x00003c3f (0x20) IX[B]
	[22] -1	0	0x00003c40 - 0x00003c4f (0x10) IX[B]
	[23] -1	0	0x00003800 - 0x0000387f (0x80) IX[B]
	[24] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[25] -1	0	0x00003880 - 0x000038bf (0x40) IX[B]
	[26] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[27] -1	0	0x00003c00 - 0x00003c1f (0x20) IX[B]
	[28] -1	0	0x000038e0 - 0x000038ff (0x20) IX[B]
	[29] -1	0	0x000038c0 - 0x000038df (0x20) IX[B]
	[30] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[31] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
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
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
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
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon Mobility X600 (M24)".
(--) Chipset ATI Radeon Mobility X600 (M24) 3150 (PCIE) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xc8209400 - 0xc82094ff (0x100) MX[B]
	[6] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[7] -1	0	0xc8208000 - 0xc82087ff (0x800) MX[B]
	[8] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[9] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[10] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[11] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[14] -1	0	0xc8208800 - 0xc82088ff (0x100) MX[B]
	[15] -1	0	0xc8208c00 - 0xc8208cff (0x100) MX[B]
	[16] -1	0	0xc8209000 - 0xc82090ff (0x100) MX[B]
	[17] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[21] -1	0	0x00003c20 - 0x00003c3f (0x20) IX[B]
	[22] -1	0	0x00003c40 - 0x00003c4f (0x10) IX[B]
	[23] -1	0	0x00003800 - 0x0000387f (0x80) IX[B]
	[24] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[25] -1	0	0x00003880 - 0x000038bf (0x40) IX[B]
	[26] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[27] -1	0	0x00003c00 - 0x00003c1f (0x20) IX[B]
	[28] -1	0	0x000038e0 - 0x000038ff (0x20) IX[B]
	[29] -1	0	0x000038c0 - 0x000038df (0x20) IX[B]
	[30] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[31] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
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
	[5] -1	0	0xc8209400 - 0xc82094ff (0x100) MX[B]
	[6] -1	0	0xc8200000 - 0xc8203fff (0x4000) MX[B]
	[7] -1	0	0xc8208000 - 0xc82087ff (0x800) MX[B]
	[8] -1	0	0xc8000400 - 0xc80004ff (0x100) MX[B]
	[9] -1	0	0xc8000800 - 0xc80009ff (0x200) MX[B]
	[10] -1	0	0xc8000000 - 0xc80003ff (0x400) MX[B]
	[11] -1	0	0xc8100000 - 0xc810ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xc8206000 - 0xc8207fff (0x2000) MX[B]
	[14] -1	0	0xc8208800 - 0xc82088ff (0x100) MX[B]
	[15] -1	0	0xc8208c00 - 0xc8208cff (0x100) MX[B]
	[16] -1	0	0xc8209000 - 0xc82090ff (0x100) MX[B]
	[17] -1	0	0xc8204000 - 0xc8205fff (0x2000) MX[B]
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[24] -1	0	0x00003c20 - 0x00003c3f (0x20) IX[B]
	[25] -1	0	0x00003c40 - 0x00003c4f (0x10) IX[B]
	[26] -1	0	0x00003800 - 0x0000387f (0x80) IX[B]
	[27] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[28] -1	0	0x00003880 - 0x000038bf (0x40) IX[B]
	[29] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[30] -1	0	0x00003c00 - 0x00003c1f (0x20) IX[B]
	[31] -1	0	0x000038e0 - 0x000038ff (0x20) IX[B]
	[32] -1	0	0x000038c0 - 0x000038df (0x20) IX[B]
	[33] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[34] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xc8100000
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "UseFBDev" "true"
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/X11R6/lib/modules/linux/libfbdevhw.a
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.0.2
	ABI class: X.Org Video Driver, version 0.7
(**) RADEON(0): Using framebuffer device
(--) RADEON(0): Chipset: "ATI Radeon Mobility X600 (M24) 3150 (PCIE)" (ChipID = 0x3150)
(--) RADEON(0): Linear framebuffer at 0xd0000000
(--) RADEON(0): VideoRAM: 0 kByte (128 bit DDR SDRAM)
(II) RADEON(0): PCI card detected
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
(WW) RADEON(0): Video BIOS not detected in PCI space!
(WW) RADEON(0): Attempting to read Video BIOS from legacy ISA space!
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): LVDS port is not in connector table, added in.
(II) RADEON(0): Connector0: DDCType-0, DACType-1, TMDSType--1, ConnectorType-1
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 0
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- LVDS
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- Proprietary
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) RADEON(0): PLL parameters: rf=2700 rd=6 min=20000 max=40000; xclk=23000
(EE) RADEON(0): MergedFB does not work with Option UseFBDev, MergedFB mode is disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Panel ID string: SEC                     
(II) RADEON(0): Panel Size from BIOS: 1440x900
(II) RADEON(0): BIOS provided dividers will be used.

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting


Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```

Here it is. Maybe someone else can make something of it?

---

### Post by Protostar on 2005-10-28
Noone was able to make anything out of my X log? I cannot be the only one having these problems.

---

### Post by cesiel1990 on 2005-10-29
Yes, I'm having this exact same problem can someone help?

---

### Post by matw on 2005-10-29
The only error I saw in your log file doesn't mean a thing to me. Sorry.

This is may be amateur advice, but hopefully you'll learn something by trying it out.

Get one of the "live" CDs (e.g. knoppix or [http://us.releases.ubuntu.com/releases/5.10/](http://us.releases.ubuntu.com/releases/5.10/)) and see if your video works. These CDs are safe to run and surprisingly good at autoconfiguring your video. Just toss one into your CDROM drive and reboot.

If this works, compare the log file, which you located, with the one that didn't work. Look for infomation that you can use (e.g. chipsets and driver names) when you run dpkg-reconfigure as Ampersand suggested.

Finally, if you don't have too much time invested in this installation, you might consider reinstalling Ubuntu. I've never heard of making swap bootable. It's probably a good idea to accept the default installation settings unless you know they aren't what you want.

---

### Post by edurm on 2006-05-28
Ubuntu does not native works with ATI X200/X300/X600/X700/X800 series, just do as this topic: [http://www.ubuntuforums.org/showthread.php?t=183643](http://www.ubuntuforums.org/showthread.php?t=183643)

good luck

---

### Post by gerasmus on 2006-06-11
I had the exact same issue, on ATI X800SE (PCI-E) card. 
Ubuntu V6.06 AMD64-bit. 
Ubuntu 6.06 64-bit Live gave black screen when X should've appeared. I assumed same issue would be if I install.
I trawled the Dutch language and international forums for hours...

**I EVENTUALLY got X to work, and here's how:**
*Executed Ubuntu 6.06 32-bit.*
Clicked the **Install to Hard disk** button on the Ubuntu desktop. System hard disk setup was done + files copied to hard disk.
 32-bit Live. I was (amazingly) greeted by the X desktop, which was great start :D  
Ubuntu v6.06 64-bit Liver version didn't wanna bring X up.  Monitor frequence was at eye 1024x768@ eye damaging 60Hz.
Non graphical setup went ok, restarted and was :p greeted by X :) :) 
Monitor resolution was max 1024x768 @ 60hz max (hurt the eyes). I was unable to change refresh to 75Hz. At least I had X.
Next I couldn't get correct ATI video driver installed.
**What is the EXACT URL for ATI Radeon X800SE drivers ?**

*In the end I have up with Ubuntu*. At that stage I've already spent more than 15 hours (all weekend and some more).  Prior to getting it up I already spent time with different versions of Ubuntu, this past week, including Ubuntu 5.10 32-bit and Ubuntu 5.10 64-bit installing and attempted to reconfigure fgx cards. None would bring up X. 

next mission was to get the Synaptic to download updates/apps. Impossible mission. I added the required repositories in the Synaptic, updated required files the \etc\apt\<filename> as well. Clicked reload on synaptic. Unable to connect to repositories, I tried from about4 different countries. No luck. 
Also tried to update using the command prompt. In both cases unable to connect to repositories (in Netherlands). No spelling mistakes, everything was default. Synaptic returned "check connection". 
I had a live internet connection and could surf with Firefox. 
Disappointed, i decided that I've wasted enuf time with Ubuntu. 

Time to go for Fedora 5 or SuSe 10.

I installed SuSe 10. From previous experience (on a covert PC at work).I liked the advanced KDE interface, huge amount of available standard software and easy of install.. It plays MP3s out of the box, etc. Software updates easier than Ubuntu. 
Above all, Suse 10 64-bit, recognised ALL my hardware without a glitch. Flawless.

Luckily I had a internet connected laptop so I can monitor forums while trying all this..

I hope the issue with Radeon X800 cards get sorted out so that it works right after install. 

My config:
CPU:           AMD64 3000+ 
Ram:           4x 512Mb Micron memory = 2Gb
Video:         ATI Radeon X800SE with 256Mb Ram.
Monitor:      Proview 19"
Motherbord: Asus A8N-E.
Broadband via cable router.

---

### Post by misterlizard on 2006-06-13
Not sure if this will help, but try this thread:

[http://www.ubuntuforums.org/showthread.php?p=1134252](http://www.ubuntuforums.org/showthread.php?p=1134252)

which suggests commenting out the Load "extmod" line from your xorg.conf.

I spent ages trying different fglrx install guides with no luck, and this tip worked first time.

---

### Post by abirdman on 2006-06-13
Thank you. I had this problem (had to change video cards after installation, after that GDM wouldn't start), and your solution worked perfectly.

---

### Post by Totson on 2006-06-14
Got a similar issue with the following specs :

AMD64 x2 AM2
2Gb Corsair RAM
ATI Radeon X1600XT
Philips Brilliance 200W
MSI K9N

None of the proposed solution helped (including commenting out the extmod module) until I commented out ALL xorg modules in xorg.conf : X would finally start with fglrx...

I then added one by one the modules and tried. In my case, it happened to be the glx module that crashed X...

So now I'm a step further : how to load the glx extensions (would like to go for Compiz/Xgl...)


[EDIT an hour later]

Just gave some wrong info : commenting out the extmod also works for me.

Got confused by the fact that extmod and glx seam to be mutually exclusive : can't run both together, but do run if the other one is not...

---


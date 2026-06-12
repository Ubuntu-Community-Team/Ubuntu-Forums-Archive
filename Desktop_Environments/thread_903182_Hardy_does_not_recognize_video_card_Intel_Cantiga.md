---
title: "Hardy does not recognize video card Intel Cantiga"
date: 2008-08-28
forum: Desktop Environments
---

### Post by guido_damico on 2008-08-28
I am setting up Hardy on a Sony Vaio FW190. According to lspci it uses an "Intel Corporation Cantiga Memory Controller Hub (rev 07)"
video card.

Installation through the alternate cd went fine, but now at boot time when X comes up the screen is all white and unusable.

I attempted to use the "safe graphics mode" and that basically loaded the "vesa" driver in xorg.conf but the result is only marginally better and still unusable.

Has anyone any experience with getting X (X.Org X Server 1.4.0.90) working on a Cantiga card?

Here is the Xorg.0.log:
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
Current Operating System: Linux bartolo 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 20 21:16:15 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
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
(II) Loader magic: 0x7bd660
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
(II) PCI: 00:00:0: chip 8086,2a40 card 104d,9035 rev 07 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2a42 card 104d,9035 rev 07 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2a43 card 104d,9035 rev 07 class 03,80,00 hdr 80
(II) PCI: 00:1a:0: chip 8086,2937 card 104d,9035 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 104d,9035 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 104d,9035 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 104d,9035 rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2942 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2946 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 104d,9035 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 104d,9035 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 104d,9035 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,2939 card 104d,9035 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 104d,9035 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 93 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2919 card 104d,9035 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2929 card 104d,9035 rev 03 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 104d,9035 rev 03 class 0c,05,00 hdr 00
(II) PCI: 05:00:0: chip 8086,4232 card 8086,1301 rev 00 class 02,80,00 hdr 00
(II) PCI: 07:00:0: chip 11ab,4363 card 104d,9035 rev 13 class 02,00,00 hdr 00
(II) PCI: 09:03:0: chip 1180,0832 card 104d,9035 rev 05 class 0c,00,10 hdr 80
(II) PCI: 09:03:1: chip 1180,0822 card 104d,9035 rev 22 class 08,05,00 hdr 80
(II) PCI: 09:03:2: chip 1180,0592 card 104d,9035 rev 12 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,9), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00005000 - 0x00005fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd4100000 - 0xd54fffff (0x1400000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00004000 - 0x00004fff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xd2d00000 - 0xd40fffff (0x1400000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:3), (0,5,6), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00003000 - 0x00003fff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xd1900000 - 0xd2cfffff (0x1400000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:28:4), (0,7,8), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 7 I/O range:
	[0] -1	0	0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xd0500000 - 0xd18fffff (0x1400000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 9: bridge is at (0:30:0), (0,9,9), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 9 non-prefetchable memory range:
	[0] -1	0	0xd5500000 - 0xd55fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile Integrated Graphics Controller rev 7, Mem @ 0xd0000000/22, 0xc0000000/28, I/O @ 0x6140/3
(--) PCI: (0:2:1) Intel Corporation Mobile Integrated Graphics Controller rev 7, Mem @ 0xd0400000/20
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
	[0] -1	0	0xd5500800 - 0xd55008ff (0x100) MX[B]
	[1] -1	0	0xd5500900 - 0xd55009ff (0x100) MX[B]
	[2] -1	0	0xd5500000 - 0xd55007ff (0x800) MX[B]
	[3] -1	0	0xd0520000 - 0xd0523fff (0x4000) MX[B]
	[4] -1	0	0xd1900000 - 0xd1901fff (0x2000) MX[B]
	[5] -1	0	0xd5604000 - 0xd56047ff (0x800) MX[B]
	[6] -1	0	0xd5604800 - 0xd5604bff (0x400) MX[B]
	[7] -1	0	0xd5600000 - 0xd5603fff (0x4000) MX[B]
	[8] -1	0	0xd5604c00 - 0xd5604fff (0x400) MX[B]
	[9] -1	0	0xd0400000 - 0xd04fffff (0x100000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xd03fffff (0x400000) MX[B](B)
	[12] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[13] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[14] -1	0	0x00006020 - 0x0000603f (0x20) IX[B]
	[15] -1	0	0x00006100 - 0x00006103 (0x4) IX[B]
	[16] -1	0	0x00006110 - 0x00006117 (0x8) IX[B]
	[17] -1	0	0x00006120 - 0x00006123 (0x4) IX[B]
	[18] -1	0	0x00006130 - 0x00006137 (0x8) IX[B]
	[19] -1	0	0x00006040 - 0x0000605f (0x20) IX[B]
	[20] -1	0	0x00006060 - 0x0000607f (0x20) IX[B]
	[21] -1	0	0x00006080 - 0x0000609f (0x20) IX[B]
	[22] -1	0	0x000060a0 - 0x000060bf (0x20) IX[B]
	[23] -1	0	0x000060c0 - 0x000060df (0x20) IX[B]
	[24] -1	0	0x000060e0 - 0x000060ff (0x20) IX[B]
	[25] -1	0	0x00006140 - 0x00006147 (0x8) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xd5605000 - 0xd56050ff (0x100) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd5500800 - 0xd55008ff (0x100) MX[B]
	[1] -1	0	0xd5500900 - 0xd55009ff (0x100) MX[B]
	[2] -1	0	0xd5500000 - 0xd55007ff (0x800) MX[B]
	[3] -1	0	0xd0520000 - 0xd0523fff (0x4000) MX[B]
	[4] -1	0	0xd1900000 - 0xd1901fff (0x2000) MX[B]
	[5] -1	0	0xd5604000 - 0xd56047ff (0x800) MX[B]
	[6] -1	0	0xd5604800 - 0xd5604bff (0x400) MX[B]
	[7] -1	0	0xd5600000 - 0xd5603fff (0x4000) MX[B]
	[8] -1	0	0xd5604c00 - 0xd5604fff (0x400) MX[B]
	[9] -1	0	0xd0400000 - 0xd04fffff (0x100000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xd03fffff (0x400000) MX[B](B)
	[12] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[13] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[14] -1	0	0x00006020 - 0x0000603f (0x20) IX[B]
	[15] -1	0	0x00006100 - 0x00006103 (0x4) IX[B]
	[16] -1	0	0x00006110 - 0x00006117 (0x8) IX[B]
	[17] -1	0	0x00006120 - 0x00006123 (0x4) IX[B]
	[18] -1	0	0x00006130 - 0x00006137 (0x8) IX[B]
	[19] -1	0	0x00006040 - 0x0000605f (0x20) IX[B]
	[20] -1	0	0x00006060 - 0x0000607f (0x20) IX[B]
	[21] -1	0	0x00006080 - 0x0000609f (0x20) IX[B]
	[22] -1	0	0x000060a0 - 0x000060bf (0x20) IX[B]
	[23] -1	0	0x000060c0 - 0x000060df (0x20) IX[B]
	[24] -1	0	0x000060e0 - 0x000060ff (0x20) IX[B]
	[25] -1	0	0x00006140 - 0x00006147 (0x8) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xd5605000 - 0xd56050ff (0x100) MX[B]
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
	[4] -1	0	0xd5500800 - 0xd55008ff (0x100) MX[B]
	[5] -1	0	0xd5500900 - 0xd55009ff (0x100) MX[B]
	[6] -1	0	0xd5500000 - 0xd55007ff (0x800) MX[B]
	[7] -1	0	0xd0520000 - 0xd0523fff (0x4000) MX[B]
	[8] -1	0	0xd1900000 - 0xd1901fff (0x2000) MX[B]
	[9] -1	0	0xd5604000 - 0xd56047ff (0x800) MX[B]
	[10] -1	0	0xd5604800 - 0xd5604bff (0x400) MX[B]
	[11] -1	0	0xd5600000 - 0xd5603fff (0x4000) MX[B]
	[12] -1	0	0xd5604c00 - 0xd5604fff (0x400) MX[B]
	[13] -1	0	0xd0400000 - 0xd04fffff (0x100000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd03fffff (0x400000) MX[B](B)
	[16] -1	0	0xd5605000 - 0xd56050ff (0x100) MX[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[20] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[21] -1	0	0x00006020 - 0x0000603f (0x20) IX[B]
	[22] -1	0	0x00006100 - 0x00006103 (0x4) IX[B]
	[23] -1	0	0x00006110 - 0x00006117 (0x8) IX[B]
	[24] -1	0	0x00006120 - 0x00006123 (0x4) IX[B]
	[25] -1	0	0x00006130 - 0x00006137 (0x8) IX[B]
	[26] -1	0	0x00006040 - 0x0000605f (0x20) IX[B]
	[27] -1	0	0x00006060 - 0x0000607f (0x20) IX[B]
	[28] -1	0	0x00006080 - 0x0000609f (0x20) IX[B]
	[29] -1	0	0x000060a0 - 0x000060bf (0x20) IX[B]
	[30] -1	0	0x000060c0 - 0x000060df (0x20) IX[B]
	[31] -1	0	0x000060e0 - 0x000060ff (0x20) IX[B]
	[32] -1	0	0x00006140 - 0x00006147 (0x8) IX[B](B)
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
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset Intel Integrated Graphics Device found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd5500800 - 0xd55008ff (0x100) MX[B]
	[5] -1	0	0xd5500900 - 0xd55009ff (0x100) MX[B]
	[6] -1	0	0xd5500000 - 0xd55007ff (0x800) MX[B]
	[7] -1	0	0xd0520000 - 0xd0523fff (0x4000) MX[B]
	[8] -1	0	0xd1900000 - 0xd1901fff (0x2000) MX[B]
	[9] -1	0	0xd5604000 - 0xd56047ff (0x800) MX[B]
	[10] -1	0	0xd5604800 - 0xd5604bff (0x400) MX[B]
	[11] -1	0	0xd5600000 - 0xd5603fff (0x4000) MX[B]
	[12] -1	0	0xd5604c00 - 0xd5604fff (0x400) MX[B]
	[13] -1	0	0xd0400000 - 0xd04fffff (0x100000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd03fffff (0x400000) MX[B](B)
	[16] -1	0	0xd5605000 - 0xd56050ff (0x100) MX[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[20] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[21] -1	0	0x00006020 - 0x0000603f (0x20) IX[B]
	[22] -1	0	0x00006100 - 0x00006103 (0x4) IX[B]
	[23] -1	0	0x00006110 - 0x00006117 (0x8) IX[B]
	[24] -1	0	0x00006120 - 0x00006123 (0x4) IX[B]
	[25] -1	0	0x00006130 - 0x00006137 (0x8) IX[B]
	[26] -1	0	0x00006040 - 0x0000605f (0x20) IX[B]
	[27] -1	0	0x00006060 - 0x0000607f (0x20) IX[B]
	[28] -1	0	0x00006080 - 0x0000609f (0x20) IX[B]
	[29] -1	0	0x000060a0 - 0x000060bf (0x20) IX[B]
	[30] -1	0	0x000060c0 - 0x000060df (0x20) IX[B]
	[31] -1	0	0x000060e0 - 0x000060ff (0x20) IX[B]
	[32] -1	0	0x00006140 - 0x00006147 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd5500800 - 0xd55008ff (0x100) MX[B]
	[5] -1	0	0xd5500900 - 0xd55009ff (0x100) MX[B]
	[6] -1	0	0xd5500000 - 0xd55007ff (0x800) MX[B]
	[7] -1	0	0xd0520000 - 0xd0523fff (0x4000) MX[B]
	[8] -1	0	0xd1900000 - 0xd1901fff (0x2000) MX[B]
	[9] -1	0	0xd5604000 - 0xd56047ff (0x800) MX[B]
	[10] -1	0	0xd5604800 - 0xd5604bff (0x400) MX[B]
	[11] -1	0	0xd5600000 - 0xd5603fff (0x4000) MX[B]
	[12] -1	0	0xd5604c00 - 0xd5604fff (0x400) MX[B]
	[13] -1	0	0xd0400000 - 0xd04fffff (0x100000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd03fffff (0x400000) MX[B](B)
	[16] -1	0	0xd5605000 - 0xd56050ff (0x100) MX[B]
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[23] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[24] -1	0	0x00006020 - 0x0000603f (0x20) IX[B]
	[25] -1	0	0x00006100 - 0x00006103 (0x4) IX[B]
	[26] -1	0	0x00006110 - 0x00006117 (0x8) IX[B]
	[27] -1	0	0x00006120 - 0x00006123 (0x4) IX[B]
	[28] -1	0	0x00006130 - 0x00006137 (0x8) IX[B]
	[29] -1	0	0x00006040 - 0x0000605f (0x20) IX[B]
	[30] -1	0	0x00006060 - 0x0000607f (0x20) IX[B]
	[31] -1	0	0x00006080 - 0x0000609f (0x20) IX[B]
	[32] -1	0	0x000060a0 - 0x000060bf (0x20) IX[B]
	[33] -1	0	0x000060c0 - 0x000060df (0x20) IX[B]
	[34] -1	0	0x000060e0 - 0x000060ff (0x20) IX[B]
	[35] -1	0	0x00006140 - 0x00006147 (0x8) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Intel Integrated Graphics Device
(--) intel(0): Chipset: "Intel Integrated Graphics Device"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xD0000000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 131008 kB
(II) intel(0): VESA VBE OEM: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)Cantiga Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1600x900
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 130556 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x00000000 to 0x00000400
(WW) intel(0): Register 0x321b (FBC_FENCE_OFF) changed from 0x04008200 to 0x1400a000
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x00000010 to 0x000c0010
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x00606000
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710088
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x4e2d1dc8
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x8000085e
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00028283
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00014141
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MS[B]
	[1] 0	0	0xd0000000 - 0xd03fffff (0x400000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd5500800 - 0xd55008ff (0x100) MX[B]
	[7] -1	0	0xd5500900 - 0xd55009ff (0x100) MX[B]
	[8] -1	0	0xd5500000 - 0xd55007ff (0x800) MX[B]
	[9] -1	0	0xd0520000 - 0xd0523fff (0x4000) MX[B]
	[10] -1	0	0xd1900000 - 0xd1901fff (0x2000) MX[B]
	[11] -1	0	0xd5604000 - 0xd56047ff (0x800) MX[B]
	[12] -1	0	0xd5604800 - 0xd5604bff (0x400) MX[B]
	[13] -1	0	0xd5600000 - 0xd5603fff (0x4000) MX[B]
	[14] -1	0	0xd5604c00 - 0xd5604fff (0x400) MX[B]
	[15] -1	0	0xd0400000 - 0xd04fffff (0x100000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xd03fffff (0x400000) MX[B](B)
	[18] -1	0	0xd5605000 - 0xd56050ff (0x100) MX[B]
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 0	0	0x00006140 - 0x00006147 (0x8) IS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[26] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[27] -1	0	0x00006020 - 0x0000603f (0x20) IX[B]
	[28] -1	0	0x00006100 - 0x00006103 (0x4) IX[B]
	[29] -1	0	0x00006110 - 0x00006117 (0x8) IX[B]
	[30] -1	0	0x00006120 - 0x00006123 (0x4) IX[B]
	[31] -1	0	0x00006130 - 0x00006137 (0x8) IX[B]
	[32] -1	0	0x00006040 - 0x0000605f (0x20) IX[B]
	[33] -1	0	0x00006060 - 0x0000607f (0x20) IX[B]
	[34] -1	0	0x00006080 - 0x0000609f (0x20) IX[B]
	[35] -1	0	0x000060a0 - 0x000060bf (0x20) IX[B]
	[36] -1	0	0x000060c0 - 0x000060df (0x20) IX[B]
	[37] -1	0	0x000060e0 - 0x000060ff (0x20) IX[B]
	[38] -1	0	0x00006140 - 0x00006147 (0x8) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 716032 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 2864124 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1600 -> 1664).
(II) intel(0): [drm] Registers = 0xd0000000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] mapped front buffer at 0xc0100000, handle = 0xc0100000
(II) intel(0): [drm] mapped back buffer at 0xc29a0000, handle = 0xc29a0000
(II) intel(0): [drm] mapped depth buffer at 0xc33c8000, handle = 0xc33c8000
(II) intel(0): [drm] mapped classic textures at 0xc3df0000, handle = 0xc3df0000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 31948800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x07f7f000 (pgoffset 32639)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00041fff: exa G965 state buffer (64 kB)
(II) intel(0): 0x00042000-0x00042fff: overlay registers (4 kB)
(II) intel(0): 0x00100000-0x00b27fff: front buffer (10400 kB) X tiled
(II) intel(0): 0x00b28000-0x0299ffff: exa offscreen (31200 kB)
(II) intel(0): 0x029a0000-0x033c7fff: back buffer (10400 kB) X tiled
(II) intel(0): 0x033c8000-0x03deffff: depth buffer (10400 kB) Y tiled
(II) intel(0): 0x03df0000-0x05deffff: classic textures (32768 kB)
(II) intel(0): 0x07f7f000:            end of stolen memory
(II) intel(0): 0x07f7f000-0x07f7ffff: HW status (4 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 423 x 238
Atom 4, CARD32 4, unsigned long 8
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
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
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
(--) Synaptics Touchpad touchpad found
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 0

```

---

### Post by Crafty Kisses on 2008-08-28
Post results of > glxinfo

---

### Post by guido_damico on 2008-08-28
Codename: using the console I can run "glxinfo" but the only thing I get back "Could not open display". Should it always work?

---

### Post by tamagotono on 2008-08-28
I was just looking at a VAIO VGN-FW140E and am thinking about buying it.
My research lead me to a site Phoronix that did a review on this GPU.
I recommend researching it by it's common name 4500MHD.

[http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=1)

this website was saying it is needing to use a new version of the MESA drivers that have not been released yet.  However, Intrepid Alpha 3 did include them.  You may want to try running the Alpha 4 to see if that works.

I am probably going to buy the laptop tomorrow, and if so then I will be facing the same battle as you.  Perhaps we can battle it together.

How does the rest of your system work?

---

### Post by Crafty Kisses on 2008-08-28
How about glxgears, do you get anything?

---

### Post by guido_damico on 2008-08-28
**tamagotono**: thanks for the link I'll check it out. Also: sure, let's battle together!

Given the fact that I have no X I am still using mostly Vista so my judgement is impaired by the OS (and the staggering amount of crapware the PC came with, as usual). This was a replacement for a less than one year old Vaio FZ190 that got stolen about a month ago. Once I got all correctly setup on that one I really liked it, for reliability and performance; I expect this new one to be as good at least (and I got one more inch of screen to look at!).

**Codename**: I tried several glx... commands and they all returned the same, but am not sure about glxgears in particular. I have not the laptop with me now and will post the result later on tonight (PST time). Thanks for your help!

---

### Post by tamagotono on 2008-08-29
Well, I just bought the VGN-FW140E with this problem chipset.  I have only had a chance to play with it for a short while so all that I have found is if you edit your xorg.conf file and under 'configured device' add

driver   "vesa"

then restart X, you can at least get a 800X600 display.  I am going to try some other intel settings and see if I get any luck.  Then I will work on getting the proper drivers going.. :)

Hope this makes it at least a little bit more bearable.

---

### Post by guido_damico on 2008-08-29
**tamagotono**: that's almost what I got whenstarting in "safe graphics" mode, with the exception that I could not get a usable screen. I might have not tried the 800x600 resolution (though I thought I did), I'll give it another try and let you know.

**Codename**: no suck luck, all the glx* commands return the same error ("canot open display"), except glxdemo which goes in segmentation fault.

---

### Post by guido_damico on 2008-08-29
**tamagotono**: I remembered correctly and even with a 800x600 I got an unusable scattered screen. It looks like I'm one step behind: could you post here the xorg.conf that worked for you with 800x600?

---

### Post by tamagotono on 2008-08-29
**Guido_damico:** here is a copy of the xorg.conf file that is working for me with 800x600 VESA mode. The only modification I made to the default configuration is the driver line that I have made bold.  I hope this helps.  800x600 sucks but it's better than nothing. :)


```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    **Driver        "vesa"**

EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

```

---

### Post by tamagotono on 2008-08-30
Well, I have some good news.  I am able to get 3D video from this laptop and compiz works great.  The problem is this, it is only on the HDMI and VGA outputs!  I am still getting a whiteish display on the laptop itself.:(  This is using the Kubuntu 8.10 Alpha 4 install.

If you are trying to use the 8.04 version you can get a slightly older version of the driver but it should work.  Download it from here [http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/]("http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/")

Apparently it has a few problems too, perhaps the same as I am getting.  I found this information [U][I][here]("http://ubuntuforums.org/showthread.php?t=889323")
[/I][/U]
The rest of the laptop seems to work almost perfectly out of the box with 8.10.  There are a few issues with KDE4.1 that prevent me from verifying everything but most everything is working great.  The only other issue I have found is that the speakers do not mute when headphones are plugged in.  I will try to figure this out next and will report back with what I find.

I have verified the following work properly out of the box:
[B]Wired Networking
Wireless Networking [/B](knetwork manager is currently broke, using nm-applet)
**Audio** (with exception of speakers not muting with headphones plugged in)
[B]Standby
Hibernate
SDHC/MMC reader
Webcam
Touchpad[/B] (tapping broke after latest update)
[B]DVD Burner
Bluetooth
Backlight adjustment[/B] (through the power manager applet)

I think we are just going to have to wait for the drivers to be properly developed for the video on the laptop.  Everything else should work real well and easily.

---

### Post by guido_damico on 2008-08-30
[I just saw you last comment.]
Thanks **tamagotono**, using the vesa driver still does not work on 8.04.

Now, my FW190EDH uses a GMA 4700MHD, not a 4500, so maybe that's why the default on vesa does not work for me. I'll keep trying, while they keep testing Intrepid (Alpha 4 did not work either).

I'll check the drivers you mentioned in the links and see if that gets any better (am somewhat doubtful, though...).

*I think we are just going to have to wait for the drivers to be properly developed for the video on the laptop.*
I agree. Thanks for the help, by the way!

---

### Post by tamagotono on 2008-08-30
Did you try the VESA driver with Alpha 4?  That is what is working for me.  I was able to get external video with Alpha 4, how about you?

These drivers should cover the whole 4000 series chipsets so it should work for yours as well.  Let me know if it works for you at all.

I have 8.10 Alpha4 installed and will keep trying the video whenever there is an update.  I'll report back when I see it working.

This system appears to be very promising to work out-of-the-box with no propriatary drivers.  I can't wait for 8.10 Final to be released!

---

### Post by eeejay on 2008-08-31
> **tamagotono said:**
> This system appears to be very promising to work out-of-the-box with no propriatary drivers.  I can't wait for 8.10 Final to be released!

I have a T400 with similar Cantiga specs. I reported a bug about a system crash when starting the X server with the "intel" driver. If you guys have similar experiences, could you chime in on the report?

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/263114](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/263114)

---

### Post by tamagotono on 2008-09-01
eeejay,  I have tried setting the driver to "intel" and have seen no difference than without.  I believe this is the driver Xorg is being autoconfigured with.  The video works on the external monitor in both cases.

X does lock up if I plug in or remove the external monitor when X is running.

---

### Post by Croccydile on 2008-09-01
I'm rather certain the updated Intel driver wont work in 8.04 unless you go mucking about recompiling alot of things, unfortunately that wound up not being an option and I'm using an add-in card on my machine till 8.10 to upgrade then.

Sorry, I could not figure out how to rebuild the necessary packages without blowing up my system. I'll just have to wait.

---

### Post by guido_damico on 2008-09-03
> Did you try the VESA driver with Alpha 4?

I tried to, but both ubuntu and kubuntu alpha 4 gave me wrong CD images: when I try to boot using them, it gives me a **# Initramfs** prompt and does not continue on the boot sequence. I will try to get the ISO images again and see if something went wrong during the initial download.

---

### Post by tamagotono on 2008-09-08
OK, word on the street is that there will be a big driver fix for xserver-xorg-video-intel on the 10th.  Just 2 more days and hopefully we will have some success.

I tried Mandriva 2009 beta that was released last week and it suffers from the same issue, so this is an intel thing not an ubuntu thing.  I had a bit more success after trying Mandriva as it was able to set the VESA to 1024x768 which ubuntu couldn't do.  After rebooting from the live CD, I booted into my install of intrepid and it all the sudden worked at 1024x768 using the VESA driver.  Looking in the logs, it now recognizes the VESA BIOS which it did not do before.  I am wondering if it will still work after I power it down...

Lets all cross our fingers and hope this driver update takes care of the problem.

---

### Post by Cannaregio on 2008-09-12
Slightly different, but related, problem here:
Toshiba Satellite U400-136
Mobile Intel GMA 4500MHD
Ubuntu Intrepid Ibex
lspci: 
```
VGA compatible controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)
```

No problems with 600*800

Recognizes 1280*800 VGA out of the box:
```
sudo displayconfig-gtk
```

*Some* Visual effects work (Mod4+E works fine)

glxgears is a sad story (357 frames in 5.2 seconds = 68.884 FPS)
regnum on line: unsupported video card (not true, drivers amiss, works in windows)

does anyone know if the drivers can be found somewhere?

---

### Post by mrnick8687 on 2008-09-22
Looks like a kernel update fixes it.  Just got in a Lenovo T500 with the same video card.  Updated the kernel to the newest version (apt-get install linux-image-generic) rebooted and it works. 

Hope that helps.

---

### Post by JC SHOT U on 2008-09-23
I have a Dell Latitue E5500 with the Intel GMA 4500MHD. This card is not working on my computer. The screen is set at 1024x768 resolution and is giving me a headache. I cannot change the resolution to a higher setting, NOT EVEN 1280x800. I need my resolution to be 1280x800. I also cannot dual monitor with the GMA 4500 MHD. Does anyone have a fix for this? Is there a possibilty for it to work in Fedora if Ubuntu doesn't have a fix?

---

### Post by tamagotono on 2008-09-27
> **JC SHOT U said:**
> I have a Dell Latitue E5500 with the Intel GMA 4500MHD. This card is not working on my computer. The screen is set at 1024x768 resolution and is giving me a headache. I cannot change the resolution to a higher setting, NOT EVEN 1280x800. I need my resolution to be 1280x800. I also cannot dual monitor with the GMA 4500 MHD. Does anyone have a fix for this? Is there a possibilty for it to work in Fedora if Ubuntu doesn't have a fix?
We need a bit of info from you.  What version of ubuntu are you using 8.04 or 8.10alpha?  Which driver are you using, Intel or VESA?  

You can try Fedora's latest beta and see if it works, they have a live CD version so there is no risk involved.  If it does work then you could copy off the xorg.conf file that it generates and see if it works in ubuntu too.

It might help if you posted your /var/log/Xorg.0.log file too.

---

### Post by bull205 on 2008-10-12
I have been trying to work this out for about two to three weeks on a sony vaio SR-165E with the problem cantiga chipset.  I have to run the kernel that ends in .19 instead of the one that ends in .24 (i think that is right, next time I reboot, I'll make a note and post it to make sure I'm giving the correct numbers) nevertheless, I can't use the most updated Hardy because the sony freaks out when I try to load it.  I am running 800x600 right now.  Using the vesa driver

I am a supernoob, so as much as I can help I will.

BTW, my wireless doesn't work and ejecting my cd driver has to be done with a paperclip....

---

### Post by ponar on 2008-10-20
I have a Sony VGN-FW140E with the exact same issue. I've install the latest 8.10 Beta, compiled the latest intel drivers (2.4.2), updated the kernel, all to no avail.

It works great when I connect an external monitor to the VGA output of the laptop, but the built-in display refuses to work with anything other than vesa mode.

Any new developments from anyone???

---

### Post by igknighted on 2008-10-26
> **ponar said:**
> I have a Sony VGN-FW140E with the exact same issue. I've install the latest 8.10 Beta, compiled the latest intel drivers (2.4.2), updated the kernel, all to no avail.

It works great when I connect an external monitor to the VGA output of the laptop, but the built-in display refuses to work with anything other than vesa mode.

Any new developments from anyone???

BUMP

I've got the exact same machine, exact same issues.  Even in the very latest releases from around the linux world (Ibex RC, Fedora 10 beta, Suse 11.1 beta3).  I am trying enabling intrepid-proposed updates, perhaps that will help.  Will post back results.

EDIT: no luck

---

### Post by Malawi on 2008-11-21
I have the same problem with the same machine.
I can not figure out how to fix this.

Do you have any solution, any news?

Thanks

---

### Post by aeid79 on 2008-11-26
same machine, same problem! 
any solution ?

---

### Post by guido_damico on 2008-11-26
With the released Intrepid (8.10) and the vesa driver you can get an ugly 800x600 (see **tamagotono** post [#7]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=5685698&postcount=7") in this thread).

If **tamagotono** could let us know if there's a safe way to get the 1024x768 to be recognized (as stated [here]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=5753345&postcount=18")) I think we'd be already in a better place.

As for the my laptop (**Sony Vaio FW190EDH** with **GMA 4700MHD**) I would notice that the following works out of the box on Intrepid:
[LIST]
[*]CPU -- recognizes both cores;
[*]Wireless -- is recognized, connects without any issue, even the green led is ok :);
[*]CD driver -- read, eject, etc...;
[*]Sound -- tested only with flash videos from youtube so far, but it sounds OK;
[/LIST]

The only issue (besides the screen resolution, that is) is with the **Suspend** mode that still freezes up and cannot recover afterwards.

Thanks everybody for your help!

---

### Post by guido_damico on 2008-11-28
**Update:** Using the xorg.conf file posted [here]("http://www.claudiocamacho.org/tech/sr11m_debian.php#s4s4") I am able to run at 1024x768.

---

### Post by Cannaregio on 2008-12-20
I found a solution for 1280*800 on a Toshiba Satellite U 400

see 
[http://ubuntuforums.org/showthread.php?t=1013929]("http://ubuntuforums.org/showthread.php?t=1013929")
Basically some changes to xorg.conf

Still running with the vesa driver, though.

---

### Post by guido_damico on 2009-02-05
Well it looks like we are caught up: with **Interpid**'s install and the latest update of the Xorg packages the driver recognizes the video card and I can run happily at [COLOR="Red"]1600x900[/COLOR] without the VESA driver.

---


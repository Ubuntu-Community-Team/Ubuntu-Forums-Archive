---
title: "System freezes at boot [i810/intel]"
date: 2008-08-12
forum: Desktop Environments
---

### Post by trs80-vga on 2008-08-12
The intel/i810 driver is currently giving me a challenge, maybe some of you can give a clue to help me resolve the problem. 

Every morning when i power my system on the computer will freeze at the second from splash screen to Xorg, the screen is black and the lamp in the floppy drive is on, the lamps on the keyboard is off and do not turn on if i press Caps Lock etc. no input at all is accepted ie. Ctrl+ALT+F1. The only thing i can do is to power off the system by holding the power button for a few seconds, this may happen three or four times then at the fifth time the system will load normally and i can log in, the number of times that the system will crash is different every time. If the system is booted the same problem can sometimes occur when the screen saver is running, the screen will freeze at the moment where i move the mouse, and i will have to turn the system off by holding the power button. Exactly the same behaviour is also seen on another computer also using the i810/intel driver, in Xorg.0.log.old the Error "Error in I830WaitLpRing(), timeout for 2 seconds" would show up, the solution on that system became to change to another graphic card not using the i810/intel driver. 

Here is some info on my system:

Dell Optiplex 745 [VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)]
Ubuntu Hardy 8.04.1 with all the latest updates installed.

I have tried to change between intel and i810 driver but no difference, I have also tried to disable DRI but no difference either. Here is the Xorg log from a crash:


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
Current Operating System: Linux dr-schnell-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 11 14:07:32 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(II) PCI: 00:00:0: chip 8086,2990 card 1028,01da rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2991 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2992 card 1028,01da rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2993 card 1028,01da rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,01da rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,01da rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,01da rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,01da rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2847 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,01da rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,01da rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,01da rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,01da rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2810 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2820 card 1028,01da rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,01da rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2825 card 1028,01da rev 02 class 01,01,85 hdr 00
(II) PCI: 03:00:0: chip 14e4,167a card 1028,01da rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfb00000 - 0xdfbfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:4), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdfa00000 - 0xdfafffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82Q963/Q965 Integrated Graphics Controller rev 2, Mem @ 0xdfe00000/20, 0xc0000000/28, I/O @ 0xecb8/3
(--) PCI: (0:2:1) Intel Corporation 82Q963/Q965 Integrated Graphics Controller rev 2, Mem @ 0xdff00000/20
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
	[0] -1	0	0xdfaf0000 - 0xdfafffff (0x10000) MX[B]
	[1] -1	0	0xdfdfbb00 - 0xdfdfbbff (0x100) MX[B]
	[2] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[3] -1	0	0xdfdfc000 - 0xdfdfffff (0x4000) MX[B]
	[4] -1	0	0xdfdfbc00 - 0xdfdfbfff (0x400) MX[B]
	[5] -1	0	0xdff00000 - 0xdfffffff (0x100000) MX[B](B)
	[6] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B](B)
	[8] -1	0	0x0000ecd0 - 0x0000ecdf (0x10) IX[B]
	[9] -1	0	0x0000fed0 - 0x0000fedf (0x10) IX[B]
	[10] -1	0	0x0000fe70 - 0x0000fe73 (0x4) IX[B]
	[11] -1	0	0x0000fe60 - 0x0000fe67 (0x8) IX[B]
	[12] -1	0	0x0000fe50 - 0x0000fe53 (0x4) IX[B]
	[13] -1	0	0x0000fe40 - 0x0000fe47 (0x8) IX[B]
	[14] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[15] -1	0	0x0000ecc0 - 0x0000eccf (0x10) IX[B]
	[16] -1	0	0x0000fec0 - 0x0000fecf (0x10) IX[B]
	[17] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[18] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[19] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[22] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[25] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[26] -1	0	0x0000ecb8 - 0x0000ecbf (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfaf0000 - 0xdfafffff (0x10000) MX[B]
	[1] -1	0	0xdfdfbb00 - 0xdfdfbbff (0x100) MX[B]
	[2] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[3] -1	0	0xdfdfc000 - 0xdfdfffff (0x4000) MX[B]
	[4] -1	0	0xdfdfbc00 - 0xdfdfbfff (0x400) MX[B]
	[5] -1	0	0xdff00000 - 0xdfffffff (0x100000) MX[B](B)
	[6] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B](B)
	[8] -1	0	0x0000ecd0 - 0x0000ecdf (0x10) IX[B]
	[9] -1	0	0x0000fed0 - 0x0000fedf (0x10) IX[B]
	[10] -1	0	0x0000fe70 - 0x0000fe73 (0x4) IX[B]
	[11] -1	0	0x0000fe60 - 0x0000fe67 (0x8) IX[B]
	[12] -1	0	0x0000fe50 - 0x0000fe53 (0x4) IX[B]
	[13] -1	0	0x0000fe40 - 0x0000fe47 (0x8) IX[B]
	[14] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[15] -1	0	0x0000ecc0 - 0x0000eccf (0x10) IX[B]
	[16] -1	0	0x0000fec0 - 0x0000fecf (0x10) IX[B]
	[17] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[18] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[19] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[22] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[25] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[26] -1	0	0x0000ecb8 - 0x0000ecbf (0x8) IX[B](B)
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
	[4] -1	0	0xdfaf0000 - 0xdfafffff (0x10000) MX[B]
	[5] -1	0	0xdfdfbb00 - 0xdfdfbbff (0x100) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdfdfc000 - 0xdfdfffff (0x4000) MX[B]
	[8] -1	0	0xdfdfbc00 - 0xdfdfbfff (0x400) MX[B]
	[9] -1	0	0xdff00000 - 0xdfffffff (0x100000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000ecd0 - 0x0000ecdf (0x10) IX[B]
	[15] -1	0	0x0000fed0 - 0x0000fedf (0x10) IX[B]
	[16] -1	0	0x0000fe70 - 0x0000fe73 (0x4) IX[B]
	[17] -1	0	0x0000fe60 - 0x0000fe67 (0x8) IX[B]
	[18] -1	0	0x0000fe50 - 0x0000fe53 (0x4) IX[B]
	[19] -1	0	0x0000fe40 - 0x0000fe47 (0x8) IX[B]
	[20] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[21] -1	0	0x0000ecc0 - 0x0000eccf (0x10) IX[B]
	[22] -1	0	0x0000fec0 - 0x0000fecf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[28] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[29] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[30] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[31] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[32] -1	0	0x0000ecb8 - 0x0000ecbf (0x8) IX[B](B)
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
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
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
(--) Chipset 965Q found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfaf0000 - 0xdfafffff (0x10000) MX[B]
	[5] -1	0	0xdfdfbb00 - 0xdfdfbbff (0x100) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdfdfc000 - 0xdfdfffff (0x4000) MX[B]
	[8] -1	0	0xdfdfbc00 - 0xdfdfbfff (0x400) MX[B]
	[9] -1	0	0xdff00000 - 0xdfffffff (0x100000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000ecd0 - 0x0000ecdf (0x10) IX[B]
	[15] -1	0	0x0000fed0 - 0x0000fedf (0x10) IX[B]
	[16] -1	0	0x0000fe70 - 0x0000fe73 (0x4) IX[B]
	[17] -1	0	0x0000fe60 - 0x0000fe67 (0x8) IX[B]
	[18] -1	0	0x0000fe50 - 0x0000fe53 (0x4) IX[B]
	[19] -1	0	0x0000fe40 - 0x0000fe47 (0x8) IX[B]
	[20] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[21] -1	0	0x0000ecc0 - 0x0000eccf (0x10) IX[B]
	[22] -1	0	0x0000fec0 - 0x0000fecf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[28] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[29] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[30] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[31] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[32] -1	0	0x0000ecb8 - 0x0000ecbf (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfaf0000 - 0xdfafffff (0x10000) MX[B]
	[5] -1	0	0xdfdfbb00 - 0xdfdfbbff (0x100) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdfdfc000 - 0xdfdfffff (0x4000) MX[B]
	[8] -1	0	0xdfdfbc00 - 0xdfdfbfff (0x400) MX[B]
	[9] -1	0	0xdff00000 - 0xdfffffff (0x100000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ecd0 - 0x0000ecdf (0x10) IX[B]
	[18] -1	0	0x0000fed0 - 0x0000fedf (0x10) IX[B]
	[19] -1	0	0x0000fe70 - 0x0000fe73 (0x4) IX[B]
	[20] -1	0	0x0000fe60 - 0x0000fe67 (0x8) IX[B]
	[21] -1	0	0x0000fe50 - 0x0000fe53 (0x4) IX[B]
	[22] -1	0	0x0000fe40 - 0x0000fe47 (0x8) IX[B]
	[23] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[24] -1	0	0x0000ecc0 - 0x0000eccf (0x10) IX[B]
	[25] -1	0	0x0000fec0 - 0x0000fecf (0x10) IX[B]
	[26] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[27] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[28] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[31] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[32] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[33] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[34] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[35] -1	0	0x0000ecb8 - 0x0000ecbf (0x8) IX[B](B)
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
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965Q
(--) intel(0): Chipset: "965Q"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xDFE00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
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
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "DEL", prod id 16404
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): EDID vendor "DEL", prod id 16404
(II) intel(0): Output VGA connected
(II) intel(0): Output VGA using initial mode 1280x1024
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 7676 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (380, 300) mm
(**) intel(0): DPI set to (85, 108)
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
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x00000000 to 0x00000b00
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000000 to 0x00000207
(WW) intel(0): PIPEASTAT before: status:
(WW) intel(0): PIPEASTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MS[B]
	[1] 0	0	0xdfe00000 - 0xdfefffff (0x100000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfaf0000 - 0xdfafffff (0x10000) MX[B]
	[7] -1	0	0xdfdfbb00 - 0xdfdfbbff (0x100) MX[B]
	[8] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[9] -1	0	0xdfdfc000 - 0xdfdfffff (0x4000) MX[B]
	[10] -1	0	0xdfdfbc00 - 0xdfdfbfff (0x400) MX[B]
	[11] -1	0	0xdff00000 - 0xdfffffff (0x100000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] 0	0	0x0000ecb8 - 0x0000ecbf (0x8) IS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ecd0 - 0x0000ecdf (0x10) IX[B]
	[21] -1	0	0x0000fed0 - 0x0000fedf (0x10) IX[B]
	[22] -1	0	0x0000fe70 - 0x0000fe73 (0x4) IX[B]
	[23] -1	0	0x0000fe60 - 0x0000fe67 (0x8) IX[B]
	[24] -1	0	0x0000fe50 - 0x0000fe53 (0x4) IX[B]
	[25] -1	0	0x0000fe40 - 0x0000fe47 (0x8) IX[B]
	[26] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[27] -1	0	0x0000ecc0 - 0x0000eccf (0x10) IX[B]
	[28] -1	0	0x0000fec0 - 0x0000fecf (0x10) IX[B]
	[29] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[30] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[31] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[37] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[38] -1	0	0x0000ecb8 - 0x0000ecbf (0x8) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 488704 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1954812 kB available
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
(II) intel(0): [drm] Registers = 0xdfe00000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] mapped front buffer at 0xc0100000, handle = 0xc0100000
(II) intel(0): [drm] mapped back buffer at 0xc1a00000, handle = 0xc1a00000
(II) intel(0): [drm] mapped depth buffer at 0xc2040000, handle = 0xc2040000
(II) intel(0): [drm] mapped classic textures at 0xc2680000, handle = 0xc2680000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(WW) intel(0): Failed to set up write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 19660800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0077f000 (pgoffset 1919)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01a00000 (pgoffset 6656)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x02040000 (pgoffset 8256)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x02680000 (pgoffset 9856)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00041fff: exa G965 state buffer (64 kB)
(II) intel(0): 0x00042000-0x00042fff: overlay registers (4 kB)
(II) intel(0): 0x00100000-0x0073ffff: front buffer (6400 kB) X tiled
(II) intel(0): 0x00740000-0x019fffff: exa offscreen (19200 kB)
(II) intel(0): 0x0077f000:            end of stolen memory
(II) intel(0): 0x01a00000-0x0203ffff: back buffer (6400 kB) X tiled
(II) intel(0): 0x02040000-0x0267ffff: depth buffer (6400 kB) Y tiled
(II) intel(0): 0x02680000-0x0467ffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
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
(II) intel(0): Setting screen physical size to 376 x 301
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
(**) Option "XkbLayout" "dk"
(**) Generic Keyboard: XkbLayout: "dk"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): EDID vendor "DEL", prod id 16404
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): EDID vendor "DEL", prod id 16404
(II) intel(0): EDID vendor "DEL", prod id 16404
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): EDID vendor "DEL", prod id 16404
(II) intel(0): EDID vendor "DEL", prod id 16404
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): EDID vendor "DEL", prod id 16404
(II) intel(0): EDID vendor "DEL", prod id 16404
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): EDID vendor "DEL", prod id 16404
(II) intel(0): EDID vendor "DEL", prod id 16404
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): EDID vendor "DEL", prod id 16404
SetGrabKeysState - disabled
SetGrabKeysState - enabled
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xf8b64000 at 0xb7f78000
(II) intel(0): [drm] Closed DRM master.
```

---

### Post by woaibbhemm on 2008-08-12
hello~
      nice    to   meet  you .thank you   for   your  sharing    and  welcome   to  our   website ~










Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by tschew on 2008-08-12
I have the boot lockup problem on an asus motherboard with an intel g35 integrated chipset.

---

### Post by gcee on 2008-08-12
I don't have the same system as you, but I too have been experiencing random freezes, not always but most frequently while in ffox 3 (garbage) but I found disabling dpms stopped the freezes.

turned off screen saver
turned off all bells and whistles

to no avail, the only thing making the difference is the dpms

I went from freezing every several hours to not freezing at all

I used 

sudo xset -dpms

I have a desktop and don't need that energy saver crap

I have an Athlon 2000+ 
nvidia gforce 6200 agp

best to you

---

### Post by mtx512 on 2008-10-20
The solution to this problem was installing **xserver-xorg-video-intel_2.3.2-2+lenny2_i386.deb** and **libdrm2_2.3.1-1_i386.deb** from [http://packages.debian.org/testing/](http://packages.debian.org/testing/) then change the screensaver from Molecule to Blank Screen to avoid freezing while in screensaver mode. The system has now been used for months without any problems at all.

---


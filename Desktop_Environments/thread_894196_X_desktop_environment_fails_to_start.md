---
title: "X desktop environment fails to start"
date: 2008-08-19
forum: Desktop Environments
---

### Post by Delta62 on 2008-08-19
Hi everyone,

I have a problem whenever I ty to boot into any variant of ubuntu. 

When booting, the computer automatically starts as text based (no GUI). if I type:
```
startx
```
into terminal, I get 2 error messages:

xinit: connection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): Server error.

Please help me get a desktop running here :)

---

### Post by prshah on 2008-08-19
> **Delta62 said:**
> 
```
startx
```
into terminal, I get 2 error messages:
xinit: connection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): Server error.


There will be other more relevant errors before this; post those (Most likely: "display not found").

You should also post your /var/log/Xorg.0.log file (or just the last part of it) for further clues:```
tail /var/log/Xorg.0.log
``` Please pay attention to the case of the filename.

---

### Post by Delta62 on 2008-08-19
Here's what is shown before the two error messages:

```

X.org X Server 1.4.0.90
Release Date: 5 sept 2007
[....]
Fatal server error:
no screens found

waiting for X server to begin accepting connections
giving up
```


And here's the log file. I included the whole thing, because I do not know what you wanted, exactly. Sorry for the length:
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
Current Operating System: Linux Delta40 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 18 21:26:08 2008
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
(II) PCI: 00:00:0: chip 1106,3205 card 1106,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 1814,0201 card 1462,6833 rev 01 class 02,80,00 hdr 00
(II) PCI: 00:0a:0: chip 1217,6972 card 1001,0000 rev 00 class 06,07,00 hdr 02
(II) PCI: 00:10:0: chip 1106,3038 card 14ff,c905 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 14ff,c905 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 14ff,c905 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 14ff,c905 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 14ff,1205 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 14ff,0408 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 14ff,1005 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 14ff,0207 rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1106,7205 card 14ff,030d rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdde00000 - 0xdfefffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd5d00000 - 0xddcfffff (0x8000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,5), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x24000000 - 0x27ffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x23ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x7205) rev 1, Mem @ 0xd8000000/26, 0xde000000/24, BIOS @ 0xdfef0000/16
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdfffde00 - 0xdfffdeff (0x100) MX[B]
	[1] -1	0	0xdfffdf00 - 0xdfffdfff (0x100) MX[B]
	[2] -1	0	0xdfffe000 - 0xdfffffff (0x2000) MX[B]
	[3] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[4] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[5] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[6] -1	0	0xd8000000 - 0xdbffffff (0x4000000) MX[B](B)
	[7] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[9] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[10] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfffde00 - 0xdfffdeff (0x100) MX[B]
	[1] -1	0	0xdfffdf00 - 0xdfffdfff (0x100) MX[B]
	[2] -1	0	0xdfffe000 - 0xdfffffff (0x2000) MX[B]
	[3] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[4] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[5] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[6] -1	0	0xd8000000 - 0xdbffffff (0x4000000) MX[B](B)
	[7] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[9] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[10] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
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
	[4] -1	0	0xdfffde00 - 0xdfffdeff (0x100) MX[B]
	[5] -1	0	0xdfffdf00 - 0xdfffdfff (0x100) MX[B]
	[6] -1	0	0xdfffe000 - 0xdfffffff (0x2000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[9] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdbffffff (0x4000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[16] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
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
(II) Matched openchrome from file name openchrome.ids in autoconfig
(II) Matched via from file name via.ids in autoconfig
(==) Matched openchrome for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.2.901
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
(II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
	K8M800/K8N800, PM800/PM880/CN400, P4M800Pro/VN800/CN700,
	K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset KM400/KN400 found
(!!) VIA Technologies does not support or endorse this driver in any way.
(!!) For support, refer to http://www.openchrome.org/.
(!!) (development build, compiled on Wed Jan 23 11:46:14 2008)
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffde00 - 0xdfffdeff (0x100) MX[B]
	[5] -1	0	0xdfffdf00 - 0xdfffdfff (0x100) MX[B]
	[6] -1	0	0xdfffe000 - 0xdfffffff (0x2000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[9] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdbffffff (0x4000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[16] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffde00 - 0xdfffdeff (0x100) MX[B]
	[5] -1	0	0xdfffdf00 - 0xdfffdfff (0x100) MX[B]
	[6] -1	0	0xdfffe000 - 0xdfffffff (0x2000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[9] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdbffffff (0x4000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) CHROME(0): VIAPreInit
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) CHROME(0): VIAGetRec
(II) CHROME(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) CHROME(0): Depth 24, (==) framebuffer bpp 32
(==) CHROME(0): RGB weight 888
(==) CHROME(0): Default visual is TrueColor
(--) CHROME(0): Chipset: "KM400/KN400"
(--) CHROME(0): Chipset revision: 132
(--) CHROME(0): Probed amount of VideoRAM = 32768 kB
(II) CHROME(0): Setting up default chipset options...
(II) CHROME(0): VIASetupDefaultOptions
(II) CHROME(0): Starting to parse config file options...
(==) CHROME(0): ShadowFB is disabled.
(==) CHROME(0): Acceleration is enabled.
(==) CHROME(0): Using XAA acceleration architecture.
(==) CHROME(0): Hardware two-color cursors; software full-color cursors.
(==) CHROME(0): GPU virtual command queue will be enabled.
(==) CHROME(0): DRI IRQ will be disabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be enabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be used for 2D acceleration.
(==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
(==) CHROME(0): Will not enable VBE modes.
(==) CHROME(0): VBE VGA register save & restore will not be used
	if VBE modes are enabled.
(==) CHROME(0): Xv Bandwidth check is enabled.
(==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
(==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
(==) CHROME(0): Digital output bus width is 12 bits.
(==) CHROME(0): DVI Center is disabled.
(==) CHROME(0): Panel size is not selected from config file.
(==) CHROME(0): Panel will not be forced.
(==) CHROME(0): TV dotCrawl is disabled.
(==) CHROME(0): TV deflicker is set to 0.
(==) CHROME(0): No default TV type is set.
(==) CHROME(0): No default TV output signal type is set.
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xde000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xde200000 with size 0x20000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) CHROME(0): Will not print VGA registers.
(==) CHROME(0): Will not scan I2C buses.
(II) CHROME(0): ...Finished parsing config file options.
(--) CHROME(0): Detected Averatec 322x.
(II) CHROME(0): Detected MemClk 5
(II) CHROME(0): ViaGetMemoryBandwidth
(II) CHROME(0): Detected TV standard: PAL.
(==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) CHROME(0): ViaI2CInit
(II) CHROME(0): ViaI2CBus1Init
(II) CHROME(0): I2C bus "I2C bus 1" initialized.
(II) CHROME(0): ViaI2cBus2Init
(II) CHROME(0): I2C bus "I2C bus 2" initialized.
(II) CHROME(0): ViaI2CBus3Init
(II) CHROME(0): I2C bus "I2C bus 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) CHROME(0): I2C device "I2C bus 1:ddc2" removed.
(II) CHROME(0): ViaOutputsDetect
(II) CHROME(0): Enabling panel from PCI-subsystem ID information.
(II) CHROME(0): VIATVDetect
(II) CHROME(0): ViaOutputsSelect
(II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
(II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x07
(II) CHROME(0): ViaOutputsSelect: Panel.
(II) CHROME(0): ViaModesAttach
(II) CHROME(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) CHROME(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) CHROME(0): Unable to estimate virtual size
(II) CHROME(0): Clock range:  20.00 to 230.00 MHz
(II) CHROME(0): ViaValidMode: Validating 640x350 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): VIAGetPanelSize
(II) CHROME(0): VIAGetPanelSizeFromDDCv1
(II) CHROME(0): VIAGetPanelSizeFromDDCv2
(WW) CHROME(0): Unable to retrieve PanelSize: using default (1024x768)
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "640x350" (unknown reason)
(II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x400 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "640x400" (unknown reason)
(II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 720x400 (35500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "720x400" (unknown reason)
(II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "640x480" (unknown reason)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "640x480" (unknown reason)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "640x480" (unknown reason)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (36000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "640x480" (unknown reason)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "800x600" (unknown reason)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "800x600" (unknown reason)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "800x600" (unknown reason)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "800x600" (unknown reason)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (56300)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "800x600" (unknown reason)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (44900)
(II) CHROME(0): Not using default mode "1024x768" (interlace mode not supported)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1024x768" (unknown reason)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1024x768" (unknown reason)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1024x768" (unknown reason)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (94500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1024x768" (unknown reason)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1152x864" (unknown reason)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1280x960" (unknown reason)
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (148500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1280x960" (unknown reason)
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1280x1024" (unknown reason)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1280x1024" (unknown reason)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (157500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1280x1024" (unknown reason)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (162000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1600x1200" (unknown reason)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (175500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1600x1200" (unknown reason)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (189000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1600x1200" (unknown reason)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (202500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1600x1200" (unknown reason)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (229500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1600x1200" (unknown reason)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1792x1344 (204800)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1792x1344" (unknown reason)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1856x1392 (218300)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1856x1392" (unknown reason)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "832x624" (unknown reason)
(II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x768 (80140)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1280x768" (unknown reason)
(II) CHROME(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x800 (83460)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1280x800" (unknown reason)
(II) CHROME(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x768 (64995)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1152x768" (unknown reason)
(II) CHROME(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (121500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1152x864" (unknown reason)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (122000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1400x1050" (unknown reason)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (151000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1400x1050" (unknown reason)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (155800)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): CrtcHSyncEnd out of range.
(II) CHROME(0): Not using default mode "1400x1050" (horizontal sync too wide)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (184000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1400x1050" (unknown reason)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1440x900 (108840)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): CrtcHSyncEnd out of range.
(II) CHROME(0): Not using default mode "1440x900" (horizontal sync too wide)
(II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1024 (106910)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1600x1024" (unknown reason)
(II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (147140)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1680x1050" (unknown reason)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1920x1200 (193160)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1920x1200" (unknown reason)
(II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1920x1200 (230000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1920x1200" (unknown reason)
(II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (25312)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 640x480
(II) CHROME(0): ViaGetResolutionIndex: 0
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "640x480" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 800x600 (39822)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 800x600
(II) CHROME(0): ViaGetResolutionIndex: 1
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "800x600" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65028)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1024x768
(II) CHROME(0): ViaGetResolutionIndex: 2
(II) CHROME(0): ViaPanelGetIndex:index: 2 (1024x768)
(II) CHROME(0): ViaComputeDotClock 65028 : 866d : 866d
(II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (81613)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1152x864
(II) CHROME(0): ViaGetResolutionIndex: 3
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1152x864" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108280)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1280x1024
(II) CHROME(0): ViaGetResolutionIndex: 4
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1280x1024" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (161793)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1600x1200
(II) CHROME(0): ViaGetResolutionIndex: 5
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1600x1200" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1280x768 (81135)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1280x768
(II) CHROME(0): ViaGetResolutionIndex: 7
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1280x768" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (108280)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1280x960
(II) CHROME(0): ViaGetResolutionIndex: 8
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1280x960" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 848x480 (33750)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 848x480
(II) CHROME(0): ViaGetResolutionIndex: 10
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "848x480" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (122726)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1400x1050
(II) CHROME(0): ViaGetResolutionIndex: 11
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1400x1050" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 720x480 (26591)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 720x480
(II) CHROME(0): ViaGetResolutionIndex: 12
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "720x480" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 720x576 (32663)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 720x576
(II) CHROME(0): ViaGetResolutionIndex: 13
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "720x576" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1024x512 (41164)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1024x512
(II) CHROME(0): ViaGetResolutionIndex: 14
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1024x512" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 856x480 (31704)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 856x480
(II) CHROME(0): ViaGetResolutionIndex: 15
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "856x480" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1024x576 (46981)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1024x576
(II) CHROME(0): ViaGetResolutionIndex: 16
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1024x576" (unknown reason)
(WW) CHROME(0): Mode pool is empty
(EE) CHROME(0): No valid modes found
(II) CHROME(0): VIAFreeRec
(II) CHROME(0): VIAUnmapMem
(II) CHROME(0): VIAFreeScreen
(II) CHROME(0): VIAFreeRec
(II) UnloadModule: "openchrome"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

---

### Post by prshah on 2008-08-19
> **Delta62 said:**
> 
```

Fatal server error:
no screens found

```


As expected. As to your log file, yikes! I don't know where to begin troubleshooting it!

Essentially, whatever modes (resolution, color, refresh rate settings) your display driver (CHROME) suggests is not acceptable to the monitor, and whatever your monitor suggests it not acceptable to the display driver.

Since this is auto-detection, it is probably (in this case) sub-optimal; you can force a usable config out of this.

Can you post your "/etc/X11/xorg.conf" file? It's probably useless, but if there are some entries already there, it will be easier to change them rather than put in the whole thing from scratch.

Are you running a laptop, or a desktop with a LCD monitor? In such case, what is the optimal (native) resolution of the lcd panel? This is required.

Can you also post back output of ```
lspci -vv | grep -i -A 5 "01:00"
```

---

### Post by Delta62 on 2008-08-19
I am running an averatec 3200 series laptop. The native resolution of the screen is, I beleive, 1024X768.

Here is the xorg.conf file:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
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

```

And here is the output of the command:
```

01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome]
Integrated Video (rev 01) (prog-if 00 [VGA Controller])
	Subsystem: TWINHEAD INTERNATIONAL Corp Unknown Device 030d
	Control: I/O+ Mem+ Busmaster+ SpecXyxle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- >MAbort- >SERR- <PERR-
	Latency: 32 (500ns min)
	Interrupt: pin A routed to IRQ 11

```

---

### Post by banned bandit on 2008-08-19
I had the same issues with my averatec laptop.  The way I finaly got the display to work is I installed ubuntu 7.10 which automaticaly detects the display properly then updated to 8.04LTS after the install.  You will need a working network or WIFI card.  I had to used a old PCMCIA linsys wireless B card to get wifi working.  the onboard doesn't wor properly.

---


---
title: "GDM Segfault"
date: 2008-05-18
forum: Desktop Environments
---

### Post by TimHeckman on 2008-05-18
I've had this issue every since I updated to Hard Heron, and needless to say I've not been pleased.  This release seems to be unstable, compared to 7.10 -- And now I want to go back. :(

So here's the story.  I have an emerald theme I am running, and every time I reboot and attempt to login I enter my Username and Password and then a black screen appears.  About 3 seconds later I get returned to the login screen.  

I log back in, and the window manager is using the default "Human" theme.  I type ALT + F2 and use emerald --replace and the theme reapplies and works fine.

So, I got curious and looked in my kern.log and here's what I see:

```
May 18 14:19:26 trance kernel: [  285.202202] gdm[6139]: segfault at 7672657f eip b78037e2 esp bfb6fba0 error 6
```

Now we'll grab it from the syslog

```
May 18 14:19:26 trance kernel: [  285.202202] gdm[6139]: segfault at 7672657f eip b78037e2 esp bfb6fba0 error 6
May 18 14:19:26 trance gdm[6138]: WARNING: gdm_cleanup_children: child 6139 crashed of signal 11 
May 18 14:19:26 trance gdm[6138]: WARNING: gdm_cleanup_children: Slave crashed, killing its children 
```

Not sure if this is needed, but I'll throw in the Xorg log.

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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux trance 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 18 14:19:28 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL 1707FP"
(**) |   |-->Device "nVidia Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) PCI: 00:00:0: chip 8086,2578 card 1028,0157 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2579 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 8086,257e card 0000,0000 rev 02 class 08,80,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 1028,0157 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1028,0157 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1028,0157 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1028,0157 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1028,0157 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1028,0157 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1028,0157 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1028,0157 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1028,0157 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 10de,01b9 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 14e4,4212 card 1028,0001 rev 02 class 07,03,00 hdr 00
(II) PCI: 02:08:0: chip 8086,1050 card 1028,0157 rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd000000 - 0xfeafffff (0x1b00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfcf00000 - 0xfcffffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfd000000/24, 0xf0000000/27, BIOS @ 0xfea00000/17
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
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xefffffff to 0xe7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfcfff000 - 0xfcffffff (0x1000) MX[B]
	[1] -1	0	0xfcffe000 - 0xfcffefff (0x1000) MX[B]
	[2] -1	0	0xfebff900 - 0xfebff9ff (0x100) MX[B]
	[3] -1	0	0xfebffa00 - 0xfebffbff (0x200) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[5] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[6] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[7] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[8] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[12] -1	0	0x0000df30 - 0x0000df3f (0x10) IX[B]
	[13] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[14] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[15] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[16] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[17] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[18] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[19] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[20] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[28] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[29] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfcfff000 - 0xfcffffff (0x1000) MX[B]
	[1] -1	0	0xfcffe000 - 0xfcffefff (0x1000) MX[B]
	[2] -1	0	0xfebff900 - 0xfebff9ff (0x100) MX[B]
	[3] -1	0	0xfebffa00 - 0xfebffbff (0x200) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[5] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[6] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[7] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[8] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[12] -1	0	0x0000df30 - 0x0000df3f (0x10) IX[B]
	[13] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[14] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[15] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[16] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[17] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[18] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[19] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[20] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[28] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[29] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
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
	[4] -1	0	0xfcfff000 - 0xfcffffff (0x1000) MX[B]
	[5] -1	0	0xfcffe000 - 0xfcffefff (0x1000) MX[B]
	[6] -1	0	0xfebff900 - 0xfebff9ff (0x100) MX[B]
	[7] -1	0	0xfebffa00 - 0xfebffbff (0x200) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[11] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[18] -1	0	0x0000df30 - 0x0000df3f (0x10) IX[B]
	[19] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[20] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[21] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[22] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[23] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[24] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[25] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[26] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
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
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:55:38 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcfff000 - 0xfcffffff (0x1000) MX[B]
	[5] -1	0	0xfcffe000 - 0xfcffefff (0x1000) MX[B]
	[6] -1	0	0xfebff900 - 0xfebff9ff (0x100) MX[B]
	[7] -1	0	0xfebffa00 - 0xfebffbff (0x200) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[11] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[18] -1	0	0x0000df30 - 0x0000df3f (0x10) IX[B]
	[19] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[20] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[21] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[22] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[23] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[24] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[25] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[26] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcfff000 - 0xfcffffff (0x1000) MX[B]
	[5] -1	0	0xfcffe000 - 0xfcffefff (0x1000) MX[B]
	[6] -1	0	0xfebff900 - 0xfebff9ff (0x100) MX[B]
	[7] -1	0	0xfebffa00 - 0xfebffbff (0x200) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[11] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[21] -1	0	0x0000df30 - 0x0000df3f (0x10) IX[B]
	[22] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[23] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[24] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[25] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[26] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[27] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[28] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[29] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[32] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[33] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[36] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[37] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[38] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 (NV34) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.22.bc
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     DELL 1707FP (CRT-0)
(--) NVIDIA(0): DELL 1707FP (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcfff000 - 0xfcffffff (0x1000) MX[B]
	[5] -1	0	0xfcffe000 - 0xfcffefff (0x1000) MX[B]
	[6] -1	0	0xfebff900 - 0xfebff9ff (0x100) MX[B]
	[7] -1	0	0xfebffa00 - 0xfebffbff (0x200) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[11] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[21] -1	0	0x0000df30 - 0x0000df3f (0x10) IX[B]
	[22] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[23] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[24] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[25] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[26] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[27] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[28] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[29] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[32] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[33] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[36] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[37] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[38] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) Initializing extension GLX
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
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
```

And the GDM log

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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux trance 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 18 14:19:28 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
SetClientVersion: 0 9
```

Now here's the text that keeps catching my eye:

[quote=log headers]This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.[/quote]

Is Ubuntu being shipped with a pre-release version of X?  If so, why?  Deadlines are nice to have, but it's bad news to release something if it is indeed a pre-release.  Assuming that Ubuntu was shipped with a pre-release, I think it should have been announced or something should have been said.  I would have rather stayed on 7.10 and waited for the stable.  

Not that this crashing is a critical issue, it's a huge annoyance.

Does anyone have any similar experiences, any fixes, anything!?

If anyone could help out, it would be greatly appreciated.

Thanks Beforehand,

Tim Heckman (aka eLement)

---

### Post by TimHeckman on 2008-05-25
Renewing Topic -- Someone read please!

---

### Post by buntunub on 2008-05-25
Ubuntu is not shipping with the pre-release Xorg, unlike Fedora 9. Im really not sure whats causing that segfault. If you have a stable GDM using Ubuntu defaults, then just go with that instead of messing around with weird Emerald themes.

---

### Post by TimHeckman on 2008-05-25
> **buntunub said:**
> Ubuntu is not shipping with the pre-release Xorg, unlike Fedora 9. Im really not sure whats causing that segfault. If you have a stable GDM using Ubuntu defaults, then just go with that instead of messing around with weird Emerald themes.

I was curious about the header I kept seeing.

Thanks mate!

---


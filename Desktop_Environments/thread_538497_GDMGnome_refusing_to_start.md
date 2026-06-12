---
title: "GDM/Gnome refusing to start"
date: 2007-08-30
forum: Desktop Environments
---

### Post by unca.paka on 2007-08-30
Hello all,
I was checking out the forums tonight when i stumbled upon Pypanel, installed it but couldnt get it running. So i stumbled upon this link, [http://ubuntuforums.org/showthread.php?t=327514]("http://ubuntuforums.org/showthread.php?t=327514")

After following that, everything worked out fine. Then I noticed my startup apps were missing from the panel(network manager, compiz, etc) so decided to restart X. After doing that, I was greeted with GDM just flashing at me.

After a few seconds, I could see my login screen show up, then dissapear. So, no log-in.
After checking a few threads, I've gotten KDM to work, but GDM and Gnome all together will not load.

Xorg.log
```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux EVA-02 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 30 00:22:00 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "0"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1849,2770 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1849,0888 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1849,27c8 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1849,27c9 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1849,27ca rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1849,27cb rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1849,27cc rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b8 card 1849,27b8 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1849,27df rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1849,27c0 rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1849,27da rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10ec,8168 card 1849,8168 rev 01 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 10de,0392 card 1458,3438 rev a1 class 03,00,00 hdr 00
(II) PCI: 04:02:0: chip 14b9,4800 card 0000,0000 rev 01 class 02,80,00 hdr 00
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
(II) Bus 3: bridge is at (0:1:0), (0,3,3), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfc000000 - 0xfeafffff (0x2b00000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xcff00000 - 0xcfffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:1), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfbf00000 - 0xfbffffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(3:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, I/O @ 0xdc00/7, BIOS @ 0xfeae0000/17
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
	[0] -1	0	0xfebffc00 - 0xfebffc7f (0x80) MX[B]
	[1] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B]
	[2] -1	0	0xfbefbc00 - 0xfbefbfff (0x400) MX[B]
	[3] -1	0	0xfbefc000 - 0xfbefffff (0x4000) MX[B]
	[4] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[5] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000e880 - 0x0000e8bf (0x40) IX[B]
	[9] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[10] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[11] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[12] -1	0	0x0000a880 - 0x0000a88f (0x10) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[15] -1	0	0x0000b080 - 0x0000b083 (0x4) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[23] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[25] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebffc00 - 0xfebffc7f (0x80) MX[B]
	[1] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B]
	[2] -1	0	0xfbefbc00 - 0xfbefbfff (0x400) MX[B]
	[3] -1	0	0xfbefc000 - 0xfbefffff (0x4000) MX[B]
	[4] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[5] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000e880 - 0x0000e8bf (0x40) IX[B]
	[9] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[10] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[11] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[12] -1	0	0x0000a880 - 0x0000a88f (0x10) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[15] -1	0	0x0000b080 - 0x0000b083 (0x4) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[23] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[25] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
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
	[4] -1	0	0xfebffc00 - 0xfebffc7f (0x80) MX[B]
	[5] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B]
	[6] -1	0	0xfbefbc00 - 0xfbefbfff (0x400) MX[B]
	[7] -1	0	0xfbefc000 - 0xfbefffff (0x4000) MX[B]
	[8] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e880 - 0x0000e8bf (0x40) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[17] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[18] -1	0	0x0000a880 - 0x0000a88f (0x10) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[21] -1	0	0x0000b080 - 0x0000b083 (0x4) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[29] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[31] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
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
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebffc7f (0x80) MX[B]
	[5] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B]
	[6] -1	0	0xfbefbc00 - 0xfbefbfff (0x400) MX[B]
	[7] -1	0	0xfbefc000 - 0xfbefffff (0x4000) MX[B]
	[8] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e880 - 0x0000e8bf (0x40) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[17] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[18] -1	0	0x0000a880 - 0x0000a88f (0x10) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[21] -1	0	0x0000b080 - 0x0000b083 (0x4) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[29] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[31] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebffc7f (0x80) MX[B]
	[5] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B]
	[6] -1	0	0xfbefbc00 - 0xfbefbfff (0x400) MX[B]
	[7] -1	0	0xfbefc000 - 0xfbefffff (0x4000) MX[B]
	[8] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e880 - 0x0000e8bf (0x40) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[20] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[21] -1	0	0x0000a880 - 0x0000a88f (0x10) IX[B]
	[22] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[24] -1	0	0x0000b080 - 0x0000b083 (0x4) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[32] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[33] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[34] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[35] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "MetaModes" "1280x1024_60 +0+0; 1024x768 +0+0; 832x624 +0+0; 800x600 +0+0; 640x480 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.51.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:3:0:0:
(--) NVIDIA(0):     AY_ (CRT-0)
(--) NVIDIA(0): AY_ (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024_60+0+0"
(II) NVIDIA(0):     "1024x768+0+0"
(II) NVIDIA(0):     "832x624+0+0"
(II) NVIDIA(0):     "800x600+0+0"
(II) NVIDIA(0):     "640x480+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfebffc00 - 0xfebffc7f (0x80) MX[B]
	[8] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B]
	[9] -1	0	0xfbefbc00 - 0xfbefbfff (0x400) MX[B]
	[10] -1	0	0xfbefc000 - 0xfbefffff (0x4000) MX[B]
	[11] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] 0	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000e880 - 0x0000e8bf (0x40) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[24] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[25] -1	0	0x0000a880 - 0x0000a88f (0x10) IX[B]
	[26] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[28] -1	0	0x0000b080 - 0x0000b083 (0x4) IX[B]
	[29] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[32] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[36] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[37] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[38] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[39] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024_60+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

```

Xorg.conf
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
#    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AY_"
    HorizSync       15.0 - 79.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x1024_60 +0+0; 1024x768 +0+0; 832x624 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection



```

I've tried init.rc'ing gdm all the way to next week, removed pypanel, reconfiguring GDM(dpkg).
Nothing works. Me thinks its the last line of Xorg.log thats causing the problems.
While following the guide in the link above, it asked me to downgrade 2 packages, but of course, I didnt make of note of which ones it downgraded.

All in all, im pretty upset. Just got gnome to way I like it, and it goes BOOM.
Any help would be appreciated, thanks in advance.

---

### Post by tzulberti on 2007-08-30
Try runing "sudo dpkg-reconfigure xserver-xorg". And then:
"sudo /etc/init.d/kdm stop"
"sudo /etc/init.d/gdm start"

---

### Post by unca.paka on 2007-08-31
I've done that, took all the defaults in the new xorg, but GDM still refuses to start. I can start fluxbox, and KDE sessions no problem. But Gnome is really hating life I guess. Id really like to get Gnome/GDM back up and running, just not into the other WM's.

Id also like to figure where the problem came from, very puzzling.

---

### Post by bmorency on 2007-08-31
have you done this yet?

```
sudo aptitude install ubuntu-desktop
```

maybe something got delete that shouldn't have?

---


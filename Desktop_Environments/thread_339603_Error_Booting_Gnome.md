---
title: "Error Booting Gnome"
date: 2007-01-16
forum: Desktop Environments
---

### Post by tspec on 2007-01-16
I'm currently getting the error when booting gnome on edgy: fatal IO error 104 (Connection reset by peer) on X server "0:0" after 0 requests (0 known processed) with 0 events remaining.

The graphics card in question is an AGP Nvidia 6200 NV44A. The install was working fine, how this came about was that I was logged in as 1 user, switched to another, then when I went to switch back I accidently hit restart which is what caused it.

I have gone through a fair few potential solutions but nothing has worked as yet. So I've tried:
dpkg-reconfigure xserver-xorg
dpkg-reconfigure gdm

apt-get install update
apt-get install upgrade

Tried, removing all the resolutions besides 640x480 and tried changing the "device" to nv rather than nvidia and back again. Also tried setting the monitor back as a generic monitor.

Anyway, if anyone has any more suggestions, that would be greatly appreciated. Seems strange that what I did would cause this error, wouldn't mind testing it on another box but I don't have any currently lying around that I'd want to potentially screw up :)

Here's the output from Xorg.0.log if that helps:
```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux gumby 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 16 14:55:40 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "LG Flatron L1710M"
(**) |   |-->Device "NVIDIA GeForce 6200"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3099 card 1043,807f rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b099 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 13f6,0111 card 1043,80e2 rev 10 class 04,01,00 hdr 00
(II) PCI: 00:09:0: chip 1106,3038 card 1043,8080 rev 50 class 0c,03,00 hdr 80
(II) PCI: 00:09:1: chip 1106,3038 card 1043,8080 rev 50 class 0c,03,00 hdr 80
(II) PCI: 00:09:2: chip 1106,3104 card 1043,8080 rev 51 class 0c,03,20 hdr 80
(II) PCI: 00:0e:0: chip 1033,0035 card 1799,0001 rev 41 class 0c,03,10 hdr 80
(II) PCI: 00:0e:1: chip 1033,0035 card 1799,0001 rev 41 class 0c,03,10 hdr 00
(II) PCI: 00:0e:2: chip 1033,00e0 card 1799,0002 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:0f:0: chip 1186,4c00 card 1186,4c00 rev 11 class 02,00,00 hdr 00
(II) PCI: 00:10:0: chip 10b7,9200 card 10b7,1000 rev 74 class 02,00,00 hdr 00
(II) PCI: 00:11:0: chip 1106,3147 card 1043,808c rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1043,808c rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:2: chip 1106,3038 card 1043,808c rev 23 class 0c,03,00 hdr 00
(II) PCI: 00:11:3: chip 1106,3038 card 1043,808c rev 23 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0221 card 1682,2152 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xcd000000 - 0xcfdfffff (0x2e00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xcff00000 - 0xdfffffff (0x10100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 6200 rev 161, Mem @ 0xce000000/24, 0xd0000000/28, 0xcd000000/24, BIOS @ 0xcffe0000/17
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
	[0] -1	0	0xca000000 - 0xca00007f (0x80) MX[B]
	[1] -1	0	0xca800000 - 0xca803fff (0x4000) MX[B]
	[2] -1	0	0xcb000000 - 0xcb0000ff (0x100) MX[B]
	[3] -1	0	0xcb800000 - 0xcb800fff (0x1000) MX[B]
	[4] -1	0	0xcc000000 - 0xcc000fff (0x1000) MX[B]
	[5] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[8] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xca000000 - 0xca00007f (0x80) MX[B]
	[1] -1	0	0xca800000 - 0xca803fff (0x4000) MX[B]
	[2] -1	0	0xcb000000 - 0xcb0000ff (0x100) MX[B]
	[3] -1	0	0xcb800000 - 0xcb800fff (0x1000) MX[B]
	[4] -1	0	0xcc000000 - 0xcc000fff (0x1000) MX[B]
	[5] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[8] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
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
	[4] -1	0	0xca000000 - 0xca00007f (0x80) MX[B]
	[5] -1	0	0xca800000 - 0xca803fff (0x4000) MX[B]
	[6] -1	0	0xcb000000 - 0xcb0000ff (0x100) MX[B]
	[7] -1	0	0xcb800000 - 0xcb800fff (0x1000) MX[B]
	[8] -1	0	0xcc000000 - 0xcc000fff (0x1000) MX[B]
	[9] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[12] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
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
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9629
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9629
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  1.0-9629  Wed Nov  1 19:31:54 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xca000000 - 0xca00007f (0x80) MX[B]
	[5] -1	0	0xca800000 - 0xca803fff (0x4000) MX[B]
	[6] -1	0	0xcb000000 - 0xcb0000ff (0x100) MX[B]
	[7] -1	0	0xcb800000 - 0xcb800fff (0x1000) MX[B]
	[8] -1	0	0xcc000000 - 0xcc000fff (0x1000) MX[B]
	[9] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[12] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xca000000 - 0xca00007f (0x80) MX[B]
	[5] -1	0	0xca800000 - 0xca803fff (0x4000) MX[B]
	[6] -1	0	0xcb000000 - 0xcb0000ff (0x100) MX[B]
	[7] -1	0	0xcb800000 - 0xcb800fff (0x1000) MX[B]
	[8] -1	0	0xcc000000 - 0xcc000fff (0x1000) MX[B]
	[9] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[12] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[23] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

---

### Post by tspec on 2007-01-16
Fixed. Ended up reinstalling the nvidia drivers from scratch.

---


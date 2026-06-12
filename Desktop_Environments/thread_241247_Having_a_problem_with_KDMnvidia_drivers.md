---
title: "Having a problem with KDM/nvidia drivers"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Phil Donahue on 2006-08-22
I seem to be having a problem with the proprietary nvidia drivers.  When I boot up, Kubuntu displays all of its messages, then stops and just shows the splash screen with the progress bar.  X does start (I can go into the other terminals and switch to my backup copy of xorg.conf), however I can't restart it without rebooting the entire system.  I'm attaching a copy of the Xorg.0.log if that helps.  Thanks.

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux hyphen2mobile 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 22 02:31:22 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce Go 6600]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2590 card 1043,1888 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2591 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,2668 card 1043,1964 rev 04 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 04 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 1043,1888 rev 04 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1043,1888 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1043,1888 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1043,1888 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1043,1888 rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev d4 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2641 card 0000,0000 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2653 card 1043,1888 rev 04 class 01,01,80 hdr 00
(II) PCI: 01:00:0: chip 10de,0144 card 1043,1889 rev a2 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 11ab,4320 card 1043,1885 rev 13 class 02,00,00 hdr 00
(II) PCI: 03:01:0: chip 1180,0476 card d000,0000 rev ac class 06,07,00 hdr 82
(II) PCI: 03:01:1: chip 1180,0476 card dc00,0000 rev ac class 06,07,00 hdr 82
(II) PCI: 03:01:2: chip 1180,0552 card 1043,1888 rev 04 class 0c,00,10 hdr 80
(II) PCI: 03:03:0: chip 8086,4223 card 8086,1000 rev 05 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,8), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa900000 - 0xfe9fffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbfe00000 - 0xdfefffff (0x20100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,11), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x54ffffff (0x5000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 4: bridge is at (3:1:0), (3,4,7), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x51ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 8: bridge is at (3:1:1), (3,8,11), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 8 I/O range:
	[0] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 8 prefetchable memory range:
	[0] -1	0	0x52000000 - 0x53ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce Go 6600] rev 162, Mem @ 0xfd000000/24, 0xc0000000/28, 0xfc000000/24, BIOS @ 0xfe9e0000/17
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
	[0] -1	0	0xfeafa000 - 0xfeafafff (0x1000) MX[B]
	[1] -1	0	0xfeafb800 - 0xfeafbfff (0x800) MX[B]
	[2] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[3] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[4] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[5] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[6] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[10] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[12] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[14] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeafa000 - 0xfeafafff (0x1000) MX[B]
	[1] -1	0	0xfeafb800 - 0xfeafbfff (0x800) MX[B]
	[2] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[3] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[4] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[5] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[6] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[10] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[12] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[14] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
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
	[4] -1	0	0xfeafa000 - 0xfeafafff (0x1000) MX[B]
	[5] -1	0	0xfeafb800 - 0xfeafbfff (0x800) MX[B]
	[6] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[7] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[9] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[18] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[20] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafa000 - 0xfeafafff (0x1000) MX[B]
	[5] -1	0	0xfeafb800 - 0xfeafbfff (0x800) MX[B]
	[6] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[7] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[9] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[18] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[20] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafa000 - 0xfeafafff (0x1000) MX[B]
	[5] -1	0	0xfeafb800 - 0xfeafbfff (0x800) MX[B]
	[6] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[7] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[9] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[21] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[23] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

---

### Post by b_martinez on 2006-08-22
Boot your machine into 'recovery' mode. Once booted and logged in (text mode) type the command "lsmod |less" (without the quotation marks) to list the installed kernel modules. Use the up/down arrows to see the whole list. Do you see nvidia listed? 
According to your log, you have the xorg.conf file edited to load the nvidia driver, but the kernel you are booting to does not have the module. Perhaps the command "insmod nvidia" will load the kernel module for you.
Did you update to a newer kernel? If so, then you need to boot to that kernel in recovery mode and use apt-get to install the nvidia drivers for that particular kernel. 
hth
Bill

---


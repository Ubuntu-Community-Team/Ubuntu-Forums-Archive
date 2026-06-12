---
title: "Warsow/OpenGL direct rendering error on startup of game."
date: 2007-11-15
forum: Gaming &amp; Leisure
---

### Post by The Pinny Parlour on 2007-11-15
I'm getting this error upon starting Warsow, any ideas on what to do to correct it?

Youre OpenGL installation doesn't support direct
rendering. If you have an NVIDIA or an ATI card you'll probably need to
install the propritary driver.

Thanks

---

### Post by aoanla on 2007-11-16
> **The Pinny Parlour said:**
> I'm getting this error upon starting Warsow, any ideas on what to do to correct it?

Youre OpenGL installation doesn't support direct
rendering. If you have an NVIDIA or an ATI card you'll probably need to
install the propritary driver.

Thanks

I would suggest doing as it says...

(A hint - System menu -> Administration -> Restricted Drivers Manager
to turn on the repository version of the restricted/proprietary drivers for your graphics card.)

---

### Post by The Pinny Parlour on 2007-11-17
> **aoanla said:**
> I would suggest doing as it says...

(A hint - System menu -> Administration -> Restricted Drivers Manager
to turn on the repository version of the restricted/proprietary drivers for your graphics card.)

Thanks for your reply.  I checked the area you mentioned and it's already turned on.

---

### Post by aoanla on 2007-11-17
Okay.

So, can you type 

glxinfo | grep render

into a terminal and tell us what the output is?

---

### Post by The Pinny Parlour on 2007-11-17
Thank you for your assistance.

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: GeForce 7600 GS/AGP/SSE/3DNOW!

---

### Post by aoanla on 2007-11-18
Right, so your problem is that the restricted driver isn't working, even though it says it is turned on. (If it was working, you'd get a yes for Direct rendering...)

Can you post the contents of your /var/log/Xorg.0.log, please? It is likely that if there's a problem loading the driver, it will be listed in there...

Have you previously tried to install newer versions of the nVidia driver, or otherwise messed with the driver install?

---

### Post by The Pinny Parlour on 2007-11-18
Again thank you.


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux ian-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 19 06:41:19 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0741 card 1849,0741 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0003 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0963 card 0000,0000 rev 25 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1849,5513 rev 00 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1849,7012 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7002 card 1849,7002 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1849,0900 rev 90 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,02e1 card 0000,0000 rev a2 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xcbd00000 - 0xcfefffff (0x4200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xaba00000 - 0xcbbfffff (0x20200000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 7600 GS rev 162, Mem @ 0xce000000/24, 0xb0000000/28, 0xcd000000/24, BIOS @ 0xcfee0000/17
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd3ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[1] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[2] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[3] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[6] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[7] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[13] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[1] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[2] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[3] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[6] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[7] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[13] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
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
	[4] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[5] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[6] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[11] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[5] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[6] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[11] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[5] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[6] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[11] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[21] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[22] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.16.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(0):     CMO CMC 22 W (DFP-0)
(--) NVIDIA(0): CMO CMC 22 W (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): CMO CMC 22 W (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1600x1200"; removing.
(WW) NVIDIA(0): No valid modes for "1280x854"; removing.
(WW) NVIDIA(0): No valid modes for "1200x800"; removing.
(WW) NVIDIA(0): No valid modes for "1152x768"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050"
(II) NVIDIA(0):     "1440x900"
(II) NVIDIA(0):     "1400x1050"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0):     "1280x768"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B]
	[1] 0	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B]
	[2] 0	0	0xce000000 - 0xceffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[8] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[9] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[10] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[11] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[12] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[13] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[14] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[25] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1680x1050"
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
(**) Generic Keyboard: Core Keyboard
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
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9

---

### Post by moxer on 2007-11-20
the exact same thing happened to me after doing what is described in this topic:

[http://ubuntuforums.org/showthread.php?t=616279](http://ubuntuforums.org/showthread.php?t=616279)


i did it because i couldn't use the desktop effects, now i have a neat looking desktop but i can't play warsow :(


btw, i have a mobility radeon 9600 on my laptop

---

### Post by DeadSuperHero on 2007-11-20
Try going into Synaptic, and getting as many bindings for OpenGL as you can. It helped me run quite a few games that wouldn't start.

---

### Post by The Pinny Parlour on 2007-11-25
I tried to install some bindings (didn't find many) it didn't help.   Can anyone else help please?  I would like to play some games.

---

### Post by paulle on 2007-11-25
ii have the same problem with warsow/open Gl.
tried all the advices here but no success.   (ati x800)

---

### Post by dummyhead3 on 2007-11-28
Gutsy enables xgl by default. To disable xgl: "touch ~/.config/xserver-xgl/disable" (make sure ~/.config/xserver-xgl is created first). Once XGL is not used, it should work (at least for me). Also, I suggest you go to metacity if in gnome (metacity --replace)

---

### Post by ShangTsungOmega on 2008-02-26
So you're telling me that i cant have a pretty desktop and play warsow at the same time? I would have hoped that there would have been work around at least. is there a way to make a script to disable xgl on startup and still be able to run a session with xgl?

---

### Post by esteth on 2008-02-26
There is indeed a workaround. Unfortunately because of ati's rather lacking drivers, you can't have XGL for fancy effects and Direct rendering on one screen. You can, however, start another screen (or session, or whatever it's called, and play your game in that. This has some drawbacks, since i beleive it's difficult to switch between the game and anything else while playing).

I have forgotten the command for this, but the script "xgame" automates this process if i remember correctly. A quick google should get you the script

---


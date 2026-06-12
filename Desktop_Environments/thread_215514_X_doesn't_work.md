---
title: "X doesn't work :/"
date: 2006-07-14
forum: Desktop Environments
---

### Post by gevans on 2006-07-14
Hi,

Currently running ubuntu (server)  Compaq Proliant 1600.
lspci reports the video as:

0000:00:06.0 VGA compatible controller: Cirrus Logic GD 5430/40 [Alpine] (rev 22)

and my monitor is a Sun 447z. I looked up the specs on the monitor:

Horizsync: 31-72
VertRefresh: 50-120

X starts but all I get is a black screen.

Output of Xorg.0.log (sans top few lines):
[INDENT]
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 13 16:46:15 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Cirrus Logic GD 5430/40 [Alpine]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) PCI: 00:00:0: chip 1166,0005 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:06:0: chip 1013,00a0 card 0000,0000 rev 22 class 03,00,00 hdr 00
(II) PCI: 00:08:0: chip 1000,000f card 0000,0000 rev 04 class 01,00,00 hdr 00
(II) PCI: 00:0a:0: chip 1045,c861 card 1045,c861 rev 10 class 0c,03,10 hdr 00
(II) PCI: 00:0f:0: chip 0e11,0001 card 0000,0000 rev 07 class 06,02,00 hdr 00
(II) PCI: 00:11:0: chip 1166,0005 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 01:07:0: chip 0e11,ae43 card 0000,0000 rev 10 class 02,80,00 hdr 00
(II) PCI: 01:09:0: chip 1000,000f card 0000,0000 rev 04 class 01,00,00 hdr 00
(II) PCI: 01:0a:0: chip 10b7,5950 card 0000,0000 rev 00 class 02,00,00 hdr 00
(II) PCI: 01:0b:0: chip 10b7,5950 card 0000,0000 rev 00 class 02,00,00 hdr 00
(II) PCI: 01:0d:0: chip 10b7,7646 card 10b7,7646 rev 30 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-EISA bridge:
(II) Bus -1: bridge is at (0:15:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Host-to-PCI bridge:
(II) Bus 1: bridge is at (0:0:0), (1,1,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:6:0) Cirrus Logic GD 5430/40 [Alpine] rev 34, Mem @ 0xc5000000/24
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
	[0] -1	0	0xc6ffee80 - 0xc6ffeeff (0x80) MX[B]
	[1] -1	0	0xc6fff000 - 0xc6ffffff (0x1000) MX[B]
	[2] -1	0	0xc6ffef00 - 0xc6ffefff (0x100) MX[B]
	[3] -1	0	0xc6ffee70 - 0xc6ffee7f (0x10) MX[B]
	[4] -1	0	0xc6efe000 - 0xc6efefff (0x1000) MX[B]
	[5] -1	0	0xc6eff000 - 0xc6efffff (0x1000) MX[B]
	[6] -1	0	0xc6efdf00 - 0xc6efdfff (0x100) MX[B]
	[7] -1	0	0xc5000000 - 0xc5ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x00007400 - 0x0000747f (0x80) IX[B]
	[9] -1	0	0x000074a0 - 0x000074bf (0x20) IX[B]
	[10] -1	0	0x00007480 - 0x0000749f (0x20) IX[B]
	[11] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[12] -1	0	0x000074c0 - 0x000074cf (0x10) IX[B]
	[13] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc6ffee80 - 0xc6ffeeff (0x80) MX[B]
	[1] -1	0	0xc6fff000 - 0xc6ffffff (0x1000) MX[B]
	[2] -1	0	0xc6ffef00 - 0xc6ffefff (0x100) MX[B]
	[3] -1	0	0xc6ffee70 - 0xc6ffee7f (0x10) MX[B]
	[4] -1	0	0xc6efe000 - 0xc6efefff (0x1000) MX[B]
	[5] -1	0	0xc6eff000 - 0xc6efffff (0x1000) MX[B]
	[6] -1	0	0xc6efdf00 - 0xc6efdfff (0x100) MX[B]
	[7] -1	0	0xc5000000 - 0xc5ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x00007400 - 0x0000747f (0x80) IX[B]
	[9] -1	0	0x000074a0 - 0x000074bf (0x20) IX[B]
	[10] -1	0	0x00007480 - 0x0000749f (0x20) IX[B]
	[11] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[12] -1	0	0x000074c0 - 0x000074cf (0x10) IX[B]
	[13] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
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
	[4] -1	0	0xc6ffee80 - 0xc6ffeeff (0x80) MX[B]
	[5] -1	0	0xc6fff000 - 0xc6ffffff (0x1000) MX[B]
	[6] -1	0	0xc6ffef00 - 0xc6ffefff (0x100) MX[B]
	[7] -1	0	0xc6ffee70 - 0xc6ffee7f (0x10) MX[B]
	[8] -1	0	0xc6efe000 - 0xc6efefff (0x1000) MX[B]
	[9] -1	0	0xc6eff000 - 0xc6efffff (0x1000) MX[B]
	[10] -1	0	0xc6efdf00 - 0xc6efdfff (0x100) MX[B]
	[11] -1	0	0xc5000000 - 0xc5ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00007400 - 0x0000747f (0x80) IX[B]
	[15] -1	0	0x000074a0 - 0x000074bf (0x20) IX[B]
	[16] -1	0	0x00007480 - 0x0000749f (0x20) IX[B]
	[17] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[18] -1	0	0x000074c0 - 0x000074cf (0x10) IX[B]
	[19] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
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
(II) LoadModule: "cirrus"
(II) Loading /usr/lib/xorg/modules/drivers/cirrus_drv.so
(II) Module cirrus: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) CIRRUS: driver for Cirrus chipsets: CLGD5430, CLGD5434-4, CLGD5434-8,
	CLGD5436, CLGD5446, CLGD5480, CL-GD5462, CL-GD5464, CL-GD5464BD,
	CL-GD5465, CL-GD7548
(II) Primary Device is: PCI 00:06:0
(--) Chipset CLGD5430 found
(II) Loading sub module "cirrus_alpine"
(II) LoadModule: "cirrus_alpine"
(II) Loading /usr/lib/xorg/modules/drivers/cirrus_alpine.so
(II) Module cirrus_alpine: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc6ffee80 - 0xc6ffeeff (0x80) MX[B]
	[5] -1	0	0xc6fff000 - 0xc6ffffff (0x1000) MX[B]
	[6] -1	0	0xc6ffef00 - 0xc6ffefff (0x100) MX[B]
	[7] -1	0	0xc6ffee70 - 0xc6ffee7f (0x10) MX[B]
	[8] -1	0	0xc6efe000 - 0xc6efefff (0x1000) MX[B]
	[9] -1	0	0xc6eff000 - 0xc6efffff (0x1000) MX[B]
	[10] -1	0	0xc6efdf00 - 0xc6efdfff (0x100) MX[B]
	[11] -1	0	0xc5000000 - 0xc5ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00007400 - 0x0000747f (0x80) IX[B]
	[15] -1	0	0x000074a0 - 0x000074bf (0x20) IX[B]
	[16] -1	0	0x00007480 - 0x0000749f (0x20) IX[B]
	[17] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[18] -1	0	0x000074c0 - 0x000074cf (0x10) IX[B]
	[19] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
(WW) Registering the following despite conflicts with estimated resources:
	[0] 0	0	0x200a0000 - 0x200affff (0x10000) MS[B]
	[1] 0	0	0x200b0000 - 0x200b7fff (0x8000) MS[B]
	[2] 0	0	0x200b8000 - 0x200bffff (0x8000) MS[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc6ffee80 - 0xc6ffeeff (0x80) MX[B]
	[5] -1	0	0xc6fff000 - 0xc6ffffff (0x1000) MX[B]
	[6] -1	0	0xc6ffef00 - 0xc6ffefff (0x100) MX[B]
	[7] -1	0	0xc6ffee70 - 0xc6ffee7f (0x10) MX[B]
	[8] -1	0	0xc6efe000 - 0xc6efefff (0x1000) MX[B]
	[9] -1	0	0xc6eff000 - 0xc6efffff (0x1000) MX[B]
	[10] -1	0	0xc6efdf00 - 0xc6efdfff (0x100) MX[B]
	[11] -1	0	0xc5000000 - 0xc5ffffff (0x1000000) MX[B](B)
	[12] 0	0	0x200a0000 - 0x200affff (0x10000) MS[B]
	[13] 0	0	0x200b0000 - 0x200b7fff (0x8000) MS[B]
	[14] 0	0	0x200b8000 - 0x200bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00007400 - 0x0000747f (0x80) IX[B]
	[18] -1	0	0x000074a0 - 0x000074bf (0x20) IX[B]
	[19] -1	0	0x00007480 - 0x0000749f (0x20) IX[B]
	[20] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[21] -1	0	0x000074c0 - 0x000074cf (0x10) IX[B]
	[22] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[23] 0	0	0x200003b0 - 0x200003bb (0xc) IS[B]
	[24] 0	0	0x200003c0 - 0x200003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) CIRRUS(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) CIRRUS(0): initializing int10
(II) CIRRUS(0): Primary V_BIOS segment is: 0xc000
(**) CIRRUS(0): Depth 24, (--) framebuffer bpp 24
(==) CIRRUS(0): RGB weight 888
(==) CIRRUS(0): Default visual is TrueColor
(==) CIRRUS(0): Using SW cursor
(--) CIRRUS(0): Linear framebuffer at 0xC5000000
(EE) CIRRUS(0): No valid MMIO address in PCI config space
(--) CIRRUS(0): Not Using MMIO
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(EE) CIRRUS(0): I2C initialization failed
(==) CIRRUS(0): Using gamma correction (1.0, 1.0, 1.0)
(--) CIRRUS(0): Memory Config reg 1 is 0x15
(--) CIRRUS(0): VideoRAM: 1024 kByte
(==) CIRRUS(0): Min pixel clock is 12 MHz
(--) CIRRUS(0): Max pixel clock is 28 MHz
(II) CIRRUS(0): Generic Monitor: Using hsync range of 31.00-72.00 kHz
(II) CIRRUS(0): Generic Monitor: Using vrefresh range of 50.00-120.00 Hz
(II) CIRRUS(0): Clock range:  12.00 to  28.50 MHz
(II) CIRRUS(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "800x600" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "800x600" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "800x600" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "800x600" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "800x600" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "800x600" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "800x600" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "800x600" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "800x600" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "800x600" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "896x672" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "896x672" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "928x696" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "928x696" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "960x720" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "960x720" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "832x624" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1280x768" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1280x800" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1152x768" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "700x525" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "700x525" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "700x525" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "700x525" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) CIRRUS(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "800x512" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "840x525" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "840x525" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "840x525" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "960x600" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "960x600" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "960x720" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) CIRRUS(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) CIRRUS(0): Not using mode "1024x768" (no mode of this name)
(II) CIRRUS(0): Not using mode "800x600" (no mode of this name)
(--) CIRRUS(0): Virtual size is 640x480 (pitch 640)
(**) CIRRUS(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) CIRRUS(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(==) CIRRUS(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc5000000 - 0xc5ffffff (0x1000000) MX[B]
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xc6ffee80 - 0xc6ffeeff (0x80) MX[B]
	[6] -1	0	0xc6fff000 - 0xc6ffffff (0x1000) MX[B]
	[7] -1	0	0xc6ffef00 - 0xc6ffefff (0x100) MX[B]
	[8] -1	0	0xc6ffee70 - 0xc6ffee7f (0x10) MX[B]
	[9] -1	0	0xc6efe000 - 0xc6efefff (0x1000) MX[B]
	[10] -1	0	0xc6eff000 - 0xc6efffff (0x1000) MX[B]
	[11] -1	0	0xc6efdf00 - 0xc6efdfff (0x100) MX[B]
	[12] -1	0	0xc5000000 - 0xc5ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x200a0000 - 0x200affff (0x10000) MS[B](OprU)
	[14] 0	0	0x200b0000 - 0x200b7fff (0x8000) MS[B](OprU)
	[15] 0	0	0x200b8000 - 0x200bffff (0x8000) MS[B](OprU)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00007400 - 0x0000747f (0x80) IX[B]
	[19] -1	0	0x000074a0 - 0x000074bf (0x20) IX[B]
	[20] -1	0	0x00007480 - 0x0000749f (0x20) IX[B]
	[21] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[22] -1	0	0x000074c0 - 0x000074cf (0x10) IX[B]
	[23] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[24] 0	0	0x200003b0 - 0x200003bb (0xc) IS[B]
	[25] 0	0	0x200003c0 - 0x200003df (0x20) IS[B]
(II) CIRRUS(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) CIRRUS(0): Using 66 lines for offscreen memory
(II) CIRRUS(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
(==) CIRRUS(0): Silken mouse enabled
(**) Option "dpms"
(**) CIRRUS(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
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
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
[/INDENT]

Any help much appreciated

---

### Post by ayoli on 2006-07-14
the onlyrror i saw in your log was:
```
(EE) CIRRUS(0): I2C initialization failed
```
so you may try to edit your /etc/X11/xorg.conf as root to comment with a # the line which loads i2c module. then try to restart X (and maybe pray :p).
edit: woh, it looks like you have a pb with your modlines also, mabe try to reconfigure X with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
regards,

---

### Post by gevans on 2006-07-14
Well, editing out the I2C didn't work :( and after the reconfigure....still just a black screen....::sigh::

Thanks for the help. anyone have any other ideas?  I am downloading a live CD now to see if it will come up so maybe I can steal the info from that?

Regards,

---

### Post by gevans on 2006-07-14
now that it is busier...anyone have an idea on this?

---

### Post by gevans on 2006-07-15
bump?

---


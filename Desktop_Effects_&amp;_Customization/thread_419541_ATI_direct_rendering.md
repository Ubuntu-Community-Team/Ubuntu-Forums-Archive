---
title: "ATI direct rendering"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by kikazaru on 2007-04-23
Please someone tell me how to get direct rendering with my ATI graphics card! 

(Just upgraded from 6.10 to 7.04, but I didn't manage to get it working in 6.10 either...)


Output of glxinfo:

```

name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


```

/var/log/Xorg.0.log

```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux nakata 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 23 16:58:22 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. RV370 5B64 [FireGL V3100 (PCIE)]"
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
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
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
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,359e card 1028,0168 rev 09 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 8086,3591 card 1028,0168 rev 09 class ff,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,3595 card 0000,0000 rev 09 class 06,04,00 hdr 01

...

(II) PCI: 05:00:0: chip 1002,5b64 card 1002,0102 rev 80 class 03,00,00 hdr 80
(II) PCI: 05:00:1: chip 1002,5b74 card 1002,0103 rev 80 class 03,80,00 hdr 00
(II) PCI: 06:0c:0: chip 104c,8023 card 1028,0168 rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000dfff (0x2000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfefffff (0x300000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:3:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xdfb00000 - 0xdfbfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:4:0), (0,5,5), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xdf900000 - 0xdfafffff (0x200000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,6), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xdf800000 - 0xdf8fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (1:0:0), (1,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfefffff (0x200000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (1:0:2), (1,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfcfffff (0x100000) MX[B]
(--) PCI:*(5:0:0) ATI Technologies Inc RV370 5B64 [FireGL V3100 (PCIE)] rev 128, Mem @ 0xd0000000/27, 0xdf9e0000/16, I/O @ 0xbc00/8, BIOS @ 0xdfa00000/17
(--) PCI: (5:0:1) ATI Technologies Inc RV370 5B64 [FireGL V3100 (PCIE)] (Secondary) rev 128, Mem @ 0xdf9f0000/16
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
	[0] -1	0	0xdf8fc000 - 0xdf8fffff (0x4000) MX[B]
	[1] -1	0	0xdf8fb800 - 0xdf8fbfff (0x800) MX[B]

...

	[28] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[29] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[1] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdf8fc000 - 0xdf8fffff (0x4000) MX[B]
	[1] -1	0	0xdf8fb800 - 0xdf8fbfff (0x800) MX[B]
	[2] -1	0	0xdfce0000 - 0xdfcfffff (0x20000) MX[B]

...

	[28] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[29] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[1] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
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

...

	[38] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) Primary Device is: PCI 05:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(WW) fglrx: No matching Device section for instance (BusID PCI:5:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x5B64) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

...

	[37] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[38] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x81e4718
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

...

	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 5 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI FireGL V3100" (Chipset = 0x5b64)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0102)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xdf9e0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RV380
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V380
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(WW) EDID preferred timing clock 162.00MHz exceeds claimed max 160MHz, fixing
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: DEL  Model: a008  Serial#: 809064268
(II) fglrx(0): Year: 2004  Week: 34
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 41  vert.: 31
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.293 greenY: 0.608
(II) fglrx(0): blueX: 0.146 blueY: 0.067   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 162.0 MHz   Image Size:  367 x 275 mm
(II) fglrx(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) fglrx(0): Serial No: C064948H09WL
(II) fglrx(0): Monitor name: DELL 2001FP
(II) fglrx(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 80 kHz, PixClock max 162 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0010ac08a04c573930
(II) fglrx(0): 	220e010380291f78ee6390a3574b9b25
(II) fglrx(0): 	115054a54b008180a940714f01010101
(II) fglrx(0): 	010101010101483f403062b0324040c0
(II) fglrx(0): 	13006f131100001e000000ff00433036
(II) fglrx(0): 	34393438483039574c20000000fc0044
(II) fglrx(0): 	454c4c203230303146500a20000000fd
(II) fglrx(0): 	00384c1f5010000a2020202020200025
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 392/196MHz @ 50Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 29 modes found for primary display.
(--) fglrx(0): Virtual size is 1600x1200 (pitch 0)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250

.....

(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (410, 310) mm
(--) fglrx(0): DPI set to (99, 98)
(--) fglrx(0): Virtual size is 1600x1200 (pitch 1600)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
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
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdf9e0000 - 0xdf9effff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdf8fc000 - 0xdf8fffff (0x4000) MX[B]
	[7] -1	0	0xdf8fb800 - 0xdf8fbfff (0x800) MX[B]
	[8] -1	0	0xdfce0000 - 0xdfcfffff (0x20000) MX[B]
	[9] -1	0	0xdfdfe000 - 0xdfdfffff (0x2000) MX[B]
	[10] -1	0	0xdffff900 - 0xdffff9ff (0x100) MX[B]
	[11] -1	0	0xdffffa00 - 0xdffffbff (0x200) MX[B]
	[12] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[13] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[14] -1	0	0xdf9f0000 - 0xdf9fffff (0x10000) MX[B](B)
	[15] -1	0	0xdfa00000 - 0xdfa1ffff (0x20000) MX[B](B)
	[16] -1	0	0xdf9e0000 - 0xdf9effff (0x10000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000ccc0 - 0x0000ccff (0x40) IX[B]
	[25] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[27] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[28] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[29] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[30] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[31] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[32] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[35] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[36] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[38] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[39] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[40] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[41] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[42] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
	[43] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[44] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): Composite extension enabled, disabling direct rendering
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x07fe0000
(II) fglrx(0): Splitting WC range: base: 0xd0000000, size: 0x7fe0000
(II) fglrx(0): Splitting WC range: base: 0xd4000000, size: 0x3fe0000
(II) fglrx(0): Splitting WC range: base: 0xd6000000, size: 0x1fe0000
(II) fglrx(0): Splitting WC range: base: 0xd7000000, size: 0xfe0000
(II) fglrx(0): Splitting WC range: base: 0xd7800000, size: 0x7e0000
(II) fglrx(0): Splitting WC range: base: 0xd7c00000, size: 0x3e0000
(II) fglrx(0): Splitting WC range: base: 0xd7e00000, size: 0x1e0000
(II) fglrx(0): Splitting WC range: base: 0xd7f00000, size: 0xe0000
(II) fglrx(0): Splitting WC range: base: 0xd7f80000, size: 0x60000
(==) fglrx(0): Write-combining range (0xd7fc0000,0x20000)
(==) fglrx(0): Write-combining range (0xd7f80000,0x60000)
(==) fglrx(0): Write-combining range (0xd7f00000,0xe0000)
(==) fglrx(0): Write-combining range (0xd7e00000,0x1e0000)
(==) fglrx(0): Write-combining range (0xd7c00000,0x3e0000)
(==) fglrx(0): Write-combining range (0xd7800000,0x7e0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd7000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd6000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd4000000,0x3fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd0000000,0x7fe0000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1600 x 6991
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "UseFBDev" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
fbarea0->box.x1 0x00000000, fbarea0->box.y1 0x000004b3
fbarea0->box.x2 0x00000640, fbarea0->box.y2 0x000004b5
icon[0].start=0x758000
fbarea1->box.x1 0x00000000, fbarea1->box.y1 0x000004b5
fbarea1->box.x2 0x00000640, fbarea1->box.y2 0x000004b7
icon[1].start=0x75b000
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
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
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
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(II) 3rd Button detected: disabling emulate3Button

```

---

### Post by trotur on 2007-04-23
> **kikazaru said:**
> 

/var/log/Xorg.0.log

```


(II) fglrx(0): Composite extension enabled, disabling direct rendering
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


```

It seems that you are using fglrx driver from Ati. You also have composite extension enabled which causes problems with fglrx driver.
See [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) for more info.

To disable composite extension edit your xorg.conf file (I suggest making a backup file before doing this)
```
sudo gedit /etc/X11/xorg.conf
```

and add following lines at the end of file
```
Section "Extensions"
        Option      "Composite" "0"
EndSection
```

save file and restart xorg by pressing Ctrl, Alt and Backspace simultaneously and check from glxinfo (or fglrxinfo) whether direct rendering is working.

---

### Post by kikazaru on 2007-04-23
Thanks for your help! Adding those lines did indeed give me direct rendering, but then the OpenGL programs that I had written wouldn't run!?

I just ran through the instructions in [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL) and now I am back to direct rendering: No, but I have got nice wobbly windows... I guess my OpenGL isn't accelerated though.. or maybe Xgl is taking care of that.

---

### Post by stocks29 on 2007-04-25
Help. I am having the same problem, but that solution did not work for me. Here is the output of glxinfo:

```
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None

```

In addition, here is my Xorg.conf:

```
Section "ServerLayout"
        #Option     "AIGLX" "true"
        Identifier     "Default Layout"
        Screen      0  "Screen0" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        Option      "Clone" "off"
        Option      "Xinerama" "on"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "dbe"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "on"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "Monitor1"
        Option      "DPMS" "true"
EndSection

Section "Device"
        #Driver         "ati"
        #Driver         "radeon"
        #Option     "XAANoOffscreenPixmaps"
        #Option     "RenderAccel" "true"
        #Option     "GARTSize" "64"
        Identifier  "Device0"
        Driver      "fglrx"
        Option      "DRI" "true"
        #Option     "MonitorLayout" "CRT, CRT"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "on"
        Option      "DesktopSetup" "horizontal"
        Option      "OverlayOnCRTC2" "1"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"

        #Driver         "ati"
        #Driver      "radeon"
        #Screen      1
        #Option     "XAANoOffscreenPixmaps"
        #Option     "RenderAccel" "true"
        #Option     "GARTSize" "64"
        Identifier  "Device1"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "on"
        Option      "DRI" "true"
        #Option         "MonitorLayout" "CRT, CRT"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Device0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Virtual   1600 1200
                Depth     24
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "Device1"
        Monitor    "Monitor1"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Virtual   1600 1200
                Depth     24
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection
```

Any help would be greatly appreciated as I have been struggling with this for months!

---

### Post by mrThefter on 2007-04-25
Turn off OpenGLOverlay.
It's in the device section of xorg.conf.

---

### Post by kikazaru on 2007-04-26
Back to square one... I did manage to have my OpenGL code running with Xgl, and get beryl working with a cool 3D desktop, but it turned out to be unstable. It kept crashing and locking up the whole computer so I had give up on Xgl. 

I can get direct rendering by adding this to the end of my xorg.conf:

```

#Enables direct rendering but causes gl apps to crash, it seems
Section "Extensions"
        Option      "Composite" "0"
EndSection

```

But my OpenGL code doesn't run:

```

X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
*** glibc detected *** ./my_Qt3_Mesa_App: free(): invalid pointer: 0xb46585d0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb74287cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb742be30]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb75ead11]
/usr/lib/libscim-1.0.so.8[0xaae72156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xaae72f77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xaae6df05]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0xab01bcf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0xab01dace]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0xab016cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb7cb6f67]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb7cb6b34]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0xab1f3c9b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0xab1f3e4f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0xab1f40be]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb7cb6b58]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb7a09965]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb7a09c6b]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7b8a0e5]
/usr/lib/libqt-mt.so.3(_ZN8QSpinBox13updateDisplayEv+0x78)[0xb7be7510]
/usr/lib/libqt-mt.so.3(_ZN8QSpinBox11initSpinBoxEv+0x27d)[0xb7be8797]
/usr/lib/libqt-mt.so.3(_ZN8QSpinBoxC1EP7QWidgetPKc+0xae)[0xb7be8a2c]
./my_Qt3_Mesa_App[0x830d201]
./my_Qt3_Mesa_App[0x8305a49]
./my_Qt3_Mesa_App[0x806f1fb]
./my_Qt3_Mesa_App(_ZN9QGLWidget10setContextEP10QGLContextPKS0_b+0x34a)[0x805292e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb73d6ebc]
./my_Qt3_Mesa_App(_ZN7QWidget17setUpdatesEnabledEb+0x3d)[0x80526f1]
======= Memory map: ========
08048000-08341000 r-xp 00000000 00:16 15564802   /home/hrcn/jhale/projects/cb-sim/trunk/src/my_Qt3_Mesa_App
08341000-08357000 rw-p 002f8000 00:16 15564802   /home/hrcn/jhale/projects/cb-sim/trunk/src/my_Qt3_Mesa_App
08357000-084af000 rw-p 08357000 00:00 0          [heap]
aad00000-aad7e000 rw-p aad00000 00:00 0 
aad7e000-aae00000 ---p aad7e000 00:00 0 
aae0a000-aaede000 r-xp 00000000 08:02 3097047    /usr/lib/libscim-1.0.so.8.1.0
aaede000-aaeec000 rw-p 000d4000 08:02 3097047    /usr/lib/libscim-1.0.so.8.1.0
aaf00000-aaffc000 rw-p aaf00000 00:00 0 
aaffc000-ab000000 ---p aaffc000 00:00 0 
ab008000-ab026000 r-xp 00000000 08:02 3967556    /usr/lib/qt3/plugins/inputmethods/libqscim.so
ab026000-ab027000 rw-p 0001e000 08:02 3967556    /usr/lib/qt3/plugins/inputmethods/libqscim.so
ab027000-ab04b000 r-xp 00000000 08:02 3967191    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
ab04b000-ab04c000 rw-p 00024000 08:02 3967191    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
ab04c000-ab1b1000 rw-p ab04c000 00:00 0 
ab1c2000-ab1cd000 r-xp 00000000 08:02 3967192    /usr/lib/qt3/plugins/inputmethods/libqxim.so
ab1cd000-ab1ce000 rw-p 0000a000 08:02 3967192    /usr/lib/qt3/plugins/inputmethods/libqxim.so
ab1ce000-ab1e3000 r-xp 00000000 08:02 3097601    /usr/lib/libXmu.so.6.2.0
ab1e3000-ab1e4000 rw-p 00015000 08:02 3097601    /usr/lib/libXmu.so.6.2.0
ab1e6000-ab1e8000 r-xp 00000000 08:02 3097048    /usr/lib/libscim-x11utils-1.0.so.8.1.0
ab1e8000-ab1e9000 rw-p 00001000 08:02 3097048    /usr/lib/libscim-x11utils-1.0.so.8.1.0
ab1e9000-ab1ed000 r-xp 00000000 08:02 3967190    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
ab1ed000-ab1ee000 rw-p 00003000 08:02 3967190    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
ab1ee000-ab1f7000 r-xp 00000000 08:02 3966774    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
ab1f7000-ab1f8000 rw-p 00009000 08:02 3966774    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
ab1f8000-ab240000 rw-p ab1f8000 00:00 0 
ab240000-ab3d0000 rw-s 00044000 00:0d 18640      /dev/dri/card0
ab3d0000-aba10000 rw-s 00022000 00:0d 18640      /dev/dri/card0
aba10000-abb10000 rw-s 00021000 00:0d 18640      /dev/dri/card0
abb10000-abb20000 rw-s 0001f000 00:0d 18640      /dev/dri/card0
abb20000-b3b00000 rw-s 0001e000 00:0d 18640      /dev/dri/card0
b3b00000-b3b07000 r-xp 00000000 08:02 20824814   /lib/tls/i686/cmov/librt-2.5.so
b3b07000-b3b09000 rw-p 00006000 08:02 20824814   /lib/tls/i686/cmov/librt-2.5.so
b3b09000-b3bb9000 r-xp 00000000 08:02 3098090    /usr/lib/libstdc++.so.5.0.7
b3bb9000-b3bbe000 rw-p 000af000 08:02 3098090    /usr/lib/libstdc++.so.5.0.7
b3bbe000-b3bc3000 rw-p b3bbe000 00:00 0 
b3bc3000-b4420000 r-xp 00000000 08:02 3102182    /usr/lib/dri/fglrx_dri.so
b4420000-b446a000 rw-p 0085d000 08:02 3102182    /usr/lib/dri/fglrx_dri.so
b446a000-b44f4000 rw-p b446a000 00:00 0 
b44f4000-b450e000 r--p 00000000 08:02 3326175    /usr/share/fonts/type1/gsfonts/n019003l.pfb
b450e000-b4538000 r-xp 00000000 08:02 3102875    /usr/lib/libkdefx.so.4.2.0
b4538000-b4539000 rw-p 0002a000 08:02 3102875    /usr/lib/libkdefx.so.4.2.0
b4539000-b4541000 rw-p b4539000 00:00 0 
b4541000-b4544000 rw-s 00047000 00:0d 18640      /dev/dri/card0
b4544000-b4546000 rw-s 0001d000 00:0d 18640      /dev/dri/card0
b4546000-b454d000 rwxp b4546000 00:00 0 
b454d000-b4580000 r-xp 00000000 08:02 4047892    /usr/lib/kde3/plugins/styles/keramik.so
b4580000-b4582000 rw-p 00033000 08:02 4047892    /usr/lib/kde3/plugins/styles/keramik.so
b4582000-b4585000 r--s 00000000 08:02 23530016   /var/cache/fontconfig/5e10083637a12ecd1bff191eb66bfa2f-x86.cache-2
b4585000-b4588000 r--s 00000000 08:02 23530015   /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b4588000-b458e000 r--s 00000000 08:02 23530014   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b458e000-b4591000 r--s 00000000 08:02 23530012   /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86.cache-2
b4591000-b4592000 r--s 00000000 08:02 23530010   /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b4592000-b4595000 r--s 00000000 08:02 23530009   /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b4595000-b4596000 r--s 00000000 08:02 23530008   /var/cache/fontconfig/6edd069ccec3ba28096b368c434fa861-x86.cache-2
b4596000-b4597000 r--s 00000000 08:02 23530007   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b4597000-b4598000 r--s 00000000 08:02 23530006   /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b4598000-b459c000 r--s 00000000 08:02 23530005   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b459c000-b45b7000 r--s 00000000 08:02 23530003   /var/cache/fontconfig/4ca92cf76c0cf3dfa7f011127eff595d-x86.cache-2
b45b7000-b45d3000 r--s 00000000 08:02 23530002   /var/cache/fontconfig/6abf76b0b4cc7192703d8431ac929b75-x86.cache-2
b45d3000-b45f1000 r--s 00000000 08:02 23530496   /var/cache/fontconfig/f408d08d2fce062ab660f628db78bf96-x86.cache-2
b45f1000-b45f2000 r--s 00000000 08:02 23530000   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b45f2000-b45f4000 r--s 00000000 08:02 23529999   /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b45f4000-b45f6000 r--s 00000000 08:02 23530549   /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b45f6000-b45f7000 r--s 00000000 08:02 23529997   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b45f7000-b45f8000 r--s 00000000 08:02 23529996   /var/cache/fontconfig/a8d35ba226d862df35f7c320f882e11a-x86.cache-2
b45f8000-b45fa000 r--s 00000000 08:02 23530548   /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b45fa000-b4600000 r--s 00000000 08:02 23530028   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4600000-b46de000 rw-p b4600000 00:00 0 
b46de000-b4700000 ---p b46de000 00:00 0 
b4700000-b4702000 r--s 00000000 08:02 23529982   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4702000-b4708000 r--s 00000000 08:02 23529992   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b4708000-b4709000 r--s 00000000 08:02 23529981   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4709000-b4720000 r--s 00000000 08:02 23529991   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b4720000-b4722000 r--s 00000000 08:02 23529990   /var/cache/fontconfig/2c5ba8142dffc8bf0377700342b8ca1a-x86.cache-2
b4722000-b4724000 r--s 00000000 08:02 23530026   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b4724000-b472a000 r--s 00000000 08:02 23529989   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b472a000-b472e000 r--s 00000000 08:02 23529988   /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b472e000-b4731000 r--s 00000000 08:02 23529987   /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b4731000-b4735000 r--s 00000000 08:02 23529986   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4735000-b473c000 r--s 00000000 08:02 23527920   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b473c000-b473d000 r--s 00000000 08:02 23529535   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b473d000-b473f000 r--s 00000000 08:02 23529537   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b473f000-b4740000 r--s 00000000 08:02 23529536   /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b4740000-b4741000 r--s 00000000 08:02 23529534   /var/cache/fontconfig/e22b663d51a3e226824aa2afd6c591f7-x86.cache-2
b4741000-b4742000 r--s 00000000 08:02 23529533   /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b4742000-b4743000 r--s 00000000 08:02 23529532   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b4743000-b4746000 r--s 00000000 08:02 23529551   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b4746000-b474a000 r--s 00000000 08:02 23529527   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b474a000-b4753000 r--s 00000000 08:02 23529529   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b4753000-b4755000 r--s 00000000 08:02 23530507   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b4755000-b4756000 r--s 00000000 08:02 23529531   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b4756000-b4758000 r--s 00000000 08:02 23529528   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b4758000-b4759000 r--s 00000000 08:02 23530547   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b4759000-b475e000 r--s 00000000 08:02 23530550   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b475e000-b4762000 r--s 00000000 08:02 23529984   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b4762000-b4767000 r--s 00000000 08:02 23529979   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b4767000-b476a000 r--s 00000000 08:02 23529985   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b476a000-b476b000 r--s 00000000 08:02 23529978   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b476b000-b476d000 r--s 00000000 08:02 23530025   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b476d000-b4770000 r--s 00000000 08:02 23529542   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b4770000-b4776000 r--s 00000000 08:02 23530024   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b4776000-b477c000 r--s 00000000 08:02 23530023   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b477c000-b477d000 r--s 00000000 08:02 23530022   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b477d000-b4786000 r--s 00000000 08:02 23530021   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b4786000-b478c000 r--s 00000000 08:02 23530020   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b478c000-b4790000 r--s 00000000 08:02 23530019   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b4790000-b4795000 r--s 00000000 08:02 23530018   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b4795000-b4796000 r--s 00000000 08:02 23529980   /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b4796000-b47d1000 r--p 00000000 08:02 3162585    /usr/lib/locale/en_US.utf8/LC_CTYPE
b47d1000-b48a8000 r--p 00000000 08:02 3163237    /usr/lib/locale/en_US.utf8/LC_COLLATE
b48a8000-b48a9000 r--p 00000000 08:02 3163029    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b48a9000-b48aa000 r--p 00000000 08:02 3163030    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b48aa000-b48b1000 r--s 00000000 08:02 3096758    /usr/lib/gconv/gconv-modules.cache
b48b1000-b48de000 rw-p b48b1000 00:00 0 
b48de000-b48df000 ---p b48de000 00:00 0 
b48df000-b50df000 rwxp b48df000 00:00 0 
b50df000-b50e0000 ---p b50df000 00:00 0 
b50e0000-b58e0000 rwxp b50e0000 00:00 0 
b58e0000-b58e1000 ---p b58e0000 00:00 0 
b58e1000-b60e1000 rwxp b58e1000 00:00 0 
b60e1000-b60e2000 ---p b60e1000 00:00 0 
b60e2000-b68e2000 rwxp b60e2000 00:00 0 
b68e2000-b68e3000 ---p b68e2000 00:00 0 
b68e3000-b70e3000 rwxp b68e3000 00:00 0 
b70e3000-b70e5000 rw-p b70e3000 00:00 0 
b70e5000-b70e9000 r-xp 00000000 08:02 3098273    /usr/lib/libXdmcp.so.6.0.0
b70e9000-b70ea000 rw-p 00003000 08:02 3098273    /usr/lib/libXdmcp.so.6.0.0
b70ea000-b70eb000 rw-p b70ea000 00:00 0 
b70eb000-b70ed000 r-xp 00000000 08:02 3097531    /usr/lib/libXau.so.6.0.0
b70ed000-b70ee000 rw-p 00001000 08:02 3097531    /usr/lib/libXau.so.6.0.0
b70ee000-b70f2000 r-xp 00000000 08:02 3100146    /usr/lib/libXfixes.so.3.1.0
b70f2000-b70f3000 rw-p 00003000 08:02 3100146    /usr/lib/libXfixes.so.3.1.0
b70f3000-b7111000 r-xp 00000000 08:02 3099640    /usr/lib/libexpat.so.1.0.0
b7111000-b7113000 rw-p 0001d000 08:02 3099640    /usr/lib/libexpat.so.1.0.0
b7113000-b7115000 r-xp 00000000 08:02 20824788   /lib/tls/i686/cmov/libdl-2.5.so
b7115000-b7117000 rw-p 00001000 08:02 20824788   /lib/tls/i686/cmov/libdl-2.5.so
b7117000-b7118000 rw-p b7117000 00:00 0 
b7118000-b712d000 r-xp 00000000 08:02 3099552    /usr/lib/libICE.so.6.3.0
b712d000-b712f000 rw-p 00014000 08:02 3099552    /usr/lib/libICE.so.6.3.0
b712f000-b7130000 rw-p b712f000 00:00 0 
b7130000-b7138000 r-xp 00000000 08:02 3099560    /usr/lib/libSM.so.6.0.0
b7138000-b7139000 rw-p 00007000 08:02 3099560    /usr/lib/libSM.so.6.0.0
b7139000-b7226000 r-xp 00000000 08:02 3099538    /usr/lib/libX11.so.6.2.0
b7226000-b722a000 rw-p 000ed000 08:02 3099538    /usr/lib/libX11.so.6.2.0
b722a000-b7237000 r-xp 00000000 08:02 3100131    /usr/lib/libXext.so.6.4.0
b7237000-b7238000 rw-p 0000d000 08:02 3100131    /usr/lib/libXext.so.6.4.0
b7238000-b72a0000 r-xp 00000000 08:02 3096791    /usr/lib/libfreetype.so.6.3.10
b72a0000-b72a3000 rw-p 00068000 08:02 3096791    /usr/lib/libfreetype.so.6.3.10
b72a3000-b72b4000 r-xp 00000000 08:02 3100098    /usr/lib/libXft.so.2.1.2
b72b4000-b72b5000 rw-p 00010000 08:02 3100098    /usr/lib/libXft.so.2.1.2
b72b5000-b72b6000 rw-p b72b5000 00:00 0 
b72b6000-b72b8000 r-xp 00000000 08:02 3098097    /usr/lib/libXinerama.so.1.0.0
b72b8000-b72b9000 rw-p 00001000 08:02 3098097    /usr/lib/libXinerama.so.1.0.0
b72b9000-b72c1000 r-xp 00000000 08:02 3100150    /usr/lib/libXcursor.so.1.0.2
b72c1000-b72c2000 rw-p 00007000 08:02 3100150    /usr/lib/libXcursor.so.1.0.2
b72c2000-b72c7000 r-xp 00000000 08:02 3100140    /usr/lib/libXrandr.so.2.1.0
b72c7000-b72c8000 rw-p 00005000 08:02 3100140    /usr/lib/libXrandr.so.2.1.0
b72c8000-b72cf000 r-xp 00000000 08:02 3097582    /usr/lib/libXrender.so.1.3.0
b72cf000-b72d0000 rw-p 00006000 08:02 3097582    /usr/lib/libXrender.so.1.3.0
b72d0000-b72d7000 r-xp 00000000 08:02 3100136    /usr/lib/libXi.so.6.0.0
b72d7000-b72d8000 rw-p 00006000 08:02 3100136    /usr/lib/libXi.so.6.0.0
b72d8000-b72eb000 r-xp 00000000 08:02 3099646    /usr/lib/libz.so.1.2.3
b72eb000-b72ec000 rw-p 00012000 08:02 3099646    /usr/lib/libz.so.1.2.3
b72ec000-b72ed000 rw-p b72ec000 00:00 0 
b72ed000-b730f000 r-xp 00000000 08:02 3099544    /usr/lib/libpng12.so.0.15.0
b730f000-b7310000 rw-p 00021000 08:02 3099544    /usr/lib/libpng12.so.0.15.0
b7310000-b732e000 r-xp 00000000 08:02 3098550    /usr/lib/libjpeg.so.62.0.0
b732e000-b732f000 rw-p 0001d000 08:02 3098550    /usr/lib/libjpeg.so.62.0.0
b732f000-b737c000 r-xp 00000000 08:02 3102152    /usr/lib/libXt.so.6.0.0
b737c000-b7380000 rw-p 0004c000 08:02 3102152    /usr/lib/libXt.so.6.0.0
b7380000-b7395000 r-xp 00000000 08:02 3098098    /usr/lib/libaudio.so.2.4
b7395000-b7396000 rw-p 00015000 08:02 3098098    /usr/lib/libaudio.so.2.4
b7396000-b73b9000 r-xp 00000000 08:02 3097488    /usr/lib/libfontconfig.so.1.2.0
b73b9000-b73c1000 rw-p 00023000 08:02 3097488    /usr/lib/libfontconfig.so.1.2.0
b73c1000-b74fc000 r-xp 00000000 08:02 20824774   /lib/tls/i686/cmov/libc-2.5.so
b74fc000-b74fd000 r--p 0013b000 08:02 20824774   /lib/tls/i686/cmov/libc-2.5.so
b74fd000-b74ff000 rw-p 0013c000 08:02 20824774   /lib/tls/i686/cmov/libc-2.5.so
b74ff000-b7503000 rw-p b74ff000 00:00 0 
b7503000-b750e000 r-xp 00000000 08:02 20824114   /lib/libgcc_s.so.1
b750e000-b750f000 rw-p 0000a000 08:02 20824114   /lib/libgcc_s.so.1
b750f000-b7534000 r-xp 00000000 08:02 20824790   /lib/tls/i686/cmov/libm-2.5.so
b7534000-b7536000 rw-p 00024000 08:02 20824790   /lib/tls/i686/cmov/libm-2.5.so
b7536000-b7615000 r-xp 00000000 08:02 3099920    /usr/lib/libstdc++.so.6.0.8
b7615000-b7618000 r--p 000de000 08:02 3099920    /usr/lib/libstdc++.so.6.0.8
b7618000-b761a000 rw-p 000e1000 08:02 3099920    /usr/lib/libstdc++.so.6.0.8
b761a000-b7620000 rw-p b761a000 00:00 0 
b7620000-b764d000 r-xp 00000000 08:02 3098381    /usr/lib/libglut.so.3.8.0
b764d000-b7652000 rw-p 0002c000 08:02 3098381    /usr/lib/libglut.so.3.8.0
b7652000-b76d1000 r-xp 00000000 08:02 3099378    /usr/lib/libGLU.so.1.3.060502
b76d1000-b76d2000 rw-p 0007e000 08:02 3099378    /usr/lib/libGLU.so.1.3.060502
b76d2000-b776a000 r-xp 00000000 08:02 3102177    /usr/lib/libGL.so.1.2
b776a000-b776f000 rw-p 00098000 08:02 3102177    /usr/lib/libGL.so.1.2
b776f000-b7773000 rw-p b776f000 00:00 0 
b7773000-b7f39000 r-xp 00000000 08:02 3099437    /usr/lib/libqt-mt.so.3.3.7
b7f39000-b7f7f000 rw-p 007c5000 08:02 3099437    /usr/lib/libqt-mt.so.3.3.7
b7f7f000-b7f83000 rw-p b7f7f000 00:00 0 
b7f83000-b7f96000 r-xp 00000000 08:02 20824810   /lib/tls/i686/cmov/libpthread-2.5.so
b7f96000-b7f98000 rw-p 00013000 08:02 20824810   /lib/tls/i686/cmov/libpthread-2.5.so
b7f98000-b7f9a000 rw-p b7f98000 00:00 0 
b7f9a000-b7f9c000 r--s 00000000 08:02 23529993   /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b7f9c000-b7f9d000 r--p 00000000 08:02 3163031    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f9d000-b7f9e000 rw-s 00020000 00:0d 18640      /dev/dri/card0
b7f9e000-b7fa6000 r--s 00000000 08:02 23530027   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b7fa6000-b7fa7000 r--p 00000000 08:02 3163243    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7fa7000-b7fa8000 r--p 00000000 08:02 3163025    /usr/lib/locale/en_US.utf8/LC_TIME
b7fa8000-b7fa9000 r--p 00000000 08:02 3163026    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7fa9000-b7faa000 r--p 00000000 08:02 3163286    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7faa000-b7fab000 r--p 00000000 08:02 3163374    /usr/lib/locale/en_US.utf8/LC_PAPER
b7fab000-b7fac000 r--p 00000000 08:02 3163027    /usr/lib/locale/en_US.utf8/LC_NAME
b7fac000-b7fad000 r--p 00000000 08:02 3163028    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fad000-b7fb0000 rw-p b7fad000 00:00 0 
b7fb0000-b7fc9000 r-xp 00000000 08:02 20824068   /lib/ld-2.5.so
b7fc9000-b7fcb000 rw-p 00019000 08:02 20824068   /lib/ld-2.5.so
bfb6b000-bfb7f000 rwxp bfb6b000 00:00 0          [stack]
bfb7f000-bfb81000 rw-p bfb7f000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

and beryl doesn't seem too happy:

```

(heliodor:9792): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to have a specified colormap. All windows have a colormap, however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise a colormap must be set on them with gdk_drawable_set_colormap

(heliodor:9792): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

glxinfo yields the following:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: FireGL V3100
OpenGL version string: 2.0.6334 (8.34.8)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_element_array, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer, 
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object, 
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3, 
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

```

Any ideas...?

---

### Post by kpolice on 2007-04-27
Beryl/Compiz won't run with your ATi card + fglrx driver without XGL.

You can try the open source driver but I don't know if your card is supported.

---

### Post by kikazaru on 2007-04-27
I did get Beryl working but then glxinfo reported 'no' for direct rendering, and the CPU usage by XGL was quite high. Is it performing software rendering? Also, it seemed to crash if I ran my own openGL code a few times. It would cause gnome to restart, and then if I opened any app it would freeze the computer...

---

### Post by stocks29 on 2007-04-27
Ok, I turned off OpenGLOverlay in both device sections and still no direct rendering.

---

### Post by mrThefter on 2007-04-27
OpenGL software doesn't play well with XGL.
You have to decide, OpenGL software, or Beryl. That's the grim fate for ATI users.

---

### Post by theRaven13 on 2007-04-27
I have an ATI Radeon Mobility card with 16mb memory and after a long struggle I finally got direct rendering by removing all fglrx components from synaptic and changing the driver to radeon instead of ati in the xorg.conf. There are other options too but they slowed down my system.
I installed beryl today and it works tolerably well. I need more time with it to fine tune it, if this can be done. 
To get direct rendering and getting beryl to work you should reference the HOWTO threads in this forum regarding these.

---

### Post by mrThefter on 2007-04-28
See, the thing about it is, radeon drivers only fully support the cards up to 9800. x1## series cards are 2d supported, and x1### aren't at all. In your case, you CAN use radeon to have AIGLX compatibility.
But if you have an x-series card, you can't use beryl unless you use XGL, then you can't use OpenGL software.

---


---
title: "Xlib:  extension &quot;XFree86-DRI&quot; missing on display with fglrx and xgl"
date: 2007-04-29
forum: Desktop Environments
---

### Post by santiagozky on 2007-04-29
Hi, I had beryl with the fglrx running pretty good, but trying to fix de problem with some java swing applications now direct rendering doesnt work whith xgl (they work without it).

with glxinfo i get:

[PHP]name of display: :1.0
**Xlib:  extension "XFree86-DRI" missing on display ":1.0".**
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 1.2 (2.0.6334 (8.34.8))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
[/PHP]

The Xorg log :

[PHP]
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux santiago-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
....
.....
.....
....
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
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
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(--) Chipset Supported AMD Graphics Processor (0x5975) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0302400 - 0xd03024ff (0x100) MX[B]
	[5] -1	0	0xd0302000 - 0xd03020ff (0x100) MX[B]
	[6] -1	0	0xd0300000 - 0xd0301fff (0x2000) MX[B]
	[7] -1	0	0xd0200000 - 0xd0203fff (0x4000) MX[B]
	[8] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[9] -1	0	0xd0004800 - 0xd0004bff (0x400) MX[B]
	[10] -1	0	0xd0004400 - 0xd00044ff (0x100) MX[B]
	[11] -1	0	0xd0009000 - 0xd0009fff (0x1000) MX[B]
	[12] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[13] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[14] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[15] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[16] -1	0	0xd0004000 - 0xd00043ff (0x400) MX[B]
	[17] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[18] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[22] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[27] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[28] -1	0	0x00008450 - 0x00008453 (0x4) IX[B]
	[29] -1	0	0x00008430 - 0x00008437 (0x8) IX[B]
	[30] -1	0	0x00008454 - 0x00008457 (0x4) IX[B]
	[31] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[32] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e6928
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0302400 - 0xd03024ff (0x100) MX[B]
	[5] -1	0	0xd0302000 - 0xd03020ff (0x100) MX[B]
	[6] -1	0	0xd0300000 - 0xd0301fff (0x2000) MX[B]
	[7] -1	0	0xd0200000 - 0xd0203fff (0x4000) MX[B]
	[8] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[9] -1	0	0xd0004800 - 0xd0004bff (0x400) MX[B]
	[10] -1	0	0xd0004400 - 0xd00044ff (0x100) MX[B]
	[11] -1	0	0xd0009000 - 0xd0009fff (0x1000) MX[B]
	[12] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[13] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[14] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[15] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[16] -1	0	0xd0004000 - 0xd00043ff (0x400) MX[B]
	[17] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[18] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[25] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[30] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[31] -1	0	0x00008450 - 0x00008453 (0x4) IX[B]
	[32] -1	0	0x00008430 - 0x00008437 (0x8) IX[B]
	[33] -1	0	0x00008454 - 0x00008457 (0x4) IX[B]
	[34] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[35] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
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
(--) fglrx(0): Chipset: "ATI Radeon Xpress Series" (Chipset = 0x5975)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x01f5)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd4000000
(--) fglrx(0): MMIO registers at 0xd0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI Radeon® Xpress 1150    
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
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
(--) fglrx(0): VideoRAM: 65536 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LPL  Model: 0  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 30  vert.: 19
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.581 redY: 0.344   greenX: 0.325 greenY: 0.547
(II) fglrx(0): blueX: 0.157 blueY: 0.137   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) fglrx(0):  G9653141WX1
(II) fglrx(0):  /?OWŸ·ß
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00320c000000000000
(II) fglrx(0): 	000f0103801e13780ac4409458538c28
(II) fglrx(0): 	23505400000001010101010101010101
(II) fglrx(0): 	010101010101bc1b00a0502017303020
(II) fglrx(0): 	360030be10000018bc1b00a050201730
(II) fglrx(0): 	3020360030be10000000000000fe0047
(II) fglrx(0): 	39363533013134315758310a000000fe
(II) fglrx(0): 	002f3f4f577f9fb7df01010a20200089
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  2 power states available:
(II) fglrx(0):   1. 401/401MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 100/133MHz @ 60Hz [low voltage]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 13 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.00  1280 1328 1360 1440  800 803 809 823
(**) fglrx(0):  Default mode "1280x768": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   71.00  1280 1328 1360 1440  768 787 793 823
(**) fglrx(0):  Default mode "1024x768": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.00  1024 1200 1232 1440  768 787 793 823
(**) fglrx(0):  Default mode "848x480": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   71.00  848 1112 1144 1440  480 643 649 823
(**) fglrx(0):  Default mode "800x600": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.00  800 1088 1120 1440  600 703 709 823
(**) fglrx(0):  Default mode "720x480": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.00  720 1048 1080 1440  480 643 649 823
(**) fglrx(0):  Default mode "640x480": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.00  640 1008 1040 1440  480 643 649 823
(**) fglrx(0):  Default mode "640x400": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.00  640 1008 1040 1440  400 603 609 823
(**) fglrx(0):  Default mode "640x350": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   71.00  640 1008 1040 1440  350 578 584 823
(**) fglrx(0):  Default mode "512x384": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.00  512 944 976 1440  384 595 601 823
(**) fglrx(0):  Default mode "400x300": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   71.00  400 888 920 1440  300 703 709 823 doublescan
(**) fglrx(0):  Default mode "320x240": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   71.00  320 848 880 1440  240 643 649 823 doublescan
(**) fglrx(0):  Default mode "320x200": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   71.00  320 848 880 1440  200 603 609 823 doublescan
(--) fglrx(0): Display dimensions: (300, 190) mm
(--) fglrx(0): DPI set to (108, 106)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.00  1280 1328 1360 1440  800 803 809 823
(**) fglrx(0):  Default mode "1280x768": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   71.00  1280 1328 1360 1440  768 787 793 823
(**) fglrx(0):  Default mode "1024x768": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.00  1024 1200 1232 1440  768 787 793 823
(**) fglrx(0):  Default mode "848x480": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   71.00  848 1112 1144 1440  480 643 649 823
(**) fglrx(0):  Default mode "800x600": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.00  800 1088 1120 1440  600 703 709 823
(**) fglrx(0):  Default mode "720x480": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.00  720 1048 1080 1440  480 643 649 823
(**) fglrx(0):  Default mode "640x480": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.00  640 1008 1040 1440  480 643 649 823
(**) fglrx(0):  Default mode "640x400": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.00  640 1008 1040 1440  400 603 609 823
(**) fglrx(0):  Default mode "640x350": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   71.00  640 1008 1040 1440  350 578 584 823
(**) fglrx(0):  Default mode "512x384": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.00  512 944 976 1440  384 595 601 823
(**) fglrx(0):  Default mode "400x300": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   71.00  400 888 920 1440  300 703 709 823 doublescan
(**) fglrx(0):  Default mode "320x240": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   71.00  320 848 880 1440  240 643 649 823 doublescan
(**) fglrx(0):  Default mode "320x200": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   71.00  320 848 880 1440  200 603 609 823 doublescan
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
(==) fglrx(0): cpuFlags: 0x4000001f
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
	[0] 0	0	0xd0100000 - 0xd010ffff (0x10000) MX[B]
	[1] 0	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd0302400 - 0xd03024ff (0x100) MX[B]
	[7] -1	0	0xd0302000 - 0xd03020ff (0x100) MX[B]
	[8] -1	0	0xd0300000 - 0xd0301fff (0x2000) MX[B]
	[9] -1	0	0xd0200000 - 0xd0203fff (0x4000) MX[B]
	[10] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[11] -1	0	0xd0004800 - 0xd0004bff (0x400) MX[B]
	[12] -1	0	0xd0004400 - 0xd00044ff (0x100) MX[B]
	[13] -1	0	0xd0009000 - 0xd0009fff (0x1000) MX[B]
	[14] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[15] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[16] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[17] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[18] -1	0	0xd0004000 - 0xd00043ff (0x400) MX[B]
	[19] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[20] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[24] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[28] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[33] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[34] -1	0	0x00008450 - 0x00008453 (0x4) IX[B]
	[35] -1	0	0x00008430 - 0x00008437 (0x8) IX[B]
	[36] -1	0	0x00008454 - 0x00008457 (0x4) IX[B]
	[37] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[38] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x83a000
(II) fglrx(0): [drm] mapped SAREA 0x83a000 to 0xb7f93000
(II) fglrx(0): [drm] framebuffer handle = 0x83b000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-15-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x0083c000
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x00840000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x1c000000 FBMappedSize: 0x005e9000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1210)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(**) fglrx(0): Video overlay enabled on CRTC1
(II) fglrx(0): Interrupt handler installed at IRQ 18.
(II) fglrx(0): Exposed events to the /proc interface
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
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
....
....
....
[/PHP]

finally my xorg.conf:

[PHP]
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "latam"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

Section "ServerFlags"
Option "AIGLX"	"off"
EndSection[/PHP]

I have tried to reinstall them several times. As I said before direct rendering works fine without xgl.

any ideas of what the problem could be?

---

### Post by superyounan1 on 2007-05-02
I'm in the same boat, if you find a solution please post it

---

### Post by makeyre on 2007-05-03
Check this thread: [http://ubuntuforums.org/showthread.php?t=414604](http://ubuntuforums.org/showthread.php?t=414604)

---


---
title: "Compiz on Gateway MX6522"
date: 2007-11-14
forum: Desktop Effects &amp; Customization
---

### Post by matchstick on 2007-11-14
Well I have been reading around, and it seems everyone has a different problem with getting compiz to work under Gutsy, and I seem to have my own.  I know I can run it because I manually tried to install it, but I had some issues with certain features not working, as well as not having any title bars.  I have a Gateway laptop with and AMD cpu, and an ATI Radeon Xpress 200M.  I am using the "ati - ATI Mach8, Mach32, Mach64, and Rage..." driver by default and it works fine, except for compiz.  I do have the option for ATI Restricted Drivers, but I didnt use them since everything is working right now.

What I asking is for someone to kind of guide me through the process of setting up compiz since it wont enable by default.

I saw in another post that these file outputs might help so here they are ahead of time.

glxinfo
```
name of display: :0.0

Warning, xpress200 detected.

display: :0  screen: 0

direct rendering: Yes

server glx vendor string: SGI

server glx version string: 1.2

server glx extensions:

    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 

    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 

    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 

    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group

client glx vendor string: SGI

client glx version string: 1.4

client glx extensions:

    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 

    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 

    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 

    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 

    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 

    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 

    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap

GLX version: 1.2

GLX extensions:

    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 

    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 

    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 

    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 

    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group

OpenGL vendor string: DRI R300 Project

OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL

OpenGL version string: 1.3 Mesa 7.0.1

OpenGL extensions:

    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 

    GL_ARB_multitexture, GL_ARB_texture_border_clamp, 

    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 

    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 

    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 

    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 

    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 

    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 

    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 

    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 

    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 

    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 

    GL_EXT_draw_range_elements, GL_EXT_gpu_program_parameters, 

    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 

    GL_EXT_rescale_normal, GL_EXT_secondary_color, 

    GL_EXT_separate_specular_color, GL_EXT_stencil_two_side, 

    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 

    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 

    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 

    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 

    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 

    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 

    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 

    GL_ATI_texture_mirror_once, GL_IBM_rasterpos_clip, 

    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 

    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 

    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 

    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_OES_read_format, 

    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 

    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 

    GL_SGIS_texture_lod



   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav

 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat

----------------------------------------------------------------------

0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow

0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow

0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow

0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow

0x55 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


```

xorg.conf
```
Section "Files"

	FontPath	"/usr/share/fonts/X11/misc"

	FontPath	"/usr/share/fonts/X11/cyrillic"

	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"

	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"

	FontPath	"/usr/share/fonts/X11/Type1"

	FontPath	"/usr/share/fonts/X11/100dpi"

	FontPath	"/usr/share/fonts/X11/75dpi"

	# path to defoma fonts

	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

EndSection



Section "Module"

	Load	"i2c"

	Load	"bitmap"

	Load	"ddc"

	Load	"dri"

	Load	"extmod"

	Load	"freetype"

	Load	"glx"

	Load	"int10"

	Load	"vbe"

EndSection



Section "InputDevice"

	Identifier	"Generic Keyboard"

	Driver		"kbd"

	Option		"CoreKeyboard"

	Option		"XkbRules"	"xorg"

	Option		"XkbModel"	"pc105"

	Option		"XkbLayout"	"us"

EndSection



Section "InputDevice"

	Identifier	"Configured Mouse"

	Driver		"mouse"

	Option		"CorePointer"

	Option		"Device"		"/dev/input/mice"

	Option		"Protocol"		"ImPS/2"

	Option		"ZAxisMapping"		"4 5"

	Option		"Emulate3Buttons"	"true"

EndSection



Section "InputDevice"

	Identifier	"Synaptics Touchpad"

	Driver		"synaptics"

	Option		"SendCoreEvents"	"true"

	Option		"Device"		"/dev/psaux"

	Option		"Protocol"		"auto-dev"

	Option		"HorizScrollDelta"	"0"

EndSection



Section "InputDevice"

	Driver		"wacom"

	Identifier	"stylus"

	Option		"Device"	"/dev/input/wacom"

	Option		"Type"		"stylus"

	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY

EndSection



Section "InputDevice"

	Driver		"wacom"

	Identifier	"eraser"

	Option		"Device"	"/dev/input/wacom"

	Option		"Type"		"eraser"

	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY

EndSection



Section "InputDevice"

	Driver		"wacom"

	Identifier	"cursor"

	Option		"Device"	"/dev/input/wacom"

	Option		"Type"		"cursor"

	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY

EndSection



Section "Device"

	Identifier	"ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"

	Driver		"ati"

	BusID		"PCI:1:5:0"

EndSection



Section "Monitor"

	Identifier	"Generic Monitor"

	Option		"DPMS"

EndSection



Section "Screen"

	Identifier	"Default Screen"

	Device		"ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"

	Monitor		"Generic Monitor"

	DefaultDepth	24

	SubSection "Display"

		Depth		1

		Modes		"1280x800"

	EndSubSection

	SubSection "Display"

		Depth		4

		Modes		"1280x800"

	EndSubSection

	SubSection "Display"

		Depth		8

		Modes		"1280x800"

	EndSubSection

	SubSection "Display"

		Depth		15

		Modes		"1280x800"

	EndSubSection

	SubSection "Display"

		Depth		16

		Modes		"1280x800"

	EndSubSection

	SubSection "Display"

		Depth		24

		Modes		"1280x800"

	EndSubSection

EndSection



Section "ServerLayout"

	Identifier	"Default Layout"

	Screen		"Default Screen"

	InputDevice	"Generic Keyboard"

	InputDevice	"Configured Mouse"

	InputDevice     "stylus"	"SendCoreEvents"

	InputDevice     "cursor"	"SendCoreEvents"

	InputDevice     "eraser"	"SendCoreEvents"

	InputDevice	"Synaptics Touchpad"

EndSection



Section "DRI"

	Mode	0666

EndSection
```

---


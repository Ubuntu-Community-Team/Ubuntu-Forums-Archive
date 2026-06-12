---
title: "ATI Radeon + MergedFB Dual Monitor + Beryl. Kinda works...?"
date: 2007-04-04
forum: Desktop Effects &amp; Customization
---

### Post by imluxwhoru on 2007-04-04
Ok guys. Here is a fun one.  Oh how I love Ati *sigh*. Anyways. On my system, Beryl works amazingly well with a single monitor setup. And Kubuntu works amazingly well with a dual-screen setup using MergedFB. But, when I run beryl with both screens some strange things start happening.

1st of all, one of the screens works just fine. So all of the issues I'm about to mention only happen on the second screen (It's my 'primary' screen, plugged into the dri output on my card) Second, just for reference, I'm using a ATI radeon 9250 AGP card, using the 'radeon' driver. Also, as I've read about a thousand threads on this forum about this kinda stuff... I'm -not- using Xinerama, and I have Composite --Disabled-- in Xorg. So, those can't be the problem. Sooo... On with the show.

On the monitor that doesn't function properly, I have these issues. When I 1st start beryl, I have some very interesting artifacts. Actually the entire screen fills up with blue rectangles about half an inch -by- an inch and a half. So, after that happens, I can clear that up by spinning the beryl 'desktop cube' around a little. But, that's a problem too! When I spin the cube, half the cube (diagonally from corner to corner) will black out. Then, when I go back to just a normal desktop, the blacked out portion will stay blacked out (but any windows I have open over that will appear as normal). When I hit the K menu, and then click off it to close it, it will leave an image of itself on my desktop.... The 'bouncing cursor' when you start a program leaves trails.... When I click and drag a window it leaves trails.... 

This all seems reminiscent of old OpenGL issues from back in (Dare I say it) windows 95, and I wondered if this was an OpenGL issue. I'm attaching a copy of my  xorg.conf and the output of glxinfo just for kicks. 

I know a lot of people have had tons of problems getting beryl to run with a dual-head setup with ati at all. So, I'm hoping this thread will help more people than just myself. It's taken me about 2 weeks just to get where I am now. I'm so close I can taste it!! 

My xorg.conf :

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV200 QW [Radeon 7500]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option         "MergedFB" "true"
 	Option         "MonitorLayout" "LCD, CRT" 
 	Option         "CRT2Hsync" "30-70" 
 	Option         "CRT2VRefresh" "50-120" 
 	Option         "OverlayOnCRTC2" "true"
 	Option         "CRT2Position" "RightOf"
 	Option         "MetaModes" "1024x768-1024x768"
	Option         "MergedXineramaCRT2IsScreen0" "true"
	Option         "DRI" "true"
	Option         "GARTSize" "64"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-150
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV200 QW [Radeon 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "0"
	Option "Xinerama" "0"
EndSection

-------Here comes the output of glxinfo

name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram,
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

Thanks for reading!!

---

### Post by imluxwhoru on 2007-04-05
**bump**

---

### Post by mtxf on 2007-05-11
i have the exact same problem
pretty much the same setup as well, radeon 9250 card with the opensource drivers

i think it is a beryl bug unfortunately, as metacity can handle both screens for me and ive been able to reproduce the problem using the latest version of sabayon. a quick google seems to indicate this is the case :(

if anyone knows of a fix please post!
thanks

---


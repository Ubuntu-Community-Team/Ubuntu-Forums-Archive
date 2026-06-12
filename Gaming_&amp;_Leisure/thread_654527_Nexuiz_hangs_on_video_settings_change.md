---
title: "Nexuiz hangs on video settings change"
date: 2007-12-31
forum: Gaming &amp; Leisure
---

### Post by kr0n1x on 2007-12-31
hi, i've ubuntu gutsy 64 bit and i installed Nexuiz.
I launch it and it works.. but when i try to change some video settings, it restart and the screen (of the game) stay black...

why i've this problem?:(

there is the output:
```
pasquale@pasquale-desktop:~$ nexuiz
Console initialized.
Nexuiz Linux 09:41:43 Jul  6 2007
Trying to load library... "libz.so.1" - loaded.
Compressed files support enabled
Added packfile /usr/share/games/nexuiz/data/data20070531.pk3 (3665 files)
Trying to load library... "libcurl.so.4" - loaded.
cURL support enabled
Initializing client
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Ogg Vorbis support enabled
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Starting video system
Video: window 800x600x32x60hz
Linked against SDL version 1.2.11
Using SDL library version 1.2.11
checking for OpenGL 1.1.0...  enabled
GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 7600 GS/PCI/SSE2
GL_VERSION: 2.1.1 NVIDIA 100.14.19
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
SDL_EXTENSIONS: 
Checking OpenGL extensions...
checking for glDrawRangeElements...  enabled
checking for GL_ARB_multitexture...  enabled
checking for GL_ARB_texture_env_combine...  enabled
checking for GL_ARB_texture_env_dot3...  enabled
checking for GL_EXT_texture3D...  enabled
checking for GL_ARB_texture_cube_map...  enabled
checking for GL_ARB_texture_non_power_of_two...  enabled
checking for GL_EXT_compiled_vertex_array...  enabled
checking for GL_EXT_texture_edge_clamp...  enabled
checking for GL_EXT_texture_filter_anisotropic...  enabled
checking for GL_EXT_blend_minmax...  enabled
checking for GL_EXT_blend_subtract...  enabled
checking for glStencilOpSeparate...  enabled
checking for GL_EXT_stencil_two_side...  enabled
checking for GL_ARB_vertex_buffer_object...  enabled
checking for GL_ARB_shader_objects...  enabled
checking for GL_ARB_shading_language_100...  enabled
checking for GL_ARB_vertex_shader...  enabled
checking for GL_ARB_fragment_shader...  enabled
1 SDL joystick(s) found:
joystick #0: opened "Microsoft Microsoft SideWinder Plug & Play Game Pad" with 2 axes, 6 buttons, 0 balls
OpenGL Backend starting...
glDrawRangeElements detected (max vertices 4096, max indices 4096)
GLSL shader support detected: texture units = 4 texenv, 16 image, 8 array
OpenGL backend started.
Trying to load library... "libjpeg.so.62" - loaded.
JPEG support enabled
Trying to load library... "libpng12.so.0" - loaded.
PNG support enabled
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
SndSys_Init: using the SDL module
Sound format: 48000Hz, 2 channels, 16 bits per sample
Found 1 cdrom drives.
No CD in drive 0.
CDAudio_Init: No CD in player.
Can't get initial CD volume
CD Audio Initialized
Draw_CachePic: failed to load gfx/m_white
No CD in player.
Client using port 0
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:32797
OpenGL Backend shutting down
```

i know i can change the config modifying ~/.nexuiz/data/config.cfg but i can't find an hot to to do it...what entry to edit etc...

here is my xorg:
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option 		"Buttons" 		"7"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
	Option 		"ButtonMapping" 	"1 2 3 6 7"
	Option		"Resolution"		"800"
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
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	512000
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-86
	VertRefresh	50-160
# V-freq: 75.00 Hz  // h-freq: 80.42 KHz
	Modeline "1280x1024" 151.83  1280 1360 1544 1888  1024 1024 1027 1072
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GS]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Module"
	Load		"glx"
EndSection
```

can anyone help me? :)

thanks bye

---


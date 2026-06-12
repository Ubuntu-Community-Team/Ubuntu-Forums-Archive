---
title: "Warsow 0.42 fullscreen resolution problem"
date: 2008-06-07
forum: Gaming &amp; Leisure
---

### Post by Jedah on 2008-06-07
First of all I salute the Ubuntu community and especially the gaming one! I've recently installed Ubuntu 8.04 LTS and so far the experience is very satisfying and I managed to solve all the little problems I've encountered.
This subject is about a problem I cannot figure out a solution for...

I've downloaded the Warsow 0.42 from its official website, since the repository version is quite old (0.32). The game cannot set the fullscreen video mode I want, 1024x768 85Hz, 32 bits. Every other game/program I've installed (Enemy Territory, Open Arena, Sauerbraten, even ZSnes) can use it without any problem. The strange thing about Warsow is that although it reports in the options menu that 640x480 is used, my monitor reports that 1280x1024 60Hz is used during the startup! Is the game using some scaling of the rendered res to the displaying res? 

Here's the error message written on stderr (default console appl errors):
```

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x3200004
  Serial number of failed request:  57
  Current serial number in output stream:  62
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c25767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7c2581e]
#2 /usr/lib/libX11.so.6 [0xb7e0e518]
#3 /usr/lib/libGL.so.1 [0xb77b67d5]

```

I suspected that /etc/X11/xorg.conf does not contain the mode Warsow is trying to switch. It is indeed not mentioned in the file, but how on earth other applications manage to switch to it?

Here's the warsow full output before the error:
```
Added pk3 file ./basewsw/billboard.pk3 (14 files)
Added pk3 file ./basewsw/data0.pk3 (749 files)
Added pk3 file ./basewsw/data0_pure.pk3 (893 files)
Added pk3 file ./basewsw/data1.pk3 (121 files)
Added pk3 file ./basewsw/data1_pure.pk3 (28 files)
Added pk3 file ./basewsw/editortextures.pk3 (17 files)
Added pk3 file ./basewsw/map_wamphi.pk3 (26 files)
Added pk3 file ./basewsw/map_wca1.pk3 (14 files)
Added pk3 file ./basewsw/map_wca2.pk3 (6 files)
Added pk3 file ./basewsw/map_wca4.pk3 (6 files)
Added pk3 file ./basewsw/map_wctf1.pk3 (6 files)
Added pk3 file ./basewsw/map_wctf2.pk3 (13 files)
Added pk3 file ./basewsw/map_wctf3.pk3 (4 files)
Added pk3 file ./basewsw/map_wctf5.pk3 (6 files)
Added pk3 file ./basewsw/map_wda1.pk3 (23 files)
Added pk3 file ./basewsw/map_wda2.pk3 (8 files)
Added pk3 file ./basewsw/map_wda3.pk3 (31 files)
Added pk3 file ./basewsw/map_wda4.pk3 (13 files)
Added pk3 file ./basewsw/map_wda5.pk3 (22 files)
Added pk3 file ./basewsw/map_wda6.pk3 (21 files)
Added pk3 file ./basewsw/map_wdm1.pk3 (14 files)
Added pk3 file ./basewsw/map_wdm10.pk3 (6 files)
Added pk3 file ./basewsw/map_wdm10a.pk3 (6 files)
Added pk3 file ./basewsw/map_wdm11.pk3 (6 files)
Added pk3 file ./basewsw/map_wdm14.pk3 (6 files)
Added pk3 file ./basewsw/map_wdm15.pk3 (14 files)
Added pk3 file ./basewsw/map_wdm17.pk3 (9 files)
Added pk3 file ./basewsw/map_wdm19.pk3 (25 files)
Added pk3 file ./basewsw/map_wdm2.pk3 (6 files)
Added pk3 file ./basewsw/map_wdm3.pk3 (14 files)
Added pk3 file ./basewsw/map_wdm4.pk3 (14 files)
Added pk3 file ./basewsw/map_wdm5.pk3 (6 files)
Added pk3 file ./basewsw/map_wdm6.pk3 (6 files)
Added pk3 file ./basewsw/map_wdm7.pk3 (45 files)
Added pk3 file ./basewsw/map_wdm8.pk3 (70 files)
Added pk3 file ./basewsw/map_wdm9.pk3 (6 files)
Added pk3 file ./basewsw/map_wtest13.pk3 (66 files)
Added pk3 file ./basewsw/map_wtest18.pk3 (11 files)
Added pk3 file ./basewsw/modules_04.pk3 (15 files)
Added pk3 file ./basewsw/modules_041.pk3 (15 files)
Added pk3 file ./basewsw/modules_042.pk3 (15 files)
Added pk3 file ./basewsw/tex_blx_pure.pk3 (320 files)
Added pk3 file ./basewsw/tex_blxbis_pure.pk3 (80 files)
Added pk3 file ./basewsw/tex_chaoswsw_pure.pk3 (76 files)
Added pk3 file ./basewsw/tex_ecel_pure.pk3 (109 files)
Added pk3 file ./basewsw/tex_exwsw_pure.pk3 (139 files)
Added pk3 file ./basewsw/tex_factory_pure.pk3 (56 files)
Added pk3 file ./basewsw/tex_hazelh_pure.pk3 (89 files)
Added pk3 file ./basewsw/tex_hexagons_pure.pk3 (26 files)
Added pk3 file ./basewsw/tex_refly_pure.pk3 (8 files)
Added pk3 file ./basewsw/tex_russus_pure.pk3 (16 files)
Added pk3 file ./basewsw/tex_supersymmetry_ctf_pure.pk3 (8 files)
Added pk3 file ./basewsw/tex_supersymmetry_pure.pk3 (9 files)
Added pk3 file ./basewsw/tex_terrain_pure.pk3 (6 files)
Using /home/miltos/.warsow for writing
Executing: default.cfg
Executing: config.cfg
Couldn't execute: autoexec.cfg
fs_basepath is write protected.
fs_usehomedir is write protected.
Hostname: Miltos-Ubuntu
IP: 127.0.1.1
Game running at 62 fps. Server transmit at 20 pps
Console initialized.
------- sound initialization -------
Loading sound module: qf
SDL Audio driver initializing...
Calling SDL_Init(SDL_INIT_AUDIO)...
SDL_Init(SDL_INIT_AUDIO) passed.
SDL audio driver is "alsa"
Format we requested from SDL audio device:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Format we actually got:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Starting SDL audio callback...
SDL audio initialized.
Sound sampling rate: 44100
Initialization of qf succesful
------------------------------------

----- R_Init -----
Using libGL.so.1 for OpenGL...Display initialization
..XFree86-VidMode Extension Version 2.2
..XFree86-Xinerama Extension Version 1.1
..Got colorbits 24, depthbits 24, stencilbits 8
640x480 -> 1280x1024: 544
640x480 -> 1280x960: 480
640x480 -> 1280x800: 320
640x480 -> 1280x768: 288
640x480 -> 1152x864: 384
640x480 -> 1152x768: 288
640x480 -> 1024x768: 288
640x480 -> 1024x768: 288
640x480 -> 1024x768: 288
640x480 -> 1024x768: 288
640x480 -> 1024x768: 288
640x480 -> 840x525: 45
640x480 -> 832x624: 144
640x480 -> 800x600: 120
640x480 -> 800x600: 120
640x480 -> 800x600: 120
640x480 -> 800x600: 120
640x480 -> 800x600: 120
640x480 -> 800x600: 120
640x480 -> 800x512: 32
640x480 -> 640x512: 0
640x480 -> 640x480: 0
640x480 -> 640x480: 0
640x480 -> 640x480: 0
640x480 -> 640x480: 0
640x480 -> 640x480: 0
640x480 -> 640x480: 0
640x512 selected
...setting fullscreen mode 3:

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 7600 GS/AGP/SSE/3DNOW!
GL_VERSION: 2.1.2 NVIDIA 169.12
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GLW_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_texture_from_pixmap GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_ARB_get_proc_address 
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_TEXTURE_UNITS: 4
GL_MAX_CUBE_MAP_TEXTURE_SIZE: 4096
GL_MAX_3D_TEXTURE_SIZE: 512
GL_MAX_TEXTURE_MAX_ANISOTROPY: 16

mode: 3, fullscreen, 
CDS: enabled
picmip: 0
texturemode: GL_LINEAR_MIPMAP_LINEAR
vertical sync: disabled
multitexture: enabled
compiled_vertex_array: enabled
vertex_buffer_object: disabled
texture3D: enabled
draw_range_elements: enabled
occlusion_query: enabled
texture_env_add: enabled
texture_env_combine: enabled
texture_compression: disabled
texture_edge_clamp: enabled
texture_filter_anisotropic: enabled
texture_cube_map: enabled
bgra: enabled
depth_texture: enabled
shadow: enabled
generate_mipmap: enabled
texture_non_power_of_two: enabled
vertex_shader: enabled
fragment_shader: enabled
shader_objects: enabled
shading_language_100: enabled
GLSL: enabled
GLSL_branching: enabled
GLSL_no_half_types: disabled
swap_control: enabled
----- finished R_Init -----
Unknown command "menu_main"
Opening UDP/IP socket: *:0

Initializing Shaders:
...loading 'scripts/adv1.shader'
...loading 'scripts/amphi.shader'
...loading 'scripts/billboard.shader'
...loading 'scripts/blx.shader'
...loading 'scripts/blx_ca.shader'
...loading 'scripts/blx_dm4.shader'
...loading 'scripts/blx_grey.shader'
...loading 'scripts/blx_houses.shader'
...loading 'scripts/blx_tech2.shader'
...loading 'scripts/blx_wt3.shader'
...loading 'scripts/blxbis.shader'
...loading 'scripts/bobot.shader'
...loading 'scripts/budndumby.shader'
...loading 'scripts/common.shader'
...loading 'scripts/cubemapwater.shader'
...loading 'scripts/ecel.shader'
...loading 'scripts/effects.shader'
...loading 'scripts/evil8_base.shader'
...loading 'scripts/extra.shader'
...loading 'scripts/exwsw.shader'
...loading 'scripts/factory.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/hazelh.shader'
...loading 'scripts/headicons.shader'
...loading 'scripts/house1.shader'
...loading 'scripts/house3.shader'
...loading 'scripts/house4.shader'
...loading 'scripts/hud.shader'
...loading 'scripts/jumppad1.shader'
...loading 'scripts/models.shader'
...loading 'scripts/monada.shader'
...loading 'scripts/nateleaf.shader'
...loading 'scripts/nateshad.shader'
...loading 'scripts/padpork.shader'
...loading 'scripts/polybeams.shader'
...loading 'scripts/respawnindicators.shader'
...loading 'scripts/russus.shader'
...loading 'scripts/silverclaw.shader'
...loading 'scripts/sockter.shader'
...loading 'scripts/solidfake_credits.shader'
...loading 'scripts/solidfake_lights.shader'
...loading 'scripts/starsky.shader'
...loading 'scripts/supersymmetry.shader'
...loading 'scripts/team0ups.shader'
...loading 'scripts/telestecki.shader'
...loading 'scripts/ui.shader'
...loading 'scripts/viciious.shader'
...loading 'scripts/wctf2.shader'
...loading 'scripts/wda3.shader'
...loading 'scripts/wda5.shader'
...loading 'scripts/wda6.shader'
...loading 'scripts/wdm1.shader'
...loading 'scripts/wdm19.shader'
...loading 'scripts/wdm4.shader'
...loading 'scripts/wdm6.shader'
...loading 'scripts/wdm7.shader'
...loading 'scripts/wdm8.shader'
...loading 'scripts/wdm9.shader'
...loading 'scripts/web.shader'
...loading 'scripts/world.shader'
--------------------------------------

Checking for Warsow update.
Downloading warsow_last_version.txt from http://update.warsow.net/warsow_last_version.txt
Your Warsow version is up-to-date.
====== Warsow Initialized ======
r_mode will be changed upon restarting video.

----- R_Init -----
Using libGL.so.1 for OpenGL...Display initialization
..XFree86-VidMode Extension Version 2.2
..XFree86-Xinerama Extension Version 1.1
..Got colorbits 24, depthbits 24, stencilbits 8
1024x768 -> 1280x1024: 256
1024x768 -> 1280x960: 192
1024x768 -> 1280x800: 32
1024x768 -> 1280x768: 0
1024x768 -> 1152x864: 96
1024x768 -> 1152x768: 0
1024x768 -> 1024x768: 0
1024x768 -> 1024x768: 0
1024x768 -> 1024x768: 0
1024x768 -> 1024x768: 0
1024x768 -> 1024x768: 0
1280x768 selected
...setting fullscreen mode 6:

```

And here's /etc/X11/xorg.conf:
```

# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,gr"
	Option		"XkbVariant"	","
	Option		"XkbOptions"	"grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by Jedah on 2008-06-09
Tried also the 0.42 debian package version from getdeb and the problem persists? Any ideas?

---

### Post by MCrittenden on 2008-12-27
Same problem in 8.10. Did you ever find a solution?

---

### Post by whoobex on 2009-12-11
got this problem aswell. how on earth do I get 5.0 going with a X1800XT ATI card?

---

### Post by cruiseoveride on 2010-02-04
How did you fix it? I have the same problem with Ubuntu-9.10

---

### Post by cruiseoveride on 2010-02-04
> **cruiseoveride said:**
> How did you fix it? I have the same problem with Ubuntu-9.10

Figured it out:
```

./warsow.x86_64 +set r_ignorehwgamma 1

```

---


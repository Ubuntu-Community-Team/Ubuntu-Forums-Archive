---
title: "Another strange ET problem"
date: 2005-08-02
forum: Gaming &amp; Leisure
---

### Post by Cyberkef on 2005-08-02
This afternoon I downloaded **et-linux-2.60.x86.run** and afaik installed it correctly.

Now when I want to start et, something strange happens. No errors, no exits... Everything seems ok in the console:

```
cyberkef@CyberTrax2000:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/cyberkef/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce2 MX/AGP/SSE/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce2 MX/AGP/SSE/3DNOW!
GL_VERSION: 1.5.3 NVIDIA 71.74
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 2

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
```
But the screen is black and stays black. No intro, no movie, no menu, nothing... :-# 

The strange thing is, I can move my mouse to the right, bottom of my screen and my desktop appears. ET is just a black box on my desktop.

Ctrl+c to close the box, and then I have to reapply the correct resolution (sticked to 800x600, i use something else)

I have the latest drivers and i think they are installed correctly (i have no errors on starting the game). 
Maybe it has to do something with the 3D card: **GeForce MX 400** because somebody on another forum had just the same problem with the same card :|

---

### Post by imnes on 2005-08-03
This seems to be a new problem.  I've always been able to play this game in the past, but recently I installed a fresh copy of ubuntu 5.04 (with all latest updates), and then installed ET 2.6.  And I have the same problem you do.  If anybody knows the fix it would be appreciated.

Nick

---

### Post by Cyberkef on 2005-08-03
[QUOTE=imnes]This seems to be a new problem.  I've always been able to play this game in the past, but recently I installed a fresh copy of ubuntu 5.04 (with all latest updates), and then installed ET 2.6.  And I have the same problem you do.  If anybody knows the fix it would be appreciated.

Nick[/QUOTE]
et +set r_mode 4 +set r_fullscreen 0 +set snddevice "/dev/null"

Temporary Fix with no sound

---

### Post by Mishura on 2005-08-04
Works fine for me.

There seems to be a slight epidemic with Quake/Doom based games black-screening (See other threads here).

Kill your Enlightenment Sound Daemon (esd) and try again.  Seems to conflict so I hear.

(Reason why it doesn't bother me is Kubuntu doesn't include ESD... I think..)

---

### Post by rimmer on 2005-08-04
From the output of the console it's locking at the sound  initialization. Which means you have something else using your sound card. Before you start et next run the System monitor and have a look at the process running and sleeping (ie if any sound processes are sleeping it will cause this problem). Then configure your sound right if you haven't already done so.

[This is pretty good](http://www.ubuntuforums.org/showthread.php?t=44753&page=1&pp=10&highlight=sound)

---


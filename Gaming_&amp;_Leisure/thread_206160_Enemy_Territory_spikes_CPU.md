---
title: "Enemy Territory spikes CPU"
date: 2006-06-29
forum: Gaming &amp; Leisure
---

### Post by DiamondX on 2006-06-29
I just got a new motherboard for my desktop. Installing the Nvidia drivers was easy, then I installed Wolfenstein Enemy Territory. When I start the game, the CPU spikes to full power (2GHz). Luckily it opens in a window, so I can read the CPU monitor on my top panel. In the game, Everything is smooth, except the mouse, which goes at about 2 seconds per frame (yea, .5FPS).

Edit: Here is what happens when I do "et" in the terminal:
```
me@Desktop:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/me/.etwolf/etmain
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
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
Xlib:  extension "XFree86-DGA" missing on display ":0.0".
Failed to detect XF86DGA Mouse
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce FX 5500/AGP/SSE2/3DNOW!
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_NV_fog_distance not found
... GL_EXT_texture_filter_anisotropic not found
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce FX 5500/AGP/SSE2/3DNOW!
GL_VERSION: 1.2 (2.0.2 NVIDIA 87.62)
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_texture_env_combine4 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow
GLX_EXTENSIONS: GLX_ARB_multisample GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_SGIX_fbconfig GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: software w/ 0 overbright bits
CPU:
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/me/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/me/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/me/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaed23f40
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: Desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
execing preset_high.cfg
r_colorbits will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_picmip will be changed upon restarting.
r_mode will be changed upon restarting.
r_texturebits will be changed upon restarting.
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce FX 5500/AGP/SSE2/3DNOW!
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_NV_fog_distance not found
... GL_EXT_texture_filter_anisotropic not found
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce FX 5500/AGP/SSE2/3DNOW!
GL_VERSION: 1.2 (2.0.2 NVIDIA 87.62)
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_texture_env_combine4 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow
GLX_EXTENSIONS: GLX_ARB_multisample GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_SGIX_fbconfig GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: software w/ 0 overbright bits
CPU:
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/me/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/me/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/me/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaeb21f40
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
execing preset_normal_ui.cfg
execing preset_high_ui.cfg
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console      <--- I closed it after (painfully) moving the mouse to the exit button
```

---

### Post by DiamondX on 2006-06-29
I fixed it with this tutorial:
[http://www.ubuntuforums.org/showthread.php?t=176636](http://www.ubuntuforums.org/showthread.php?t=176636)

---


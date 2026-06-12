---
title: "TrueCombat: Close Quarter Battle (CQB) path 0.223 no sound on Ubuntu 12.04.1 32bit"
date: 2013-02-01
forum: Gaming &amp; Leisure
---

### Post by auxilium on 2013-02-01
Hi,

I've been trying to install CQB for some time but I think I am missing something that I couldn't get the sound play inside CQB.

I Download CQB from here
[http://www.truecombatelite.com/index.php?page=downloads#cqb](http://www.truecombatelite.com/index.php?page=downloads#cqb)

I follow the Howto installation from here
[http://linuxgamecast.com/2011/04/l-g-c-how-to-%E2%80%94-truecombat-close-quarters-battle-cqb/](http://linuxgamecast.com/2011/04/l-g-c-how-to-%E2%80%94-truecombat-close-quarters-battle-cqb/)

Now the situation is like this:
I installed and play the W:ET with no problem using the et-sdl-sound launcher. 
CQB is the mod of W:ET. If I use the et-sdl-sound to launch W:ET and load the CQB mod, I can go to CQB menu with sound. But using the method I can't get into CQB game itself. When I start the server I goes out.

When I use the CQB launcher, I go directly to CQB menu and launch the game with no problem. The games works perfect except you got no sound.

I also google the net and search on this forum but I think my situation is kinda different and other suggestions won't work for me. Now this is my last option to ask for help.

Thank you guys. I like to try this free game and this no-crosshair arise my curiosity. I am a bit new to linux.


Cheers,

---

### Post by auxilium on 2013-02-03
Hi,

Checking the net and I change few things in my cqblancher but then its like nothing new happened. It has same no sound. Here is my modified cqblauncher

#!/bin/bash
export ETSDL_SDL_LIB=”libSDL.so”
export SDL_AUDIODRIVER=”alsa”
cd "/usr/local/games/enemy-territory"
LD_PRELOAD=”${LD_PRELOAD}:/usr/local/games/enemy-territory/et-sdl-sound” ./et.x86 +set fs_game cqbtest +set com_soundMegs 64 +set com_hunkMegs 256 +set com_zoneMegs 64 +set s_khz 44 +set r_maxpolyverts 16384 +set r_maxpolys 4096$*

I wonder what when wrong.

---

### Post by auxilium on 2013-02-04
Hi,

This is my log when I try to "Run from terminal" the cqblauncher

```


ERROR: ld.so: object '&#8221;' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/local/games/enemy-territory/et-sdl-sound&#8221;' from LD_PRELOAD cannot be preloaded: ignored.
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/tux/.etwolf/cqbtest
/usr/local/games/enemy-territory/cqbtest/pak5.pk3 (13 files)
/usr/local/games/enemy-territory/cqbtest/pak4.pk3 (603 files)
/usr/local/games/enemy-territory/cqbtest/pak3.pk3 (28 files)
/usr/local/games/enemy-territory/cqbtest/pak2.pk3 (2369 files)
/usr/local/games/enemy-territory/cqbtest/pak1.pk3 (473 files)
/usr/local/games/enemy-territory/cqbtest/pak0.pk3 (742 files)
/usr/local/games/enemy-territory/cqbtest/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/cqbtest
/home/tux/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
7995 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/BetaTester/etconfig.cfg
execing autoexec.cfg
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
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 210/PCIe/SSE2/3DNOW!
^3WARNNING: GL extensions string too long (6140), truncated to 4096
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 210/PCIe/SSE2/3DNOW!
GL_VERSION: 3.3.0 NVIDIA 304.64
GL_EXTENSIONS: GL_ARB_base_instance GL_ARB_blend_func_extended GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_compressed_texture_pixel_storage GL_ARB_conservative_depth GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_ES2_compatibility GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_get_program_binary GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_robustness GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_objects GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shading_language_420pack GL_ARB_shading_language_include GL_ARB_shading_language_packing GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_storage GL_ARB_texture_swizzle GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback_instanced GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_format_BGRA8888 GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_storage GL_EXT_texture_swizzle GL_EXT_texture_type_2_10_10_10_REV GL_EXT_timer_query GL_EXT_transform_feedback2 GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_x11_sync_object GL_EXT_import_sync_object GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_alpha_test GL_NV_blend_minmax GLGLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_swap_control GLX_EXT_swap_control_tear GLX_EXT_texture_from_pixmap GLX_ARB_create_context GLX_ARB_create_context_profile GLX_EXT_create_context_es2_profile GLX_ARB_create_context_robustness GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_EXT_framebuffer_sRGB GLX_NV_multisample_coverage GLX_ARB_get_proc_address 
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 16
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/tux/.etwolf/cqbtest/ui.mp.i386.so)... 
Sys_LoadDll(/home/tux/.etwolf/cqbtest/ui.mp.i386.so) failed:
"/home/tux/.etwolf/cqbtest/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/cqbtest/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0x9d9b99e0  
Sys_LoadDll(ui) succeeded!
WARNING: reused image ui/assets/fadebox.tga with mixed glWrapClampMode parm
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: tux8
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
^3WARNING: unknown UI script 0
^3WARNING: unknown UI script 1
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
------ Server Initialization ------
Server: cqb_sample
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- FS_Startup -----
Current search path:
/home/tux/.etwolf/cqbtest
/usr/local/games/enemy-territory/cqbtest/pak5.pk3 (13 files)
/usr/local/games/enemy-territory/cqbtest/pak4.pk3 (603 files)
/usr/local/games/enemy-territory/cqbtest/pak3.pk3 (28 files)
/usr/local/games/enemy-territory/cqbtest/pak2.pk3 (2369 files)
/usr/local/games/enemy-territory/cqbtest/pak1.pk3 (473 files)
/usr/local/games/enemy-territory/cqbtest/pak0.pk3 (742 files)
/usr/local/games/enemy-territory/cqbtest/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/cqbtest
/home/tux/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

handle 1: video/etintro.roq
----------------------
15990 files in pk3 files
Sys_LoadDll(/home/tux/.etwolf/cqbtest/qagame.mp.i386.so)... 
Sys_LoadDll(/home/tux/.etwolf/cqbtest/qagame.mp.i386.so) failed:
"/home/tux/.etwolf/cqbtest/qagame.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/cqbtest/qagame.mp.i386.so)... ok
Sys_LoadDll(qagame) found **vmMain** at  0x99749140  
Sys_LoadDll(qagame) succeeded!
------- Game Initialization -------
gamename: cqbtest
gamedate: Apr 10 2011
Not logging to disk.
Gametype changed, clearing session data.
Enable spawning!
Disable spawning!
0 teams with 0 entities
-----------------------------------
Setting MOTD...
-----------------------------------
write session data client 0, type 0, latched 0
RE_Shutdown( 0 )
----- R_Init -----

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 210/PCIe/SSE2/3DNOW!
GL_VERSION: 3.3.0 NVIDIA 304.64
GL_EXTENSIONS: GL_ARB_base_instance GL_ARB_blend_func_extended GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_compressed_texture_pixel_storage GL_ARB_conservative_depth GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_ES2_compatibility GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_get_program_binary GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_robustness GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_objects GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shading_language_420pack GL_ARB_shading_language_include GL_ARB_shading_language_packing GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_storage GL_ARB_texture_swizzle GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback_instanced GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_format_BGRA8888 GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_storage GL_EXT_texture_swizzle GL_EXT_texture_type_2_10_10_10_REV GL_EXT_timer_query GL_EXT_transform_feedback2 GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_x11_sync_object GL_EXT_import_sync_object GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_alpha_test GL_NV_blend_minmax GLGLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_swap_control GLX_EXT_swap_control_tear GLX_EXT_texture_from_pixmap GLX_ARB_create_context GLX_ARB_create_context_profile GLX_EXT_create_context_es2_profile GLX_ARB_create_context_robustness GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_EXT_framebuffer_sRGB GLX_NV_multisample_coverage GLX_ARB_get_proc_address 
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 16
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/tux/.etwolf/cqbtest/ui.mp.i386.so)... 
Sys_LoadDll(/home/tux/.etwolf/cqbtest/ui.mp.i386.so) failed:
"/home/tux/.etwolf/cqbtest/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/cqbtest/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0x9d9b99e0  
Sys_LoadDll(ui) succeeded!
WARNING: reused image ui/assets/fadebox.tga with mixed glWrapClampMode parm
Sys_LoadDll(/home/tux/.etwolf/cqbtest/cgame.mp.i386.so)... 
Sys_LoadDll(/home/tux/.etwolf/cqbtest/cgame.mp.i386.so) failed:
"/home/tux/.etwolf/cqbtest/cgame.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/cqbtest/cgame.mp.i386.so)... ok
Sys_LoadDll(cgame) found **vmMain** at  0x95209010  
Sys_LoadDll(cgame) succeeded!
LOADING... collision map
LOADING... sounds
voice chat memory size = 0

.........................
Initializing Sound Scripts
...loading 'sound/scripts/vo_allies.sounds'
...loading 'sound/scripts/vo_axis.sounds'
...loading 'sound/scripts/vo_common.sounds'
...loading 'sound/scripts/cqb_sample.sounds'
done.
LOADING... graphics
LOADING... maps/cqb_sample.bsp
stitched 2 LoD cracks
...loaded 13442 faces, 243 meshes, 3561 trisurfs, 0 flares 14 foliage
LOADING... entities
LOADING... game media
LOADING...  - textures
LOADING...  - models
LOADING...  - weapons
LOADING...  - items
LOADING...  - inline models
LOADING...  - server models
LOADING...  - particles
LOADING...  - classes
LOADING...  - game media done
LOADING... flamechunks
LOADING... clients
[skipnotify]^2*** You have been authorized "referee" status ***
Type: ^3ref^7 (by itself) for a list of referee commands.
CL_InitCGame: 15.21 seconds
Com_TouchMemory: 1 msec
==== ShutdownGame ====
write session data client 0, type 0, latched 0
Sys_LoadDll(/home/tux/.etwolf/cqbtest/qagame.mp.i386.so)... 
Sys_LoadDll(/home/tux/.etwolf/cqbtest/qagame.mp.i386.so) failed:
"/home/tux/.etwolf/cqbtest/qagame.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/cqbtest/qagame.mp.i386.so)... ok
Sys_LoadDll(qagame) found **vmMain** at  0x99749140  
Sys_LoadDll(qagame) succeeded!
------- Game Initialization -------
gamename: cqbtest
gamedate: Apr 10 2011
Not logging to disk.
Enable spawning!
Disable spawning!
0 teams with 0 entities
-----------------------------------
Setting MOTD...
[skipnotify]BetaTester^7 entered the game
BetaTester^7 has joined the Specops^7!
----- Server Shutdown -----
==== ShutdownGame ====
write session data client 0, type 0, latched 0
---------------------------
Sys_LoadDll(/home/tux/.etwolf/cqbtest/ui.mp.i386.so)... 
Sys_LoadDll(/home/tux/.etwolf/cqbtest/ui.mp.i386.so) failed:
"/home/tux/.etwolf/cqbtest/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/cqbtest/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0x9d9b99e0  
Sys_LoadDll(ui) succeeded!
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console


```again this is my cqblauncher

```


#!/bin/bash
export ETSDL_SDL_LIB=&#8221;libSDL.so&#8221;
export SDL_AUDIODRIVER=&#8221;alsa&#8221;
cd "/usr/local/games/enemy-territory"
LD_PRELOAD=&#8221;${LD_PRELOAD}:/usr/local/games/enemy-territory/et-sdl-sound&#8221; ./et.x86 +set fs_game cqbtest +set com_soundMegs 64 +set com_hunkMegs 256 +set com_zoneMegs 64 +set s_khz 44 +set r_maxpolyverts 16384 +set r_maxpolys 4096$*


```in the cqblauncher: line4, I tried with double quote and no double quote, the program runs the same. CQB still dont have sound. I also try to change also to pulse yet no luck.

I saw this from the terminal. Maybe this could be a clue. 

```

ERROR: ld.so: object '&#8221;' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/local/games/enemy-territory/et-sdl-sound&#8221;' from LD_PRELOAD cannot be preloaded: ignored.

```and

```

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------

```Does anybody out there got same problem with me? Sound is perfectly working with other games, audio files and video files. I am running low in idea :)



Thanks

---

### Post by auxilium on 2013-02-05
Bump...

Can this be solved?



Thank you

---

### Post by auxilium on 2013-02-15
bump..

ouch! 

where do i restart again?? i am lost

---

### Post by Perfect Storm on 2013-02-16
> ERROR: ld.so: object '/usr/local/games/enemy-territory/et-sdl-sound”' from LD_PRELOAD cannot be preloaded: ignored.

Have checked and see if path is there (plus the libs)?

---

### Post by auxilium on 2013-02-17
> 

             Quote:
                                                 ERROR: ld.so: object '/usr/local/games/enemy-territory/et-sdl-sound”' from LD_PRELOAD cannot be preloaded: ignored.                                 
Have checked and see if path is there (plus the libs)?     

I had checked the file et-sdl-sound, the file is really there and the path is right.

Things I did:
-->I checked for the mispelled command(the cqblauncher script and the original script) but its the difference there was the path to my file.

-->I look for libSDL.so in the /usr/lib folder, it was there but it was a shortcut symbol. I cant understand the file upon opening it in the gedit.

-->I had downloaded new SDL from [http://www.libsdl.org/](http://www.libsdl.org/). Now I get more confused because some forums says to change the EXPORT path to point to the new SDL. Just like this forums says [http://ubuntuforums.org/showthread.php?t=362231&page=17](http://ubuntuforums.org/showthread.php?t=362231&page=17)

I am trying to cross reference things from several forums but the problem was, those forums are too old. I am thinking they may be obsolete to apply to my current problem.

Some forums suggesting me to install libsdl1.2-dev but I got this output on terminal
```


The following NEW packages will be installed:
  libsdl1.2-dev
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0 B/825 kB of archives.
After this operation, 2,513 kB of additional disk space will be used.
(Reading database ... 406972 files and directories currently installed.)
Unpacking libsdl1.2-dev (from .../libsdl1.2-dev_1.2.14-6.4ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsdl1.2-dev_1.2.14-6.4ubuntu3_i386.deb (--unpack):
 trying to overwrite '/usr/bin/sdl-config', which is also in package sdl-devel 1.2.15-2
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libsdl1.2-dev_1.2.14-6.4ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```This myb not necessary(but this may also help others) to post where I cross reference. Below are the list of forums I checked out:

[http://ubuntuforums.org/showthread.php?t=362231&page=17](http://ubuntuforums.org/showthread.php?t=362231&page=17)

[http://askubuntu.com/questions/17579/how-to-fix-sound-in-wolfenstein-enemy-territory](http://askubuntu.com/questions/17579/how-to-fix-sound-in-wolfenstein-enemy-territory)

[https://aur.archlinux.org/packages/et-sdl-sound/](https://aur.archlinux.org/packages/et-sdl-sound/)

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

[http://ubuntuforums.org/showthread.php?t=644194](http://ubuntuforums.org/showthread.php?t=644194)

-->I also visit [http://nullkey.kapsi.fi/et-sdl-sound/](http://nullkey.kapsi.fi/et-sdl-sound/) then download and try another et-sdl-sound.so and check if some sound would go. still no sound after launching the cqb


Now I am thinking if not a wrong spelling, the problem could be, to point the script to the right SDL(the new or the old or some other file). If not could be a conflict to the new and old SDL. It could be a dependency problem. How could I sort this out. I usually start from the cqblauncher then progress

I had backed up the cqblauncher, et-sdl-sound, et-sdl-sound.so

One more thing. If I run the et-sdl-sound (not the et-sdl-sound.so) I get to Wolfenstien Enemy Territory all working well even the Omni-bot mods is working fine, with all the sounds. From the mods selection, I also had the cqbtest but when I choose it, I go back to Desktop

But then I launch the "cqblauncher" script. I can get the CQB work fine but with no sound. I go directly to the CQB menu without the Enemy Territory mod selection.

So I am thinking that the CQB launcher is not pointing to the right SDL or could be another reason I still dont know.

Yet I got the feeling that we are so close to unlock this puzzle.


Thanks guys!!!

---


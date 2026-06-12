---
title: "Enemy Territory: sound, but no screen"
date: 2005-10-23
forum: Gaming &amp; Leisure
---

### Post by WishMaster on 2005-10-23
- I downloaded "et-linux-2.60.x86.run"
- chmod +x et-linux-2.60.x86.run
- ./et-linux-2.60.x86.run

I graphically installed it as a user, but it wouldn't start up
Installed it again as root.

When I type "et" in terminal, I get:
> bert@LinuxBert:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/bert/.etwolf/etmain
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
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225 x86/MMX/SSE2
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 6.3.2
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_allocate_memory GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_group
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

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
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xacee4000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/bert/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/bert/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/bert/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xab352f40
Sys_LoadDll(ui) succeeded!
Found high quality video and normal CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: LinuxBert
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
execing preset_normal.cfg
r_subdivisions will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_texturebits will be changed upon restarting.
r_detailtextures will be changed upon restarting.
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225 x86/MMX/SSE2
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 6.3.2
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_allocate_memory GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGIS_multisample GLX_SGIX_fbconfig
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/bert/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/bert/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/bert/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xab2d1f40
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
Sys_QueEvent: overflow
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
bert@LinuxBert:~

When I type "sudo et", I get:
> bert@LinuxBert:~$ sudo et
Password:
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/bert/.etwolf/etmain
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
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225 x86/MMX/SSE2
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 6.3.2
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_allocate_memory GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGIS_multisample GLX_SGIX_fbconfig
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

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
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xaceed000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/bert/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/bert/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/bert/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xab35bf40
Sys_LoadDll(ui) succeeded!
Found high quality video and normal CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: LinuxBert
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
execing preset_normal.cfg
r_subdivisions will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_texturebits will be changed upon restarting.
r_detailtextures will be changed upon restarting.
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225 x86/MMX/SSE2
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 6.3.2
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_allocate_memory GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_group
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/bert/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/bert/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/bert/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xab2b9f40
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
bert@LinuxBert:~$


All I get is a black screen. But I hear the sound playing (with "killall -9 esd" before I type "et").

---

### Post by Zimmer on 2005-10-24
Have you downloaded and run the update file?

et-linux-2.60-update.x86.run

try from 
[http://www.gaming4all.net/de/file396_04bb09300ffc92904990f929d14516f5.html](http://www.gaming4all.net/de/file396_04bb09300ffc92904990f929d14516f5.html)

or

[http://www.fileshack.com/browse.x?cat=1774](http://www.fileshack.com/browse.x?cat=1774)
and see if that helps....

Have you read this, too?
[https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)

Hope this helps...

Regards

Zimm

---

### Post by WishMaster on 2005-10-29
I ran the patch.
Now I didn't have to "killall -9 esd" before running "et" --> sound just worked

But still no visual.

In Hoary, I was able to run Enemy Territory without any problems. Now in Breezy, it gives a black screen...

edit: this is my [hardware config.]("http://users.pandora.be/Nyx/ubuntu.html")

---

### Post by aljones15 on 2005-10-29
in package manager make sure u got GLEXT
check for it.

peace,
A

---

### Post by aljones15 on 2005-10-29
actually looks like you have glext. who knows. i fucked up my machine by messing with the opengl shit, if you try and install ligblu it uninstalls everything else. not sure which one I'm supposed to have. so in other words don't take my advice on anything graphical =)

peace,
A

---

### Post by Sionide on 2005-10-29
I can't get any sound, that's what's annoying me...

---

### Post by WishMaster on 2005-10-29
Only finding "libgtkglext" things via Synaptic 
(I did a search for "glext". None of the found results ("libgtkglext"-things) are installed)

@ Sionide:
Did you try this? -->
- Open a terminal
- type "killall -9 esd"     (your sound wil stop)
- type "et"

ET should now start with sound.

---

### Post by seethru on 2005-10-29
looks like your video card drivers aren't installed properly
```
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 6.3.2
```

Mesa is a software renderer, what video card do you have?

---

### Post by WishMaster on 2005-10-30
[My Hardware]("http://users.pandora.be/Nyx/ubuntu.html")

videocard is: Intel(R) 852GM/855GM
(82852/855GM Integrated Graphics Device)

ET runs smoothly in Windows, and did work under Hoary

---

### Post by guill on 2005-11-02
Hi!

I have the same problem, my videocard is:

Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller

Help!

---

### Post by shreevatsa on 2005-11-20
I too have exactly the same problem; I've also posted about it at [http://www.ubuntuforums.org/showpost.php?p=504471&postcount=100](http://www.ubuntuforums.org/showpost.php?p=504471&postcount=100) .

@Zimmer: Isn't the patch supposed to be for upgrading 2.56 to 2.60? I downloaded 2.60 directly, so I shouldn't need the patch, right?

---

### Post by Zimmer on 2005-11-20
> **shreevatsa]I too have exactly the same problem said:**
> http://www.ubuntuforums.org/showpost.php?p=504471&postcount=100[/url] .

@Zimmer: Isn't the patch supposed to be for upgrading 2.56 to 2.60? I downloaded 2.60 directly, so I shouldn't need the patch, right?

You could be right, but I followed the instructions on the original Hoary 5.04 documentation which (rightly or wrongly) led me to run the 2.60 install and then the patch (I had the same misgivings as yourself) .
It worked fine, after I sorted the fglrx drivers and sound , as per the instructions at

[https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)

I have just installed Breezy( I screwed up the Hoary setup by experimenting with EasyUbuntu and applied the wrong file.DOH! so bit the bullet and moved on)
 and have (apparantly) got the 3D drivers sorted on my ATI card. So the next job could be installing ET again.

I will let you know how I get on...

Zimmer

---

### Post by Buddy DarDar on 2005-11-21
I would love to know what causes this problem, I have the same thing happen.

Running a Radeon 9200SE, ati drivers are installed and working.  Sound isn't a problem (after the killall esd).

Athlon 1800+, 512mb ram, Breezy fresh install (less than 24 hours old)

Just as a note to anybody else who run into this, when the game goes blank after this intro screen try typing '~' (tilde) to bring up the ingame console, then type 'quit'.  Saves shutting down the xserver at least.

Here's what I get in the terminal


ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/connell/.etwolf/etmain
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
GL_RENDERER: RADEON 9200SE DDR Generic
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: RADEON 9200SE DDR Generic
GL_VERSION: 1.3.1017 (X4.3.0-8.19.10)
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_ATI_element_array GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_map_object_buffer GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_vertex_array_object GL_ATI_vertex_attrib_array_object GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_blend_square GL_NV_occlusion_query GL_NV_texgen_reflection GL_SGI_color_matrix GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_ARB_get_proc_address GLX_ARB_multisample
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 6

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
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xa7656000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/connell/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/connell/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/connell/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa5ac4f40
Sys_LoadDll(ui) succeeded!
Found high quality video and normal CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: ubuntu
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
execing preset_normal.cfg
r_subdivisions will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_texturebits will be changed upon restarting.
r_detailtextures will be changed upon restarting.
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: RADEON 9200SE DDR Generic
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: RADEON 9200SE DDR Generic
GL_VERSION: 1.3.1017 (X4.3.0-8.19.10)
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_ATI_element_array GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_map_object_buffer GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_vertex_array_object GL_ATI_vertex_attrib_array_object GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_blend_square GL_NV_occlusion_query GL_NV_texgen_reflection GL_SGI_color_matrix GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_ARB_get_proc_address GLX_ARB_multisample
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 6

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/connell/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/connell/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/connell/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa59e1f40
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
]\quit
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
</code>

---

### Post by Zimmer on 2005-11-22
Buddy, it still looks from the Terminal output that you have a sound problem.

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
1 stereo
32768 samples
16 samplebits
1 submission_chunk
22050 speed
0x0xa7656000 dma buffer
No background file.
----------------------
if the sound is muted, have you looked at the ALSA mixer to check the relevant settings?

Here is the Help file I wrote for myself to get Sound going on Hoary..

You may have sound related problems.......
Some of the ways to cure them...

(For Ubuntu )make sure gstreamer defaults are set to  alsasink and alsasrc
then in Terminal..

killall -9 esd
....I do not do that as I have re configed ESD as follows:-

re configure esd in it's config file to release to other applications

[esd] 
auto_spawn=0
spawn_wait_ms=100
default_options= -terminate -nobeeps -as 2

..******....but I still do this to get it to produce sound....*******

sudo sh -c 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'

**note the exact use of single and double quotes in the example above***
or try
esddsp --mmap et  (did nothing for me..)

make sure gstreamer defaults are reset to esdsink and osssrc after playing if you changed them earlier ...or your sound for other stuff might be compromised..

Zimm

---

### Post by Buddy DarDar on 2005-11-22
Not quite sure if I threadjacked here, but my last post was my first. :)

[QUOTE=Zimmer]
Buddy, it still looks from the Terminal output that you have a sound problem.
if the sound is muted, have you looked at the ALSA mixer to check the relevant settings?
[/quote]

Actually, I've seen that "Sound is muted" line in a few other threads around the net, usually unrelated to sound.  My sound hasn't really been a problem, I switched just about everything over to ALSA earlier because I'd heard of these problems.  The "killall esd" I just run once, it hasn't lead to any other sound problems.  I like those changes you have in there though and am definately going to apply them-- nothing beats saving a few steps. :)

I never had a problem with the sound in Hoary either, other than low volume.  I somehow fixed that (wasn't a muted channel or some connector 'on' when it should have been off) and it's never been a problem with Breezy.

My basic problem is still the video blanking after the intro splash screen.  I've played ET for a while now, and I believe it should be the screen before the main menu when you setup the default profile.  Music still plays fine in the background, and typing 'quit' in the console shuts ET down as it should (although I can't see what I'm typing).

Could it be a problem with creating the default profile?  I have ownership of both th e /usr/local/games/enemy-territory and (obviously) my .wolfet folder.  Something else I'm not thinking of?

I installed America's Army last night at it works a-ok.

Kinda strange.  My re-install ugrade from Hoary was stupidly smooth up until now.  

Thanks for the help.

EDIT: fixed quote.

---

### Post by Zimmer on 2005-11-23
Hi Buddy,
I just installed ET on Breezy, no problems, except I still had to go through the killall -9 esd and popping a value into the /proc files routine to get sound.
as for your output.......
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
execing preset_normal_ui.cfg
execing preset_normal_ui.cfg
You are quite correct, it appears to be failing/stalling  execing preset_normal.ui.cfg


this config file is located in pak0.pk3  ..do you have that file? is there a problem with it? permissions etc? (I assume you chmod'd the installation .run file ..)

on a standard install it is in /usr/local/games/enemy-territory/etmain
The contents aren't exactly exciting...
seta ui_r_subdivisions 12

seta ui_r_lodbias 0

seta ui_r_colorbits 0

seta ui_r_depthbits 24

seta ui_r_picmip 1

seta ui_r_mode 4

seta ui_r_texturebits 32

seta ui_r_ext_compressed_textures 1

seta ui_r_dynamiclight 1

seta r_fastSky 0

seta r_inGameVideo 1

seta cg_shadows 1

seta cg_brassTime 2500

seta ui_r_texturemode GL_LINEAR_MIPMAP_NEAREST

seta ui_r_detailtextures 0

Anything there give you a clue? 
 Did you install as sudo or with your user login (user login is best, and from your terminal output it would indicate a USER install, but I thought I would ask just in case)
Because if you installed as sudo then the permissions would be the problem!
 Check if the profile has been created in your home/.etwolf/etmain/profiles folder
You could try copying in your old ET profile and see if the game runs then(assuming you backed it up )

Good luck
Zimmer

---

### Post by Buddy DarDar on 2005-11-24
Well, well.

I started my computer up today, chmod'ed both ET folders to 777 for good measure, and tried to start ET.  Hey, my ATI drivers vanished!  For some reason I was back at the software rendering (MESA or whatever).  Only change I made to the system was downloading the updates.  I figured that the kernal upgrade had borked something, so I tried to re-install them.  No dice.

Oh, well.  I forced ET to use the software rendering for startup, and despite the really choppy video and sound, it DID make it past the intro screen into the profile setup screen.  Of course, I couldn't actually enter information because of the choppiness, but it did make it.

So, this narrows the problem down to 2 possiblities.  Either the ATI drivers are really buggy with R200 derivatives (which my 9200 SE apparently falls under), or it was the permissions.

Anybody having this problem still, try this from terminal.
Without the quotes, mind you:

"sudo chmod -R 777 /usr/local/games/enemy-territory"
and from your home directory...
"sudo chmod -R 777 /.etwolf"

The sudo isn't really needed for the 2nd one I think, but it can't hurt.

@Zimmer, Thanks for the help.  I can't get the ATI drivers to re-install, so I'm just doing a fresh install and I'm going to 1) install ATI drivers, 2) install ET.  The profiles folder wasn't being created along with the install.

Now, could you settle a question running around in my head?  The group that games are run as, is it actually "games" or something?  I had full ownership of both folders earlier, but no dice.  I still pretty new to linux and am still trying to figure this all out.
I'm pretty sure I did a sudo install, I'm going to finish my re-install up now, I'll let you know how it goes.

Thanks again,
Buddy DarDar.

---

### Post by Buddy DarDar on 2005-11-24
It really appears to be a driver issue.  From the post above, it succeeds in making it to the profile screen using software OpenGL (it's obviously unplayable due to frame rates).

Here's what I did:
1) Install Breezy.
2) Install ATI drivers following this procedure. 
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)
3) Install gtklib-1.2 and dependancies. (w/ Synaptic)
4) Install ET.

I had to use sudo to install ET because it couldn't write to the /usr/local/games directory.

5) chmodded both ET directories to 777 (with -R)

No go, unfortuantely.  Same exact problem.  Must be the driver.

Zimmer, what video card are you using?

Thanks.

Buddy DarDar

---

### Post by Zimmer on 2005-11-24
I am using a Radeon 9600 with 256mb
In Breezy (and in Hoary) I use the XFree drivers, I do not use the ATI drivers from the ATI website. This is the path I followed to enlightenment ;)
1. [https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)
which points you to 
2. [https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)
and asks you to verify you have a Radeon card or 9xxx series above 9500 etc.. (you say your card is a Radeon , so...)
which points you to 
3. [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
read the 4 steps very carefully, particularly about editing the xorg.conf to say 'fglrx' instead of 'ati' (easiest way to edit it is to
 sudo gedit /etc/X11/xorg.conf       )
read the bottom of the page, Troubleshooting, and 
issue the fglrxinfo command at a terminal...
..and if you are ok
..then back to 1. to follow the instructions on installing ET, reading right down to the bottom of the page before you start, else you might miss this.....

**Before you install  **    
Change the permission of the ET install filewith this command:
Assuming you have this file in your own home directory
open a terminal and..
sudo chmod +x et-linux-2.60.x86.run
this will give your user the ability to install :)
Verify that the directory that it downloads maps to is chmoded for access by your user! If you do not do this, you'll be unable to download and install the maps & other files you need to join games!

sudo chown -R user:user ~/.etwolf/

Replace user:user with your own user name & user group (usually the same name, in Ubuntu). 
I think yours would be 
sudo chown -R connell:connell /home/connell/.etwolf/
..judging by the output of your post earlier.
Keep going, you know it is worth it !!
As for which group runs the games..if installed properly any user can run a game. If a new user was to type et at the terminal he should get the profile setup routine (because the program would search for the .etwolf folder and it would not be there )and would set up a user profile in his home/hisusername/.etwolf folder with the basic maps etc.
I will test this and report back...
Regards
Zimmer

---

### Post by Buddy DarDar on 2005-11-24
Zimmer, I would kiss you if I could, and I was gay.  (I happily live in Vancouver folks, so I'm definately no homophobe.  Bartended on too many Pride cruises to bat an eye anymore :) ).

It WAS the crappy ATI drivers that were doing it.  I used apt-get to remove the xorg-whateveritis-fglrx driver from ATI, then replaced it with the one from the Breezy repositories, followed the rest of the the steps, and SUCCESS!

I now remember following those steps when using Hoary instead of the ATI driver, I wish I would have saved myself the trouble by re-checking the wiki and not doing it all by memory.  I didn't even have to re-install ET.

So, for everybody else, get rid of the Propritary ati driver (using "sudo apt-get remove xorg-driver-fglrx") and get the ones from the Ubuntu repository (using "sudo apt-get install xorg-driver-fglrx").  Make sure you have Universe enabled, or was it restricted?  Think it was restricted actually.  Solves all problems.

I was nearly about to go out and buy a copy of XP because I can't live without my ET.  You have saved the day, Zimmer.  Let me know if you come up to BC so I can buy you a beer.

Thanks again,

Buddy DarDar.

---

### Post by Sohlman on 2008-11-12
Hi
I have some sort of the same problem.
I just installed ET and want to begin playing.
but when i come to the profile screen, my computer start to slow down, to the point where it take 5 sec before the mouse moves.
When i close the game i see in console; Sys_QueEvent: overflow, all over the page.

So any help pleas, I'm caind a new to Linux - Ubuntu
*pleas say what info i need to add, for help*

---

### Post by Zimmer on 2008-11-13
What is your graphics card?

---

### Post by Sohlman on 2008-11-14
That's one of the problem, i don't know.

I have a IBM computer
35 GB hard drive
508 Mb Ram

is there any commands to see the "cards".

---

### Post by Zimmer on 2008-11-15
> **Sohlman said:**
> That's one of the problem, i don't know.

I have a IBM computer
35 GB hard drive
508 Mb Ram

is there any commands to see the "cards".

Quite possibly, but offhand I cannot tell you. Instead, view the xorg log 
via System>Administration>System log  and scroll down to look for where it probes your video card: an entry probably beginning   (--) PCI 
for example, I have an NVidia GeForce 8400M 

(--) PCI:*(1:0:0) nVidia Corporation GeForce 8400M GS

reading the xorg log for errors and warnings may also give you a clue as to what drivers are loading for your card.

---

### Post by Sohlman on 2008-11-22
i found this in that file,

[B](WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"[/B]


[B](II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)865G Graphics Controller[/B]

(II) AIGLX: Screen 0 is not DRI capable

This i think has something whit my driver...  
Edit...
found this to
[B](II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 8000 kB
(II) VESA(0): VESA VBE OEM: Intel(r)865G Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)865G Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0xb7197000,
	physical address = 0xf0000000, size = 8192000[/B]
and
[B](II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00@00:02[/B]:0

---

### Post by Zimmer on 2008-11-24
What does the  Terminal command  
glxinfo

tell you?

and which driver are you loading in your xorg.conf?

---

### Post by lakersforce on 2008-11-24
Please make sure that your gpu supports OpenGL 2.0. Cards like Intel 965G only supports OpenGL 1.5.

---

### Post by Sohlman on 2008-11-26
???????????
her is the Xorg.0.log

When i tried to open this file it didn't work, so download it first then open

---


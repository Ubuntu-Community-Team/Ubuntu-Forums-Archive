---
title: "Enemy Territory Quake Wars help needed"
date: 2008-08-28
forum: Gaming &amp; Leisure
---

### Post by gardara on 2008-08-28
I am trying to run ET:QW on my laptop but I keep getting errors...


```
--------------------------------------
----- Initializing Decls -----
Decompressing the global token cache...3566Kb
------------------------------
couldn't exec 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
couldn't exec 'etqwbinds.cfg'
couldn't exec 'autoexec.cfg'
Vendor: Device:
/proc/cpuinfo CPU frequency: 1833 MHz
parse /proc/cpuinfo for CPU information
2 logical, 1 physical CPU(s)
detecting video ram (set sys_videoRam on command line to override) ..
trying /proc/dri/0/umm
guess failed, return default low-end VRAM setting ( 128MB VRAM )
Detected
 	1 1.83 GHz CPU
	3280 MB of System memory
	128 MB of Video memory on an optimal video architecture

This system qualifies for Low quality.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1280x800
execing 'specs/minspec.dat'
execing 'specs/minspec_cpu.dat'
execing 'specs/minspec_gamedetail.dat'
execing 'specs/minspec_gpu.dat'
execing 'specs/minspec_gpudetail.dat'
execing 'specs/minspec_lighting.dat'
execing 'specs/minspec_foliage.dat'
Vendor: Device:
execing 'specs/minspec_foliage.dat'
thread priority set to 1
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
SDL_ListModes:
1280x800 1280x768 1024x768 800x600 640x480 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
vsync: SDL reports -1076966584 - broken?
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
X..GL_ARB_texture_non_power_of_two not found
...using GL_ARB_texture_compression
X..GL_EXT_texture_compression_s3tc not found
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 2.000000
X..GL_EXT_texture_lod not found
X..GL_1.4_texture_lod_bias not found
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_ARB_texture_rectangle
...using GL_EXT_texture_rectangle
...using GL_EXT_stencil_wrap
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..GL_EXT_depth_bounds_test not found
X..GL_ARB_point_sprite not found
X..GL_ARB_occlusion_query not found
X..GL_EXT_framebuffer_object not found
X..GL_EXT_packed_depth_stencil not found
...using GL_EXT_blend_minmax
...using GL_ARB_multisample
X..GL_ARB_shader_objects not found
X..GL_ARB_vertex_shader not found
X..GL_ARB_fragment_shader not found
X..GL_ARB_fragment_program_shadow not found
...using GL_ARB_shadow
...using GL_ARB_depth_texture
X..GL_EXT_gpu_program_parameters not found
0x0
[0x082e80e1]
[0x081a4a12]
[0x0810ae94]
[0x0810b81f]
[0x0819e4cc]
[0x0819eb12]
[0x0819ecee]
[0x083dc3ae]
[0xb7ba3450]
[0x0804ca41]
********************
ERROR: The current video card / driver combination does not support the necessary features: GL_ARB_occlusion_query
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
Sys_Error: Error during initialization

```

What is this *GL_ARB_occlusion_query*?
Any way I can fix it?

---

### Post by Crafty Kisses on 2008-08-28
Post the results of > glxinfo

---

### Post by gardara on 2008-08-29
> **Codename said:**
> Post the results of > glxinfo


```
name of display: :0.0
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x57 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by aoanla on 2008-08-30
> **gardara said:**
> 
What is this *GL_ARB_occlusion_query*?
Any way I can fix it?

ETQW is checking your graphics card for the features it supports. All OpenGL features start with GL. If they're an "officially supported" extension (that is, one which is standardised and implemented by all graphics cards makers in the same way), then they start with GL_ARB_ (otherwise, they start with something like GL_ATI_, if they're ATI-only, for example). GL_ARB_occulusion_query is an extension which allows applications to check if a given object is visible from the current viewpoint - if it isn't, they can avoid drawing it.

It appears that your graphics solution doesn't support this extension, which isn't surprising, given that it's the second worst Intel built-in graphics solution in existence.

---

### Post by lakersforce on 2008-08-30
If I remember correctly etqw requires a graphics card capable of OpenGL 2.0. 945G only supports OpenGL 1.5.

---

### Post by Crafty Kisses on 2008-08-30
Yep upon research I found the same thing. :(

---

### Post by richardkhe on 2008-09-08
Does this mean i can't play quake in my laptop with Intel graphics after all?! 

...

it's so sad :(

---

### Post by gardara on 2008-09-27
> **richardkhe said:**
> Does this mean i can't play quake in my laptop with Intel graphics after all?! 

...

it's so sad :(


Seems that way... Really sad yes :(

---


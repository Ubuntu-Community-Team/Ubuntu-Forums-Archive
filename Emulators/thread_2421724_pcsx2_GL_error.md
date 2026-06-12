---
title: "pcsx2 GL error"
date: 2019-06-26
forum: Emulators
---

### Post by rideordie0216 on 2019-06-26
brand new to ubuntu and trying to learn it more in depth, and wanted to get a ps2 emulator going. tried setting up pcsx2, got an error, discovered a thread giving a step by step to uninstall then reinstall micove ppa, still getting same error. here is my log, 

PCSX2 1.4.0-0- compiled on Jan  6 2016
Savestate version: 0x9a0b0000

Host Machine Init:
    Operating System =  Linux 4.15.0-52-generic x86_64
    Physical RAM     =  3745 MB
    CPU name         =  Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
    Vendor/Model     =  GenuineIntel (stepping 02)
    CPU speed        =  2.126 ghz (4 logical threads)
    x86PType         =  Standard OEM
    x86Flags         =  bfebfbff 0098e3bd
    x86EFlags        =  28100000

x86 Features Detected:
    SSE2.. SSE3.. SSSE3.. SSE4.1.. SSE4.2

Installing POSIX SIGSEGV handler...
Reserving memory for recompilers...

Loading plugins...
    Binding   GS: /usr/lib/games/PCSX2/libGSdx-1.0.0.so 
    Binding  PAD: /usr/lib/games/PCSX2/libonepad-1.1.0.so 
    Binding SPU2: /usr/lib/games/PCSX2/libspu2x-2.0.0.so 
    Binding CDVD: /usr/lib/games/PCSX2/libCDVDnull.so 
    Binding  USB: /usr/lib/games/PCSX2/libUSBnull-0.7.0.so 
    Binding   FW: /usr/lib/games/PCSX2/libFWnull-0.7.0.so 
    Binding DEV9: /usr/lib/games/PCSX2/libdev9null-0.5.0.so 
Plugins loaded successfully.

(GameDB) 9693 games on record (loaded in 305ms)
HLE Host: Will load ELF: 

HLE Notice: ELF does not have a path.


Initializing plugins...
    Init GS
    Init PAD
    Init SPU2
    Init CDVD
    Init USB
    Init FW
    Init DEV9
Plugins initialized successfully.

Opening plugins...
    Opening GS
Current Renderer: OpenGL (Hardware mode)
Failed to create the opengl context. Check your drivers support openGL 3.3. Hint: opensource drivers don't
GSopen Failed: return code: 0xffffffff
Closing plugins...
    Closing GS
Plugins closed successfully.
Shutting down plugins...
    Shutdown DEV9
    Shutdown FW
    Shutdown USB
    Shutdown CDVD
    Shutdown SPU2
    Shutdown PAD
    Shutdown GS
Plugins shutdown successfully.
(p) GS plugin failed to open!(thread:MTGS)(thread:EE Core)
User-canceled plugin configuration after plugin initialization failure.  Plugins unloaded.

---

### Post by deadflowr on 2019-06-26
It's seems it's indeterminate what the gpu gl version is
As this is an older i3 cpu it's probably a lower version such as 3.0 (or even less)
You can find out with
```
inxi -G
```
inxi should be installed, if not you can install it.
You can also get more verbose output for the card by install the package mesa-utils and running
```
glxinfo
or
glxinfo | grep OpenGL
```

---

### Post by rideordie0216 on 2019-06-26
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 18.0.5
OpenGL shading language version string: 1.20
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 18.0.5
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:


these are the results of 
glxinfo | grep OpenGL

---

### Post by deadflowr on 2019-06-26
> Failed to create the opengl context. Check your drivers support openGL 3.3. Hint: opensource drivers don't
> OpenGL version string: 2.1 Mesa 18.0.5

:sad:

Unfortunately, no known way to update the drivers to 3.0+:
[https://askubuntu.com/questions/703761/how-do-i-upgrade-opengl-intel]("https://askubuntu.com/questions/703761/how-do-i-upgrade-opengl-intel")

---

### Post by rideordie0216 on 2019-06-26
```
Graphics:  Card: Intel Core Processor Integrated Graphics Controller
           Display Server: X.Org 1.19.6 drivers: (unloaded: fbdev,vesa)
           Resolution: 1366x768@59.64hz
           GLX Renderer: Mesa DRI Intel Ironlake Mobile
           GLX Version: 2.1 Mesa 18.0.5
```


results from inxi. the third is very long so bear with me on that a moment please

```
james@james-HP-Pavilion-dv6-Notebook-PC:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_libglvnd, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_INTEL_swap_event, 
    GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_context_flush_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_create_context_robustness, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_buffer_age, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_buffer_age, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Intel Open Source Technology Center (0x8086)
    Device: Mesa DRI Intel(R) Ironlake Mobile  (0x46)
    Version: 18.0.5
    Accelerated: yes
    Video memory: 1536MB
    Unified memory: yes
    Preferred profile: compat (0x2)
    Max core profile version: 0.0
    Max compat profile version: 2.1
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 2.0
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 18.0.5
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_3DFX_texture_compression_FXT1, GL_AMD_seamless_cubemap_per_texture, 
    GL_AMD_shader_trinary_minmax, GL_ANGLE_texture_compression_dxt3, 
    GL_ANGLE_texture_compression_dxt5, GL_APPLE_object_purgeable, 
    GL_APPLE_packed_pixels, GL_ARB_ES2_compatibility, GL_ARB_arrays_of_arrays, 
    GL_ARB_buffer_storage, GL_ARB_clear_buffer_object, GL_ARB_clear_texture, 
    GL_ARB_clip_control, GL_ARB_color_buffer_float, 
    GL_ARB_compressed_texture_pixel_storage, GL_ARB_copy_buffer, 
    GL_ARB_copy_image, GL_ARB_debug_output, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_get_program_binary, GL_ARB_get_texture_sub_image, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_internalformat_query2, GL_ARB_invalidate_subdata, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multi_bind, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_polygon_offset_clamp, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_robustness, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_seamless_cubemap_per_texture, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_draw_parameters, 
    GL_ARB_shader_group_vote, GL_ARB_shader_objects, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_barrier, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_filter_anisotropic, 
    GL_ARB_texture_float, GL_ARB_texture_mirror_clamp_to_edge, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_lod, GL_ARB_texture_rectangle, GL_ARB_texture_rg, 
    GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_storage, GL_ARB_texture_swizzle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_polygon_offset_clamp, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_array, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_IBM_multimode_draw_arrays, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_KHR_blend_equation_advanced, 
    GL_KHR_context_flush_control, GL_KHR_debug, GL_KHR_no_error, 
    GL_KHR_robustness, GL_MESA_pack_invert, GL_MESA_texture_signed_rgba, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_conditional_render, 
    GL_NV_depth_clamp, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_primitive_restart, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, GL_OES_EGL_image, 
    GL_OES_read_format, GL_S3_s3tc, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

OpenGL ES profile version string: OpenGL ES 2.0 Mesa 18.0.5
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_APPLE_texture_max_level, GL_EXT_blend_minmax, 
    GL_EXT_compressed_ETC1_RGB8_sub_texture, GL_EXT_discard_framebuffer, 
    GL_EXT_draw_buffers, GL_EXT_draw_elements_base_vertex, GL_EXT_frag_depth, 
    GL_EXT_map_buffer_range, GL_EXT_multi_draw_arrays, 
    GL_EXT_occlusion_query_boolean, GL_EXT_polygon_offset_clamp, 
    GL_EXT_read_format_bgra, GL_EXT_robustness, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_border_clamp, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_format_BGRA8888, GL_EXT_texture_rg, 
    GL_EXT_texture_type_2_10_10_10_REV, GL_EXT_unpack_subimage, 
    GL_KHR_blend_equation_advanced, GL_KHR_context_flush_control, 
    GL_KHR_debug, GL_KHR_no_error, GL_KHR_robustness, GL_NV_draw_buffers, 
    GL_NV_fbo_color_attachments, GL_NV_read_buffer, GL_NV_read_depth, 
    GL_NV_read_depth_stencil, GL_NV_read_stencil, GL_OES_EGL_image, 
    GL_OES_EGL_image_external, GL_OES_EGL_sync, 
    GL_OES_compressed_ETC1_RGB8_texture, GL_OES_depth24, GL_OES_depth_texture, 
    GL_OES_draw_elements_base_vertex, GL_OES_element_index_uint, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
    GL_OES_packed_depth_stencil, GL_OES_required_internalformat, 
    GL_OES_rgb8_rgba8, GL_OES_standard_derivatives, GL_OES_stencil8, 
    GL_OES_surfaceless_context, GL_OES_texture_3D, 
    GL_OES_texture_border_clamp, GL_OES_texture_float, 
    GL_OES_texture_float_linear, GL_OES_texture_half_float, 
    GL_OES_texture_half_float_linear, GL_OES_texture_npot, 
    GL_OES_vertex_array_object, GL_OES_vertex_half_float

46 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0d6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0d9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0da 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0db 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0dc 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0dd 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0de 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0df 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0e0 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0e1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0e2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0e4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0e5 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0e6 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x0e7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0e8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0e9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ea 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0eb 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ec 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ed 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ee 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0ef 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0f0 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0f1 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0f2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0f3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0f4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f6 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0f7 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x09b 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0f8 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f9 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0fa 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0fb 32 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0fc 32 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0fd 32 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0fe 32 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0ff 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x100 32 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None

58 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x09c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09d  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x09f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0a0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0a9 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0aa 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0ab 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0ac  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0ad  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0ae 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0af 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0b0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b2 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0b3 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x0b4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0b5  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0b6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0b7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0b8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ba 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0bb 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0bc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0be 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0bf 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c0 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0c1 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0c2 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0c3 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0c4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0c5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0c6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0c8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ca 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0cb 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x0cc 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0cd 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ce 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0cf 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0d0 32 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0d1 32 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0d2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0d3 32 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0d4 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0d5 32 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
```

---

### Post by rideordie0216 on 2019-06-27
The emulator for ps1 when trying to boot a game just force closes no matter what game too. Only game i have been able to run is runescape so far. Trying to get some racing and or shooting games i can run on it. I have a usb ps style controller so i figured a emulator for one of them would be great.

---

### Post by deadflowr on 2019-06-28
There's a runescape playstation one game?

In terms of ps1 emulators issues if running pcsx(or pcsxr) it might be a configuration issue.
See: [https://ubuntuforums.org/showthread.php?t=2314767&p=13445427#post13445427]("https://ubuntuforums.org/showthread.php?t=2314767&p=13445427#post13445427")

---


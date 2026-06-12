---
title: "Metal Blob Solid very slow ?"
date: 2005-01-16
forum: Gaming &amp; Leisure
---

### Post by HorstJENS on 2005-01-16
Hi,
i loved to play the game Metal Blob Solid on my Debian install. Since i have Ubuntu, the game is playable, but extremly slow. (It's the same Computer, 2.Ghz AMD, warty) . Did i have to install Metal Blob Solid from a special source to get it running at "normal" speed ?

---

### Post by ante0 on 2005-01-20
does other games run fast? try typing glxgears in a terminal. does the gears run really fast (over 700 frames per 5 secons) or under? type glxinfo after that and post the output. I had some problems with my graphic card before, but when I installed ubuntu it was solved.

---

### Post by HorstJENS on 2005-01-21
gxlgears shows over 11.000 frames per 5.seconds

my glxinfo:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5700/PCI/SSE/3DNOW!
OpenGL version string: 1.5.1 NVIDIA 61.11
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr,
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side,
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_HP_occlusion_test, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence,
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program,
    GL_NV_fragment_program_option, GL_NV_half_float, GL_NV_light_max_exponent,
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query,
    GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, GL_NV_point_sprite,
    GL_NV_primitive_restart, GL_NV_register_combiners,
    GL_NV_register_combiners2, GL_NV_texgen_reflection,
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4,
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle,
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3,
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2,
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  0 16  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  0 16  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  y  .  8  8  8  0  0  0  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  0  0  0  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  2 1 Ncon
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  2 1 Ncon
0x30 24 tc  0 32  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  4 1 Ncon
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  4 1 Ncon
0x32 24 tc  0 32  0 r  y  .  8  8  8  0  0 16  0 16 16 16 16  2 1 Ncon
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  0  0 16  0 16 16 16 16  4 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  4 1 Ncon
0x36 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x39 24 dc  0 32  0 r  y  .  8  8  8  0  0 16  0 16 16 16 16  0 0 None
0x3a 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 None
0x3b 24 dc  0 32  0 r  .  .  8  8  8  0  0 16  0 16 16 16 16  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 None
0x3d 24 dc  0 32  0 r  y  .  8  8  8  0  0  0  0 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  .  .  8  8  8  0  0  0  0 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  2 1 Ncon
0x42 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  2 1 Ncon
0x43 24 dc  0 32  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  4 1 Ncon
0x44 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  4 1 Ncon
0x45 24 dc  0 32  0 r  y  .  8  8  8  0  0 16  0 16 16 16 16  2 1 Ncon
0x46 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  2 1 Ncon
0x47 24 dc  0 32  0 r  y  .  8  8  8  0  0 16  0 16 16 16 16  4 1 Ncon
0x48 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  4 1 Ncon

---

### Post by fng on 2005-01-24
i just compiled it from source.
I think it runs pretty fine here. I don't see any slowdowns

---

### Post by Dylanby on 2005-01-24
Your fps for glxgears should be much higher.
I think your video card drivers aren't setup properly.

---

### Post by leech on 2005-01-24
Actually, I think that's supposed to read 11,000, which is right.  His rendering is set up right.  Otherwise glxinfo will be a lot shorter of a list and will have inderect rendering in there.

Leech

---

### Post by ante0 on 2005-05-13
yeah, 11.000 is good enough to run the game fast. maybe you should update your drivers for the graphcard...
Now i see this post is old, so this msg probably doesnt matter anymore.
Oh well..

---

### Post by foogoo on 2009-06-14
Sorry for resurrecting such an old thread, but I've scoured Google and the forums for this problem to no avail.

I am having the exact same problem as the OP - Metal Blob Solid runs very slow, almost like it's slow motion. I don't have any problems with any other games or programs.

my glxgears:
> 
3184 frames in 5.0 seconds = 636.713 FPS
3068 frames in 5.0 seconds = 613.541 FPS
3380 frames in 5.0 seconds = 675.875 FPS
3353 frames in 5.0 seconds = 670.526 FPS


glxinfo:
> 
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
OpenGL version string: 2.0 Mesa 7.4
OpenGL shading language version string: 1.10
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_separate_stencil, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays

36 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8a 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x8b 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x8c 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x8d 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x8e 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x8f 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x90 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x91 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x92 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x93 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x94 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x95 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x96 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x97 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x98 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x99 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x9a 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x9b 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x9c 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x9d 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x9e 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x9f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xa0 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xa1 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xa2 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xa3 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xa4 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xa5 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xa6 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xa7 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xa8 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xa9 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xaa 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x65 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

36 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x66  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x67  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x68  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x69  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6a  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6b  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6d  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x70  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x71  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x72  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x73  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x74  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x75  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x76  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x77  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x78  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x79  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x7a  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x7b  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x7c  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x7d  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x7e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7f  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x80  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x81  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x82  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x83  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x84  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x85  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x86  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x87  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x88  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x89  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow


Thanks.

---

### Post by SerenityKill3r on 2009-06-14
> **foogoo said:**
> Sorry for resurrecting such an old thread, but I've scoured Google and the forums for this problem to no avail.

I am having the exact same problem as the OP - Metal Blob Solid runs very slow, almost like it's slow motion. I don't have any problems with any other games or programs.

my glxgears:


glxinfo:


Thanks.

You would be better off starting a new thread as ressurecting old threads is frowned upon :(

---


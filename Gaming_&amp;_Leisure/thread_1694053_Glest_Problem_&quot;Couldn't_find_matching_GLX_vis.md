---
title: "Glest Problem &quot;Couldn't find matching GLX visual&quot;"
date: 2011-02-23
forum: Gaming &amp; Leisure
---

### Post by mattylaws on 2011-02-23
Hi there

Looked around and really couldn't find anything specific to Glest that has the same problem as I've encountered.

Anyway, I can run glest under VGA, with bit and colour depth at 16, but when I tried to raise both it failed with the following error:

```
Exception: Couldn't set video mode 800x600 (32bpp 0 stencil 32 depth-buffer). SDL Error is: Couldn't find matching GLX visual
```

I have latest nvidia driver installed, and glxgears works fine, here's the output of glxinfo:

```
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 
    GLX_NV_video_capture, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6150SE nForce 430/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 260.19.06
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_copy_buffer, GL_ARB_depth_clamp, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_ES2_compatibility, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_imaging, GL_ARB_map_buffer_range, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_provoking_vertex, 
    GL_ARB_sampler_objects, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_texture_swizzle, GL_ARB_timer_query, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, 
    GL_EXT_direct_state_access, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_shader_objects, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_texture_swizzle, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color, 
    GL_NV_depth_clamp, GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_half_float, GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

120 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x028 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x029 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x030 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x031 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x033 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x034 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x035 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x036 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x037 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x039 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x03b 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x03c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x03d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x03e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x03f 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x040 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x041 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x043 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x044 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x045 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x046 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x047 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x049 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x04c 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x04d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x04e 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x04f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x051 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x052 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x055 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x056 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x058 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x059 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x05a 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x05c 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x05d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x05e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x05f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x060 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x061 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x062 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x064 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x065 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x066 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x067 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x068 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x069 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x06a 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x06c 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x06e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x06f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x070 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x071 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x023 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x072 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x073 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x074 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x075 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x076 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x077 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x078 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x079 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x07a 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x07b 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x07c 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x07d 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x07e 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x07f 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x080 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x081 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x082 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x083 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x084 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x085 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x086 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x087 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x088 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x089 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x08a 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x08b 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x08c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x08d 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x08e 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x08f 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x090 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x091 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x092 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x093 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x094 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x095 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x096 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x097 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x098 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon

179 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x099 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x09a 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x09b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x09c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x09d 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x09e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x09f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0a0 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0a1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0a2 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0a5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0a6 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0a7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0a8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0a9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0aa 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0ab 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0ad 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0ae 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0af 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0b0 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0b1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0b2 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0b3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0b4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0b5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0b6 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0b7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0b8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0b9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0ba 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0bb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0bc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0bd 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0be 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0bf 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c1 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0c2 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0c3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0c4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0c5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c6 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0c9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0ca 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0cb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0cc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0cd 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0ce 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0cf 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0d0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0d1 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0d2 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0d3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0d4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0d5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0d6 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0d7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0d8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0d9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0da 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0db 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0dc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0dd 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0de 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0df 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0e0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0e1 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0e2 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0e3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0e4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0e5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0e6 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0e7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0e8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0e9 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0ea 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0eb 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0ec 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0ed 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0ee 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0ef 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0f0 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0f1 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0f2 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0f3 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0f4 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0f5 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0f6 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0f7 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0f8 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0f9 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0fa 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0fb 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0fc 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0fd 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0fe 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0ff 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x100 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x101 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x102 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x103 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x104 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x105 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x106 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x107 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x108 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x109 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x10a 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x10b 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x10c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x10d 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x10e 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x10f 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x110 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x111  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x112  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x113  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x114  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x115  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x116  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x117  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x118  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x119  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 16  0 16 16 16 16  0 0 None
0x11a  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  0 16 16 16 16  0 0 None
0x11b  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  8 16 16 16 16  0 0 None
0x11c  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x11d  0 sg  0  32  0    . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x11e  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x11f  0 sg  0  32  0    y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x120  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x121  0 sg  0  32  0    . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x122  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x123  0 sg  0  32  0    y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x124  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x125  0 sg  0  64  0    . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x126  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x127  0 sg  0  64  0    y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x128  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x129  0 sg  0 128  0    . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x12a  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x12b  0 sg  0 128  0    y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x12c  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x12d  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x12e  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x12f  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x130  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x131  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x132  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x133  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x134  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x135  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x136  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x137  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x138  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x139  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x13a  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x13b  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x13c  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x13d  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x13e  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x13f  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x140  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x141  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x142  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x143  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x144  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x145  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x146  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x147  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x148  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x149  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x14a  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x14b  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
```

Thanks for any help

---

### Post by oldrocker99 on 2011-02-23
As I understand it, Glest development is at a standstill, and its replacement MegaGlest is on PlayDeb.

---

### Post by disturbedite on 2011-02-24
everyone interested in *glest* should give MG (MegaGlest) a try. it rocks!

---

### Post by mattylaws on 2011-03-01
Ah thanks guys, I'll check it out

---


---
title: "Graphic card"
date: 2010-08-16
forum: Gaming &amp; Leisure
---

### Post by Zirts on 2010-08-16
Hi,

Today I installed Max Payne on my PC and it's working just brilliant even on max graphics.

I have a ATI radeon 9550 and a AMD 1.8Ghz, 1GB ram

Now when that game runs so good, how is it possible that when I try to play a game called runescape, the perfromance changes drasticly, I cant even switch the graphics option from safe mofe to OpenGL there.

Zirts

---

### Post by Zirts on 2010-08-17
Bump

---

### Post by efikkan on 2010-08-17
Wich graphics card drivers do you use?

Type "glxinfo" in terminal and show us the output.

---

### Post by Zirts on 2010-08-18
```
kaspar@kaspar-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group
client glx vendor string: Mesa Project and SGI
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
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV350 4153) 20090101 x86/MMX+/3DNow!+/SSE2 TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:
    GL_EXT_compiled_vertex_array, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_env_add, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_provoking_vertex, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_MESAX_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_object, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays, 
    GL_S3_s3tc

64 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc8 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc9 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xca 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xcb 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xcc 24 tc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xcd 24 tc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xce 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xcf 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xd0 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xd1 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xd2 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xd3 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xd4 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd5 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd6 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd7 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd8 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xd9 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xda 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xdb 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xdc 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xdd 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xde 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xdf 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xe0 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xe1 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xe2 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xe3 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xe4 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xe5 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xe6 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xe7 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xe8 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xe9 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xea 24 dc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xeb 24 dc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xec 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xed 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xee 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xef 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xf0 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xf1 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xf2 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xf3 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xf4 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xf5 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xf6 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf7 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf8 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf9 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xfa 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xfb 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xfc 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xfd 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xfe 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xff 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x100 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x101 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x102 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x103 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x104 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x67 32 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None

96 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x68  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x69  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x6a  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x6b  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x6c  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x6d  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x6e  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x6f  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x70  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0x71  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0x72  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0x73  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0x74  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0x75  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0x76  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0x77  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0x78  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x79  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x7a  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x7b  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x7c  0 tc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x7d  0 tc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x7e  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x7f  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x80  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x81  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x82  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x83  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x84  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x85  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x86  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x87  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x88  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x89  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x8a  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x8b  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x8c  0 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x8d  0 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x8e  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x8f  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x90  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x91  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x92  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x93  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x94  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x95  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x96  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x97  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x98  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x99  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x9a  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x9b  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x9c  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x9d  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x9e  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x9f  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0xa0  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0xa1  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0xa2  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0xa3  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0xa4  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0xa5  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0xa6  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0xa7  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0xa8  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xa9  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xaa  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xab  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xac  0 dc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xad  0 dc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xae  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xaf  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xb0  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xb1  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xb2  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xb3  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xb4  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xb5  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xb6  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xb7  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xb8  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xb9  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xba  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xbb  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xbc  0 dc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xbd  0 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xbe  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xbf  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xc0  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xc1  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xc2  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xc3  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xc4  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc5  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xc6  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc7  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
```

---

### Post by ronnielsen1 on 2010-08-18
Runescape runs on flash. Try this in a terminal and then reopen firefox and try to play runescape

```
sudo apt-get install sun-java6-plugin ; sudo update-java-alternatives -s java-6-sun
```

---

### Post by dfreer on 2010-08-18
> **ronnielsen1 said:**
> Runescape runs on flash. Try this in a terminal and then reopen firefox and try to play runescape

```
sudo apt-get install sun-java6-plugin ; sudo update-java-alternatives -s java-6-sun
```

Indeed. It really has very little to do with your video card, and has a lot more to do with the slow speed of your processor and/or the speed of your browser and/or flash/java plugin. Whew.

Runescape depends almost solely on your CPU. Whereas Max Payne uses the graphics card to do most of the rendering.

---

### Post by WhatAreHackers on 2010-08-18
> **dfreer said:**
> Indeed. It really has very little to do with your video card, and has a lot more to do with the slow speed of your processor and/or the speed of your browser and/or flash/java plugin. Whew.

Runescape depends almost solely on your CPU. Whereas Max Payne uses the graphics card to do most of the rendering.

 I feel somewhat insulted by your comment =(... I have a decent computer which is almost a year old... running Ubuntu 10.04, installed regular jdk, formated... sun java... then sun java from repositories then... restricted-extras... -.- ... i use mozilla firefox... not that it matter much... runescape doesn't use flash plugins, it uses java, best i couldve gotten was standard -.- ... i think the adverts uses flash, but i wouldn't know, because i use adblock plus and no script

---

### Post by Zirts on 2010-08-19
Well, if I use the option Use max CPU then yes my CPU will go to 100% fom like 70% but there is no difference in the speed of game.

I use Google Chrome as my browser wich should give the fastest experience of RS playing. This must be the fault of the Linux Java, as I installed a win 95 just to test RS out and wow I was able to run it on full HD, everything maxed and CPU still had like 20% to go till 100%.

No point to tell me now that "Lolz go to windows" too then, as I allready chose to delete my windows XP long ago and now I'm gonna stay on Linux no matter what.

---

### Post by WhatAreHackers on 2010-08-19
> **Zirts said:**
> Well, if I use the option Use max CPU then yes my CPU will go to 100% fom like 70% but there is no difference in the speed of game.

I use Google Chrome as my browser wich should give the fastest experience of RS playing. This must be the fault of the Linux Java, as I installed a win 95 just to test RS out and wow I was able to run it on full HD, everything maxed and CPU still had like 20% to go till 100%.

No point to tell me now that &quot;Lolz go to windows&quot; too then, as I allready chose to delete my windows XP long ago and now I'm gonna stay on Linux no matter what.

 amen to that, i also deleted windows XP lulz :P

---

### Post by dfreer on 2010-08-20
> **WhatAreHackers said:**
> I feel somewhat insulted by your comment =(... I have a decent computer which is almost a year old... running Ubuntu 10.04, installed regular jdk, formated... sun java... then sun java from repositories then... restricted-extras... -.- ... i use mozilla firefox... not that it matter much... runescape doesn't use flash plugins, it uses java, best i couldve gotten was standard -.- ... i think the adverts uses flash, but i wouldn't know, because i use adblock plus and no script

Don't know why you feel insulted considering I was talking to the original poster (Zirts) and not you. From what he's told us, it sounds like he's running on a machine thats approximately 5+ years old, which is probably why runescape is running slow for him. 

And as for using java, I loaded it up and thought it did, but the poster above me said it used flash so I assumed it does (I've never played the game). Either way, both technologies tend to consume a lot of CPU, and are unable to utilize the faster GPU of the graphics card (well at least flash is working on that).

In the future, try not to be offended by little things that have nothing to do with you in the first place.

> **Zirts said:**
> I use Google Chrome as my browser wich should give the fastest experience of RS playing. This must be the fault of the Linux Java, as I installed a win 95 just to test RS out and wow I was able to run it on full HD, everything maxed and CPU still had like 20% to go till 100%.

I would not be surprised that Linux Java does not perform as fast as in Windows. Same with Chrome or Firefox. But if you don't wish to switch to windows just to play Runescape I don't blame you.

Also, did you check your memory usage? You said you only had 1 GB and that might also be a contributing factor. Last I heard Chrome was the fastest, but I've heard a lot of good things about Opera as well.

---

### Post by Zirts on 2010-08-20
CPU is on a constant 100% with Java and Flash apps, only some youtube videos that use just one picture through the whole video take lik 80% or so.

RAM used is about 38,7% of 1024MB of RAM.

I have tryed using different Javas too, I mean the JDK and the sun-java6, but both give same results.

---

### Post by del_diablo on 2010-08-21
Flash got no GPU acceleration, or proper optimization of any kind of Linux.
And Compiz might be a partial hazzle.

---

### Post by Kir_B on 2010-08-25
If compiz is eating too much of your cpu, or perhaps just not playing nice with your browser etc, turn off compiz.

Just the other day, I stumbled accross the "[compiz-switch]("http://forlong.blogage.de/entries/pages/Compiz-Switch")" instructions on forlong's blog and it seems to be quite helpful in easing up some of the pressure on my cpu. Sometimes my processor activity will drop 15% - 20%. (I'm only running an amd4000+ with 1 measly gig of ram.)

Just folow the instructions for your OS/disto and afterwards you can find it in your accessories. Just left click it to turn compiz off or on, depending on it's current state of course. (I dragged it up to a drawer on my gnome panel and dropped it in there for quick and easy access.)

**I love it**, and you may very well find it helpful too.

I hope that helps. Kirby :D

Note: There is a thread here on Ubuntu forums, but it's a [read only archive]("http://ubuntuforums.org/showthread.php?t=662926&highlight=Compiz-Switch") that's quite out of date, so the instructions for lucid must be obtained from [Forlong's blog]("http://forlong.blogage.de/entries/pages/Compiz-Switch").

---


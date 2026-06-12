---
title: "3D Acceleration"
date: 2010-06-10
forum: Gaming &amp; Leisure
---

### Post by BeWop on 2010-06-10
I'm assuming this goes here, considering I need to get this working to play Knights of the Old Republic... Anyway-

Basically, I don't have 3D Acceleration turned on when I know my card can support it, which is causing all my polygons to have no textures in knights of the old republic and various other problems. I was brought aware of this after installing "PlayOnLinux" and it informed me that I didn't have it enabled...
Sidenote: KOTOR runs fine with Win7. 

Anyway, basic question: How do I turn that on/get that going?

Specs:
Acer Aspire One 532h-2527
Intel N450 1.66 ghz (PineTrail)
Intel GMA 3150
1 GB Ram
Ubuntu Netbook Remix 10.04

---

### Post by formaldehyde_spoon on 2010-06-11
You can type 
sudo apt-get install mesa-utils
glxinfo
to check whether you are using hardware or software rendering.

 If hardware rendering isn't turned on you could try going to System > Administration > Hardrware Drivers.  When I did that I was prompted to automatically install the drivers for my GOU.

---

### Post by del_diablo on 2010-06-11
> Intel GMA 3150

There is your problem.......

---

### Post by BeWop on 2010-06-11
> **formaldehyde_spoon said:**
> You can type 
sudo apt-get install mesa-utils
glxinfo
to check whether you are using hardware or software rendering.

 If hardware rendering isn't turned on you could try going to System > Administration > Hardrware Drivers.  When I did that I was prompted to automatically install the drivers for my GOU.

I get this output when typing glxinfo:
bradyn@ubuntu:~$ glxinfo
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
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) IGD GEM 20091221 2009Q4 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.7.1
OpenGL extensions:
    GL_EXT_compiled_vertex_array, GL_EXT_texture_env_add, GL_ARB_copy_buffer, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_fragment_program, 
    GL_ARB_half_float_pixel, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_provoking_vertex, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_120, GL_ARB_shadow, 
    GL_ARB_sync, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_cull_vertex, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_object, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_separate_stencil, GL_IBM_multimode_draw_arrays, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

72 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc5 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc6 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc7 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc8 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc9 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xca 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xcb 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xcc 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xcd 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xce 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xcf 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xd0 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xd1 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd2 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd3 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd4 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd5 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd6 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd7 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xd8 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xd9 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xda 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xdb 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xdc 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xdd 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xde 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xdf 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xe0 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xe1 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xe2 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xe3 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xe4 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xe5 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xe6 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xe7 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xe8 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xe9 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xea 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xeb 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xec 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xed 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xee 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xef 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xf0 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xf1 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xf2 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xf3 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xf4 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xf5 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xf6 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xf7 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xf8 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xf9 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xfa 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xfb 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xfc 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xfd 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xfe 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xff 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x100 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x101 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x102 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x103 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x104 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x105 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x106 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x107 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x108 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x109 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x64 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

96 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x65  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x66  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x67  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x68  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x69  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x6a  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x6b  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x6c  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x6d  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x6e  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x6f  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x70  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x71  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x72  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x73  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x74  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x75  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x76  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x77  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x78  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x79  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x7a  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x7b  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x7c  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x7d  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x7e  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x7f  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x80  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x81  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x82  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x83  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x84  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x85  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x86  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x87  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x88  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x89  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x8b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8c  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x8d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x8f  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x90  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x91  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x92  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x93  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x94  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x95  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x96  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x97  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x98  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x99  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x9a  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x9b  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x9c  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x9d  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x9e  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x9f  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0xa0  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0xa1  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xa2  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xa3  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xa4  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xa5  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xa6  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xa7  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xa8  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xa9  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xaa  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xab  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xac  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xad  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xae  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xaf  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xb0  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xb1  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xb2  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xb3  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xb4  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xb5  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xb6  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xb7  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xb8  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xb9  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xba  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xbb  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xbc  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xbd  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xbe  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xbf  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc0  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xc1  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc2  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xc3  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc4  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

So I don't know if I'm getting hardware or software.
It isn't under hardware drivers, unfortunately.

Also:
I have read that Intel GMA 3150 drivers are available for linux, though I haven't been able to install it, I have read that it should soon be integrated (Current stable version is like 9.10 or something, and 10 is the one that supports it.)
It's out, but I don't know how to install it. [http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html)

Any help, if that'll fix the problem? =P

---

### Post by glaze on 2010-06-11
> **BeWop said:**
> 
So I don't know if I'm getting hardware or software.
It isn't under hardware drivers, unfortunately.

You are getting hardware acceleration (Direct Rendering: Yes), but I've heard that Intel & WINE don't always work fine together.
> 
Also:
I have read that Intel GMA 3150 drivers are available for linux, though I haven't been able to install it, I have read that it should soon be integrated (Current stable version is like 9.10 or something, and 10 is the one that supports it.)
It's out, but I don't know how to install it. [http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html)


All of that stuff is already included in Ubuntu, but Ubuntu packages's version numbers are older. It's not easy to install newer versions manually (though some of them have PPAs), so your best bet is to wait to October for Ubuntu 10.10.

---

### Post by BeWop on 2010-06-11
Awesome, thanks for the info.

---

### Post by dfreer on 2010-06-11
> **BeWop said:**
> I get this output when typing glxinfo:
bradyn@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: Yes**
server glx vendor string: SGI
server glx version string: 1.2

That means it's hardware accelerated already. As much as Intel intergrated graphics can accelerate things anyways...

> **del_diablo said:**
> [QUOTE=BeWop;9446449]Intel GMA 3150There is your problem.......[/QUOTE]

+1. Can you even play KOTR in windows on this machine?

EDIT: I posted too slow.

---

### Post by BeWop on 2010-06-11
> **dfreer said:**
> 

+1. Can you even play KOTR in windows on this machine?

EDIT: I posted too slow.

Yes, KOTOR runs fine in windows.

I'll just do a separate 20 gb windows partition solely for KOTOR :KS

---


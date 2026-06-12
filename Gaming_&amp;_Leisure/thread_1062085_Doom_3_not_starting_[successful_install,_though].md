---
title: "Doom 3 not starting [successful install, though]"
date: 2009-02-06
forum: Gaming &amp; Leisure
---

### Post by UbntuJavaTrtlesClssDiagrm on 2009-02-06
Hello, :)

quick question about running Doom 3 on Intrepid Ibex. I've installed with the run file from id and installed all the files from the three disks.

When I type doom3 in the terminal:

signal caught: Illegal instruction
si_code 2
Trying to exit gracefully..


Here is some of my system information:

lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AR [Radeon 9600] [1002:4152]


glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project


glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2
OpenGL shading language version string: 1.10
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
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
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, 
    GL_ATI_separate_stencil, GL_IBM_multimode_draw_arrays, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_program_debug, 
    GL_MESA_resize_buffers, GL_MESA_texture_array, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_fragment_program, 
    GL_NV_light_max_exponent, GL_NV_point_sprite, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x70 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

32 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x71  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x72  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x73  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x74  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x75  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x76  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x77  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x78  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x79  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x7a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x7b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x7c  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x7d  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x80  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x81  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x82  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x83  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x84  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x85  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x86  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x87  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x88  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x89  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8a  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x8b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8c  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x8d  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x90  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow


Thanks in advance!!!
=)
Michael

---

### Post by Melcar on 2009-02-06
It seems that you're running the open source drivers, which lack proper opengl2.1 hardware acceleration.  Maybe that's the problem.

---

### Post by UbntuJavaTrtlesClssDiagrm on 2009-02-06
Well, I just activated the proprietary driver--which I've read has conflicted with x-org, so still I can't get Doom 3 to start.

  Any suggestions?  #-o

---

### Post by UbntuJavaTrtlesClssDiagrm on 2009-02-07
Maybe there are some tweaks I can pull off, because I shouldn't have to run Doom 3 in WINE.  Let me know if you need anymore system specs.](*,)

THanks in advance,

Mike

---

### Post by UbntuJavaTrtlesClssDiagrm on 2009-02-07
With the proprietary driver, notice the vendor string is no longer Mesa.

glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: ***ATI Technologies Inc***.

---

### Post by MaxIBoy on 2009-02-07
If you have an ATI card, the instructions for the best way to install the proprietary drivers can be found on [www.cchtml.com](www.cchtml.com). Look up your distro, follow the instructions, and you should be good.

---

### Post by UbntuJavaTrtlesClssDiagrm on 2009-02-09
Well, I mean maybe I have to modify something else here...not necessarily graphical--I'm having no trouble with any other games and Compiz is doing a great job!!! =)  Hmmm, I'm stumped   :-s

---


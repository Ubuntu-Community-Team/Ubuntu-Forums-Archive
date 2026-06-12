---
title: "Triple head with ATI FirePro 2260s xorg issues"
date: 2009-07-15
forum: Desktop Environments
---

### Post by pe_ell on 2009-07-15
So this has been driving me nuts.  The closest I've gotten to having the triple head work correctly (other than Windows which seems to work regardless of card combination) is with two Nvidia cards where I had one X session that spanned the two left monitors and one X session on the right monitor.  While looking rather lame (multiple mice and occasional freakouts over which desktop the mouse should be on) it basically worked.

In an effort to try to get triple head working with one desktop and maybe even compiz I swapped out the cards to ATI 2260s (identical cards, one PCI-E and other PCI in my Dell Optiplex).  I've tried many Xorg confs.  Closest thing I've got to three functional monitors is the third screen will turn on for the screensaver.  Generally the first two monitors run in clone which is annoying to say the least.  Three monitors and one functional workspace.

I'm also using the opensource drivers for now as the proprietary ones seem to make things worse as far as I can tell.  And so far any time I've turned on Xinerama it's resulted in X hanging on restart.

With the current files I have one desktop that's two monitors wide, but you can only see the left side since the video output is being cloned on the first card.  So I see the left side of the desktop on both monitors while the right side of the desktop is off in limbo.

Since people will ask, I'll see about spitting out as much details as I can.

Output from lspci:
```
user@host:~$ lspci | grep FirePro
01:00.0 VGA compatible controller: ATI Technologies Inc RV620 [FirePro 2260]
04:00.0 VGA compatible controller: ATI Technologies Inc RV620 [FirePro 2260]

```Output from glxinfo:
```
user@host:~$ glxinfo 
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
OpenGL version string: 2.1 Mesa 7.4
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_120, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
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
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_program_debug, GL_MESA_resize_buffers, 
    GL_MESA_texture_array, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_fragment_program, GL_NV_light_max_exponent, 
    GL_NV_point_sprite, GL_NV_texture_rectangle, GL_NV_texgen_reflection, 
    GL_NV_vertex_program, GL_NV_vertex_program1_1, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGI_texture_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

64 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xcc 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xcd 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xce 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xcf 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xd0 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xd1 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xd2 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xd3 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xd4 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xd5 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xd6 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xd7 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xd8 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd9 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xda 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xdb 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xdc 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xdd 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xde 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xdf 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xe0 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xe1 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xe2 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xe3 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xe4 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xe5 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xe6 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xe7 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xe8 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xe9 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xea 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xeb 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xec 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xed 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xee 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xef 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xf0 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xf1 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xf2 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xf3 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xf4 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xf5 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xf6 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xf7 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xf8 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xf9 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xfa 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xfb 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xfc 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xfd 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xfe 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xff 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x100 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x101 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x102 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x103 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x104 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x105 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x106 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x107 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x108 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

128 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x4c  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x4d  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x4e  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x4f  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x50  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x51  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x52  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x53  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x54  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x55  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x56  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x57  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x58  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x59  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x5a  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x5b  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x5c  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x5d  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x5e  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x5f  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x60  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x61  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x62  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x63  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x64  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x65  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x66  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x67  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x68  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x69  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x6a  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x6b  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x6c  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x6d  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x6e  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x6f  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x70  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0x71  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0x72  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0x73  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0x74  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x75  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x76  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x77  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x78  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x79  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x7a  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x7b  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x7c  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x7d  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x7e  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x7f  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x80  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x81  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x82  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x83  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x84  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x85  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x86  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x87  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x88  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x89  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8c  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x8d  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x8e  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x8f  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x90  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x91  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x92  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x93  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x94  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x95  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x96  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x97  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x98  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x99  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x9a  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x9b  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x9c  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x9d  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x9e  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x9f  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0xa0  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0xa1  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0xa2  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0xa3  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0xa4  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0xa5  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0xa6  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0xa7  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0xa8  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0xa9  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0xaa  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0xab  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0xac  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xad  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xae  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xaf  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xb0  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xb1  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xb2  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xb3  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xb4  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xb5  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xb6  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xb7  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xb8  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xb9  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xba  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xbb  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xbc  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xbd  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xbe  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xbf  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xc0  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xc1  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xc2  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xc3  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xc4  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xc5  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xc6  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xc7  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xc8  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc9  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xca  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xcb  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
```Current xorg.conf:
```
Section "ServerFlags"
        Option      "DontZap" "False"
        Option      "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier    "Monitor1"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier    "Monitor2"
    Option        "DPMS"
    Option        "RightOf" "Monitor1"
EndSection

Section "Monitor"
    Identifier    "Monitor3"
    Option        "DPMS"
    Option        "RightOf" "Monitor2"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Monitor1"
    Device        "ATI FirePro 2260 PCIE"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1680x1050" "1280x1024" "1152x864" "1024x768"
        Virtual        5040 1050
    EndSubSection
EndSection

Section "Module"
    Load        "glx"
EndSection

Section "Device"
    Identifier    "ATI FirePro 2260 PCIE"
    Driver        "ati"
    Option        "monitor-DisplayPort-0" "Monitor1"
    Option        "monitor-DisplayPort-1"    "Monitor2"
    BusID        "PCI:1:0:0"
EndSection

Section "Device"
    Identifier    "ATI FirePro 2260 PCI"
    Driver        "ati"
    BusID        "PCI:4:0:0"
EndSection
```Output from xrandr -q:
```
user@host:/etc/X11# xrandr -q
Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 5040 x 1050
DisplayPort-1 connected 1680x1050+1680+0 (normal left inverted right x axis y axis) 430mm x 270mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
DisplayPort-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 430mm x 270mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
```And my /var/log/Xorg.0.log:
```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux host 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 15 12:40:48 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "ATI FirePro 2260 PCIE"
(**) Option "DontZap" "False"
(**) Option "Xinerama" "off"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
        X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7
(--) PCI:*(0@1:0:0) ATI Technologies Inc RV620 [FirePro 2260] rev 0, Mem @ 0xc0000000/268435456, 0xfe9f0000/65536, I/O @ 0x0000dc00/256, BIOS @ 0x????????/131072
(--) PCI: (0@4:0:0) ATI Technologies Inc RV620 [FirePro 2260] rev 0, Mem @ 0xd0000000/268435456, 0xfe6f0000/65536, I/O @ 0x0000cc00/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 6.12.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 6.12.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
(II) RADEON: Driver for ATI Radeon chipsets:
        ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
        ATI Radeon Mobility X300 (M24) 3152 (PCIE),
        ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
        ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
        ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
        ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
        ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
        ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
        ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
        ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
        ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
        ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
        ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
        ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
        ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
        ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
        ATI Radeon X800PRO (R420) JI (AGP),
        ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
        ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
        ATI Radeon Mobility 9800 (M18) JN (AGP),
        ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
        ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
        ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
        ATI Radeon Mobility M7 LW (AGP),
        ATI Mobility FireGL 7800 M7 LX (AGP),
        ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
        ATI FireGL Mobility 9000 (M9) Ld (AGP),
        ATI Radeon Mobility 9000 (M9) Lf (AGP),
        ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
        ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
        ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
        ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
        ATI Radeon 9800XT NJ (AGP),
        ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
        ATI Radeon Mobility 9600 (M10) NQ (AGP),
        ATI Radeon Mobility 9600 (M11) NR (AGP),
        ATI Radeon Mobility 9600 (M10) NS (AGP),
        ATI FireGL Mobility T2 (M10) NT (AGP),
        ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
        ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
        ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
        ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
        ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
        ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
        ATI Radeon Mobility X300 (M22) 5460 (PCIE),
        ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
        ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
        ATI Radeon X800PRO (R423) UI (PCIE),
        ATI Radeon X800LE (R423) UJ (PCIE),
        ATI Radeon X800SE (R423) UK (PCIE),
        ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
        ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
        ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
        ATI FireGL unknown (R423) UR (PCIE),
        ATI FireGL unknown (R423) UT (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility Radeon X700 XL (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
        ATI Radeon Mobility 9100 IGP (U3) 5835,
        ATI Radeon XPRESS 200 5954 (PCIE),
        ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
        ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
        ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
        ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
        ATI Radeon XPRESS 200M 5975 (PCIE),
        ATI Radeon XPRESS 200 5A41 (PCIE),
        ATI Radeon XPRESS 200M 5A42 (PCIE),
        ATI Radeon XPRESS 200 5A61 (PCIE),
        ATI Radeon XPRESS 200M 5A62 (PCIE),
        ATI Radeon X300 (RV370) 5B60 (PCIE),
        ATI Radeon X600 (RV370) 5B62 (PCIE),
        ATI Radeon X550 (RV370) 5B63 (PCIE),
        ATI FireGL V3100 (RV370) 5B64 (PCIE),
        ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
        ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
        ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
        ATI Mobility Radeon X800 XT (M28) (PCIE),
        ATI Mobility FireGL V5100 (M28) (PCIE),
        ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
        ATI Radeon X850 XT PE (R480) (PCIE),
        ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
        ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
        ATI Radeon X850 XT (R480) (PCIE),
        ATI Radeon X800XT (R423) 5D57 (PCIE),
        ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
        ATI Radeon X700 PRO (RV410) (PCIE),
        ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
        ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
        ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
        ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
        ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
        ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
        ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
        ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
        ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
        ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
        ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
        ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
        ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
        ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
        ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
        ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
        ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
        ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
        ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
        ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
        ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
        ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
        ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
        ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
        ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
        ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
        ATI Mobility Radeon X1700, ATI Radeon X2300HD,
        ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
        ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
        ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
        ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
        ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
        ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
        ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
        ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
        ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
        ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
        ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
        ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
        ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
        ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
        ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
        ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
        ATI Radeon 4800 Series, ATI FirePro V8750 (FireGL),
        ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
        ATI Mobility RADEON HD 4850 X2, ATI Radeon 4800 Series,
        ATI FirePro RV770, AMD FireStream 9270, AMD FireStream 9250,
        ATI FirePro V8700 (FireGL), ATI Mobility RADEON HD 4870,
        ATI Mobility RADEON M98, ATI FirePro M7750, ATI M98, ATI M98,
        ATI M98, ATI Radeon RV730 (AGP), ATI FirePro M5750,
        ATI Radeon RV730 (AGP), ATI RV730XT [Radeon HD 4670],
        ATI RADEON E4600, ATI RV730 PRO [Radeon HD 4650],
        ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
        ATI FirePro V3750 (FireGL), ATI RV610, ATI Radeon HD 2400 XT,
        ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
        ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
        ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
        ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
        ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
        ATI Mobility Radeon HD 3850 X2, ATI RV670,
        ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
        ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
        ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
        ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
        ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
        ATI Mobility Radeon 4500 Series, ATI RV630,
        ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
        ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
        ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
        ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
        ATI FireGL V3600, ATI Radeon HD 2600 LE,
        ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
        ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
        ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
        ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
        ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
        ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
        ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
        ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
        ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
        ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
        ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
        ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
        ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
        ATI Radeon HD Graphics, ATI Radeon Graphics,
        ATI Mobility Radeon HD Graphics, ATI Mobility Radeon Graphics,
        ATI Radeon Graphics
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[b]
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[b]
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[b]
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[b]
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) RADEON(0): TOTO SAYS 00000000fe9f0000
(II) RADEON(0): MMIO registers at 0x00000000fe9f0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI FireMV 2260" (ChipID = 0x95cf)
(WW) RADEON(0): R600 support is mostly incomplete and very experimental
(--) RADEON(0): Linear framebuffer at 0x00000000c0000000
(II) RADEON(0): PCIE card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
        SubsystemVendorID: 0x1002 SubsystemID: 0x2143
        IOBaseAddress: 0xdc00
        Filename: S3B40306.100
        BIOS Bootup Message: 
113-B40306-100 RV620 GDDR2_32Mx16 64bit 256MB 500e/500m                     

(II) RADEON(0): Framebuffer space used by Firmware (kb): 16
(II) RADEON(0): Start of VRAM area used by Firmware: 0xfffc000
(II) RADEON(0): AtomBIOS requests 16kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0xfffc000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 500000
(II) RADEON(0): Default Memory Clock: 500000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: node name is /dev/dri/card14
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.1.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling disabled
(II) RADEON(0): Max desktop size set to 5040x1050
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 500.000000, mclk: 500.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
(II) RADEON(0): Output DisplayPort-1 using monitor section Monitor2
(**) RADEON(0): Option "RightOf" "Monitor1"
(II) RADEON(0): I2C bus "DisplayPort-1" initialized.
(II) RADEON(0): Output DisplayPort-0 using monitor section Monitor1
(II) RADEON(0): I2C bus "DisplayPort-0" initialized.
(II) RADEON(0): Port0:
  XRANDR name: DisplayPort-1
  Connector: DisplayPort
  DFP1: INTERNAL_UNIPHY
  DDC reg: 0x7e60
(II) RADEON(0): Port1:
  XRANDR name: DisplayPort-0
  Connector: DisplayPort
  DFP2: INTERNAL_UNIPHY
  DDC reg: 0x7e20
(II) RADEON(0): I2C device "DisplayPort-1:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "DisplayPort-1:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "DEL", prod id 53265
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Output: DisplayPort-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DisplayPort-1 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: d011  Serial#: 808530508
(II) RADEON(0): Year: 2008  Week: 24
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.328   greenX: 0.292 greenY: 0.610
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  430 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Serial No: G263H86C012L
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: DELL E207WFP
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac11d04c323130
(II) RADEON(0):         18120103802b1b78ee8db0a2544a9c25
(II) RADEON(0):         115054a54b00714f8180010101010101
(II) RADEON(0):         0101010101017c2e90a0601a1e403020
(II) RADEON(0):         3600ae0e1100001a000000ff00473236
(II) RADEON(0):         33483836433031324c0a000000fd0038
(II) RADEON(0):         4b1e530e000a202020202020000000fc
(II) RADEON(0):         0044454c4c20453230375746500a00c3
finished output detect: 0
(II) RADEON(0): I2C device "DisplayPort-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "DisplayPort-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DisplayPort-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DisplayPort-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: d011  Serial#: 808465228
(II) RADEON(0): Year: 2008  Week: 24
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.328   greenX: 0.292 greenY: 0.610
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  430 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Serial No: G263H86C003L
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: DELL E207WFP
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac11d04c333030
(II) RADEON(0):         18120103802b1b78ee8db0a2544a9c25
(II) RADEON(0):         115054a54b00714f8180010101010101
(II) RADEON(0):         0101010101017c2e90a0601a1e403020
(II) RADEON(0):         3600ae0e1100001a000000ff00473236
(II) RADEON(0):         33483836433030334c0a000000fd0038
(II) RADEON(0):         4b1e530e000a202020202020000000fc
(II) RADEON(0):         0044454c4c20453230375746500a00c3
finished output detect: 1
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "DEL", prod id 53265
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Output: DisplayPort-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DisplayPort-1 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: d011  Serial#: 808530508
(II) RADEON(0): Year: 2008  Week: 24
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.328   greenX: 0.292 greenY: 0.610
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  430 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Serial No: G263H86C012L
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: DELL E207WFP
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac11d04c323130
(II) RADEON(0):         18120103802b1b78ee8db0a2544a9c25
(II) RADEON(0):         115054a54b00714f8180010101010101
(II) RADEON(0):         0101010101017c2e90a0601a1e403020
(II) RADEON(0):         3600ae0e1100001a000000ff00473236
(II) RADEON(0):         33483836433031324c0a000000fd0038
(II) RADEON(0):         4b1e530e000a202020202020000000fc
(II) RADEON(0):         0044454c4c20453230375746500a00c3
(II) RADEON(0): Panel infos found from DDC detailed: 1680x1050
(II) RADEON(0): EDID vendor "DEL", prod id 53265
(II) RADEON(0): Output: DisplayPort-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DisplayPort-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: d011  Serial#: 808465228
(II) RADEON(0): Year: 2008  Week: 24
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.328   greenX: 0.292 greenY: 0.610
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  430 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Serial No: G263H86C003L
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: DELL E207WFP
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac11d04c333030
(II) RADEON(0):         18120103802b1b78ee8db0a2544a9c25
(II) RADEON(0):         115054a54b00714f8180010101010101
(II) RADEON(0):         0101010101017c2e90a0601a1e403020
(II) RADEON(0):         3600ae0e1100001a000000ff00473236
(II) RADEON(0):         33483836433030334c0a000000fd0038
(II) RADEON(0):         4b1e530e000a202020202020000000fc
(II) RADEON(0):         0044454c4c20453230375746500a00c3
(II) RADEON(0): Panel infos found from DDC detailed: 1680x1050
(II) RADEON(0): EDID vendor "DEL", prod id 53265
(II) RADEON(0): Output DisplayPort-1 connected
(II) RADEON(0): Output DisplayPort-0 connected
(II) RADEON(0): Using user preference for initial modes
(II) RADEON(0): Output DisplayPort-1 using initial mode 1680x1050
(II) RADEON(0): Output DisplayPort-0 using initial mode 1680x1050
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (430, 270) mm
(**) RADEON(0): DPI set to (297, 98)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Will attempt to use R6xx/R7xx EXA support if DRI is enabled.
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 2.4.0
        ABI class: X.Org Video Driver, version 5.0
(!!) RADEON(0): For information on using the multimedia capabilities
        of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[b](OprU)
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[b](OprU)
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[b](OprU)
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) RADEON(0): RADEONScreenInit c0000000 0 0
Output DIG dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Output DIG dpms success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
mc fb loc is 00cf00c0
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Allocating from a screen of 262144 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x01482000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x01486000
(II) RADEON(0): Will use 21000 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 241112 kb for X Server offscreen at offset 0x0148a000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0 0x00cf00c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(EE) RADEON(0): Acceleration initialization failed
(II) RADEON(0): Acceleration disabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
Output DIG dpms success
Output DIG dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
Output DIG dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Mode 1680x1050 - 1840 1080 9
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0 0x00cf00c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 119000000
best_freq: 119000000
best_feedback_div: 119
best_ref_div: 3
best_post_div: 9
(II) RADEON(0): crtc(0) Clock: mode 119000, PLL 119000
(II) RADEON(0): crtc(0) PLL  : refdiv 3, fbdiv 0x77(119), pdiv 9
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DIG1 encoder setup success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
Output DIG dpms success
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Lock CRTC 0 success
Output DIG dpms success
Output DIG dpms success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
Mode 1680x1050 - 1840 1080 9
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0 0x00cf00c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 119000000
best_freq: 119000000
best_feedback_div: 119
best_ref_div: 3
best_post_div: 9
(II) RADEON(0): crtc(1) Clock: mode 119000, PLL 119000
(II) RADEON(0): crtc(1) PLL  : refdiv 3, fbdiv 0x77(119), pdiv 9
Set CRTC 1 PLL success
Set CRTC Timing success
Set CRTC 1 Overscan success
Not using RMX
scaler 1 setup success
Set CRTC 1 Source success
crtc 1 YUV disable setup success
Output DIG1 encoder setup success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Unlock CRTC 0 success
Output DIG dpms success
Output DIG dpms success
Enable CRTC memreq 1 success
Enable CRTC 1 success
Unblank CRTC 1 success
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
Lock CRTC 0 success
Unlock CRTC 0 success
Lock CRTC 1 success
Unlock CRTC 1 success
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 860 x 270
(II) config/hal: Adding input device Microsoft Natural? Ergonomic Keyboard 4000
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 2.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(**) Microsoft Natural? Ergonomic Keyboard 4000: always reports core events
(**) Microsoft Natural? Ergonomic Keyboard 4000: Device: "/dev/input/event6"
(II) Microsoft Natural? Ergonomic Keyboard 4000: Found 1 mouse buttons
(II) Microsoft Natural? Ergonomic Keyboard 4000: Found keys
(II) Microsoft Natural? Ergonomic Keyboard 4000: Configuring as keyboard
(**) Microsoft Natural? Ergonomic Keyboard 4000: YAxisMapping: buttons 4 and 5
(**) Microsoft Natural? Ergonomic Keyboard 4000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Natural? Ergonomic Keyboard 4000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Natural? Ergonomic Keyboard 4000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Natural? Ergonomic Keyboard 4000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Natural? Ergonomic Keyboard 4000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Natural? Ergonomic Keyboard 4000
(**) Microsoft Natural? Ergonomic Keyboard 4000: always reports core events
(**) Microsoft Natural? Ergonomic Keyboard 4000: Device: "/dev/input/event5"
(II) Microsoft Natural? Ergonomic Keyboard 4000: Found keys
(II) Microsoft Natural? Ergonomic Keyboard 4000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Natural? Ergonomic Keyboard 4000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Natural? Ergonomic Keyboard 4000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Natural? Ergonomic Keyboard 4000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Natural? Ergonomic Keyboard 4000: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Microsoft Microsoft Trackball Explorer?
(**) Microsoft Microsoft Trackball Explorer?: always reports core events
(**) Microsoft Microsoft Trackball Explorer?: Device: "/dev/input/event3"
(II) Microsoft Microsoft Trackball Explorer?: Found 5 mouse buttons
(II) Microsoft Microsoft Trackball Explorer?: Found x and y relative axes
(II) Microsoft Microsoft Trackball Explorer?: Configuring as mouse
(**) Microsoft Microsoft Trackball Explorer?: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Trackball Explorer?: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Trackball Explorer?" (type: MOUSE)
(**) Microsoft Microsoft Trackball Explorer?: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft Trackball Explorer?: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft Trackball Explorer?: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft Trackball Explorer?: (accel) set acceleration profile 0
(II) RADEON(0): Output: DisplayPort-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DisplayPort-1 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: d011  Serial#: 808530508
(II) RADEON(0): Year: 2008  Week: 24
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.328   greenX: 0.292 greenY: 0.610
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  430 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Serial No: G263H86C012L
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: DELL E207WFP
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac11d04c323130
(II) RADEON(0):         18120103802b1b78ee8db0a2544a9c25
(II) RADEON(0):         115054a54b00714f8180010101010101
(II) RADEON(0):         0101010101017c2e90a0601a1e403020
(II) RADEON(0):         3600ae0e1100001a000000ff00473236
(II) RADEON(0):         33483836433031324c0a000000fd0038
(II) RADEON(0):         4b1e530e000a202020202020000000fc
(II) RADEON(0):         0044454c4c20453230375746500a00c3
(II) RADEON(0): EDID vendor "DEL", prod id 53265
(II) RADEON(0): EDID vendor "DEL", prod id 53265
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Output: DisplayPort-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DisplayPort-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: d011  Serial#: 808465228
(II) RADEON(0): Year: 2008  Week: 24
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.328   greenX: 0.292 greenY: 0.610
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  430 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Serial No: G263H86C003L
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: DELL E207WFP
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac11d04c333030
(II) RADEON(0):         18120103802b1b78ee8db0a2544a9c25
(II) RADEON(0):         115054a54b00714f8180010101010101
(II) RADEON(0):         0101010101017c2e90a0601a1e403020
(II) RADEON(0):         3600ae0e1100001a000000ff00473236
(II) RADEON(0):         33483836433030334c0a000000fd0038
(II) RADEON(0):         4b1e530e000a202020202020000000fc
(II) RADEON(0):         0044454c4c20453230375746500a00c3
(II) RADEON(0): EDID vendor "DEL", prod id 53265
(II) RADEON(0): Output: DisplayPort-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DisplayPort-1 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: d011  Serial#: 808530508
(II) RADEON(0): Year: 2008  Week: 24
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.328   greenX: 0.292 greenY: 0.610
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  430 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Serial No: G263H86C012L
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: DELL E207WFP
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac11d04c323130
(II) RADEON(0):         18120103802b1b78ee8db0a2544a9c25
(II) RADEON(0):         115054a54b00714f8180010101010101
(II) RADEON(0):         0101010101017c2e90a0601a1e403020
(II) RADEON(0):         3600ae0e1100001a000000ff00473236
(II) RADEON(0):         33483836433031324c0a000000fd0038
(II) RADEON(0):         4b1e530e000a202020202020000000fc
(II) RADEON(0):         0044454c4c20453230375746500a00c3
(II) RADEON(0): EDID vendor "DEL", prod id 53265
(II) RADEON(0): EDID vendor "DEL", prod id 53265
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Output: DisplayPort-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DisplayPort-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: d011  Serial#: 808465228
(II) RADEON(0): Year: 2008  Week: 24
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.328   greenX: 0.292 greenY: 0.610
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  430 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Serial No: G263H86C003L
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: DELL E207WFP
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac11d04c333030
(II) RADEON(0):         18120103802b1b78ee8db0a2544a9c25
(II) RADEON(0):         115054a54b00714f8180010101010101
(II) RADEON(0):         0101010101017c2e90a0601a1e403020
(II) RADEON(0):         3600ae0e1100001a000000ff00473236
(II) RADEON(0):         33483836433030334c0a000000fd0038
(II) RADEON(0):         4b1e530e000a202020202020000000fc
(II) RADEON(0):         0044454c4c20453230375746500a00c3
(II) RADEON(0): EDID vendor "DEL", prod id 53265
(II) RADEON(0): Output: DisplayPort-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DisplayPort-1 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: d011  Serial#: 808530508
(II) RADEON(0): Year: 2008  Week: 24
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.328   greenX: 0.292 greenY: 0.610
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  430 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Serial No: G263H86C012L
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: DELL E207WFP
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac11d04c323130
(II) RADEON(0):         18120103802b1b78ee8db0a2544a9c25
(II) RADEON(0):         115054a54b00714f8180010101010101
(II) RADEON(0):         0101010101017c2e90a0601a1e403020
(II) RADEON(0):         3600ae0e1100001a000000ff00473236
(II) RADEON(0):         33483836433031324c0a000000fd0038
(II) RADEON(0):         4b1e530e000a202020202020000000fc
(II) RADEON(0):         0044454c4c20453230375746500a00c3
(II) RADEON(0): EDID vendor "DEL", prod id 53265
(II) RADEON(0): EDID vendor "DEL", prod id 53265
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Output: DisplayPort-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DisplayPort-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: d011  Serial#: 808465228
(II) RADEON(0): Year: 2008  Week: 24
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.328   greenX: 0.292 greenY: 0.610
(II) RADEON(0): blueX: 0.146 blueY: 0.069   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  430 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Serial No: G263H86C003L
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: DELL E207WFP
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac11d04c333030
(II) RADEON(0):         18120103802b1b78ee8db0a2544a9c25
(II) RADEON(0):         115054a54b00714f8180010101010101
(II) RADEON(0):         0101010101017c2e90a0601a1e403020
(II) RADEON(0):         3600ae0e1100001a000000ff00473236
(II) RADEON(0):         33483836433030334c0a000000fd0038
(II) RADEON(0):         4b1e530e000a202020202020000000fc
(II) RADEON(0):         0044454c4c20453230375746500a00c3
(II) RADEON(0): EDID vendor "DEL", prod id 53265
```I did try the binary drivers and I have the config file that aticonfig created as well:
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
    Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-1"
    Screen         "aticonfig-Screen[1]-1" RightOf "aticonfig-Screen[1]-0"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
        Option      "DontZap" "False"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "nvidia"
    Option        "NoLogo" "True"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-1"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:4:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-1"
    Driver      "fglrx"
    BusID       "PCI:4:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-1"
    Device     "aticonfig-Device[0]-1"
    Monitor    "aticonfig-Monitor[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-1"
    Device     "aticonfig-Device[1]-1"
    Monitor    "aticonfig-Monitor[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```Any help greatly appreciated.  :)

---

### Post by Larry64 on 2009-07-20
I have been running triple head on one Xerama (what ever) X session for years now on a few different combination of nVidia cards and a couple of mobo's.

2x 6800GT

or

2x 8600GT

or 
8600Gt + 8300onboard

all worked fine and all configured the same way....

Install on one monitor.
Install the nVidia drivers (they are awesome)
Install the nVidia support tools (I am sorry I forget the ubuntu package name exactly)
Then use sudo nvidia-settings  to configure the monitor layout. (very MS Windows style really)

The sudo allows it to save the xorg.conf it generates.  Reboot and it should be all happy.

I then edit the xorg.conf to add a few custom settings such as DeactivateGrabs (which someone has dumped in Jaunty?!?!  seriously, does no one game under linux?  )  and now you need to add the Option DontZap False in case X is misbehaving etc.

Hope that helped...


Oh, and although the config allows me to run some games across 3 monitors, and openGL clearly working on all monitors compiz won't enable.  Pretty sure I have seen  many references to it having 0 support for multiple monitors.

Also since I have updated to Jaunty:
  1.  moving the mouse from one screen to the next leaves a copy of the cursor behind!!! 
  2.  when soem applications are starting up, espcially wine, the cursor gets "trapped" on the one monitor and just wraps around when it should move to the next monitor. Wait a few seconds and the cursor pops back to the place it should have been and all is well again.


Neither of these were a problem for me in Intrep.

I could no longer live without multiple monitors so hopefully it will get better support in October.

---


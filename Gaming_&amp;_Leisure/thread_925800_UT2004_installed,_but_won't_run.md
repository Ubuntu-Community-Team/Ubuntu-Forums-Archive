---
title: "UT2004 installed, but won't run"
date: 2008-09-21
forum: Gaming &amp; Leisure
---

### Post by KDB9000 on 2008-09-21
I was able to install UT2004 (installed it to the home directory). It starts normal (with the splash screen for UT2004) but disappears and nothing happens. I ran the command in a terminal and get this after the splash screen has displayed, "WARNING: ALC_EXT_capture is subject to change!" and will just sit there until I control-C.  I haven't had a chance to get the patches yet (slow DSL). I followed the instructions from Game Area's website and have the needed software for it (libgtk1.2). Any ideas?

---

### Post by Crafty Kisses on 2008-09-21
I'd like to see the results of this command:
```
glxinfo
```
It sounds like it could be a possible direct rendering issue.

---

### Post by KDB9000 on 2008-09-21
Here are my system specs if that helps. Tried to add them last night but the forums crashed.

HP Pavilion Laptop DV5000
Ubuntu 8.10 32-bit
AMD Althon 64-bit at 2 Ghz
2 GB of RAM
128 MB ATi Xpress 200M graphic card (with ATi drivers)

glxinfo
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by Brebs on 2008-09-22
> **KDB9000 said:**
> direct rendering: No
That needs to be Yes - reinstall your video driver.

---

### Post by GSZX1337 on 2008-09-22
Since there's already a thread on this, I'll post my problem here. I installed UT2k4 and whenever I try to run it I get:

```
gszx1337@GMan:~$ ut2004
bash: ut2004: command not found

```

---

### Post by Perfect Storm on 2008-09-22
**KDB9000**
You need to install the driver for your card.

**GSZX1337**

Where did you install UT2004? If you installed it as default (/usr/local/games), check if it made a bin file in /usr/local/bin

If you installed locally - you need to make a "run" script for UT2004

---

### Post by KDB9000 on 2008-09-22
According to CCHTML (ATi's Unofficial Wiki for Linux) I need to remove Mesa drivers. I have already tried reinstalling the drivers (needed to so I could use my external monitor port). I am going to search the forum for removing Mesa drivers. The wiki said to remove xserver-xgl, well it isn't installed on my system. Any thoughts while I look though the forum?

---

### Post by Perfect Storm on 2008-09-22
Properly - libgl1-mesa-dri
Not sure, I don't have ATI.

---

### Post by KDB9000 on 2008-09-22
I got it fixed. Had to reinstall the drivers. Think I broke something while trying to fix something. Everything (except sound) works. With the sound, it says that the device is busy.

---

### Post by GSZX1337 on 2008-09-22
> **Artificial Intelligence said:**
> 
**GSZX1337**

Where did you install UT2004? If you installed it as default (/usr/local/games), check if it made a bin file in /usr/local/bin

If you installed locally - you need to make a "run" script for UT2004

I found UT2004 in my home folder. I tried running the script in the terminal, but the game just shows the splash screen and then crashes.

EDIT: Here's what the terminal showed when I typed glxinfo

```
gszx1337@GMan:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7900 GT/GTO/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 173.14.12
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x46 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x5a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x61 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x71 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x72 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x75 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x76 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x77 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x78 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x79 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x7e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x7f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x80 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x82 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x83 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x84 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x85 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x86 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x87 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x89 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8b 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x8c 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x8d 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8e 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x90 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x91 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x92 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x93 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x94 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x95 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x96 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x97 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x98 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon

```

---

### Post by Perfect Storm on 2008-09-22
Do you run 64-bit?

Try launch the script from the terminal and see what it says.

---

### Post by GSZX1337 on 2008-09-22
```
Your CD key appears to be invalid.  You will need to reinstall the game and enter your CD key to fix this problem.
```

Why the hell didn't the game just tell me the CD Key was invalid I entered it! :mad: (Yes, I do own the game, I'm not pirating it)

Anyway, thanks for the help A.I.

---

### Post by GSZX1337 on 2008-09-22
Great, now when I try to install the game, the installer won't let me unmount the drive.

---

### Post by Brebs on 2008-09-22
> **GSZX1337 said:**
> won't let me unmount
Then don't have any user cd'd into a CD directory. E.g.:

cd ~
/media/cdrom/setup.run (or whatever the executable filename is)

Then you should be able to type "eject" to swap CDs.

---

### Post by GSZX1337 on 2008-09-24
> **Brebs said:**
> Then don't have any user cd'd into a CD directory. E.g.:

cd ~
/media/cdrom/setup.run (or whatever the executable filename is)

Then you should be able to type "eject" to swap CDs.

I found out that my problem was that I was running the installer through the terminal. I didn't run the installer through the terminal, and I was able to eject CDs. Thanks for the suggestion, though. :)

---


---
title: "Calling all (X)perts"
date: 2005-04-17
forum: Gaming &amp; Leisure
---

### Post by brk3 on 2005-04-17
I just installed Hoary and everything works *perfect* except opengl games. I have the drivers installed and glxgears runs fine with a high framerate so theres no problem there.
The error I get is:

X Error of failed request:  BadColor (invalid Colormap parameter)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x22
  Serial number of failed request:  17
  Current serial number in output stream:  20

This didnt happen on Warty so is there some new configuration on the X system hoarys' using thats causing this?
If anyone knows what needs to be done it would be great.
Cheers.

---

### Post by dataw0lf on 2005-04-17
If you could post the output of glxinfo that'd be great. Thanks!

---

### Post by brk3 on 2005-04-18
Sure, I can do that when I get home, but I dont think its a problem with the opengl drivers themselves. Because I can run SDL games with opengl acceleration e.g. cube.
It more seems to be a problem with some X settings.  When I was googling for a answer I saw 1 or 2 pages that said set your DISPLAY enviroment variable to contain the computers name i.e. localhost. So it becomes :localhost0.0 or something similar. But that didnt work, it just caused it not to be albe to find the display at all.
Anyway il stop going on and post that glxinfo later.
Thanks

---

### Post by dataw0lf on 2005-04-18
it's 'set DISPLAY localhost:0'

---

### Post by brk3 on 2005-04-29
That still gives:
Error: Could not open display (DISPLAY=[localhost:0])

Umm..

paul@localhost:~/games/Doom $ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce2 MX/AGP/SSE/3DNOW!
OpenGL version string: 1.5.3 NVIDIA 71.74
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr,
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shared_texture_palette,
    GL_EXT_stencil_wrap, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fence,
    GL_NV_fog_distance, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil,
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_register_combiners,
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4,
    GL_NV_texture_rectangle, GL_NV_vertex_array_range,
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_SGIS_generate_mipmap, GL_SGIS_multitexture, GL_SGIS_texture_lod,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x33 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None

---


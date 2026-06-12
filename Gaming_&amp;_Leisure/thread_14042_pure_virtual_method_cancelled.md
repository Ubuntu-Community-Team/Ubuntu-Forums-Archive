---
title: "pure virtual method cancelled"
date: 2005-02-04
forum: Gaming &amp; Leisure
---

### Post by lycos on 2005-02-04
hi,
i have nvidia mx400 and with drivers.
when i entered a server and started playing suddenly it is closing and givin a message:
pure virtual method cancelled. :(
any suggestion?
thanks for your time..

---

### Post by jdodson on 2005-02-04
[QUOTE=lycos]hi,
i have nvidia mx400 and with drivers.
when i entered a server and started playing suddenly it is closing and givin a message:
pure virtual method cancelled. :(
any suggestion?
thanks for your time..[/QUOTE]

so what game are you playing?  can you run glxgears successfully?  what is your FPS?

---

### Post by lycos on 2005-02-04
[QUOTE=jdodson]so what game are you playing?  can you run glxgears successfully?  what is your FPS?[/QUOTE]
 @jdodson sorry didnt state the name of the game :)
it is bzflag.
when i run glxgears the output is like this:
root@mrCloud:~ # glxgears
2256 frames in 5.0 seconds = 451.200 FPS
2434 frames in 5.0 seconds = 486.800 FPS
2393 frames in 5.0 seconds = 478.600 FPS
2436 frames in 5.0 seconds = 487.200 FPS
2435 frames in 5.0 seconds = 487.000 FPS
2435 frames in 5.0 seconds = 487.000 FPS
2437 frames in 5.0 seconds = 487.400 FPS
2435 frames in 5.0 seconds = 487.000 FPS
2435 frames in 5.0 seconds = 487.000 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
root@mrCloud:~ #

what do you suggest?

---

### Post by lycos on 2005-02-04
my fps' are good or bad?
are they the problem? :(

---

### Post by jdodson on 2005-02-04
[QUOTE=lycos]my fps' are good or bad?
are they the problem? :([/QUOTE]

i get around 2,500-3,000 FPS.  did you install the nvidia drivers using the method in the [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by valadil on 2005-02-04
That fps sounds about right for a card like that.  Depends on the rest of your comp though.  The geforce2 in my laptop gets about 500.  The one that used to be in my desktop (RIP) got around 2000.  My 5900 gets 6500-7000.

First of all this is not something you need to run as root.  I noticed the root@mrCloud thing and just thought I'd warn ya. 

Try glxinfo.  That might spout out some info more useful than glxgears had.

The error you gave initially doesn't tell me much.  What game were you trying to play?  Did it let you start playing at all and then quit or did it quit as soon as you joined?

---

### Post by lycos on 2005-02-05
i have tried everything in the game options.
even when i changed the quality normal or low or effects .....
pure virtual method cancelled.
even i tried to play it under xp. 
but the same thing again. :(
pure virtual method cancelled.
it is really killing me..

whatever, my glxinfo is like this;
root@mrCloud:~ # glxinfo
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
    GLX_NV_swap_group, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce2 MX/PCI/SSE2
OpenGL version string: 1.5.1 NVIDIA 61.11
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array,
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
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2f 24 dc  0 32  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  0  0 16  0 16 16 16 16  0 0 None
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 None
0x33 24 dc  0 32  0 r  .  .  8  8  8  0  0 16  0 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  y  .  8  8  8  0  0  0  0 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  .  .  8  8  8  0  0  0  0 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 None

thanks for your time..

---


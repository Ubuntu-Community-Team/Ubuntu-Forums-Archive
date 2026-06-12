---
title: "Please help me with Quake2"
date: 2006-08-11
forum: Gaming &amp; Leisure
---

### Post by sherpah on 2006-08-11
I run the latest Ubuntu release on a fujitsu lifebook P5010 which has an onboard intel 855gm processor. 

I have 3d working - Glgears runs at about 600fps. I have penguin racer (tuxracer) installed and it runs perfectly. However, when I run Quake in GLX rendering mode, it is unplayable - stutteringly slow frame rates even in the lowest resolution. Quake2 runs smoothly in all resolutions with software rendering. I have no idea what to do - any help is appreciated.

My GLXinfo is below:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20050225
OpenGL version string: 1.3 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1,
    GL_APPLE_client_storage, GL_APPLE_packed_pixels,
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

---

### Post by dtfinch on 2006-08-12
I've actually never gotten Quake2's OpenGL support to work on Windows. I've tried on several systems, all of which run Quake 3 fine.

---

### Post by pharcyde on 2006-08-12
Have a look at the following link, it may be what you need to get it running.
[https://help.ubuntu.com/community/Games/Native/Quake2](https://help.ubuntu.com/community/Games/Native/Quake2)

---

### Post by HAARP on 2006-08-12
Better use the icculus.org installer. The packages provided by the Ubuntu repos  - to put it simply - suck.
[http://www.liflg.org/?catid=6&gameid=55](http://www.liflg.org/?catid=6&gameid=55)

---

### Post by sherpah on 2006-08-17
Well,

I ended up using the packages provided by the ubuntu installer, cause when I use the icculus loki installer, 3d CRAWLS and like 3 fps. When I use the Ubuntu packages for quake2 and simply dump the data files over from my windows retail disc - 3d works beautifully (meaning GLX).

However - I now have a new problem - the sound is choppy - terribly choppy - I have read all over the forums, but I am not finding a clear solution. Can someone please explain to me why the 3d now works but the sound is choppy? And please tell me how to fix the sound issue? Also an explanation is appreciated.

Thanks

---


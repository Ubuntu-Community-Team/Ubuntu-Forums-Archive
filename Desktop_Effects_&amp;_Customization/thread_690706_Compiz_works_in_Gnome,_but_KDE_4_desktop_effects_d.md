---
title: "Compiz works in Gnome, but KDE 4 desktop effects don't"
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by noahsark1126 on 2008-02-07
I'm running Gutsy with an ATI x1400 card, fglrx version 8.40.4 and Xgl installed.  Compiz works great in Gnome - perfectly smooth, everything's fine.

But when I installed KDE 4 and logged into a full session, I cannot get the desktop effects to work.  It says they are enabled, but none of them actually function, even after restarting X.  Anything I could try?

It might also be of note that although compiz works fine, fglrxinfo and glxinfo give some odd results:

```
$ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.2 (2.0.6747 (8.40.4))
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

So apparently I don't have direct rendering, even if compiz works, and oddly my screen and display are different.  If I get my fglrxinfo, we see

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

But if I add in -display :1

```
$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.2 (2.0.6747 (8.40.4))

```

Perhaps this has something to do with the problem?

---

### Post by noahsark1126 on 2008-02-08
anyone?

---

### Post by noahsark1126 on 2008-02-09
Is it possibly because of Xgl?  Can Kwin use Xgl for compositing, or do I need AIGLX?

---

### Post by joshuachad on 2008-02-09
Try installed from the git master branch which is at 0.7.1. There was some KDE4 things that were implemented recently. Also make sure you compile to support KDE. I know this works for nVidia folks like myself. The Xgl question im not sure. I havent use Xgl since the Vietnam war. Also this is a pretty damn good guide 

[http://ubuntuforums.org/showthread.php?t=643485]("http://ubuntuforums.org/showthread.php?t=643485")

---

### Post by noahsark1126 on 2008-02-09
> **joshuachad said:**
> Try installed from the git master branch which is at 0.7.1. There was some KDE4 things that were implemented recently. Also make sure you compile to support KDE. I know this works for nVidia folks like myself. The Xgl question im not sure. I havent use Xgl since the Vietnam war. Also this is a pretty damn good guide 

[http://ubuntuforums.org/showthread.php?t=643485]("http://ubuntuforums.org/showthread.php?t=643485")

My problem is not with Compiz Fusion, it's with Kwin's desktop effects in KDE 4 (which are quite similar).  Compiz works fine.  I'm trying to get Kwin to realize that my system is capable of compositing.

---

### Post by noahsark1126 on 2008-02-10
not possible?

---

### Post by noahsark1126 on 2008-02-12
any other ideas?

---

### Post by awakatanka on 2008-02-13
Having the same problem, can't get desktop effects to work under kde4 hardy. If i use kde4 opensuse everything is working. I'm using a nvidia 6200 card.

---

### Post by noahsark1126 on 2008-02-15
one more bump...

---

### Post by bongo on 2008-04-04
Any resolution on this?

---


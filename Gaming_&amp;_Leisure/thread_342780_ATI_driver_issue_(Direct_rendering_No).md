---
title: "ATI driver issue? (Direct rendering: No)"
date: 2007-01-20
forum: Gaming &amp; Leisure
---

### Post by Hellcom on 2007-01-20
I've been having problems running a couple of 3d games both under wine and native that have cause crashes, games hanging, and errors. On another forum someone suggested that it might be that direct rendering is currently off:


glxinfo output
```
hellcom@hellcom-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
[COLOR="Red"]direct rendering: No[/COLOR]
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x4b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
hellcom@hellcom-desktop:~$ 
```

Running Ubuntu 6.10, ATI 9800 pro 128 MB with official drivers 8.33.6.

---

### Post by Ferrat on 2007-01-20
Did you install the ATi linux driver from ati.com or the one in the repos?

---

### Post by Hellcom on 2007-01-20
Both. I tried from the repositories first then and then tried ATI.com

---

### Post by Hellcom on 2007-01-20
Fixed, wrong driver.

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---


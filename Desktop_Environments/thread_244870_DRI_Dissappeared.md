---
title: "DRI Dissappeared?"
date: 2006-08-27
forum: Desktop Environments
---

### Post by Blairboy on 2006-08-27
I'm not sure if I'm the only person this has happened to, but up until a little while ago, I had DRI under xgl/compiz.  Now I can't open up picasa under xgl, which is mighty annoying.  Anybody else got this problem or a solution for it?

---

### Post by Woei on 2006-08-27
> **Blairboy said:**
> I'm not sure if I'm the only person this has happened to, but up until a little while ago, I had DRI under xgl/compiz.  Now I can't open up picasa under xgl, which is mighty annoying.  Anybody else got this problem or a solution for it?

Please attach your /var/log/X.org.log file here along with /etc/X11/xorg.conf and the output of glxinfo.

---

### Post by Blairboy on 2006-08-27
Here's the output of glxinfo and the xorg files are in the archive.


```
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 1.2 (2.0.6011 (8.28.8))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by kickblow on 2006-08-27
i have the same problem.

glxinfo says gl 1.2
fglxnifo says gl 2.0

but i can't run java web start programs that requires extensions (vp,fp).

it works when i log out of xgl sessions and back into gnome.

---

### Post by Blairboy on 2006-08-28
Would using the LD preload option to start compiz fix that?  Or is there some other way that I need to link to the correct glx files?

---


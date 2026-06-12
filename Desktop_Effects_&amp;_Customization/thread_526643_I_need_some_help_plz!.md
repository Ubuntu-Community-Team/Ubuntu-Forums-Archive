---
title: "I need some help plz!"
date: 2007-08-15
forum: Desktop Effects &amp; Customization
---

### Post by kbzona on 2007-08-15
i just installed compiz-fusion and i have some problems

1) sometimes the cubecaps disappear 

2) sometimes the Window Previews loses his form, shape.. i mean that is not "cute" anymore.. instead of drawing the rounded preview .. it just draws a ugly white square with the preview

Plz help!

thnx in advance :)

---

### Post by kbzona on 2007-08-16
Bump. :( :confused:

---

### Post by kbzona on 2007-08-16
*Bump*  ... damn... its falling fast

---

### Post by kbzona on 2007-08-18
BUMP!!!!!!!! please!!

---

### Post by kbzona on 2007-08-20
is really no one having this problem?

---

### Post by Rupertronco on 2007-08-20
When you post a thread you've got to give some more information. The title of your thread should describe your problem, and not just say something like "I need help", it allows people fluent in your problem to identify the post and help you. 

What graphics card are you using? What are your system specs? Are you using XGL or AiGLX ? 

Go to a terminal and type glxinfo and post the output of it.

---

### Post by kbzona on 2007-08-20
CARD:  ATI X1950.. so XGL :(

GLXINFO:

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
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 1.2 (2.0.6650 (8.39.4))
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

---

### Post by Rupertronco on 2007-08-21
Direct rendering needs to be enabled. Somewhere along the line your setup has gone wrong.  Post a copy of your /etc/X11/xorg.conf file.

---

### Post by kbzona on 2007-08-21
> **Rupertronco said:**
> Direct rendering needs to be enabled. Somewhere along the line your setup has gone wrong.  Post a copy of your /etc/X11/xorg.conf file.

I think that is a common bug with the drivers + xgl...

It says "direct rendering: No", but is enabled.... correct me if im wrong.... , but i know that i readed it somewhere...

---

### Post by kbzona on 2007-08-21
Any other suggestions?

---


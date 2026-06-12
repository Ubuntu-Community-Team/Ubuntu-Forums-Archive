---
title: "trying to use compiz, but its not working"
date: 2007-01-17
forum: Desktop Environments
---

### Post by moshuptrail on 2007-01-17
I'm having problems getting compiz to run.  One thing that really bothers me is that glxinfo indicates direct rendering: no.  Video Card: ATI Radeon 320M.  about 5 years old.

glxinfo gives:
```
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 4x NO-TCL
OpenGL version string: 1.2 (1.2 (1.3 Mesa 6.5.1))
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

fglrxinfo:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 4x NO-TCL
OpenGL version string: 1.2 (1.2 (1.3 Mesa 6.5.1))

```

Also, while Firefox has focus the CPU  goes to 100% and things get real slow.  Xorg is running at or near 100%.  If I shrink the size of the Firefox window it runs at less.

---

### Post by Fitzy_oz on 2007-01-17
> **moshuptrail said:**
> I'm having problems getting compiz to run.  One thing that really bothers me is that glxinfo indicates direct rendering: no.  Video Card: ATI Radeon 320M.  about 5 years old.

glxinfo gives:
```
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
[COLOR="Red"]direct rendering: No[/COLOR]
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 4x NO-TCL
OpenGL version string: 1.2 (1.2 (1.3 Mesa 6.5.1))
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

fglrxinfo:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 4x NO-TCL
OpenGL version string: 1.2 (1.2 (1.3 Mesa 6.5.1))

```

Also, while Firefox has focus the CPU  goes to 100% and things get real slow.  Xorg is running at or near 100%.  If I shrink the size of the Firefox window it runs at less.


[COLOR="Red"]direct rendering: No[/COLOR]
TSpot on, thats the problem right there.
I don't use XGL/Compiz i use Beryl which works alot better.  Try installing the fglrx drivers for your ati card with this [howto]("http://wiki.cchtml.com"), it worked for me with my radeon 9600se.

You'll need to add the beryl repos to synaptic - And i'm not on my home computer so I can't tell you what they are off the top of my head.  Just do a forum search and you should be able to find them.

---

### Post by moshuptrail on 2007-01-17
I've tried to get the flgrx driver to work.  I couldn't find my card listed there.  I tried installing one that looked close, but flgrx wont run.  If I set the driver = "flgrx" in the xorg.conf, I get an error message on boot and it drops back to black screen mode.

However, I think something is right (maybe I'm getting software rendering-that would explain the heavy CPU use) because I was able to enable the GL desktop. But then all the window borders disappeared.  I've seen that problem before in the forum.  Do you remember what causes that?

---

### Post by Fitzy_oz on 2007-01-18
> **moshuptrail said:**
> I've tried to get the flgrx driver to work.  I couldn't find my card listed there.  I tried installing one that looked close, but flgrx wont run.  If I set the driver = "flgrx" in the xorg.conf, I get an error message on boot and it drops back to black screen mode.

However, I think something is right (maybe I'm getting software rendering-that would explain the heavy CPU use) because I was able to enable the GL desktop. But then all the window borders disappeared.  I've seen that problem before in the forum.  Do you remember what causes that?

[This thread]("http://www.ubuntuforums.org/showthread.php?t=310018&highlight=mobility+320m") might have been the one

---


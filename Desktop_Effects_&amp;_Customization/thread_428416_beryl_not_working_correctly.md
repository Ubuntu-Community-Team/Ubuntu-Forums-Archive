---
title: "beryl not working correctly"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by mattigus on 2007-04-30
I'm having a strange error when I load Beryl.  Nothing really loads, and my windows get frozen into place.  I've checked the Beryl manager, and it says its running.  When I type Beryl in the terminal, I get this:

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

Im running on XGL, and have a radeon x1800 graphics card.  Can anyone help me?

---

### Post by khughitt on 2007-04-30
Which ATI drivers did you install? Post the output you get for the commands **glxinfo** and **fglrxinfo**.

---

### Post by rickycodie on 2007-04-30
i don't want to be instulting, so don't take it that way but did you install the ati drivers first? if not you can get them with the restricted drivers manager.

---

### Post by rickycodie on 2007-04-30
[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557) 
go here if you can't do it that way.

---

### Post by mattigus on 2007-04-30
GLX info

```
glxinfo
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 1.2 (2.0.6334 (8.34.8))
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

Fglrx info

```
fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 1.2 (2.0.6334 (8.34.8))

```

Don't worry about sounding insulting.  This is the beginners forum, and I am pretty noobish.

---

### Post by palmerthegeek on 2007-04-30
mattigus.

I searched around for other related beryl ati posts.  I'm not sure your platform (laptop or desktop) however if you haven't looked at this already it might work for you.  (Worked for me):
[http://ubuntuforums.org/showthread.php?p=2420732#post2420732](http://ubuntuforums.org/showthread.php?p=2420732#post2420732)

---

### Post by rolf-c on 2007-04-30
..also from your post above:

```
direct rendering: No
```

That needs to be a Yes, check the various threads and search the forum (use the Search function) for many howto's and tips.  I do not have an ATI card.

---

### Post by rickycodie on 2007-04-30
see my above post to enable direct rendering

---


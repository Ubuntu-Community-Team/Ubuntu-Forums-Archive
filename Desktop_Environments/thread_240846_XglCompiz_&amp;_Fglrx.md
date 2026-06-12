---
title: "Xgl/Compiz &amp; Fglrx"
date: 2006-08-21
forum: Desktop Environments
---

### Post by Naros on 2006-08-21
I have a problem with Xgl/compiz and my video card. Compiz and movies runs slowly, compiz doesn't start with all sessions. Here is my fglrxinfo : ```
 Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8) 
```

And glxinfo: ```
 naros@naros-desktop:~$ glxinfo
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
OpenGL renderer string: RADEON 9000 DDR Generic
OpenGL version string: 1.2 (1.3.1091 (X4.3.0-8.28.8))
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

Any ideas ? :???:

---

### Post by Ziox on 2006-08-21
> **Naros said:**
> I have a problem with Xgl/compiz and my video card. Compiz runs slowly and movies too. Here is my fglrxinfo : ```
 Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8) 
```

And glxinfo: ```
 naros@naros-desktop:~$ glxinfo
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
OpenGL renderer string: RADEON 9000 DDR Generic
OpenGL version string: 1.2 (1.3.1091 (X4.3.0-8.28.8))
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

Any ideas ? :???:

Direct Rendering isn't enabled on your card, meaning that Compiz and anything that is heavy on graphics wouldn't run fast...try searching the forum for this > Xlib:  extension "XFree86-DRI" missing on display ":1.0".

I think the solution is to link a file, but i'm not sure...

---

### Post by peabody on 2006-08-21
> **Ziox said:**
> Direct Rendering isn't enabled on your card, meaning that Compiz and anything that is heavy on graphics wouldn't run fast...try searching the forum for this 

I think the solution is to link a file, but i'm not sure...

Direct rendering does NOT show up even when enabled in Xgl because xgl is a hack.  It's basically something that gets grafted on top the xserver.  I'm guessing the user does have direct rendering enable for their display :0 because xgl/compiz is non-functional without hardware acceleration and it sounds as if he/she's got it working.

Xv playback under xgl is the suckage.  Either use the x11 output driver of your video player, or follow this very hard to implement scheme by which Xgl is bypassed so Xv can be used:

[http://www.compiz.net/viewtopic.php?pid=11827#p11827](http://www.compiz.net/viewtopic.php?pid=11827#p11827)

---

### Post by Ziox on 2006-08-21
> **peabody said:**
> Direct rendering does NOT show up even when enabled in Xgl because xgl is a hack.  It's basically something that gets grafted on top the xserver.  I'm guessing the user does have direct rendering enable for their display :0 because xgl/compiz is non-functional without hardware acceleration and it sounds as if he/she's got it working.

Xv playback under xgl is the suckage.  Either use the x11 output driver of your video player, or follow this very hard to implement scheme by which Xgl is bypassed so Xv can be used:

[http://www.compiz.net/viewtopic.php?pid=11827#p11827](http://www.compiz.net/viewtopic.php?pid=11827#p11827)

from the commands and outputs the user has provided, it clearly says that ```
direct rendering: No
```

---

### Post by peabody on 2006-08-21
```
name of display: :1.0
```

Trust me, under xgl it will tell you that direct rendering isn't enabled.  I'll bet $10 that if the user logs into a non-Xgl session glxinfo will say direct rendering: yes.  You don't understand how Xgl works.  It's basically one big Window that's running ontop of display :0.  Display :0 has direct rendering which is what xgl uses.  Display :1 doesn't because it's Xgl's internal display surface.

---

### Post by Ziox on 2006-08-21
> **peabody said:**
> ```
name of display: :1.0
```

Trust me, under xgl it will tell you that direct rendering isn't enabled.  I'll bet $10 that if the user logs into a non-Xgl session glxinfo will say direct rendering: yes.  You don't understand how Xgl works.  It's basically one big Window that's running ontop of display :0.  Display :0 has direct rendering which is what xgl uses.  Display :1 doesn't because it's Xgl's internal display surface.

Alright, I trust you, since I never tried running xgl before...I was just wondering....

---


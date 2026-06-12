---
title: "no sound and slow video after hibernate"
date: 2006-06-12
forum: Desktop Environments
---

### Post by megamania on 2006-06-12
Today I had the bad idea of testing hibernation on my pc. I had never tested it before, neither on windows nor on linux. Dapper didn't really like it. :-|

The system apparently hibernated, but when I restarted it all I got was a messy screen. After 30 seconds, the system rebooted by itself and the familiar ubuntu logo appeared.

Unfotunately, I have two problems now:
1) my ATI 9000 video card works slowly (I mean, even slower than usual). When I run glxgears, sometimes the gears start rolling quickly, but after two or three seconds they slow down. Most of the times they're just slow though, and I get around 180 fps (it used to be 1200 fps).

This is what I get with LSPCI:

```

g@desktop:~$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)

```

2) I have no sound. I tried System -> Multimedia Systems Selector (not sure that's the appropriate translation in english)  and I have ALSA output with "alsalink" pipeline. I tried ESD and OSS as well, with no results.

Can anybody please help me? I don't want to reinstall my system, but have no idea what to check/do to fix this!

---

### Post by megamania on 2006-06-12
regarding the problem with the video card, here the output of glxinfo:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

```
Also, I just noticed that the graphical splash boot screen disappears after a few seconds and I get the old text mode.

should I just follow the wiki howto and install the ATI drivers again? and what about sound?

anybody please?

---

### Post by megamania on 2006-06-13
Sorry for bumping this, but I really do need some help.

I'm wondering if I can just re-install the ATI drivers following the wiki guide, and regarding the sound issue I have no clue.

Dapper is my only O.S., so if I can't solve the problem I'll be forced to make a clean install and won't be able to work on my computer for a while.

Once again, sorry for re-posting here, but these forums are my only source of help.

---


---
title: "Compiz Fusion works fine, just not the cube"
date: 2007-10-03
forum: Desktop Effects &amp; Customization
---

### Post by wiberg on 2007-10-03
Hi,

I have Compiz Fusion set up just fine, everything works except for all plugins that use multiple desktops, like expo and cube.
It is not a 'horizontal virtual size' issue!
I'm running on Ubuntu 7.04 with an ATI X1300, fglrx and xgl. I installed CF using the amaranth repositories (I updated from a perfectly smooth running Compiz where the Cube and everything else was working).
When I try to activate the cube in CCSM, CF will stop and the session will fall back to a regular X session (no error messages).
Doing compiz --replace trashes everything, i get "Wnck-WARNING **: Unhandled action type (nil)", I loose the window borders (Emerald, btw) and all basic GUI functionality.
CF runs on startup. Just to give you as much information as possible, here is glxinfo (note that direct rendering is off, but remember, the cube worked with compiz):

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
OpenGL renderer string: Radeon X1300 / X1550 Series
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

plus, a screenshot of synaptic, showing all the CF packages that are installed (see attachment).
I am happy to provide any additional information as quickly as possible.


maybe somebody knows :)
thanks!
wiberg

---

### Post by wiberg on 2007-10-03
The good ol' uninstalling - reinstalling routine worked out very well. Now everything works as expected. Sorry!

---


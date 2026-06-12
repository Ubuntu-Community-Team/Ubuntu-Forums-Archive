---
title: "Odd OpenGL problem with fglrx w/ Dual screen"
date: 2006-08-23
forum: Desktop Environments
---

### Post by johnsd8 on 2006-08-23
I'm running a 3200x1200 desktop on an ATI X600 PRO card, using the 8.27.10 drivers.

Whenever I run an OpenGL app, everything is shifted offscreen to the left by about 500 pixels or so. In other words, I cant see the left side of the graphics, no matter where I put the window on my desktop. I can make the full window appear by dragging the horizontal size of the window to be larger than 2000px. 
I've attached two screenshots to demonstrate. The first is with a small window - you can just see the tip of the 'spinning cube' of glxgears on the left side of the window. In the second screenshot, I've made the window huge, and everything displays fine.

I've treid making various changes to my xorg.conf file, to no avail. I've tried several versions of the fglrx drivers (the last 4 or 5 versions) none of which made any difference.

Using Mesa works just fine - but this isn't a sufficient fix, I do a bit of graphics work. Any ideas? My xorg.conf file is attached as well.

[5020] glxinfo
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 PRO Generic
OpenGL version string: 2.0.5946 (8.27.10)
...

---

### Post by johnsd8 on 2006-08-24
anyone? I'm about out of ideas.

---


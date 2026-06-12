---
title: "xgl configuration madness"
date: 2006-08-07
forum: Desktop Environments
---

### Post by netdur on 2006-08-07
I did read this page [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389) to enable XGL on my computer, I have p4 3 ghz, 1 gb ram, asus a9250 (ati 9250) 128 ram

at first it ran fine, but after re-install I had some madness I can't understand, as normal session "glxinfo" command out put this

...
direct rendering: Yes
...
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
...

but loggin with XGL it become so slow, and shows 100% cpu usage by XGL and then "glxinfo" command out put this

...
direct rendering: No
...
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
...

I have no idea what went wrong, and how configuration changes on fly! please help

---

### Post by Anduu on 2006-08-07
Your output should look like this...

```
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
[COLOR="Red"]OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```[/COLOR]

You need to get your ati driver installed correctly...note the red highlights...

See here for the fix...[http://www.ubuntuforums.org/showthread.php?t=143283&highlight=fix+mesa](http://www.ubuntuforums.org/showthread.php?t=143283&highlight=fix+mesa)

---


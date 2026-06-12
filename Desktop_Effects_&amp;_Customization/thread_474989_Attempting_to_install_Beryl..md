---
title: "Attempting to install Beryl."
date: 2007-06-15
forum: Desktop Effects &amp; Customization
---

### Post by Tekee on 2007-06-15
I'm following some tutorials online, but I can't seem to get glx direct rendering to turn "on" (ATI graphics card).

Is there some sort of elaborate tutorial that can help me with Beryl?

---

### Post by overdrank on 2007-06-15
> **Tekee said:**
> I'm following some tutorials online, but I can't seem to get glx direct rendering to turn "on" (ATI graphics card).

Is there some sort of elaborate tutorial that can help me with Beryl?

HI which version of ubuntu Feisty , Edgy?
:popcorn:

---

### Post by skymera on 2007-06-15
[www.ubuntuguide.org](www.ubuntuguide.org)
that site tells you steb by step for beryl on ATI cards

---

### Post by Hobo Joe on 2007-06-15
Direct rendering is not related to Beryl, however, direct rendering is a must if you want to run Beryl. 

You must no have drivers properly installed, try [Envy]("http://www.albertomilone.com/nvidia_scripts1.html").

Also, post the output of:
```

glxinfo

```

---

### Post by Tekee on 2007-06-15
I'm currently using Fesity - 7.0.4...and here is the log you requested

```
bobby@bobby-desktop:~$ glxinfo
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x43 32 tc  1  0  0 c  .  
```

Also, I attempted following the ubuntuguide.org site, but when I tried to:

```
"Step 1 : Edit your sources.list file adding

deb http://ubuntu.beryl-project.org feisty main"
```

do that, I got an error that said it is out of date (I was using the Software Sources from system>admin):

"W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA"

Sorry for the long response, but thanks in advance :)

---

### Post by Tekee on 2007-06-15
Bump

---

### Post by overdrank on 2007-06-15
> **Tekee said:**
> Bump

Hi this is the link I used and worked great. Good luck!:popcorn:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

### Post by Tekee on 2007-06-15
> Hi this is the link I used and worked great. Good luck!
[http://www.howtoforge.com/ubuntu_fei...ryl_ati_radeon](http://www.howtoforge.com/ubuntu_fei...ryl_ati_radeon)

Yeah, I was also trying that one earlier.
I got to getting direct rendering to enable, but it doesn't seem to work.

(direct rendering: Yes) <---- what it's supposed to say...mine says 'no'

---

### Post by freshmeatz on 2007-06-21
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

this is a problem

mine is

fresh-Beryl:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
snipped

---


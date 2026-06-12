---
title: "Beryl?"
date: 2007-04-14
forum: Desktop Effects &amp; Customization
---

### Post by Gorthus on 2007-04-14
I just got Beryl, and everything installed right, but I have no clue what to do...

Can anyone post a simple howto to get started and all that?

I'd really like to get this working :)

---

### Post by DoubleQuadword on 2007-04-14
To run Beryl just type (in a terminal):

```
beryl-manager
```

If you want to start Beryl at system startup go to: 
System >> Preferences >> Sessions >> Startup Programs (tab), then click 'Add' and type the above command there.

Regards.

PS: You should see a red diamond in the notification area when Beryl is active.

---

### Post by Gorthus on 2007-04-14
Yep, thanks...

But there's a problem.. None of the key commands from the first-time-user thingy are working... Everything is exactly the same as before beryl.

---

### Post by DoubleQuadword on 2007-04-14
> **Gorthus said:**
> Everything is exactly the same as before beryl.

You need to change the Window manager from **Metacity** (Gnome) to **Beryl**. To do so just 'right-click' on the red diamond, (I'm supposing you can see it), then look for a sub-menu called "Select Window Manager" and finally select Beryl.

Regards.

---

### Post by Gorthus on 2007-04-14
Ah, thanks! :)

---

### Post by Gorthus on 2007-04-14
Wait what... I just checked and it had itself set back to metacity... When I select Beryl it twitches between workspaces 2 or 3 times and then stops and is set to metacity again...

Did I do something wrong?

---

### Post by DoubleQuadword on 2007-04-14
You're quite welcome.

Regards.

---

### Post by Detonate on 2007-04-14
When you get it running, open this link in yur browser and bookmark it.  I kept it on my bookmark toolbar until I was used to using Beryl.

[http://wiki.beryl-project.org/wiki/Tips/Default_Commands](http://wiki.beryl-project.org/wiki/Tips/Default_Commands)

---

### Post by Gorthus on 2007-04-14
Heh... Look at the post above.

---

### Post by DoubleQuadword on 2007-04-14
> **Gorthus said:**
> Wait what... I just checked and it had itself set back to metacity... When I select Beryl it twitches between workspaces 2 or 3 times and then stops and is set to metacity again...

Did I do something wrong?

I don't think you actually did something wrong. This could be an error, in those cases Beryl automatically switches to **Metacity** again because it's configured by default as the fall-back window manager. Try to login anew. (Before doing that, in case you've added Beryl to your startup programs, disable its entry; doing so helps preventing some ugly issues).

Regards.

PS: Just to be sure, did you install 'emerald-themes' along with 'Beryl'?
Here's a complete official installation guide: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

---

### Post by Gorthus on 2007-04-14
I just did [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI)

Everything in there... That's it.


EDIT: By the way, my Terminal, nor my Shut Down, button work any more... When I hit terminal it says "starting terminal" but then nothing happens... WHen I hit the shut down button nothing happens at all.

---

### Post by Gorthus on 2007-04-15
24-hour bump...

Can anyone help me?

---

### Post by 00arthuryu on 2007-04-17
are you sure you installed the graphic drivers correctly??
can you post what comes up if you enter
```

glxinfo

```
into terminal?

---

### Post by Gorthus on 2007-04-17
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
OpenGL renderer string: RADEON X800 GTO
OpenGL version string: 1.2 (2.0.6334 (8.34.8))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon

```

---

### Post by 00arthuryu on 2007-04-17
hmm.. the shutdown button maybe to do with your startxgl file
```

sudo gedit /usr/bin/startxgl

```
or depending on which one you saved it as
```

sudo gedit /usr/bin/startxgl.sh

```
should look like
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```
i'm sure your terminal bug will be sorted by doing a restart, beryl is quite buggy and crashes most of the time even when doing 'normal' stuff. just gotta accept it really XD

---

### Post by memos on 2007-04-19
how to install themes on berryl?:( :(

---


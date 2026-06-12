---
title: "XGL stops working after reboot"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by virgilnilson on 2007-05-27
It seemed like the text in FF was a little blurry so I searched around and saw that someone said installing the msttfonts package helped them. So I used synaptic to install the package and it seemed worse, so I uninstalled it using synaptic and the text didn't seem to change so I rebooted.

When I logged in again suddenly, I'm not sure how to describe it but it looked like everything had been through a cheese grater. Basically it was just a mess of jagged lines and I could just barely make out the larger shapes and so was able to log back out.

The login screen is fine, and gnome by itself is fine. I tried to update XGL but it says that it has the latest version.

Any ideas on what could have possibly happened? =/

EDIT: Running an ATI x850.

---

### Post by Crafty Kisses on 2007-05-27
This is happened to me before, it's like little specs of rainbow colors, Here's the shot.
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-1-1.png[/IMG]



In some cases it can be a lot worse, this is a mild case of that problem.
That's usually caused by a corrupt driver file. You should have backed up your Xorg.conf file. The worst thing that could of happened is a hardware issue, possibly a loose wire, or your video card is not plugged in properly, update me, so I can look into this further.

---

### Post by virgilnilson on 2007-05-27
Here's a picture of what I'm experiencing. It does not appear to be a loose wire as it only appears like this when I start an XGL session. 

[IMG]http://img91.imageshack.us/img91/1628/screenshotcn7.png[/IMG]

---

### Post by Crafty Kisses on 2007-05-27
This definatley looks like it can be 1 of two things.

1. A hardware issue, which could be anything to your video card, to your video card memory. Just to be sure i'd check the plug-points, or replace them, and also make sure your video card is firmly plugged in, and also make sure your computer is free of dust. One question I have to ask is there any over-heating issues with your computer?

2. A driver issue, which can be solved by going to your video card manufacturer website and downloading the appropiate drivers. Which I have so much troubles doing myself, I stopped trying. But hey you can give it a shot.

Also can you please give me your "glxinfo".

---

### Post by homergreg on 2007-05-27
I'll bet something in the uninstall messed up your ATI driver or some dependent package.  Login under Gnome without XGL and check the restricted driver manager area.  Does it say that the ATI accelerated driver is enabled but not in use?  

I got in a similar situation, and ended up with xwindows messed up while trying to fix it, so be sure and back up your xorg.conf file before trying to fix it!

---

### Post by virgilnilson on 2007-05-27
Okay so I just spent all this time uninstalling and reinstalling fglrx, and now XGL seems to be working again except even after typing

```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```

which would work BEFORE to enable the cube, the cube will not work. Everything else seems to be fine however.

```
glxinfo
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
OpenGL renderer string: RADEON X850 XT Platinum Edition
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

---

### Post by virgilnilson on 2007-05-27
It was working an hour ago, then I uninstalled a font package and that seemed to have wrecked my video drivers so I uninstalled and reinstalled fglrx. Now XGL works again but for some reason the cube doesn't.

I tried doing 

```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```

which would previously work like a charm, but now absolutely nothing happens when I enter those commands.

---

### Post by icechen1 on 2007-05-27
Is the cube option is enabled in Desktop Effects?

---

### Post by joe.turion64x2 on 2007-05-27
Which graphics card are you using? Which method, AIXGL or XGL?

---

### Post by virgilnilson on 2007-05-27
> **icechen1 said:**
> Is the cube option is enabled in Desktop Effects?

Yes, it is. I have even checked and unchecked it to no avail. =/

---

### Post by virgilnilson on 2007-05-27
> **joe.turion64x2 said:**
> Which graphics card are you using? Which method, AIXGL or XGL?

ATI x850 and I am using XGL.

---

### Post by virgilnilson on 2007-05-27
I seem to have fixed the cube problem by first disabling the cube, then right clicking the desktop switcher and adding four desktops, then enabling the cube.

---

### Post by joe.turion64x2 on 2007-05-27
Don't forget to lock Beryl's installed version because if you update them you'll most likely loose your beautiful 3D desktop.

---

### Post by Crafty Kisses on 2007-05-27
To be honest your glxinfo looks ok, to be honest at this point you might want to check your plug points, or optimize your OS, I really can't say at this point. Possibly make sure all the effects are enabled, is there anyway when it glitches you can give me the log?

---

### Post by virgilnilson on 2007-05-28
> **Codename said:**
> To be honest your glxinfo looks ok, to be honest at this point you might want to check your plug points, or optimize your OS, I really can't say at this point. Possibly make sure all the effects are enabled, is there anyway when it glitches you can give me the log?

Heh, you saw what it looks like when it glitches. I can barely navigate to the power button and log off when that happens.

So far all day I haven't had any more problems, XML has been working and all the display tricks have been working as well.

---

### Post by jkwarras on 2007-05-28
It seems that you doesn't have DRI enabled. I experienced the same problem in my system with fglrx drivers and XGL. Be sure that fglrxinfo doesn't have a problem loading your drivers and that it doesn't said MESA instead of ATI.

---


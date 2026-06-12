---
title: "[Help] Beryl, Ubuntu, Cant apply themes"
date: 2007-04-06
forum: Desktop Effects &amp; Customization
---

### Post by PtOs on 2007-04-06
Info: Im using the latest version/release of ubuntu! Im running an ATI gfx card, with the latest drivers (i assume this, as it told me that it would install the latest ATI drivers when i installed Beryl)

However, im having serious trouble applying themes. When i double click on the theme in the "theme manager" absolutely nothing happens. 

I've previously had Beryl installed, although with a wrong "version" (nvidia or something else) (i dont have a clue of what was wrong) since it actually worked. I double clicked and swoosh a new theme. 

I've done a bit of research and came up with quite a few errors with the "gnome-settings-deamon" which apparently often fails to load/crash with the use of ATI and XGL gfx cards (or drivers?)


As i now read this through now, i realize that it may seem like nonsense to pretty much anyone than myself. And the reason is either my inability to use the english language (im from denmark) or just the fact that i really have no clue of what to make of these problems.

Any help will be greatly appreciated!!!! (!)

---

### Post by lazyrussian on 2007-04-06
After you highlight the theme you want, make sure you right click the beryl icon and hit reload window manager (or something of that nature).

---

### Post by PtOs on 2007-04-06
thanks for your answer!

but im afraid that it didn't help me much! I tried doing what you said, and it didn't help at all. Another thing is, that none of the extras work, wobbly windows, or the rain effect. :(

i think i need help running the deamon settings thing..

---

### Post by lukew on 2007-04-06
> **PtOs said:**
> thanks for your answer!

but im afraid that it didn't help me much! I tried doing what you said, and it didn't help at all. Another thing is, that none of the extras work, wobbly windows, or the rain effect. :(

i think i need help running the deamon settings thing..

i had this problem; also i did not have the min/max buttons on my windows. Turns out there was a few little lines required in the xorg.conf file.

[HTML]http://ubuntuguide.org/wiki/Ubuntu_Edgy[/HTML]
```


There is the following section:

    * Add this to xorg.conf "Screen" section 

# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
    Option "DisableGLXRootClipping" "True"

    * Add this to xorg.conf "Device" section 

Option          "TripleBuffer" "true"

```


Basically for me there was two sets of instructions under UDSF. The EYE Candy Extraordinare and the item in the Start Here First Section. The first, which I followed, did not have the part above, which is detailed in the second.

The rain and snow require pixel shading; some older cards do not support this.

With respect to the wobbly windows; are you sure emerald/beryl is running and that you have 3d graphics set up?

Hope this helps you.

Luke

---

### Post by lukew on 2007-04-06
> **PtOs said:**
> Info: Im using the latest version/release of ubuntu! Im running an ATI gfx card, with the latest drivers (i assume this, as it told me that it would install the latest ATI drivers when i installed Beryl)

Beryl does not install this. Are you sure you installed 3D drivers? What steps did you take?

---

### Post by PtOs on 2007-04-06
thanks guys... 

all these questions are really confusing me... cause i've only been using Ubuntu (linux) for a few days.. i dont even now how to add these lines to that config file (i've found the file)

about these graphic drivers.. well no idea.. 

i followed these steps 

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI)

whats really weird is that when i yesterday night (or so) installed a "wrong version" "everything" seemed to work.. and im not just stupid, im quite sure that im running with an ATI gfx card..

i thought these steps (the linked tut) would provide me with everything i needed, thus make it alot easier for me, as a noob! but ohh no...

---

### Post by lukew on 2007-04-06
> **PtOs said:**
> thanks guys... 

all these questions are really confusing me... cause i've only been using Ubuntu (linux) for a few days.. i dont even now how to add these lines to that config file (i've found the file)

about these graphic drivers.. well no idea.. 

i followed these steps 

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI)

whats really weird is that when i yesterday night (or so) installed a "wrong version" "everything" seemed to work.. and im not just stupid, im quite sure that im running with an ATI gfx card..

i thought these steps (the linked tut) would provide me with everything i needed, thus make it alot easier for me, as a noob! but ohh no...

Did you run the script? That should install drivers.

Try in the terminal;

```
glxgears
```

Do you get some magic gears or do you get some debug into the terminal?

---

### Post by PtOs on 2007-04-06
im getting gears... so that means my gfx drivers are working properly..

on a note, they are not running smoothly..

---

### Post by lukew on 2007-04-07
> **PtOs said:**
> im getting gears... so that means my gfx drivers are working properly..

on a note, they are not running smoothly..

That does not sound too good.

Post the results of 

```
glxinfo

```

---

### Post by PtOs on 2007-04-07
```
phill@phill-laptop:~$ glxinfo
name of display: :0.0
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
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
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
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
phill@phill-laptop:~$
```

sorry had to make it short

thanks in advance, Phill

---

### Post by PtOs on 2007-04-07
uhmm hello?? 

Im still in urgent need of help.. :D

---

### Post by lukew on 2007-04-08
> **PtOs said:**
> uhmm hello?? 

Im still in urgent need of help.. :D

I do not believe that not being able to apply the themes is urgent; besides 15 hours is not long to wait for help. If I were you I would be more interested in installing 3D drivers to get beryl to work as aposed to worrying about themes:

From the following command
```
glxinfo | grep rendering
```

You should have:
```
direct rendering: Yes
``` 


You actually have
```
direct rendering: No
```

Good clear instructions can be found here:
[HTML]http://ubuntuguide.org/wiki/Ubuntu_Edgy[/HTML]

Luke

---


---
title: "3d desktop no direct rendering"
date: 2007-03-09
forum: Desktop Effects &amp; Customization
---

### Post by Recon20k on 2007-03-09
I cant seem to get 3d desktop working on my system. Can anyone help??
Maybe i haven't installed the proper drivers for my graphics card?? If so how do i do this? I'd really appreciate any help with this one.

**Here is my glxinfo**

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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x3c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

**and my class display**

 *-display:0             
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@01:00.0
       version: 00
       size: 256MB
       width: 64 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       configuration: driver=fglrx_pci
       resources: iomemory:c0000000-cfffffff iomemory:dfde0000-dfdeffff ioport:dc00-dcff irq:169
  *-display:1 UNCLAIMED
       description: Display controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@01:00.1
       version: 00
       size: 64KB
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:dfdf0000-dfdfffff

---

### Post by Jmccaffrey on 2007-03-09
What driver are you using for your video card? Many ATI cards do not have a properly supported driver.

---

### Post by Recon20k on 2007-03-14
i don't know what driver i'm using for my graphics card,.. how do i find out??

I was talking to some people here that were saying that the drivers for this particular card (ati) are not properly developed yet, so i guess ill just have to wait for software updates to fix the problem. 

I checked the ati website and they don't have any drivers that support ubuntu edgy operating system.

---

### Post by nevernamed on 2007-03-14
I'm also having a similar problem. I can't seem to get the 3d effects needed for beryl working on ubuntu 6.10

When I first installed, metacity wasn't installed correctly, so I had to reinstall that package because things like keyboard shortcuts, holding down keys until they repeated, etc didn't work.

The ubuntu desktop still isn't displaying 100% correctly for some reason but I think I'll live with it since I wanted to install beryl.

I was following the guide [HTML]<a href="https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html">here</a>[/HTML] and when I was told to restart xorg I did and then it wouldn't restart.

I've been messing around with getting 6.10 working properly for several days now and am getting very frustrated and tired. Any help from anybody would be really helpful.

Thanks.

---

### Post by PONGsiFU on 2007-08-01
I have the same type of problem, no direct rendering whatsoever.  Even when I countlessly reformat and freshly reinstall Ubuntu, the same problem shows up.  *This never happened before by the way*

Fglrx does not work, and besides Fglrx, for me, makes Beryl obsolete.  I need to stick with ALGLX.  I've tweaked the X11/xorg.conf file but didn't work.  

It would be nice if someone would relieve our pain, you can't do anything cool without direct rendering. and it sucks without it. no kiba-dock...no beryl...

---


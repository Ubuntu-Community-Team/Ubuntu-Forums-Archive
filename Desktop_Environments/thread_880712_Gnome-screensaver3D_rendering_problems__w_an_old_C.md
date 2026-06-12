---
title: "Gnome-screensaver/3D rendering problems  w/ an old Celeron machine"
date: 2008-08-05
forum: Desktop Environments
---

### Post by Glw8z on 2008-08-05
My problem involves the Gnome-screensaver in Xubuntu and 3D rendering (and the lack thereof). Xubuntu Hardy works on another machine (P4 1,7GHz, 512MB RAM, an old Nvidia card) with no screensaver/3D problems after installing the restricted driver. This troubled machine is even older, P3 Celeron 800 MHz, 320 MB RAM and an Intel 82815 card. The display shouldn't be to blame, as I have two identical 17" screens and have tried the P3 on both. Can it be up to the ancient processor that I can't have those 3D screensavers working, as RAM shouldn't be an issue (the P4 ran those screensavers even w/ 256 MB). Or does the problem lie with the integrated Intel video card? It looks to an untrained eye that the required x.org packages for my i815 chipset are installed, i.e. xserver-xorg-video-i810 & -video-intel. 

I've tried (with no change whatsoever in behavior) to remove gnome-screensaver (even purge it), reinstall it as well as install the xscreensaver package as an alternative. This is not a matter of life and death, but I'd like to know what lies at the core of this problem. Besides, I'd like to have a few games like Emilia Pinball w/ 3d on the P3 machine. Nothing ambitious, for sure. I don't intend to enable (or need, for that matter) Compiz or anything. Just to keep this humming Celeron buddy in tune and not moping in the dark.

Of the default screensavers, the following work: Deco, Distort, Fiberlamp, Floating Ubuntu, Floating Feet, Fuzzy Flakes, Galaxy, MetaBalls, Penrose, Ripples, Shade Bobs, SlideScreen, Sonar, Swirl, Universe, Xlyap and the Pictures folder. I know that's more than a few to choose from, but I wonder if the rest could be working too.

Here's my glxinfo as illustration. It's mainly gibberish to me, but isn't 3D rendering supposedly working there? If something's missing or amiss, I'd appreciate you pointing me in the right direction. I can provide more info too, so long as I know where to look and what to type. 

```
glxinfo:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Keith Whitwell
OpenGL renderer string: Mesa DRI i815 20050821 x86/MMX/SSE
OpenGL version string: 1.2 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_compression, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x25 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x26 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x27 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x28 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x29 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2a 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2b 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x2c 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x2d 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x2e 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x2f 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x30 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x31 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x32 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x4c 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

The final word: I don't plan on buying a new video card, should anyone suggest that. If this problem is solvable otherwise, brilliant; if not, that's life on the edge of cyberspace. Xubuntu works fine otherwise, so then I'll live w/o 3D - at least in the computer realm.

---

### Post by Glw8z on 2008-08-07
Is this hopeless? Am I the only one puttering around with such antiquated hardware? I've seen, while searching for some answer, lots of posts involving gnome-screensaver and its problems or bugs, but this can't be classified as a bug since the default screensavers work with the exception of those using 3D. The packages needed have been installed. 

I did notice, with a fresh pair of eyes, [COLOR="Blue"]Slow[/COLOR] in *glxinfo*, which probably indicates the troubles w/ 3D rendering. That just won't give me any insight into changing the settings or anything. 

If somebody came here to say I should stop dreaming of shuttling to the moon with a rickety biplane and keep my feet on the ground, I'd probably heed that advice. But now, I'm just floating in my sea of ignorance. 

I wonder if anyone'll come to my rescue or lead me in the right direction. That would definitely be appreciated.

---

### Post by Glw8z on 2008-08-09
It feels like I'm talking to empty walls here or shouting into the black hole of cyberspace, but I'd still like an answer or explanation of sorts. Sure there must be something I could do to explore this issue if only I knew what. 

Anyway, I've tried the glxgears too, with following results (both on the Celeron 800 and the functioning PIV):
The Celeron came back w/ ~259FPS in the test, but there was no 3D visible, no gears but all these whacky lines that even stretched beyond the glxgears window. In other words, there was no vertical component. This also happens w/ the installed 3D screensavers.

The PIV had about 246FPS, and (as expected) the gears appeared perfectly. 

What do the test results indicate? Is [COLOR="Red"]259FPS[/COLOR] better than [COLOR="Blue"]246FPS[/COLOR], and if so, why does the 3D fail to work? Processor or video card? 

Can I still do something (besides futile googling), or is it better to quietly vanish and drop such trivialities of dimensions?

---

### Post by bondo101 on 2008-08-09
Too new linux version for old celeron machine.Just think of win xp on old machine with small memory ammount . Try dam small linux on the celeron machine it might work better.
At lesst a gig of memory for ubuntu 8.04. and i know i will get arguments on this. try older versions of linux on older machines on older machines and be paitent  it takes time with linux.                                            bondo101

---

### Post by Glw8z on 2008-08-09
> **bondo101 said:**
> Too new linux version for old celeron machine.Just think of win xp on old machine with small memory ammount . Try dam small linux on the celeron machine it might work better.
At lesst a gig of memory for **ubuntu** 8.04. and i know i will get arguments on this. try older versions of linux on older machines on older machines and be paitent  it takes time with linux.                                            bondo101

No. [COLOR="Blue"]Xubuntu[/COLOR] Hardy works fine on the Celeron machine. Sure, it's not turbocharged, but the basic things work just fine. And memory, however small at the moment, isn't that big an issue, really. I can use OOo Writer, GIMP and Firefox (well, not at the same time :)) without any problems. I am patient as well. 

Second, the other machine I've installed Xubuntu Hardy on has 512MB RAM, and it runs really well. One of the main reasons why I picked Xubuntu rather than Ubuntu.

My only issue is finding out why 3D rendering, although supposedly working based on glxinfo, fails to work. Whether it comes down to the processor or the limitations of the video card or some other factor I can't address on my own.

---

### Post by Glw8z on 2008-08-12
It's the bloody Intel card that won't play with me. No, I didn't solve it with my nonexistent terminal skills, though I tried to tinker with xorg.conf, all to no avail. So I grabbed a pre-millennial 16MB Diamond video card off a crappy Pentium and plugged it in. Install the restricted driver *nvidia-glx-legacy*, alter the resolution that first reverted to 640x480, ```
sudo dpkg-reconfigure -phigh xserver-xorg
```, then reinstall the driver, restart, and *voilà*, *direct rendering: yes* and glxgears appears normal. All screensavers work fine now, and even the pinball game runs w/o problems. This new/old card even has 24bit capabilities compared to the Intel's 16bit, and no *Slow* caveats in glxinfo. 

So bye-bye, open-source driver and onboard video card. Much as I'd like to use those, if it's such a hassle for an inexperienced keyboarder w/o helpful assistance, screw it :tongue:. Well, that's it, folks.

---

### Post by woaibbhemm on 2008-08-12
hello~
      nice    to   meet  you .thank you   for   your  sharing    and  welcome   to  our   website ~










Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by DyBurke on 2008-10-23
Damnit.  I had the same problem. T_T  I don't have another video card.  Lame how people wont try to help. wtf  I'm sure somebody is good enough with linux to give us a general direction.

---


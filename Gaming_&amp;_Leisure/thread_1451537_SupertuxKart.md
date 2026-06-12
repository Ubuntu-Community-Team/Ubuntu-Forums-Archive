---
title: "SupertuxKart"
date: 2010-04-10
forum: Gaming &amp; Leisure
---

### Post by Tux118 on 2010-04-10
What Comes with Ubuntu, won't load no matter what I do, but seems like a really great game? 

Can someone tell me how to get this thing to load?

Thank You,

Tux 118

---

### Post by Noraphalem on 2010-04-10
> **Tux118 said:**
> What Comes with Ubuntu, won't load no matter what I do, but seems like a really great game? 

Can someone tell me how to get this thing to load?

Thank You,

Tux 118

What version of SuperTuxKart do you have installed?

What happens after the start?

Start the game via terminal and post terminal output.

How to start a program via terminal and get the terminal output:

1. Open a terminal ([Alt] + [F2], Type in "gnome-terminal", Press [Enter])
2. Type in "supertuxkart" and press [Enter].
3. Mark all the terminal output via mouse.
4. Click with the right mouse button into the terminal and click "Copy".
5. Paste it.

---

### Post by Tux118 on 2010-04-10
Alright, when I try and run it, this is what happens: 

Data files will be fetched from: '/usr/share/games/supertuxkart/'
Config file '/home/ethan/.supertuxkart/config' does not exist, it will be created.
Highscores will be saved in '/home/ethan/.supertuxkart/highscore.data'.
FATAL: ssgInit called without a valid OpenGL context.


I think I need OpenGL or something. Can you help me with this error?

I am not sure about the version, but it is Supertuxkart, not Tuxkart.

---

### Post by Noraphalem on 2010-04-10
> **Tux118 said:**
> Alright, when I try and run it, this is what happens: 

Data files will be fetched from: '/usr/share/games/supertuxkart/'
Config file '/home/ethan/.supertuxkart/config' does not exist, it will be created.
Highscores will be saved in '/home/ethan/.supertuxkart/highscore.data'.
FATAL: ssgInit called without a valid OpenGL context.


I think I need OpenGL or something. Can you help me with this error?

I am not sure about the version, but it is Supertuxkart, not Tuxkart.

How did you install SuperTuxKart?
Package Manager (Synaptic Package Manager or Software-Center) or manually?

The current version of SuperTuxKart is *0.6.2+dsfg1-1*. On Ubuntu 9.10.

If you installed it via Package Manager the dependencies should all be installed too.

What GPU is in your machine? Perhaps this is the reason of the malfunction. It needs 3d hardware acceleration.

And you need a propritary graphics driver (ATI/AMD or Nvidia).

---

### Post by Tux118 on 2010-04-10
> **Noraphalem said:**
> How did you install SuperTuxKart?
Package Manager (Synaptic Package Manager or Software-Center) or manually?

The current version of SuperTuxKart is *0.6.2+dsfg1-1*. On Ubuntu 9.10.

If you installed it via Package Manager the dependencies should all be installed too.

What GPU is in your machine? Perhaps this is the reason of the malfunction. It needs 3d hardware acceleration.

And you need a propritary graphics driver (ATI/AMD or Nvidia).

I have an old chasi, or whatever they call them nowdays. About 5 years old. 

Supertuxkart came with my system. 

I don't think I have a graphics driver, so I don't think this game will work. :(

Do you know any other similar games for linux or ubuntu?

Thanks!

- Tux118

---

### Post by Sockerdrickan on 2010-04-10
Get a graphics driver then! :) Do check in the system > administration menu

---

### Post by Tux118 on 2010-04-10
> **Sockerdrickan said:**
> Get a graphics driver then! :) Do check in the system > administration menu

A virtual driver or a physical driver? 

Sorry, I am new to ubuntu. Only my 2nd year.

---

### Post by Noraphalem on 2010-04-10
> **Tux118 said:**
> A virtual driver or a physical driver? 

Sorry, I am new to ubuntu. Only my 2nd year.

There is a tool (Hardware driver) in the system administration menu. Isn't it?

---

### Post by Tux118 on 2010-04-10
> **Noraphalem said:**
> There is a tool (Hardware driver) in the system administration menu. Isn't it?

Yes, I found the program. The only hardware that shows up is my network card. 

Do you think I might have to buy a graphics card to get the game to work?

---

### Post by Sockerdrickan on 2010-04-11
> **Tux118 said:**
> Yes, I found the program. The only hardware that shows up is my network card. 

Do you think I might have to buy a graphics card to get the game to work?
Yes that might be the case ;-)

---

### Post by Tux118 on 2010-04-11
> **Sockerdrickan said:**
> Yes that might be the case ;-)

Alright, I will buy a graphics card and see if that gets it to work.

Thank You!!

- Tux118

---

### Post by jombra on 2010-04-11
Not that this is the case here - but if you would have an Intel Centrino Chipset
common in laptops you would also not see any driver - but Intel´s GMA chipset
graphics would work if you habe installed the game via synaptics.
It´s OpenGL performance should be sufficient for a game like supertuxkart
and on the command line you may see starting it (<user> being your user name):
-
Data files will be fetched from: '/usr/share/games/supertuxkart/'
Config directory '/home/<user>/.supertuxkart' successfully created.
SDL_LoadWAV() failed to load /usr/share/games/supertuxkart//data/sfx/horn.wav
New highscore file '/home/<user>/.supertuxkart/highscore.data' created.
-

---

### Post by efikkan on 2010-04-11
Please enter "glxinfo" in terminal and post the output.

---

### Post by Tux118 on 2010-04-11
> **efikkan said:**
> Please enter "glxinfo" in terminal and post the output.

Alright, if it will help:

 glxinfo
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
OpenGL version string: 1.2 Mesa 7.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_compression, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
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

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x22 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x3c 32 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None

16 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x3d  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x3e  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x3f  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x40  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x41  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x42  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x43  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x44  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x45  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x46  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x47  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x48  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x49  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x4a  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x4b  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x4c  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow

How can this help me....

---

### Post by efikkan on 2010-04-11
That tells me wich gpu and driver you got.

I've been looking trough the source code and the error message is caused by OpenGL wich has failed to load. Have you tried any other games wich uses SDL?

Does glxgears run?

---

### Post by Tux118 on 2010-04-11
> **efikkan said:**
> That tells me wich gpu and driver you got.

I've been looking trough the source code and the error message is caused by OpenGL wich has failed to load. Have you tried any other games wich uses SDL?

Does glxgears run?

No, I haven't tried any games that use SDL. 

GLX Gears runs perfectly.

---

### Post by efikkan on 2010-04-11
It's hard to find games running in old OpenGL 1.2, wich I suspect might be the problem.

Other [SDL games]("http://en.wikipedia.org/wiki/List_of_games_using_SDL").

Unfortunately I don't know of any SDL test tools.

---

### Post by Tux118 on 2010-04-12
> **efikkan said:**
> It's hard to find games running in old OpenGL 1.2, wich I suspect might be the problem.

Other [SDL games]("http://en.wikipedia.org/wiki/List_of_games_using_SDL").

Unfortunately I don't know of any SDL test tools.

Alright, I looked at the list and saw that supertux was on there. I have been playing supertux for a long time!

---

### Post by Arthur_D on 2010-04-12
What version of SuperTux are you using? SuperTux 0.1.3 or 0.3.1?

---

### Post by efikkan on 2010-04-12
It might be a driver bug then.

---

### Post by Tux118 on 2010-04-14
Okay when I was upgrading my Hardy Heron to Intreiped, a power outage came and I was in the middle of an upgrade so everything got messed up. Luckily, I had all of my data backed up to a different hard disc so I could safely re-install Karmic over my crashed system. Karmic didn't come with supertuxkart like Hardy did. I am going to install via synaptic and see if that gets it to work.

---

### Post by Tux118 on 2010-04-14
Yep, I just inststalled and.....

It works!

Thank you everyone for your efforts, it means a lot to me!

---

### Post by Arthur_D on 2010-04-14
Great to hear!
Next version (0.7) will be even better, with the change of 3D engine, new GUI, new features, tweaks and a lot of new bugs. ;)

---

### Post by Noraphalem on 2010-04-15
No problem.

---

### Post by su-37 on 2010-07-08
Hey just downloaded STK and love it. How do i add new tracks and karts? i try navigating to the usr/share/games/..../karts but it says i dont have permission even when i am root.

---

### Post by Arthur_D on 2010-07-09
Hmm, that should do the trick... you should be able to do whatever you want in these folders if you are root. Let me try a guess: you copied from Nautilus non-root to Nautilus root. That won't work. Try using Nautlius as root both when you copy the file(s) and when you paste it/them.

---

### Post by su-37 on 2010-07-09
I became root. Opened the karts download and copied it to the karts folder still same result.

---

### Post by pme 72 on 2010-08-13
I was able to add tracks and karts by changing the file permissions on the folder SuperTuxKart and copying the downloaded files to their respective folders, Tracks and Karts. I changed the permissions to 777: Read, write and execute permissions for Owner, Group and Other. 

Not sure if it was necessary but I tried to change the permissions back when I was done. Not sure what they were originally. I changed them back to 555: Read and execute permissions for all. That seemed to work.

---

### Post by rudysuryanto on 2012-02-07
I have a similar problem, can not play supertuxkart


rudy@rudy-P4M800PRO-M:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 7.11
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_copy_texture, GL_EXT_polygon_offset, GL_EXT_subtexture, 
    GL_EXT_texture_object, GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, 
    GL_EXT_texture, GL_EXT_texture3D, GL_IBM_rasterpos_clip, 
    GL_ARB_point_parameters, GL_EXT_draw_range_elements, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_separate_specular_color, GL_EXT_texture_edge_clamp, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_ARB_texture_env_add, 
    GL_ARB_transpose_matrix, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, GL_EXT_texture_lod_bias, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_compression, GL_MESA_window_pos, 
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_APPLE_packed_pixels, GL_ARB_draw_buffers, 
    GL_ATI_draw_buffers, GL_EXT_stencil_wrap, GL_ARB_vertex_buffer_object, 
    GL_OES_read_format, GL_EXT_texture_env_combine, GL_ARB_copy_buffer, 
    GL_ARB_robustness

24 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x05b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x05c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x05d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x05e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x05f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x060 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x061 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x062 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x063 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x064 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x065 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x066 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x067 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x068 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x069 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x06a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x06c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x06d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x042 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 Ncon

24 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x043 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x044 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x046 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x047 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x049 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x04a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x04b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x04c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x04d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x04e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x04f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x051 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x053 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x056 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x057 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x058 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x059 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x05a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  137 (XFree86-DRI)
  Minor opcode of failed request:  9 ()
  Resource id in failed request:  0x4600004
  Serial number of failed request:  44
  Current serial number in output stream:  44

What should I do, so I can play supertuxkart? thanks?

---


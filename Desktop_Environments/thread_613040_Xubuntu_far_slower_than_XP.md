---
title: "Xubuntu far slower than XP"
date: 2007-11-14
forum: Desktop Environments
---

### Post by revolutio on 2007-11-14
Currently have a dual boot of Xubuntu and Windows XP (too lazy to try and make games work on Linux).  Instead of the noted speed increase I expected I found a profoundly slower operating system.  Video stutters, loading thumbnails takes longer than drawing them manually in MS Paint, running multiple applications (read: two) makes my CPU cry, menus are a tedious and time consuming process of waiting for each branch to open, even downsizing windows of any kind is slow.  I'm not sure what other information to post about my problems with this "lightweight" operating system.  XP is The Flash compared to this.

My system specs in case some of you were thinking that this sounds like I am trying to run it on a Commodore 64:
AMD Athlon 64 3400+
1 Gb DDR 3200 RAM
ATI Radeon 9800 Pro

Xubuntu 7.10 running on a 10,000 rpm Raptor hard drive

So, I don't know what else to toss to you guys.  I'm all ears.

---

### Post by louieb on 2007-11-14
I have Ubuntu and XP dual booting on 3 PCs from a P II 400 384MB memory to a P4 Dual core 3.1GHZ 1GB memory. The speed on those machines is about the same except Ubuntu boots faster. The P II and the P4 have low end nVidia cards (FX5200 and 7300GT).  

I suspect its your ATI video card. See posts  all the time  about speed problems w/those cards.   

:guitar: There is one distro that I put on the P II that blows xUbuntu and XP away.  Actually has turned it into more that just a play thing to test stuff on. [PCFluxboxOS]("http://pcfluxboxos.wikidot.com/") Might try it if runs or should I say walks like an old dog too:  Then I'd guess its the video card.

---

### Post by revolutio on 2007-11-14
> **louieb said:**
> I have Ubuntu and XP dual booting on 3 PCs from a P II 400 384MB memory to a P4 Dual core 3.1GHZ 1GB memory. The speed on those machines is about the same except Ubuntu boots faster. The P II and the P4 have low end nVidia cards (FX5200 and 7300GT).  

I suspect its your ATI video card. See posts  all the time  about speed problems w/those cards.   

:guitar: There is one distro that I put on the P II that blows xUbuntu and XP away.  Actually has turned it into more that just a play thing to test stuff on. [PCFluxboxOS]("http://pcfluxboxos.wikidot.com/") Might try it if runs or should I say walks like an old dog too:  Then I'd guess its the video card.
Have had another thread going in the multimedia forum about that.  I've done pretty much every thing imaginable to my video card with no success.  It is certainly fine structurally since it handles gaming quite well under XP.  Having exhausted my options there I have become inclined to believe that the video lagging is just a facet of an overall problem with the speed of Xubuntu.

---

### Post by DyDx on 2007-11-14
Xubuntu doesn't use compositing effects by default, so are you? 

If you are not then I fail to see how your video card would have a significant impact on the speed of your system.

Have you tried reinstalling it, or using regular Ubuntu for comparison? That really doesn't make much sense at all. Both Ubuntu and Xubuntu work great on my Intel Inspiron 700m (2 ghz, 1.25 gb ram, intel graphics).

---

### Post by mcduck on 2007-11-14
Are your video card drivers working correctly? Xubuntu sure should not be slow.. I have it running on a 450Mhz machine with 128MB of RAM and it's pretty fast even on such an old piece of waste so it should be blazingly fast on your hardware..

Run 'glxinfo' on a terminal and post the output here.

You could also check that any program isn't using insanely much CPU power, and also that you have correctly working swap space (even if you have enough RAM to never actually need to use it, some things just might not work correctly if there is no swap available..) 'top' will tell you about running programs, and 'free -m' about available/used memory and swap.

---

### Post by revolutio on 2007-11-14
Thanks for the speedy response.  And yes I have done a new install of Xubuntu on another partition (same HD) with the same results.  My next step is testing regular Ubuntu.

glxinfo:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

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

```

Well this is interesting, all my work to get my video card recognized seems to have disappeared.  Last I remember checking it was about 14 days ago.

Also here is the fglrxinfo output which previously correctly identified my video card.  I still did have jerkiness when it was registering correctly but if it resets like that I have doubts about the output's sincerity.  This annoys me I spent two full days getting it to say something other than Mesa.
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

Free space also shouldn't be a problem.  My mem never maxes out and I never even see the swap get used (don't know whether that is a bad sign).

"free -m" output:
```
             total       used       free     shared    buffers     cached
Mem:          1011        500        510          0         38        272
-/+ buffers/cache:        189        822
Swap:         1906          0       1906

```

---

### Post by mcduck on 2007-11-14
> **revolutio said:**
> Thanks for the speedy response.  And yes I have done a new install of Xubuntu on another partition (same HD) with the same results.  My next step is testing regular Ubuntu.

glxinfo:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

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

```

Well this is interesting, all my work to get my video card recognized seems to have disappeared.  Last I remember checking it was about 14 days ago.

Also here is the fglrxinfo output which previously correctly identified my video card.  I still did have jerkiness when it was registering correctly but if it resets like that I have doubts about the output's sincerity.  This annoys me I spent two full days getting it to say something other than Mesa.
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

Free space also shouldn't be a problem.  My mem never maxes out and I never even see the swap get used (don't know whether that is a bad sign).

"free -m" output:
```
             total       used       free     shared    buffers     cached
Mem:          1011        500        510          0         38        272
-/+ buffers/cache:        189        822
Swap:         1906          0       1906

```
Ok, based on that I'd say your problems come from the fact that your graphics card is not running on the correct driver. Your CPU is now doing all the work, and normal CPU's suck pretty badly with graphical stuff so that can easily slow otherwise fast system to a crawl..

How did you install the driver? Simple 'sudo apt-get install xorg-driver-fglrx' followed by 'sudo aticonfig --initial' has worked on every machine with Radeon card to which I have installed Ubuntu..

---

### Post by tdrusk on 2007-11-14
If you get Xubuntu running faster but you still want more speed try puppy linux. It's the best lite distro imo.

---

### Post by louieb on 2007-11-14
> **revolutio said:**
> Have had another thread .....believe that the video lagging is just a facet of an overall problem with the speed of Xubuntu.

> **mcduck said:**
> ... Simple 'sudo apt-get install xorg-driver-fglrx' followed by 'sudo aticonfig --initial' has worked on every machine with Radeon card to which I have installed Ubuntu..

Thanks, mcduck When I said thought it was the card I should have said the Linux ATI driver.

---

### Post by sonicmaker on 2007-11-15
I have the same problem - Xubuntu running crazy slow - except that my hardware config is different. I'm running a much older machine, an old Toshiba laptop with a Celeron 667 with 192MB RAM and an S3 Savage IX  graphics chipset. Since it's a laptop, I can't really change the hardware I have! I had hoped to breathe some new life into the old thing with Xubuntu, but it looks like it'll be harder than all that.

glxinfo gave me roughly the same output as yours, revolutio - by which I mean that it listed the Mesa driver as the renderer. I suspect it's a similar graphics-based problem as yours.

Any help that the community could give us users of ancient hardware would be greatly appreciated :o)

---

### Post by revolutio on 2007-11-25
> **mcduck said:**
> Ok, based on that I'd say your problems come from the fact that your graphics card is not running on the correct driver. Your CPU is now doing all the work, and normal CPU's suck pretty badly with graphical stuff so that can easily slow otherwise fast system to a crawl..

How did you install the driver? Simple 'sudo apt-get install xorg-driver-fglrx' followed by 'sudo aticonfig --initial' has worked on every machine with Radeon card to which I have installed Ubuntu..
I don't know how to thank you enough.  You were right on.  I should have gotten around to guessing that the CPU was handling the video load but I didn't.  The reason my earlier fix of the ATI drivers didn't have the desired effect was that I did a kernel update immediately afterwards and didn't check it again.  The kernel update apparently reset the drivers so I never actually got to use them.

Things run great.  The test that finally made me feel like Linux was worth it.  Watching the gorgeous HD Gears of War trailer running smooth as silk.  I still need to turn off other programs (particularly that memory hog that is Thunar) but it was actually capable of it.

Many thanks my friend.

---

### Post by mcduck on 2007-11-25
No problem, great that you got the machine running smoothly.

HD video can be a bit of a task for older machines, but if you aren't using it already, try mplayer. It seems to be a bit lighter than other video players around and performs better on low end machines.

---

### Post by IeU on 2007-12-11
i am also having some performance issues here.

Is it not Ubuntu/Linux well-known for its performance as a multi-tasking system ?

So, i have here "4 Virtual Desktops" and distributed on them are likely:
* X-Chat with around 15 channels.
* 2 x Terminal Windows doing nothing.
* Listening Music ( MP3 ) on Exaile.
* 3 x Firefox windows and on each of them around 5 Tabs opened.
* Eudora running with 3 IMAP accounts configured ( GMail ), 1 account with around 4000 emails, the others not more then 100.
* Azureus seeding around 20 torrents.
* a weather applet running

that is all, if i want to install a app for example, using add/remove or Synaptic, my system comes to an almost frozen state, with the mouse moving slow and sloopy, not moving, but jumping from here to there. Music jumps, stops, recontinues. Switching btw virtual desktops does not take 1 second or less, as should be, but 5-10 seconds . . .

what is wrong with my system ?

(info needed: is there an app or command that will give me a general info about my system ? like partitions, cpu, memory, etc . . . )

---

### Post by rsambuca on 2007-12-11
> **IeU said:**
> i am also having some performance issues here.

Is it not Ubuntu/Linux well-known for its performance as a multi-tasking system ?

So, i have here "4 Virtual Desktops" and distributed on them are likely:
* X-Chat with around 15 channels.
* 2 x Terminal Windows doing nothing.
* Listening Music ( MP3 ) on Exaile.
* 3 x Firefox windows and on each of them around 5 Tabs opened.
* Eudora running with 3 IMAP accounts configured ( GMail ), 1 account with around 4000 emails, the others not more then 100.
* Azureus seeding around 20 torrents.
* a weather applet running

that is all, if i want to install a app for example, using add/remove or Synaptic, my system comes to an almost frozen state, with the mouse moving slow and sloopy, not moving, but jumping from here to there. Music jumps, stops, recontinues. Switching btw virtual desktops does not take 1 second or less, as should be, but 5-10 seconds . . .

what is wrong with my system ?

(info needed: is there an app or command that will give me a general info about my system ? like partitions, cpu, memory, etc . . . )
LOL!!!  That's a good one!

---

### Post by mcduck on 2007-12-11
> **IeU said:**
> i am also having some performance issues here.

Is it not Ubuntu/Linux well-known for its performance as a multi-tasking system ?
Yes, it is.
> **IeU said:**
> 
So, i have here "4 Virtual Desktops" and distributed on them are likely:
* X-Chat with around 15 channels.
* 2 x Terminal Windows doing nothing.
* Listening Music ( MP3 ) on Exaile.
* 3 x Firefox windows and on each of them around 5 Tabs opened.
* Eudora running with 3 IMAP accounts configured ( GMail ), 1 account with around 4000 emails, the others not more then 100.
* Azureus seeding around 20 torrents.
* a weather applet running

that is all, if i want to install a app for example, using add/remove or Synaptic, my system comes to an almost frozen state, with the mouse moving slow and sloopy, not moving, but jumping from here to there. Music jumps, stops, recontinues. Switching btw virtual desktops does not take 1 second or less, as should be, but 5-10 seconds . . .
what is wrong with my system ?
15 tabs of Firefox and Azureus.

While Linux is good with running multiple applications at the same time it doesn't make memory and resource hog applications any lighter. Firefox still uses lots of memory, Flash on web pages still uses lots of CPU, and anything made with Java still uses lots of both CPU power and memory.
> **IeU said:**
> 
(info needed: is there an app or command that will give me a general info about my system ? like partitions, cpu, memory, etc . . . )
"fdisk -l" will list all partitions.
'cat /proc/cpuinfo' will tell you about your CPU.
'cat /proc/meminfo' does the same with RAM.
'lspci' lists all your hardware.
'top' will tell about running programs and their CPU & memory usage.
'free -m' will tell about memory and swap usage. Read the "+/-  buffers/cache" line.

---

### Post by IeU on 2007-12-11
```
felipe@felipe-desktop:~$ fdisk -l

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sde: 1014 MB, 1014497280 bytes
65 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0x32b73a58

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         953      990704    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(967, 64, 32) logical=(952, 39, 32)
felipe@felipe-desktop:~$ 

```

```
felipe@felipe-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
stepping        : 1
cpu MHz         : 2400.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4838.95
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
stepping        : 1
cpu MHz         : 2400.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4838.95
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

felipe@felipe-desktop:~$ 

```

```
felipe@felipe-desktop:~$ cat /proc/meminfo
MemTotal:      2063632 kB
MemFree:         23392 kB
Buffers:        689952 kB
Cached:         801168 kB
SwapCached:          0 kB
Active:         521748 kB
Inactive:      1408744 kB
SwapTotal:     1020116 kB
SwapFree:       981728 kB
Dirty:             392 kB
Writeback:           0 kB
AnonPages:      439500 kB
Mapped:          80316 kB
Slab:            59920 kB
SReclaimable:    35584 kB
SUnreclaim:      24336 kB
PageTables:      17800 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   2051932 kB
Committed_AS:   939884 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     45004 kB
VmallocChunk: 34359684091 kB
felipe@felipe-desktop:~$ 

```

```
felipe@felipe-desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
05:08.0 Multimedia audio controller: Creative Labs SB X-Fi
felipe@felipe-desktop:~$ 

```

```
felipe@felipe-desktop:~$ top

top - 21:30:50 up 33 min,  2 users,  load average: 1.95, 2.07, 1.45
Tasks: 132 total,   2 running, 130 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.6%us, 50.8%sy,  0.0%ni, 43.2%id,  0.0%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   2063632k total,  2042464k used,    21168k free,   690208k buffers
Swap:  1020116k total,    38388k used,   981728k free,   801432k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 8354 lp        25   0 61576 2008 1496 R  100  0.1  14:15.30 hp                                                                                                                  
 6210 felipe    15   0  206m  24m  15m S    6  1.2   2:34.10 gnome-system-mo                                                                                                     
 8366 lp        18   0  101m  15m 4224 S    4  0.8   0:08.13 gs                                                                                                                  
 5632 root      15   0  168m  40m   9m S    2  2.0   2:35.85 Xorg                                                                                                                
 8368 lp        18   0 69440 2744 2084 S    1  0.1   0:06.80 hpijs                                                                                                               
 8448 felipe    15   0  260m  28m  13m S    1  1.4   0:00.54 gnome-terminal                                                                                                      
    1 root      18   0  5112 1968  572 S    0  0.1   0:02.05 init                                                                                                                
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                            
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                         
    4 root      34  19     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0                                                                                                         
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                          
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.92 migration/1                                                                                                         
    7 root      34  19     0    0    0 S    0  0.0   0:01.25 ksoftirqd/1                                                                                                         
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                          
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0                                                                                                            
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                                                            
   11 root      11  -5     0    0    0 S    0  0.0   0:00.01 khelper                                                                                                             
   30 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                                           
   31 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                                           
   32 root      11  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                              
   33 root      11  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                        
  166 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                                             
  199 root      15   0     0    0    0 S    0  0.0   0:00.31 pdflush                                                                                                             
  201 root      10  -5     0    0    0 S    0  0.0   0:00.80 kswapd0                                                                                                             
  254 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                               
  255 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                               
 2147 root      14  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                       
 2148 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                               
 2198 root      17  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                                                                               
 2199 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/1                                                                                                               
 2200 root      17  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                             
 2409 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                                           
 2410 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                                           
 2435 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                                                           
 2436 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                                           
 2460 root      12  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4                                                                                                           
 2461 root      10  -5     0    0    0 S    0  0.0   0:00.98 usb-storage                                                                                                         
 2464 root      12  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                                                                           
 2465 root      10  -5     0    0    0 S    0  0.0   0:00.00 usb-storage                                                                                                         

```

```
felipe@felipe-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2015       1999         16          0        673        781
-/+ buffers/cache:        544       1471
Swap:          996         37        958
felipe@felipe-desktop:~$ 

```


now everything seems ok, bcse i had to reboot . . .

> **rsambuca said:**
> LOL!!!  That's a good one!

windows xp can handle everything i listed.
atleast on my machine.

not so useful comment from you.

---

### Post by rsambuca on 2007-12-11
> **mcduck said:**
> Yes, it is.

15 tabs of Firefox and Azureus.

While Linux is good with running multiple applications at the same time it doesn't make memory and resource hog applications any lighter. Firefox still uses lots of memory, Flash on web pages still uses lots of CPU, and anything made with Java still uses lots of both CPU power and memory.

"fdisk -l" will list all partitions.
'cat /proc/cpuinfo' will tell you about your CPU.
'cat /proc/meminfo' does the same with RAM.
'lspci' lists all your hardware.
'top' will tell about running programs and their CPU & memory usage.
'free -m' will tell about memory and swap usage. Read the "+/-  buffers/cache" line.

Was he being serious?  I just assumed it was a joke!  20 torrents at once, using Azureus???  Tracking 4000 emails???  15 websites running???

sudo lshw

will give you the most comprehensive info.

---

### Post by rsambuca on 2007-12-11
Sorry LeU.  I didn't mean to offend.  Most rigs would have trouble with that, but you have a pretty awesome setup, so it should handle it.  Are you using the nvidia-glx-new drivers by chance?  If so, you should know that there is a memory leak which will eventually cause your system to really bog down over time.

---

### Post by IeU on 2007-12-11
what i am saying, is that xp on my machine could handle that

k, on xp i was using utorrent, but still

edit,

its ok :)

i ll check out about nvidia driver

---

### Post by mcduck on 2007-12-11
> **IeU said:**
> 
```
felipe@felipe-desktop:~$ top

top - 21:30:50 up 33 min,  2 users,  load average: 1.95, 2.07, 1.45
Tasks: 132 total,   2 running, 130 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.6%us, 50.8%sy,  0.0%ni, 43.2%id,  0.0%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   2063632k total,  2042464k used,    21168k free,   690208k buffers
Swap:  1020116k total,    38388k used,   981728k free,   801432k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 8354 lp        25   0 61576 2008 1496 R  100  0.1  14:15.30 hp                                                                                                                  
 6210 felipe    15   0  206m  24m  15m S    6  1.2   2:34.10 gnome-system-mo                                                                                                     
 8366 lp        18   0  101m  15m 4224 S    4  0.8   0:08.13 gs                                                                                                                  
 5632 root      15   0  168m  40m   9m S    2  2.0   2:35.85 Xorg                                                                                                                
 8368 lp        18   0 69440 2744 2084 S    1  0.1   0:06.80 hpijs                                                                                                               
 8448 felipe    15   0  260m  28m  13m S    1  1.4   0:00.54 gnome-terminal                                                                                                                                                                                                         

```

I don't know what that 'hp' is, but it's using 100% of your another CPU core, and that could be your problem.

(It could be part of HP printer driver.. At least hpijs is, and they seem to be running as same user)

Also, try running 'glxinfo' and post the output here, just to check that your video drivers are working correctly.

---

### Post by IeU on 2007-12-12
```
[tuche@minwinpc ~]$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

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
0x63 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
[tuche@minwinpc ~]$ 

```

---

### Post by mcduck on 2007-12-12
> **IeU said:**
> ```

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```


Your graphics card drivers are not working, and the CPU is doing all the work. Fix that and probably your performance issues will go away as well. Have you tried the Restricted Drivers Manager? (System/Administration/Restricted Drivers Manager)

At least you are not suffering from the memory leak problem some people have with nvidia drivers, as you aren't even using the drivers at the moment. :)

---

### Post by nilgiri on 2007-12-19
I have the same symptoms and same message in my glxinfo, and I don't know where to begin to fix it:
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

According to lspci, my video card is:
```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

```

I have the xserver-xorg-video-intel and ...video-i810 installed, and am using i810 as the device in my xorg.conf.  I tried changing i810 to intel in my xorg.conf, but then gdm would not start.  Am I even close by trying that?  Do I even have the right package/drivers installed?  How would I find out?

Thanks much for any help.

---

### Post by nilgiri on 2007-12-19
Oh, and there is nothing obvious to me in the restricted drivers manger.  A software modem and my broadcom wifi drivers are there, but nothing else.

---


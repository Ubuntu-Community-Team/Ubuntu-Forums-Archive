---
title: "The graphics in 9.04 feels slow?"
date: 2009-04-27
forum: General Help
---

### Post by Hund on 2009-04-27
Hi,

I upgraded to Ubuntu 9.04 when the RC was new and when the ATI Catalyst 9.4 driver was released.

The graphics feels slow, X.org eats about 500MB to 2GB RAM, opening a windows takes 1-2 seconds depending on the application and opening a video is really really slow etc, and Tv-Out doesnt work at all.

I'm also having some problems with Compiz, I cant get it to autostart. I always have to start Fusion-icon and refresh the Window decoration there.

I didnt have any problems at all with Ubuntu 8.10 and my Radeon 4850 card.

Any idéeas? :)

Cheers

---

### Post by huntzire on 2009-04-27
> **Hund said:**
> Hi,

I upgraded to Ubuntu 9.04 when the RC was new and when the ATI Catalyst 9.4 driver was released.

The graphics feels slow, X.org eats about 500MB to 2GB RAM, opening a windows takes 1-2 seconds depending on the application and opening a video is really really slow etc, and Tv-Out doesnt work at all.

I'm also having some problems with Compiz, I cant get it to autostart. I always have to start Fusion-icon and refresh the Window decoration there.

I didnt have any problems at all with Ubuntu 8.10 and my Radeon 4850 card.

Any idéeas? :)

Cheers

Try switching to metacity, you can achieve such by system->preferences->appearance, and visual effects, and select none and tell me how it runs then.

I have had to many issues with compz-fusion, its nice concept and candy but serves utter no purpose then to amuse the windows and mac monkey's.

alt f2, type metacity and another alt f2 type gconf-editor,

then go to apps->metacity->general
make sure composing manager off, and also click reduced resources and see how that runs on your system, note these are my default settings as i can careless if i have i candy lol.

---

### Post by Hund on 2009-04-27
I like Compiz and some of the real functions it brings (Not the cube etc, that was funny about 2 years ago :P). Compiz doesnt make the computer/apps running slow, I can watch HD movies and do other heavy stuff without any problems. The only thing thats slow is open a minimized window from the panel.

It feels like the problem is the new version of X.org?

---

### Post by huntzire on 2009-04-27
> **Hund said:**
> I like Compiz and some of the real functions it brings (Not the cube etc, that was funny about 2 years ago :P). Compiz doesnt make the computer/apps running slow, I can wathc HD movies and do other heavy stuff without any problems. The only thing thats slow is open a minimized window from the panel.

It feels like the problem is the new version of X.org?

It might be they removed alot of legecy code, and I know for a fact compiz-fusion screws somethings up like resolution setting by apps, in partcular AlienArena and Tremulous and forces me to turn it off :/

Did you do a direct upgrade to jaunty or a dist-upgrade? I offen find xorg throws a tantum when you do. Because I did a direct upgrade and it has ran the fastest I have ever had.

---

### Post by Hund on 2009-04-27
I always reinstall Ubuntu. :)

---

### Post by huntzire on 2009-04-27
> **Hund said:**
> I always reinstall Ubuntu. :)

Hmm at the moment im at a last of what direction to go,

do you know if you have a freq-govenor on and that is set to conservative?

im going to have to research this (no promises) and see what I can discover, in the mean time throw your system info into a post so i can go probing the depths of this misery.

---

### Post by true vladimir on 2009-04-27
I also upgraded to 9.04 and I am having problem with compiz ( tahat is why graphics is slow ), under 8.10 everything was fine.
From terminal copiz reported:
vladimir@vladimir-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity
Any one how to solve this?

---

### Post by huntzire on 2009-04-27
> **true vladimir said:**
> I also upgraded to 9.04 and I am having problem with compiz ( tahat is why graphics is slow ), under 8.10 everything was fine.
From terminal copiz reported:
vladimir@vladimir-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity
Any one how to solve this?

Have you tried to run metacity instead by default?
alt f2 metacity,

Also as far upgrading, did you do a reinstall or upgrade from 8.10? I shun the 2nd option and its never turned out well and its better to do it fresh.

do glxinfo and give me the output a well.

---

### Post by true vladimir on 2009-04-27
vladimir@vladimir-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
// upgrade was reporting:
// upgrade xlib: extension "generic event extension" missing on display  (0,0)<
// but it also, i am not sure, it was reporting something similar like
// upgrade xlib: extension "generic event extension" missing on display  :0.0 <

direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
OpenGL version string: 2.0 Mesa 7.4
OpenGL shading language version string: 1.10
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_separate_stencil, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays

36 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8e 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x8f 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x90 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x91 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x92 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x93 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x94 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x95 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x96 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x97 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x98 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x99 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x9a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x9b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x9c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x9d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x9e 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x9f 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xa0 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xa1 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xa2 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xa3 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xa4 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xa5 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xa6 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xa7 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xa8 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xa9 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xaa 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xab 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xac 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xad 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xae 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x69 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

36 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x6a  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6b  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6c  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6d  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6e  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6f  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x70  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x71  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x72  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x73  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x74  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x75  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x76  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x77  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x78  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x79  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7c  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x7d  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x7e  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x7f  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x80  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x81  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x82  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x83  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x84  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x85  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x86  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x87  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x88  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x89  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8a  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8c  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

found in formus that
sudo apt-get install libxcb-event0 might help but it did not

---

### Post by Hund on 2009-04-27
My Gigabyte GA-X48-DS4 mobo doesnt support CPU frequency scaling.

I just noticed something wierd. If I minimize/unminimize Firefox several times the xorg process takes about 20-30% CPU and the mem usage just getting bigger. Started at ~150MB and after a few moments it was eating about 300MB RAM. It must be new version of X.org thats causing my problems? :)

---

### Post by true vladimir on 2009-04-27
I found solution for my case in:
Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories  > Desktop Environments

---

### Post by a917585103 on 2009-04-29
The Ubuntu 9.04 is slow. Is mutch slow than 8.10.
in 8.10 i can watch RMVB AVI etc... with no gags...

In 9.04 lot of gags stops..... 

Can anybody have the same situation....?
Is there any solution... mine was downgrade to 8.10....

Thanks.

---

### Post by Primula on 2009-04-29
> **a917585103 said:**
> The Ubuntu 9.04 is slow. Is mutch slow than 8.10.
in 8.10 i can watch RMVB AVI etc... with no gags...

In 9.04 lot of gags stops..... 

Can anybody have the same situation....?
Is there any solution... mine was downgrade to 8.10....

Thanks.

Pretty much same problems. Everything seems to be running much slower; CPU increases constantly when even performing minor tasks.. I never tried 8.10 so upgraded from 8.04 to 9.04 :/

---

### Post by muhannadfa on 2009-04-29
same here
i used the revert back solution
nothing improved for me
thanks

---

### Post by MrMacman2u on 2009-04-29
There seems to be a rather large amount of feedback lacking in this thread and thus very little and/or no progress toward finding a solution for a very obvious bug has been made.

I have an IBM Thinkpad T42 with an Intel Pentium M 1.5Ghz, 2GB RAM, and an ATI Radeon 7500 Mobility with 32MB of VRAM using, of course, the open source driver as the closed source is not available.

I'm suffering from the same issue that everyone else here thus far has had after installing a fresh copy of 9.04 (had the same trouble when I upgraded as well, hence the re-install)

The problem is that Compiz is just plain SLOW. Painfully so in fact, low framerates across the board, massive CPU utilisation and horrible slow, cpu munching, scrolling in programs like Firefox or Open Office.

That said, raw 3D works ok... kinda... If I open GLXgears from the terminal and only have those two windows open I get the roughly 780FPS I expect.

Once I start opening MORE windows and programs, the performance starts to fall off almost in a linear fashion. I get to about a dozen windows and GLXGears struggles along at around 300FPS as CPU usage climbs.

Watching a DVD or video burns through 200-500% more cpu than it used to under 8.10 as well.

Now, before it is recommended to me, falling back to Metacity is not an option for three reasons: One, it does not fix the bug. Two, Compiz worked GREAT with this same system on 8.10 and Three, I like eye candy.

I would like to note that this bug does NOT seem to exist on Intel GMA or Nvidia systems and I have tested this theory to confirmation. 

CPU frequency scaling has no influence on this problem, disabling it does not change the sluggish behaviour.

The problem also seems to affect Intel and AMD users equally, the only combining factor is ATI video cards, and not all cards are affected.

After some additional research I have learned that the most likely explanation is that something has changed in the most recent version of Ubuntu, whether it be drivers, X or Compiz and the side effect is that some ATI users are getting kicked in the nuts for it.

Any help in resolving this problem would be appreciated, I will gladly attach any logs or test results that may be required to resolve this problem. I will also gladly test any possible solutions as quickly as possible. Consider me your guinea pig.

---


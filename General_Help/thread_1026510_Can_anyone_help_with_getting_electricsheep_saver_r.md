---
title: "Can anyone help with getting electricsheep saver running correctly?"
date: 2008-12-31
forum: General Help
---

### Post by markg1123 on 2008-12-31
I am fairly interested in getting this screen saver to run on my computer and any assistance would be greatly appreciated.

I am running hardy at the moment and have limited experience with ubuntu but a pretty broad technical background...

I am running the gnone-screensaver still and have installed electricsheep many many times over the past few days in many different methods...
the last way i installed was via the: sudo apt-get install electricsheep from the [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu)

when i attempt to run from the screen saver screen i just get a blank screen.

when i run from terminal with 'electricsheep' i am usually just getting a "terminated" error.

i have tried playing around with some of the different flags from the --help file and HAVE been successful to get this to run using the: electricsheep --video-driver gl switch...
This runs the sheep in a window using MPlayer....
this looks great but my only question is can anyone can help me get this running with gnone-saver in full screen as an actual screen saver?

i have googled this up and down and cannot find any up to date guides. Any installation guides i can find all seem to be a different method, all contradicting each other....

also, when i run with --zoom 1 it gives me an error that --zoom is not a valid switch, i also get this same error for the --Mplayer 1 methods that have been mentioned.

Any assistance would be greatly appreciated and want to thanks for all i have gotten from this board as a source for my ubuntu needs.
:confused:

---

### Post by stderr on 2009-01-01
Well I've just given it a go now.

For me under Intrepid, electricsheep is in the main repos anyway. I would imagine it is for hardy too (i.e. I assume you added [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu) as another source? Not sure if that's necessary).

My experience:

```
ace@ace5:~$ sudo apt-get install electricsheep
[... installing blah blah ...]
ace@ace5:~$ electricsheep
please be patient while the first sheep is downloaded...

```

... then a long, long wait. From the man page (man electricsheep):

```
 The  first  time  it  runs, it normally takes about 10 minutes
 before a sheep (as the animations  are  called)  is  downloaded  and
  displayed. After  that,  it should come up immediately.  You can use
 BitTorrent to download more sheep faster, see the web site below for how.
```

Interestingly, I see no web site in the whole man page. 

Nor is there much discernible network activity during this supposed initial download process. So I got bored and ran again with the debug flag set.

```
ace@ace5:~$ electricsheep --debug 1
=====================================
electric sheep v2.6.8
time Thu Jan  1 23:24:53 2009
decoder execvp mpeg2dec_onroot -f 23 -w -1 
updating cache path=/home/ace/.sheep/ match_gen=0
time Thu Jan  1 23:24:53 2009
please be patient while the first sheep is downloaded...
updating cache path=/home/ace/.sheep/ match_gen=0
time Thu Jan  1 23:25:03 2009
updating cache path=/home/ace/.sheep/ match_gen=0
time Thu Jan  1 23:25:13 2009
updating cache path=/home/ace/.sheep/ match_gen=0
time Thu Jan  1 23:25:23 2009
updating cache path=/home/ace/.sheep/ match_gen=0
time Thu Jan  1 23:25:33 2009
updating cache path=/home/ace/.sheep/ match_gen=0
time Thu Jan  1 23:25:43 2009

```

Eventually: (see screenshot below)

However, attempting to fullscreen it doesn't work. So, I tried the zoom switch as you did.

```
ace@ace5:~$ electricsheep --zoom 1
warning: cannot zoom without mplayer or rootwin.
```

So I tried the mplayer switch as you did.

```
ace@ace5:~$ electricsheep --mplayer 1
Terminated
```

I also tried --video-driver gl, however it doesn't recognise the --video-driver switch. Maybe that's a difference between the repo version and the one you're using?

It seemed to work fine from the screensaver window (see second screenshot below). For the life of me I don't understand why it's called electricsheep though. Or maybe just no sheep have downloaded yet...

So it would appear to be a graphics driver issue on your end, perhaps? Could you post the output of 

```
glxinfo
```

---

### Post by markg1123 on 2009-01-01
Thanks for getting back to me on this one and attempting to help me out here...
Pasted below is the output from glxinfo.
I'm thinking i may have a problem with old version installed possibly?
I tried to sudo apt-get remove electric sheep and then reinstall again but has the same results...Would you have any suggestions on the best possible way to completely uninstall/remove from my system (remember i am not terribly linux savvy yet) 
Also if it's important, i have an ati video card which also could be an issue...
i've also considering doing a clean install to intrepid soon so thats another option i may have... Thanks again

Thanks again for your assistance here and here's the output you were looking for...

```
mark@mark-delldesk:~$ glxinfo
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 2.1.7412 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x40 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x41 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x42 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x68 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x69 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x6a 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x85 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  8 1 Ncon
mark@mark-delldesk:~$ 
```



Here's the version that i have -- i guess this is a good start to the problem 

```

mark@mark-delldesk:~$ electricsheep --debug 1
=====================================
electric sheep v2.7b11
time start Thu Jan  1 20:01:25 2009

```

---

### Post by stderr on 2009-01-01
Your glxinfo output looks fine; remarkably similar to mine in fact (I'm running an ATi card too in this laptop), except ou've got slightly earlier version of OpenGL since you're on Hardy (I think).

I'm none too sure what to suggest next.

With regards to uninstalling electricsheep entirely, the best option is to use purge. Whilst remove removes the app ;) purge also removes configuration files too.

```
sudo apt-get purge electricsheep
```

All I'd say is try installing from the main repos again. If you happen to have added any 3rd party software sources to install electricsheep from, remove them first. Then purge the current installation as above, and sudo apt-get install electricsheep again.

If you still just get 

```
ace@ace5:~$ electricsheep 
Terminated
```

I'm not sure what to suggest... :|

edit: It would appear bugs were filed a couple years back relating to it not always occupying the full screen space under various conditions, even with --zoom

What you could try is grabbing the source code archive the electricsheep website and compiling it. That may help. In fact, in the development section of the wiki they've got a shell script to do just that, grabbing the latest source from SVN.

[http://electricsheep.wikispaces.com/Development]("http://electricsheep.wikispaces.com/Development")

---

### Post by markg1123 on 2009-01-01
thx again, i'll play around with it...
i'm still thinking of clean-installing to intrepid. i was going to do it sooner but have been waiting for the 'kinks' to get worked out...
this install is the first install of ubunutu i've had so i'm sure i've messed up a bunch of stuff..

here's the real goofy part.. the first time i tred installing, i installed from the synamtic package manager... and it worked just fine as a screen saver i just couldnt get it to zoom, it sat as a small box in upper left corner...

i'll keep playing w/ it but thanks again for the help

---

### Post by sigurnjak on 2009-01-02
I have used  .deb from here [https://launchpad.net/~flam3/+archive](https://launchpad.net/~flam3/+archive)

and after rebooting it worked just fine without any tinkering . You might want to purge again and start fresh , reboot and see what happens .

---

### Post by neilevan814 on 2009-03-06
I want to second the recoomend for following the instructions for add the ppa's to your sources.list and then installing the .deb package from this site.  My electricsheep were loaded immediately after installing from here.  Thanks.

---

### Post by markg1123 on 2009-03-06
Thanks for the reply; sorry i forgot all about this thread. I have recently upgraded to intrepid and all is working OK ...
well except for flicker when compbiz is enabled but i'm OK with that...I still dont understand why dell would sell a ubuntu loaded machine with an ATI card :(

---


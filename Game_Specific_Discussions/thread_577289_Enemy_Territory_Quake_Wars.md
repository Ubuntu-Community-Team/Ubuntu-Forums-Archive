---
title: "Enemy Territory: Quake Wars"
date: 2007-10-16
forum: Game Specific Discussions
---

### Post by Perfect Storm on 2007-10-16
**UGA's News Discussion of Enemy Territory: Quake Wars**

Discuss here. All discussions fall under the general rules of the UGA Code.
No swearing, profanity, nudity or other such subversive images or communications.
No Personal Attacks. Spamming of any kind will not be tolerated.

---

### Post by crane on 2007-10-16
Sorry I didn't see this post before I posted the other. If you wish, just delete the other.
Download Demo at:
[ 3D Downloads]("http://www.3ddownloads.com/Action/Enemy%20Territory:%20Quake%20Wars/Demo;jsessionid=6FA5CE4D4CCD16827479BDD6BA1FEA3F")

---

### Post by xIke on 2007-10-16
I can't get it to work.  If this question belongs in a new thread, just let me know and I'll do that.

I try to run it and it gives me this error:

```
ERROR: The current video card / driver combination does not support the necessary features: 
GL_EXT_texture3D GL_ARB_texture_rectangle or GL_EXT_texture_rectangle GL_ARB_occlusion_query 
GL_ARB_vertex_program GL_ARB_fragment_program GL_ARB_shader_objects GL_ARB_vertex_shader 
GL_ARB_fragment_shader
```

fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37.6)
```

Thanks.

---

### Post by Henaro on 2007-10-16
I couldn't get it to run either.  
```
SDL_ListModes:
1280x1024 1280x720 1152x864 1024x768 800x600 640x480 640x400 512x384 400x300 320x240 320x200 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
------- Initializing renderSystem --------
----- R_InitOpenGL -----
signal caught: 'Segmentation fault', si_code 1
callstack:
0x0
[0x082cc6d1]
[0x082bc82f]
[0xffffe440]
Trying to exit gracefully..

```
:(
Running a Radeon x1600 Pro with fglrx drivers installed.

---

### Post by DestyNovaX on 2007-10-16
Me neither, have a x1600pro running on gutsyRc1.. on my other system (nvidia) runs flawlessly.. :(

```
thread priority set to 1
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
X..GL_ARB_texture_non_power_of_two not found
X..GL_ARB_texture_compression not found
X..GL_EXT_texture_filter_anisotropic not found
X..GL_EXT_texture_lod not found
X..GL_1.4_texture_lod_bias not found
X..GL_EXT_shared_texture_palette not found
X..GL_EXT_texture3D not found
X..GL_ARB_texture_rectangle not found
X..GL_EXT_texture_rectangle not found
X..GL_EXT_stencil_wrap not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ARB_vertex_buffer_object not found
X..GL_ARB_vertex_program not found
X..GL_ARB_fragment_program not found
X..GL_EXT_depth_bounds_test not found
X..GL_ARB_point_sprite not found
X..GL_ARB_occlusion_query not found
X..GL_EXT_framebuffer_object not found
X..GL_EXT_packed_depth_stencil not found
...using GL_EXT_blend_minmax
X..GL_ARB_multisample not found
X..GL_ARB_shader_objects not found
X..GL_ARB_vertex_shader not found
X..GL_ARB_fragment_shader not found
X..GL_ARB_fragment_program_shadow not found
X..GL_ARB_shadow not found
X..GL_ARB_depth_texture not found
X..GL_EXT_gpu_program_parameters not found
0x0
[0x082cc6d1]
[0x08192769]
[0x08101078]
[0x08101ad9]
[0x0819085c]
[0x08190e02]
[0x08190fde]
[0x083ee00e]
[0xb7acc050]
[0x0804c9d1]
********************
ERROR: The current video card / driver combination does not support the necessary features: GL_EXT_texture3D GL_ARB_texture_rectangle or GL_EXT_texture_rectangle GL_ARB_occlusion_query GL_ARB_vertex_program GL_ARB_fragment_program GL_ARB_shader_objects GL_ARB_vertex_shader GL_ARB_fragment_shader
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
Sys_Error: Error during initialization

```

---

### Post by crane on 2007-10-16
Sorry I won't be much help here because I have always run nvidia.
Do other dames run well? Q4, Doom3, Quake3 or UT2k4?

---

### Post by kthakore on 2007-10-17
I have a similar problem. I use Ati 9200se rx280
(sidenote: doom, unreal work fine on it)
My lspci output

```

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

```

.
The error is:
```

ERROR: The current video card / driver combination does not support the necessary features: GL_ARB_occlusion_query GL_ARB_fragment_program GL_ARB_shader_objects GL_ARB_vertex_shader GL_ARB_fragment_shader

```

my glxinfo

```
name of display: :0.0
display: :0  screen: 0
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_S3_s3tc

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by Perfect Storm on 2007-10-17
Maybe the ATI driver isn't up for it yet.
Also Nvidia user here, so I can't give any advise.

---

### Post by Lord Illidan on 2007-10-17
Got it to work on an nvidia 7400.

---

### Post by screaminj3sus on 2007-10-17
works fine here with my 7600GS. Way better FPS than in vista.

---

### Post by DestyNovaX on 2007-10-18
> **screaminj3sus said:**
> works fine here with my 7600GS. Way better FPS than in vista.
Lucky you! I'll go Nvidia on my next (and really close, I'm starting to believe :lolflag:) system upgrade! :popcorn:

---

### Post by xIke on 2007-10-18
Yeah, stupid nvidia people. :P

I don't know what to buy next.  ATI just open sourced their drivers, so there's every hope that they'll be substantially better than nvidia's, though I have no idea how long that will take.  I just want something that "works."  Amazing concept, coming from a mac guy. :(

---

### Post by cogadh on 2007-10-18
The drivers going open source doesn't necessarily mean they will get better, just look at the Intel drivers. Nvidia's drivers work well because they don't just make a token effort at producing functional drivers, they are actually on par with the drivers they make for Windows (in some ways, they are better). If ATI had bothered to put the same effort into their old closed source drivers, people wouldn't have all the problems they have with them now.

---

### Post by compiledkernel on 2007-10-19
downloading the full client as we speak WOOHOOOOOOOO.

[http://zerowing.idsoftware.com:6969/stats.html?info_hash=561e63fd63887faaecdc17632a551d49f512a66b](http://zerowing.idsoftware.com:6969/stats.html?info_hash=561e63fd63887faaecdc17632a551d49f512a66b)

Seed away please....=)

---

### Post by madsmeg on 2007-10-19
I second that WOOHOOOOO 

Downloaded and about to install

---

### Post by mattpker on 2007-10-19
So the full version is free for Linux?

---

### Post by cogadh on 2007-10-19
You still need the data files from the retail game, this is just install/native binary for Linux.

---

### Post by mattpker on 2007-10-19
Oh I see, anybody got $50 lol?

---

### Post by go_beep_yourself on 2007-10-20
Does anyone know how to solve this problem?

chris@ubuntu:~/Desktop$ sudo ./ETQW-demo-client-1.1-full.r5.x86.run 
[sudo] password for chris:
STUBBED: ftell is 32 bit!
 at /home/timo/Build/mojosetup/fileio.c:246
chris@ubuntu:~/Desktop$

---

### Post by cogadh on 2007-10-20
Are you running 64 bit Ubuntu?

---

### Post by keyo on 2007-10-21
I get...
```
ben@ben-desktop:~$ sudo ./ETQW-demo-client-1.1-full.r5.x86.run
sudo: ./ETQW-demo-client-1.1-full.r5.x86.run: command not found

```

Help a noob out.

---

### Post by DestyNovaX on 2007-10-21
> **keyo said:**
> I get...
```
ben@ben-desktop:~$ sudo ./ETQW-demo-client-1.1-full.r5.x86.run
sudo: ./ETQW-demo-client-1.1-full.r5.x86.run: command not found

```

Help a noob out.

You gotta change permissions and make it executable. 
Try with:
```
chmod -x file_name.run
```

Cheers!

---

### Post by go_beep_yourself on 2007-10-21
> **cogadh said:**
> Are you running 64 bit Ubuntu?

yes

---

### Post by cogadh on 2007-10-21
Then you probably need to install the 32-bit compatibility libraries:
```
sudo apt-get install ia32-libs
```

---

### Post by compiledkernel on 2007-10-21
> **keyo said:**
> I get...
```
ben@ben-desktop:~$ sudo ./ETQW-demo-client-1.1-full.r5.x86.run
sudo: ./ETQW-demo-client-1.1-full.r5.x86.run: command not found

```

Help a noob out.

do a....

sudo -i 

then do a.....

chmod +x ETQW-demo-client-1.1-full.r5.x86.run

then lastly do a......

./ETQW-demo-client-1.1-full.r5.x86.run

---

### Post by go_beep_yourself on 2007-10-21
> **cogadh said:**
> Then you probably need to install the 32-bit compatibility libraries:
```
sudo apt-get install ia32-libs
```

Nope, I already had them all.

```
chris@ubuntu:~$ dpkg -l | grep ia32
ii  ia32-alsa-oss                          1.0.10-1                             32bit package for AMD64. ALSA wrapper for OS
ii  ia32-lib-firefox                       0.1                                  Libraries and other files to help 32bit Fire
ii  ia32-libs                              2.1ubuntu3                           ia32 shared libraries for use on amd64 and i
rc  ia32-libs-gtk                          25                                   gtk+ ia32 shared libraries for with OpenOffi
ii  ia32-libs-kde                          12                                   KDE ia32 shared libraries for with OpenOffic
rc  ia32-libs-sdl                          1.0ubuntu3                           ia32 shared libraries of sdl related package
ii  ia32-sun-java6-bin                     6-03-0ubuntu2                        Sun Java(TM) Runtime Environment (JRE) 6 (32
chris@ubuntu:~$ 
```

---

### Post by neurosis on 2007-10-30
Anyone having mouse issues with this game? I'm having the strangest problem -- when I move the mouse left or right I can only look so far - the view is 'locked' to about 180 degrees to either direction. This is in fullscreen mode. If I switch to windowed mode, the problem goes away.

The only thing I can think of is that I'm running a multi-monitor setup... Anyone else encounter this?

---

### Post by neurosis on 2007-10-30
Well, I discovered a fix for my mouse issues. It was related to multiple monitor setup - it seems that the mouse was "calibrated" before the "NULL, 1280x1024" was chosen for the game, if that makes any sense.. If I pre-set the resolution (using CTRL+ALT+NumpadMinus) before starting the game, the mouse behaves properly. Seems like a bug...

---

### Post by groovomata on 2007-11-12
The ETQW demo runs fine on my ubuntu 7.10 laptop however it does after a while drop out of full screen into a rather small window where I have no mouse input or keyboard input. It is getting rather frustrating. At that point all I can do is hit Ctrl>Alt>Bkspc and then log back in and restart the game. Of course then I lose all of my experience points as well. Has anyone had this happen to them? Does anyone know a fix?
Thanks,
Erik.

---

### Post by neurosis on 2007-11-12
> **groovomata said:**
> The ETQW demo runs fine on my ubuntu 7.10 laptop however it does after a while drop out of full screen into a rather small window where I have no mouse input or keyboard input. It is getting rather frustrating. At that point all I can do is hit Ctrl>Alt>Bkspc and then log back in and restart the game. Of course then I lose all of my experience points as well. Has anyone had this happen to them? Does anyone know a fix?
Thanks,
Erik.

Disabling compiz fixed this for me. Supposedly there is a fix wherein you leave compiz disabled, and go to:
System -> Preferences -> Advanced Desktop Effects Settings -> General Options (Under 'General') and untick 'Unredirect Fullscreen Windows'.

I haven't tried playing with this setting disabled so I can't say if it works or not. 

Please post back here with your results if you do try it!

---

### Post by groovomata on 2007-11-12
> **neurosis said:**
> Disabling compiz fixed this for me. Supposedly there is a fix wherein you leave compiz disabled, and go to:
System -> Preferences -> Advanced Desktop Effects Settings -> General Options (Under 'General') and untick 'Unredirect Fullscreen Windows'.

I haven't tried playing with this setting disabled so I can't say if it works or not. 

Please post back here with your results if you do try it!

It worked perfectly. I didn't need to disable compriz at all. I simply did what you suggested: 
System -> Preferences -> Advanced Desktop Effects Settings -> General Options (Under 'General') and untick 'Unredirect Fullscreen Windows'.
I just played for about an hour and had no problems.
Thanks,
Erik.

---

### Post by neurosis on 2007-11-12
> **groovomata said:**
> It worked perfectly. I didn't need to disable compriz at all. I simply did what you suggested: 
System -> Preferences -> Advanced Desktop Effects Settings -> General Options (Under 'General') and untick 'Unredirect Fullscreen Windows'.
I just played for about an hour and had no problems.
Thanks,
Erik.

Great.. *re-enables Compiz*

:guitar:

---

### Post by smartboyathome on 2007-11-12
Does anyone know where I can get the latest driver to play Quake Wars? I have an Intel GMA 950, and it won't run under gutsy.

---

### Post by sr20ve on 2007-11-15
For Compiz, I just created another user account for gaming that has XGL disabled all together.

I'm running the latest 1.2 client, and it works fine for the most part, but my fps is pretty crappy. I average about 9-15 fps.

Also the game will lock up during map change and the only way to kill the game without a hard reset is to ssh in and logoff my user account. So it's pretty annoying because I have to quit out of the game completely then start it again every map change to avoid a lock up.

Then I also get an occasional random lockup during game play, not often, but probably about once per 1-2 hours of game play.

I'm really hoping for lots of improvements in the 1.3 release.

---

### Post by impact on 2008-01-22
I tried the 1.1 demo and it worked flawlessly. Now with the 1.4 updated demo, it locks up often on the map change... that sucks. (I have to ctrl+alt+F1 to change to a terminal, kill etqw manually, alt+F7 back and ctrl+alt+bacskpace to restart x to get back to a working system...)

---

### Post by frenchn00b on 2008-01-27
btw, Is Quake Wars running slow with Linux ?
What would be a descent pc hardware to play it without any lags ?
 
--
Could the demo download link be placed in the first post of this thread ? thx

---

### Post by Perfect Storm on 2008-01-27
Nope, not on mine. Speedy fast. (but I also have killer hardware).

What's your specs.

---

### Post by Persian_Sniper2000 on 2008-01-27
Hello everyone :-)
i'm new in ubuntu & linux
i have 7900GTX and 2 gig ram and using ubuntu 7.10 ...
downloaded " ETQW-client-1.2-1.4-update.x86"   and   "ETQW-client-1.4-full.x86"  on desktop ( i have both on desktop)then  i installed game with original DVD on Wine ... i have shortcut on my desktop now , but when i clicking on it nothing happens ... i don't know why ...
installation place is :    "/home/x/.wine" wine "C:\Program Files\id Software\Enemy Territory - QUAKE Wars\etqw 
i hope someone can help me step by step about it ...
 it's my first installing game on ubuntu
Thanks

---

### Post by Perfect Storm on 2008-01-27
You don't need wine. ETQW run natively on Linux. Remove the wine ETQW installation.

[http://gaming.gwos.org/doku.php/guides:64bit:etqw](http://gaming.gwos.org/doku.php/guides:64bit:etqw)

Ignore the sudo aptitude install ia32 stuff if you're not running 64-bit

---

### Post by Persian_Sniper2000 on 2008-01-27
> **Artificial Intelligence said:**
> You don't need wine. ETQW run natively on Linux. Remove the wine ETQW installation.

[http://gaming.gwos.org/doku.php/guides:64bit:etqw](http://gaming.gwos.org/doku.php/guides:64bit:etqw)

Ignore the sudo aptitude install ia32 stuff if you're not running 64-bit

Thanks ... i did it ... but there was some problem ,  "Launcher Codes" didn't worked for me ... don't know why .... can u check it , maybe something mising on that page ... maybe ...
thanks

---

### Post by Perfect Storm on 2008-01-27
just **killall gnome-panel** should do it.

---

### Post by Persian_Sniper2000 on 2008-01-30
> **Artificial Intelligence said:**
> just **killall gnome-panel** should do it.

Thanks ... but if it's possible , tell me how i should do it ?!
don't know how i can Active/De-active panels  as i said , I'm new in ubuntu :confused:

---

### Post by Perfect Storm on 2008-01-30
It's a command that you can use in the terminal.

---

### Post by frodon on 2008-02-12
I tried the demo during the week end and i really like the game however i have to find some way to improve performances as i have to much lag to have fun. But if i can fix this i think i will buy the game.

I have :
AMD 3700+ 2.2GHz
nvidia 7600GT
2Go DDR ram

However i checked what version of nvidia driver i'm running and saw that i'm running nvidia-glx package, do you think i can safely install the nvidia-glx-new package in the hope to get some extra performance boost, would you recommend it ?
I don't want to break anything as my computer is working nicely till now so if there's any know drawback to use this driver version i would avoid it.

---

### Post by compiledkernel on 2008-02-12
Uh yes frod. You can and should install the nvidia-glx-new , I used the nvidia-glx-new on my system76.com serval which has the exact same card you are using there.

---

### Post by frodon on 2008-02-13
Aren't they known to create problems with dual core CPUs ? I remember  some threads here about issues related to this drivers specifically, like this one for instance :
[url]http://ubuntuforums.org/showthread.php?t=579586
http://ubuntuforums.org/showthread.php?t=607098[/url]

I guess it should be ok for my desktop computer but for my laptop with dual core i'm not sure.

---

### Post by Perfect Storm on 2008-02-13
I got dual cores in my computer, no trouble at all.

---

### Post by Vadi on 2008-02-13
I'm on a dualcore serval too, using the glx-new one just fine.

---

### Post by frodon on 2008-02-13
Ok i will make a ghost of my ubuntu partition (time for it after 1month since latest ghost image) and move to nvidia-glx-new i guess since gutsy is released it would have been known if these drivers are buggy, it's my last chance to get an acceptable framerate with ET:QW otherwise i will have to officially declare my comp not good enough to run ET:QW because i'm already with low settings in game.

This game eats really a lot of resources.

---

### Post by frodon on 2008-02-14
Yep, i tried but the game is still laggy. Hope they will improve performances in next release as it seems we are many to issue lag and some even with killer hardware since 1.4 release.

---

### Post by Vadi on 2008-02-14
Toned down the graphics settings, yeah?

---

### Post by frodon on 2008-02-14
Yep, all set to minimum, 1024x768 and all the needed tweaks to improve things in autoexec.cfg but still no luck, i'm stuck to 30-60FPS and in hard fight it can go down to 10-15 FPS where it becomes unplayable.

Will check agaiin when they will release next patch or if i find some other tweaks to try.

---

### Post by Vadi on 2008-02-14
Run "glxgears" in the terminal for me for a few mins, what results do you get? (yes, I know it won't be accurate, but just to compare)

---

### Post by frodon on 2008-02-14
As usual around 11000, i don't think it is my config but just the client who don't like some hardware combination, i have met some users with lower specs which run the game without big FPS drop.

---

### Post by Vadi on 2008-02-14
Yeah, that's weird - mine is about "18616 frames in 5.0 seconds = 3723.200 FPS" usually, and I play ETQW on all settings set to high fine.

---

### Post by herbster on 2008-02-18
I'm running the demo and it has no options in the GUI/menu in game to set resolution, settings, etc. for video. Is this available in the retail? I would assume yes but just want to be sure, as I'm about to buy it. The demo has been a bit tricky to work with as I've kind of randomly been fiddling with r_mode and then vidrestart'ing. It does work fine though, and I get a consistent 60fps though I'm sure I should get more (Q6600, 8800GT, 4gb ram).

---

### Post by Vadi on 2008-02-18
The options are there, they're just labelled as "Advanced" or something. Not video or graphics are one is used to.

---

### Post by herbster on 2008-02-18
Ahhh, they're at the top, had missed them before. Thanks Vadi.

---

### Post by herbster on 2008-02-18
Hmmm, my last comment was only from the starting of the training mission in the demo. I'm getting about 30fps in open areas with some stuff going on, doesn't seem right. I should be getting pretty crazy FPS in this game with my hardware, no? It doesn't seem to matter when I change things from high to low in settings or the resolution, it appears fixed. Hopefully someone can help me tweak this sucker...

---

### Post by Vadi on 2008-02-18
I don't know. I have an 8600GT, and all settings are set to "high" except the first one is normal, soft particles are on, and nothing lags.

How do you see your FPS? (I really don't care about it though as long as it's above 25, heh).

---

### Post by herbster on 2008-02-19
com_showfps 1 in console.

I'm going to have to tinker with it some more I suppose.

---

### Post by Vadi on 2008-02-19
So "./etqw-rthread com_showfps 1" to start it?

---

### Post by herbster on 2008-02-19
I only have the demo atm, so I just do ./etqw and bring console down in-game, typing the command. It's there all the time now of course.

---

### Post by etlpkby on 2008-03-18
I'm having similar issues. I've got the UT and SERIOUS SAM installed and I'm getting (periodically) kicked out of full screen mode and into a smaller window where (most of the time) I have no control and have to cntrl-alt-backspace to reset X. It's a PITA!

I'm running rather experimental system

. Ubuntu Hardy Heron (Alpha6) x86_64
. NVIDIA GeForce 9600 card with beta x86_64 drivers (ver: 171_06)

I've tried (after reading this forum) putting my mouse settings AFTER the screen defs in xorg.conf - hope this improves things.

Any other help? It's making any game playing virtually unusable :(

---

### Post by Perfect Storm on 2008-03-18
You need to disable compiz
```
metacity --replace
```

---

### Post by Vadi on 2008-03-18
Yeah. Here's a little applet that you can just press on. and it'll toggle compiz on/off:

[http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)

---

### Post by etlpkby on 2008-03-18
Thanks for reply gents :)

I managed to play 'serious sam' for a couple of hours without any issues after I put the mouse section definition **after** the screen definition in my /etc/X11/xorg.conf. Plus I then switched the windows effects to 'none' in System->Preferences->Appearance->Visual Effects (tab). 

Dunno why I did the latter - I've changed it back now (to 'Normal') - will see if it has any effect.

Otherwise I will try your suggestions and report back.

---

### Post by Vadi on 2008-03-18
Normal will still do it I'm afraid. Either set it to None, or use the Compiz Switch as I recommended.

---

### Post by herbster on 2008-03-18
Yeah, that's the window manager itself etlpkby, it's either running or it's not.

I thought I'd share a few tips that have made the game very playable for me in performance terms. Quoting from a guide:

> Smoothing FPS - Using the Timing Method & FPS unlock, you can smooth out the game.
[autoexec] seta com_unlock_timingMethod "1"
Now, there is 3 different timing methods, 0 1 and 2. 2 provides the most smoothing, but IMO it did a WORSE drop smoothing the FPS than 1 does. 1 makes the game smoother and better looking, but drops your FPS a bit. 0 doesn't technically drop your FPS (it gives you the maximum FPS you can get), but it isn't nearly as soon as it could be. Now, since the server is actually running at 30fps, things will look a bit weird once you go over the 30 FPS caps, but it will bring you smoother gameplay.
[autoexec] seta com_unlock_maxFPS 120

For the unlock_maxfps command, I set it to 0 so it is basically "unlimited." It will go from 40 to 500 at times. I know the game is capped at 60 (the engine) and the server side at 30, but the smoothness needs to be up there for me or it's rather unplayable with respect to aiming and whatnot. Hope it helps someone.

---

### Post by Vadi on 2008-03-18
Weird, it's just fine on default settings for me. (then again, 30 fps does it for me. I can't see a difference between 50 or 500)

---

### Post by herbster on 2008-03-22
Anyone experienced an issue with playing fine on a server, disconnecting, browsing again for another server, connecting and having the game hang on connecting and consequently freezing if the Cancel on connect dialog button is hit?

---

### Post by Vadi on 2008-03-22
Yeah, had it happen.

---

### Post by herbster on 2008-03-22
What's the dilly, a bug, or?

---

### Post by Vadi on 2008-03-22
Probably bug, it shouldn't be doing that :/

---

### Post by herbster on 2008-03-23
Right, ah well, it works perfectly asides from that ;)

Any recommended servers you play on?

---

### Post by Vadi on 2008-03-23
migamer.net, tacticalgamer, house of pain

Nick is "Vadi.buntu" if you ever see me about

---

### Post by herbster on 2008-03-29
Thanks, I'll be on the lookout for ya ;)

I grabbed some tutorial videos from the enemyterritory.com forums, as this game is way more detailed than Wolf ET. I think a lack of "official" tutorials from iD probably hurt this game's potential, as there's a lot to learn if one never played Wolf ET to begin with. The "training mode" playing the PC isn't nearly enough for a newcomer.

---

### Post by Vadi on 2008-03-29
Didn't play Wolfenstein, just jumped into the online play really. You get the stuff eventually, the UI is quite user-friendly.

---

### Post by paratox on 2008-04-13
since hardy beta upgrade etqw isn`t working. the mouse is jumping crazy around and is sometimes invisible. it`s unpossible to play the game. in gutsy it worked like a charm.

here some infos about my machine:

c2d e6400 @ 2920MHz
asus p5b wifi deluxe
2048mb RAM
nvidia 7900 gtx
mouse: logitech g5 refresh
keyboard: logitech g15

os: ubuntu hardy heron beta

the actual nvidia restricted driver is installed. glxgears reports about 12800 FPS. compiz is disbaled, i use metacity --replace.
the mouse is using the evdev driver, wich has some changes in the new version for handling it in xorg.conf.

here my xorg.conf:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Logitech G5"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse"
	Option		"ZAxisMapping"	"invert"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons"	"9"
	Option		"Resolution"	"800"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Inputdevice	"Logitech G5"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

and here the console output of etqw:

```
paratox@paratox-desktop:~/games$ ./etqwstarter
ETQW 1.4.12247.12247  linux-x86 Jan  4 2008 13:52:05
found interface lo - loopback
found interface eth2 - 192.168.0.131/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /home/paratox/games/etqw/base/game000.pk4 with checksum 0x1eefa237
Loaded pk4 /home/paratox/games/etqw/base/game002.pk4 with checksum 0x5f707685
Loaded pk4 /home/paratox/games/etqw/base/pak000.pk4 with checksum 0x442eb08b
Loaded pk4 /home/paratox/games/etqw/base/pak001.pk4 with checksum 0x10e16e6
Loaded pk4 /home/paratox/games/etqw/base/pak002.pk4 with checksum 0x8dbe7353
Loaded pk4 /home/paratox/games/etqw/base/pak003.pk4 with checksum 0x99dfcabb
Loaded pk4 /home/paratox/games/etqw/base/pak004.pk4 with checksum 0x7e49f838
Loaded pk4 /home/paratox/games/etqw/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /home/paratox/games/etqw/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /home/paratox/games/etqw/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /home/paratox/games/etqw/base/zpak_english000.pk4 with checksum 0x977c7bd0
Loaded pk4 /home/paratox/games/etqw/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /home/paratox/games/etqw/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /home/paratox/games/etqw/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /home/paratox/games/etqw/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /home/paratox/games/etqw/base/zpak_german000.pk4 with checksum 0xd42cc5af
Loaded pk4 /home/paratox/games/etqw/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /home/paratox/games/etqw/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /home/paratox/games/etqw/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /home/paratox/games/etqw/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /home/paratox/games/etqw/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /home/paratox/games/etqw/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /home/paratox/games/etqw/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /home/paratox/games/etqw/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /home/paratox/games/etqw/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /home/paratox/games/etqw/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /home/paratox/games/etqw/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Current search path:
/home/paratox/.etqwcl/base
/home/paratox/games/etqw/base
/home/paratox/games/etqw/base/zpak_spanish002.pk4 (119 files)
/home/paratox/games/etqw/base/zpak_spanish001.pk4 (13 files)
/home/paratox/games/etqw/base/zpak_russian002.pk4 (119 files)
/home/paratox/games/etqw/base/zpak_russian001.pk4 (13 files)
/home/paratox/games/etqw/base/zpak_polish002.pk4 (119 files)
/home/paratox/games/etqw/base/zpak_polish001.pk4 (13 files)
/home/paratox/games/etqw/base/zpak_korean002.pk4 (12 files)
/home/paratox/games/etqw/base/zpak_korean001.pk4 (12 files)
/home/paratox/games/etqw/base/zpak_korean000.pk4 (6 files)
/home/paratox/games/etqw/base/zpak_german002.pk4 (119 files)
/home/paratox/games/etqw/base/zpak_german001.pk4 (13 files)
/home/paratox/games/etqw/base/zpak_german000.pk4 (1018 files)
/home/paratox/games/etqw/base/zpak_french002.pk4 (119 files)
/home/paratox/games/etqw/base/zpak_french001.pk4 (13 files)
/home/paratox/games/etqw/base/zpak_english002.pk4 (117 files)
/home/paratox/games/etqw/base/zpak_english001.pk4 (9 files)
/home/paratox/games/etqw/base/zpak_english000.pk4 (1018 files)
/home/paratox/games/etqw/base/pak007.pk4 (1510 files)
/home/paratox/games/etqw/base/pak006.pk4 (3 files)
/home/paratox/games/etqw/base/pak005.pk4 (2172 files)
/home/paratox/games/etqw/base/pak004.pk4 (72 files)
/home/paratox/games/etqw/base/pak003.pk4 (1133 files)
/home/paratox/games/etqw/base/pak002.pk4 (1637 files)
/home/paratox/games/etqw/base/pak001.pk4 (1067 files)
/home/paratox/games/etqw/base/pak000.pk4 (9350 files)
/home/paratox/games/etqw/base/game002.pk4 (3 files)
/home/paratox/games/etqw/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
Decompressing the global token cache...3560Kb
------------------------------
execing 'etqwconfig.cfg'
r_displayRefresh is read only.
execing 'localization/german/defaultbinds.cfg'
execing 'etqwbinds.cfg'
execing 'autoexec.cfg'
Vendor: Device:
thread priority set to 1
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1280x1024
SDL_ListModes:
1280x1024 1280x960 1280x800 1280x768 1152x864 1024x768 960x600 896x672 840x525 832x624 800x600 
800x512 720x450 640x512 640x480 640x400 640x384 640x350 576x432 512x384 416x312 
400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
vsync: SDL reports -1076784152 - broken?
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_ARB_texture_rectangle
X..GL_EXT_texture_rectangle not found
...using GL_EXT_stencil_wrap
...using GL_EXT_stencil_two_side
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using GL_EXT_depth_bounds_test
...using GL_ARB_point_sprite
...using GL_ARB_occlusion_query
...using GL_EXT_framebuffer_object
...using GL_EXT_packed_depth_stencil
...using GL_EXT_blend_minmax
...using GL_ARB_multisample
...using GL_ARB_shader_objects
...using GL_ARB_vertex_shader
...using GL_ARB_fragment_shader
...using GL_ARB_fragment_program_shadow
...using GL_ARB_shadow
...using GL_ARB_depth_texture
...using GL_EXT_gpu_program_parameters
...using GL_EXT_timer_query
X..GL_GREMEDY_string_marker not found
X..GL_EXT_texture_compression_latc not found
---------- R_ARB2_Init ----------
Cg available.
---------------------------------
thread priority set to 2
thread priority set to 2
using ARB_vertex_buffer_object memory
renderSystem initialized.
--------------------------------------
72 strings read from localization/german/strings/bindings.lang
485 strings read from localization/german/strings/chat.lang
883 strings read from localization/german/strings/code.lang
2186 strings read from localization/german/strings/game.lang
3199 strings read from localization/german/strings/guis.lang
3375 strings read from localization/german/strings/lifestats.lang
3513 strings read from localization/german/strings/loadtips.lang
3852 strings read from localization/german/strings/locations.lang
4377 strings read from localization/german/strings/maps.lang
4444 strings read from localization/german/strings/tasks.lang
/proc/cpuinfo CPU frequency: 2920.18 MHz
Couldn't open journal files
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.15
opened Alsa PCM device default for playback
device buffer size: 5644 frames (22576 bytes)
allocated a mix buffer of 16384 bytes
--------------------------------------
-------- ALSA Microphone Init --------
device buffer size: 3292 frames (6584 bytes)
microphone initialized
--------------------------------------
initializating SDL Joysticks
initialized 0 controller(s)
-------- Initializing Session --------
----------------- BSE Init ------------------
--------- BSE Created Successfully ----------
session initialized
--------------------------------------
found DLL in pak file: /home/paratox/games/etqw/base/game002.pk4/gamex86.so
copy gamex86.so to /home/paratox/.etqwcl/base/gamex86.so
game using generic code for SIMD processing
enabled Flush-To-Zero mode
--------- Initializing Game ----------
gamename: baseETQW-1
gamedate: Dec 13 2007
Initializing global UI namespaces
...23 namespaces
...239 properties
Initializing event system
...898 event definitions
Initializing class hierarchy
...163 classes, 395120 bytes for event callbacks
WARNING: Couldn't load sound 'video/intro_1024x512.theora', defaulting
WARNING: idDeclLocal::ParseLocal Failed to Parse decl 'video/intro' in file 'sounds/cinematics.sndshd' line 0
game initialized.
--------------------------------------
------------- Initialized in 08 -------------
--- Common Initialization Complete ---
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 11873
2920 MHz CPU
2032 MB System Memory
detecting video ram (set sys_videoRam on command line to override) ..
found XNVCtrl extension 1.14
512 MB Video Memory
Async thread started
PunkBuster Client: Attempting to resolve master6.evenbalance.com
PunkBuster Client: Resolved to [69.59.138.4]
PunkBuster Client: PunkBuster Client (v2.012 | A0) Enabled
Opening IP socket: localhost:-1
PunkBuster Client: Game Version [ETQW 1.4.12247.12247  linux-x86 Jan  4 2008 13:52:05]
PunkBuster Client: Not Connected to a Server
no local conversion for SDL keysym: 313
no local conversion for SDL keysym: 313
set r_fullscreen = 0.000000
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
vsync: SDL reports 178345336 - broken?
initializating SDL Joysticks
initialized 0 controller(s)
set r_fullscreen = 1.000000
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
vsync: SDL reports 178345336 - broken?
initializating SDL Joysticks
initialized 0 controller(s)
------------ Game Shutdown -----------
Shutdown event system
--------------------------------------
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close mic pcm
close pcm
dlclose
--------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
shutdown terminal support
paratox@paratox-desktop:~/games$ 


```

after hours of googling i found no solution. help me, please!

**[COLOR="Red"]EDIT:[/COLOR]**

ok, it looks like i didn`t google well anough. ^^
i found the following solution:

put this in the etqw starter script or execute it in a terminal before playing the game:

```

export SDL_VIDEO_X11_DGAMOUSE=0

```

after this the mouse (in my case the logitech g5 refresh) works like it should!
i hope this helps anyone with the same problem! :)

---

### Post by lusankya23 on 2008-04-29
Upgraded to Kubuntu 8.04 the other day and also noticed the problem with the mouse scroll delay in ETQW and other first person shooter games that take up the full screen (such as Nexuiz). I had no problems with 7.10. 

Although the export SDL_VIDEO_X11_DGAMOUSE=0 does work for me, this is not a real fix. DGAMOUSE works way better in games and having it disabled is a really bad thing for a gamer.

SDL_VIDEO_X11_DGAMOUSE=0 results in much less precise mouse control as well as a lack of smoothness, although it is a temporary fix for the scroll wheel problem.

If anyone could come up with a real solution to this problem it would be much appreciated.

Thanks in advance!

-Lusankya23

---

### Post by ELD on 2008-04-30
I got a mouse delay in any game pack on the Spring engine too, what is up with that?

> 
export SDL_VIDEO_X11_DGAMOUSE=0


Made my mouse wheel run as it should do in Spring.

Has anyone submitted a bug report for it, i would like to add my experiences with the bug too.

---

### Post by _Stevie_ on 2008-04-30
hmm thats annoying. i have this problem in every game i play.
i cant move the mouse correctly, it always falls back in the right corner.
also using evdev driver here (logitech mouse with extra buttons).
its really annoying that it worked in gutsy and now fails in hardy.

---

### Post by neobuzzsaw on 2008-04-30
Ok can anyone help?

Just installed ETQW no problem :)

when I load it my monitor goes off and reports it cant display this resolution but I can hear the sound?

Ubuntu Hardy

Nvidia 7600 GS

---

### Post by gotthardt on 2008-04-30
@neobuzzsaw
I have had the same problem with monitor frequencies, resolutions, etc on etqw.

I fix it by changing r_mode in the .etqwcl/base/etqwconfig.cfg - try 4 or 5, etc..

r_mode "9" //screen resolution,4=800x600,5=1024x768,9=1280x1024,13=1680x1050

Try different values and restart etqw

---

### Post by neobuzzsaw on 2008-05-01
Thanks for the reply but I dont seem to have .etqwcl/base/etqwconfig.cfg

is this because I installed the game in a folder in my home directory?

---

### Post by ELD on 2008-05-01
> **neobuzzsaw said:**
> Thanks for the reply but I dont seem to have .etqwcl/base/etqwconfig.cfg

is this because I installed the game in a folder in my home directory?

Show all hidden files and folders and you should see it in your home directory.

---

### Post by httphttp on 2008-05-01
> **_Stevie_ said:**
> hmm thats annoying. i have this problem in every game i play.
i cant move the mouse correctly, it always falls back in the right corner.
also using evdev driver here (logitech mouse with extra buttons).
its really annoying that it worked in gutsy and now fails in hardy.

I have exactly the same problem if i try to play wolfenstein enemy territory or urban terror (didnt try other games). My mouse keeps falling in the lower right corner... For wolfenstein enemy territory if i put in etconfig.cfg seta in_dgamouse "0" the mouse is not falling anymore, however it becomes "jerky" and its difficult to play like that. The default value for in_dgamouse is 1 (falling in the lower right corner) and if i use value 2 its the same as using 1. Same as _Stevie_ i also use evdev and as he said it used to work in gutsy:) 

Would be greate if someone could shed some light on this one...

EDIT: My mouse is Logitech M-BJ69

---

### Post by httphttp on 2008-05-01
> **httphttp said:**
> I have exactly the same problem if i try to play wolfenstein enemy territory or urban terror (didnt try other games). My mouse keeps falling in the lower right corner... For wolfenstein enemy territory if i put in etconfig.cfg seta in_dgamouse "0" the mouse is not falling anymore, however it becomes "jerky" and its difficult to play like that. The default value for in_dgamouse is 1 (falling in the lower right corner) and if i use value 2 its the same as using 1. Same as _Stevie_ i also use evdev and as he said it used to work in gutsy:) 

Would be greate if someone could shed some light on this one...

EDIT: My mouse is Logitech M-BJ69

Ok now i found the solution:) In the xorg.conf under the mouse section i removed the line Option "CorePointer". I hope it works for you as well _Stevie_:)

EDIT: For wolfenstein enemy territory i had to put seta in_dgamouse "0" in etconfig.cfg becouse if the value was 1 or 2 the mouse was lagging. Urban terror is working normally without any modification.

---

### Post by _Stevie_ on 2008-05-01
hey httphttp!

thanks for the tip, i will try that. cant reboot the lappy right now, encoding some movie :)

will keep you up to date!

cheers,

stevie

---

### Post by z0mbie on 2008-05-03
Hey guys I installed the ETQW Demo works awesome, even the sound. I have [nVidia 173.08 beta]("http://www.nvidia.com/object/linux_display_ia32_173.08.html") drivers installed. It's even playable with Compiz turned on. 

How are you guys liking the game so far? I was expecting a bit more, but it's actually a fun game regardless of what people say that it's a Battlefield 2 mock. One major positive similarity with BF2 is ETWQ's teamplay, which I think ETWQ has a better focus on. It has more strategy than your average FPS, sort of reminded me of Starcraft.

---

### Post by Vadi on 2008-05-04
Haven't played BF2 myself. I find that it's not game itself but a good team also that really makes it enjoyable.

Or, well, when you join a game that's way above your level you realize that you still got ways to go...

---

### Post by FixedSys on 2008-05-04
I have searched for this but cannot find it.
I have ubuntu 8.04 installed on with it own partitions; This is a dual boot WinXP and now Ubuntu gaming pc.

I wanted to see if ETQW ran better under linux vs winxp (the assumption would be yes but I would like to see it)

My goal is to NOT have two copies of the game installed.  I would like windows to be able to look into the same install folder as Ubuntu will have to look to run the game.  I am downloading the full 1.4 Linux install now.  

Is my goal possible or do I have to waste space and have the game installed fully twice?

Thanks

---

### Post by Perfect Storm on 2008-05-04
I don't think it's possible.
Maybe installing ETQW on a third partition - but again, I think it comes down to windows uses fat/NFTS and linux uses EXT2/3 etc. etc. so there will be trouble reading/writing and accessing, and both have diffrent file stucture.

---

### Post by Vadi on 2008-05-04
You probably can point it to the maps on the windows partition, but then performance will be affected... it's a speed/space tradeoff.

---

### Post by FixedSys on 2008-05-04
ETWQ in 8.04 - OSS sound(SB-XFI) / Nvidia 7800GS (AGP/ direct rendering is working. (World of Warcraft plays nice under wine)

Went ahead and did full install onto linux partition.  I figured I would get that working 1st then address the other possibility.  I installed the game per this procedure and pulled the pak files and mega textures from the winxp install folder per this links instructions.

[http://ubuntuforums.org/showthread.php?t=583762]("http://ubuntuforums.org/showthread.php?t=583762")

The game launches, switches screen resolution to its 800by600 default. (Acking just like it does if installed on winxp machine)

It gets to Loading UI then kicks me out to the desktop leaving the screen resolution at this 800by600 and mouse is not responsive. I am able to use CTRL-ALT-DEL and enter to shutdown because I cannot get to any thing with the mouse nor keyboard.

EDIT
I launched it from a terminal in hopes to try to see what was killing it.
Many NO FONT errors!
ie:```
WARNING: mainmenu: 'lstAchievementOverviewVehicles' has no font set
WARNING: mainmenu: 'lstAchievementList' has no font set
WARNING: mainmenu: 'lstStatsOverviewGDF' has no font set
WARNING: mainmenu: 'lstStatsOverviewStrogg' has no font set
WARNING: mainmenu: 'lstStatsWeapons' has no font set
WARNING: mainmenu: 'lstStatsToolsGDF' has no font set
WARNING: mainmenu: 'lstStatsVehicles' has no font set
WARNING: mainmenu: 'lstStatsDeployables' has no font set
WARNING: mainmenu: 'lstStatsOverview' has no font set
WARNING: mainmenu: 'lstStatsOverviewClasses' has no font
```

Appears the full install did not have one of the font files to install.

Fix was to:
copy the etqw/base/video directory
copy zpak_english000.pk4 to etqw/base/
Taken from: 
[http://community.enemyterritory.com/forums/showthread.php?t=14032&page=4]("http://community.enemyterritory.com/forums/showthread.php?t=14032&page=4")

You do not need the video directory at all.  (in my windows install I had removed the file in the video directory to speed game launch)

In this situation I did not even copy over the video folder and only the zpak_english000.pk4 file.  The game runs excellent  in my monitor's native 1900x1200 resolution faster then it did under windows but with one problem: NO SOUND!

I was not surprised.  Also OSS is installed and can play sound. WoW under wine (with sound driver OSS selected for its win config) all play sound.  The problem is the ubuntu does not play system sounds at all, the sound applications in the o/s do not work. (ie: Sound Recorder)  I am hoping once I get Ubuntu to work 100% with OSS and system sounds work that ETQW will have sound.

---

### Post by _Stevie_ on 2008-05-05
> **httphttp said:**
> Ok now i found the solution:) In the xorg.conf under the mouse section i removed the line Option "CorePointer". I hope it works for you as well _Stevie_:)

EDIT: For wolfenstein enemy territory i had to put seta in_dgamouse "0" in etconfig.cfg becouse if the value was 1 or 2 the mouse was lagging. Urban terror is working normally without any modification.

unfortuneately this didnt help with quake3 :(

---

### Post by Zanshin on 2008-05-07
> **FixedSys said:**
> 
I wanted to see if ETQW ran better under linux vs winxp (the assumption would be yes but I would like to see it)


Uh, not for me.  

ETQW is not running better for me in linux that winxp.  HUH?  This wasn't the result I was expecting either.  :-k

P4 3.0GHz, Hyperthreading enabled in bios, 3.0 GB RAM, brand-spanking new BFGs nVidia 9600GT OC.  Compiz off, metacity running.  Running nvidia beta driver 171.06.  glxgears running consistently at about 11000 fps.   

Linux seems more susceptible to jerkiness in video at higher quality, resoluton, etc than WinXp.  Higher settings in linux also seem to max out cpu as shown on system monitor.  Runs pretty solid with FPS locked at 30 with mostly low quality settings, but that just doesn't seem right to me.  GPU temp doesn't seem to go up by more than a couple degrees during gaming, so I'm guessing it isn't really utilized to max.  Hoping better beta or prod release drivers soon will resolve issue and this isn't just a cpu bottleneck issue.  

If it was cpu, i'd think it would impact the windoze side also (which runs solid at for me at unlocked 60-90 fps and high quality graphics, with cpu always in 60-80% util range).

---

### Post by Perfect Storm on 2008-05-08
It could be the beta drivers fault - I run ETQW at max. and there seems to be some glitches with the beta driver (which is understandable afterall it's beta driver).

---

### Post by Vadi on 2008-05-08
I don't think some people understand what a "beta" is, it's just the "latest version of drivers that I could find" :/

---

### Post by Zanshin on 2008-05-08
> **Artificial Intelligence said:**
> It could be the beta drivers fault - I run ETQW at max. and there seems to be some glitches with the beta driver (which is understandable afterall it's beta driver).

That is what i'm thinking.  Thinking of giving the 173.08 beta a shot.  

[Vadi: yes, I know what beta software is  :lolflag:  I normally prefer not to be a beta tester, but apparently it is the only software released so far for my new 9600GT]

---

### Post by Vadi on 2008-05-08
Ahh yes then. Apologies :)

---

### Post by a2sidedcoin on 2008-05-08
Hey everyone, I have it up and running, visually, just fine, I have Heron install x64, Nvidia 8800 GTS, onboard sound, everything else I have on the install is working fine, I've installed the update (had a bit of problem with that), and I have also got it running 1024x768 on high...  

Sound is just not working at all in this game... anyone have any ideas or what do I need to show you... 

I'm a n00b on linux, but not computers by a mile.. I've really accepted the linux way, I love coding, so, it's actually fun learning.. 

someone help!!

~coin

---

### Post by Zanshin on 2008-05-09
> **a2sidedcoin said:**
> 
Sound is just not working at all in this game... anyone have any ideas or what do I need to show you... 
~coin

We have the same user profile, my friend.  Strong computer background, just not in linux.  lol

What i did:
On the Gnome/Ubuntu desktop, go to system/preferences/sound.

For my intel motherboard integrated sound, I had to choose the "STAC92xx Analog Drivers" for the "Sound Events", "Music and Movies", and "Audio Conferencing" options.  For "Default Mixer Tracks" I used my Device "HDA Intel (Alsa Mixer)".

Once you've picked all your sound devices, you must go crank up the sound.  Double left click on the speaker icon in the upper right corner by the shutdown/restart button, then you can get into all the sound controls.  Edit/preferences will let you add all the controls available to you.  

You will not see any sound devices listed in game.  some bug with that.  If you are just using ingame voip, you should then be done and all should worky-worky.  If you need to add Teamspeak, you'll have a new set of issues, cuz the game sound and ts use different, somewhat conflicting drivers:  use alsa for game and oss for TS.  

Good luck!!  :biggrin:

---

### Post by Zanshin on 2008-05-09
> **Zanshin said:**
> Thinking of giving the 173.08 beta a shot.  

173.08 Beta = no joy  :(  glxgears=> ~7300 fps

Back to 171.06 Beta.  glxgears => ~11000 fps

[all other configs equal]

---

### Post by a2sidedcoin on 2008-05-09
> **Zanshin said:**
> We have the same user profile, my friend.  Strong computer background, just not in linux.  lol

What i did:
On the Gnome/Ubuntu desktop, go to system/preferences/sound.

For my intel motherboard integrated sound, I had to choose the "STAC92xx Analog Drivers" for the "Sound Events", "Music and Movies", and "Audio Conferencing" options.  For "Default Mixer Tracks" I used my Device "HDA Intel (Alsa Mixer)".

Once you've picked all your sound devices, you must go crank up the sound.  Double left click on the speaker icon in the upper right corner by the shutdown/restart button, then you can get into all the sound controls.  Edit/preferences will let you add all the controls available to you.  



You will not see any sound devices listed in game.  some bug with that.  If you are just using ingame voip, you should then be done and all should worky-worky.  If you need to add Teamspeak, you'll have a new set of issues, cuz the game sound and ts use different, somewhat conflicting drivers:  use alsa for game and oss for TS.  

Good luck!!  :biggrin:
Thanks!  I got it working all on my own!!!   I'm so proud.. hehe..

[solution for me]

I had Pulse Audio drivers interfering, so I had to :
```
kill -9 'pgrep pulseaudio'
```

Went in selected the ALSA drivers, and works like a charm, at highest detail, 1024x768, everything cranked, runs 10x better than on a windows box... yay!!!

---

### Post by helino on 2008-05-28
I've also got the game up and running with sound and everything, it worked like a charm. It would be fun to play against/with other ubuntu user. If you ever see helino in a game, then it's me! :)

---

### Post by spadewarrior on 2008-05-31
Hi everyone. I'm not getting performance on my machine. 

I havea P4 2.8ghz, 1gb RAM, nVidia 7600GT 512mb. Even with all the settings down to minimum and running at 800x600 the game is jerky and my FPS jump down as low as 10 to 15. I'm running hardy heron.

Any ideas? Or are my specs just not good enough?

---

### Post by Vadi on 2008-05-31
Do you know what drivers are you using? Should enable the restricted ones.

---

### Post by spadewarrior on 2008-05-31
I'm using the proprietary nVidia drivers.

---

### Post by Vadi on 2008-06-01
I don't know then, it should be working okay for you.

---

### Post by spadewarrior on 2008-06-01
Hmmm it's odd. I have no idea why performance is so bad on this machine. I've even tried enabling the hardy-proposed repository and installed the newer kernel. I then decided to try xubuntu to see if there would be any perfomance boost. It's a bit faster but not by much.

If anyone has any ideas I'd be grateful to hear them.


Thanks.

---

### Post by ad_267 on 2008-06-27
> **spadewarrior said:**
> Hi everyone. I'm not getting performance on my machine. 

I havea P4 2.8ghz, 1gb RAM, nVidia 7600GT 512mb. Even with all the settings down to minimum and running at 800x600 the game is jerky and my FPS jump down as low as 10 to 15. I'm running hardy heron.

Any ideas? Or are my specs just not good enough?

My specs aren't as good as that but I'm still getting pretty jerky game play. Anyone know the command to see fps?

I've got P4 2.4GHz, 1.5GB RAM, nvidia 6600GT 128MB. I've got it on low settings at 800x600 and it's pretty jerky for me too. Is it just my old video card? The computer's also a few years old now so could be other things slowing it down.

---

### Post by Vindicate86 on 2008-07-06
How's the install work with the 1.5 client installer? Is it just install and go? Or do you have to grab some **** from the Quake Wars DVD?

[http://www.gamershell.com/download_26200.shtml](http://www.gamershell.com/download_26200.shtml)

---

### Post by ELD on 2008-07-06
> **Vindicate86 said:**
> How's the install work with the 1.5 client installer? Is it just install and go? Or do you have to grab some **** from the Quake Wars DVD?

[http://www.gamershell.com/download_26200.shtml](http://www.gamershell.com/download_26200.shtml)

Of course you need things from the DVD, their not going to give out the game for free are they.

---

### Post by Vindicate86 on 2008-07-06
Well I have the DVD... I guess I could have asked where the tutorial is for what I need to grab from the DVD... Cuz I cannot for the life of me find it. All I can find is ppl not being able to install Quake Wars Demo from way back in October 07...

---

### Post by Vadi on 2008-07-06
I think you just start the installer and it'll find the game data itself. So just put the dvd in and start it.

If you'll run into any yrouble lemme know.

---

### Post by MissingLink on 2008-07-06
Just installed Quake Wars! Everything smooth except I get a few slowdowns now and then, ping reaches about 300 ms, frames drop to 5~10 FPS. I can't figure out why, since I've had extreme firefights without any kind of slowdowns, so I'm guessing it's not graphic-wise. Any help guys?

---

### Post by AFarris01 on 2008-07-07
i just recently decided to give quake wars a try, since i used to love playing quake 3 arena on the old console :), and since a big name has decided to do a native linux port for a sweet looking game...but unfortunately ive got a couple of problems...

the install worked flawlessly, and i had the game up and running in a matter of minutes, however every time i exit out of it when its in full screen, my screen stays the size of the game window, and ive gotta change the screen resolution in order to get it back to normal.  its not like everything on the screen is tiny, or squished in a corner or something...its like the resolution of my desktop stays normal (1400x1050), but i can only look through an 1152x864 sized window of it.  it even lets me pan around the desktop when i move my mouse around...its wierd.

the other problem is with sound.  i know there were a few posts above about changing to alsa, or killing pulseaudio, but unfortunately every time i try to use alsa with my sound card, it malfunctions severely, and i can only get sound out of one of my 6 speakers, no matter what i try.  pulseaudio so far has been the only way for me to use my sound card fully, and get all of my speakers to work...so trying to switch to alsa really isnt a viable option for me.  is there any way for me to force 
ET to use pulseaudio?

thanks!

---

### Post by klerfayt on 2008-08-16
The message you have entered is too short. Please lengthen your message to at least 1 characters.

---

### Post by poisonkiller on 2008-12-22
Please delete this post.

---


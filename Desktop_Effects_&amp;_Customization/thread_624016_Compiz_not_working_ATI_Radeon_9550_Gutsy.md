---
title: "Compiz not working ATI Radeon 9550 Gutsy"
date: 2007-11-26
forum: Desktop Effects &amp; Customization
---

### Post by darolu on 2007-11-26
I made a fresh install of Gutsy, Compiz wasn't working so I followed this instructions:

[http://ubuntuforums.org/showpost.php?p=3547657&postcount=7](http://ubuntuforums.org/showpost.php?p=3547657&postcount=7)

After doing that compiz is not working and my entire system is running very slow, some graphics are damaged and I have no clue how to fix it.
When I run compiz on the console I get this:

```

dan@dan-desktop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

Also my keyboard configuration is wrong, I've set it to spanish was working before I followed the instructions and now is set to english.
Any Ideas on how to fix it?
Thanks in advance.

---

### Post by macaholic on 2007-11-26
What is the output of fglrxinfo?

---

### Post by darolu on 2007-11-26
```

dan@dan-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

Right now I had to uninstall xgl (xserver-xgl), so now my computer is running fine again (no more 1fps), I read in that thread to follow the steps ignoring the xserver-xgl part, I did but my compiz is not working, now I get this:
```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```
So far looks like ATI cards (at least my model) can't work on XGL with any of the drivers (open and private) :( I hope someone can give me some more ideas to fix it.
Thanks again.

---

### Post by mpierce on 2007-11-26
Modify your /etc/gdm/gmd.conf-custom:

[servers]
0=aiglx

Add new server section:
[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air :0
flexible=true

Restart X from terminal
sudo /etc/init.d/gdm restart

See my post on nVidia confusion and make sure your xorg file has the appropriate sections enable as I discussed as these are applicable for your card as well. 

Hope this helps...

---

### Post by darolu on 2007-11-27
Thanks for the help mpierce, I followed this post of yours (I hope is the one you mentioned, is the only one I could find that matches):
[quote="mpierce"]
If you use AIGLX, you will need the following modules in your /etc/X11/xorg.conf
Section "Module"
Load "dri"
Load "dbe"
Load "glx"
Section "Device"
Option "XANNoOffscreenPixmaps"
Server "Screen"
Option "AIGLX" "true"

uncomment
Section "DRI"
Mode 0666
EndSection

insert
Section "Extensions"
Option "Composite" "true"
EndSection
[/quote]

Then I edited the gmd.conf-custom as you told me to do; I'm sorry to say it didn't work, I had to reboot (rebooting x made the system crash) and when I logged in my video driver was not configured I re-configure it and try to run compiz and got this:
```

dan@dan-desktop:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '1002:4153' found 
aborting and using fallback: /usr/bin/metacity

```
I don't know if it means something but my keyboard settings changed too (I simply had to change it back but thought would be helpful). I really apreciate the help given so far, I'll keep researching and hope someone can give me more ideas to fix this.

---

### Post by Takster on 2007-11-27
Radeon 9600 user here, compiz, emerald and that with all it's 3D bells and whistles works just fine using this guide. 
[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#)
Just use the very latest ATI driver instead and change the package name in the guide to reflect that.

I went through every error possible over a few day's, including that keyboard one, this is the only tutorial that got it all working in harmony. Good luck. :)

---

### Post by Dynar on 2007-11-27
I was forced to do a reinstall of Ubuntu just now, I fiddled too much with the graphics. I also have the 9550. I couldn't get it to work either. I'm going to try the link above and see if I get positive results.

I had Compiz and Emerald running before the system scrambled the graphics. My only option was safemode. It wouldn't let me back up some files.. anyway. I hope with a fresh start I can get this going. I haven't touched the Restricted Driver Manager yet. Not exactly sure what to do.. I'll post results using the link above.

---

### Post by Dynar on 2007-11-27
> **Takster said:**
> Radeon 9600 user here, compiz, emerald and that with all it's 3D bells and whistles works just fine using this guide. 
[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#)
Just use the very latest ATI driver instead and change the package name in the guide to reflect that.

I went through every error possible over a few day's, including that keyboard one, this is the only tutorial that got it all working in harmony. Good luck. :)


Worked like a charm, here are my results by following with a fresh install, touching nothing but the terminal and entering the commands shown in the blog.

Here are my results:

```
dynar@Einstein:~$ glxinfo
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.0.6958 Release
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
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
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
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
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x84 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

fgl_glxgears

```
dynar@Einstein:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
2450 frames in 5.0 seconds = 490.000 FPS
2690 frames in 5.0 seconds = 538.000 FPS
2712 frames in 5.0 seconds = 542.400 FPS
2689 frames in 5.0 seconds = 537.800 FPS
2715 frames in 5.0 seconds = 543.000 FPS
2689 frames in 5.0 seconds = 537.800 FPS

```

glxgears

```
dynar@Einstein:~$ glxgears
12610 frames in 5.0 seconds = 2521.943 FPS
12607 frames in 5.0 seconds = 2521.389 FPS
12599 frames in 5.0 seconds = 2519.777 FPS
12595 frames in 5.0 seconds = 2518.924 FPS
12604 frames in 5.0 seconds = 2520.707 FPS

```

Yeah, I like naming my computer Einstein xD

---

### Post by Takster on 2007-11-28
> **Dynar said:**
> Worked like a charm, here are my results by following with a fresh install, touching nothing but the terminal and entering the commands shown in the blog.

Yeah, I like naming my computer Einstein xD

Awesome, great stuff.

I was pretty un-original and called my PC 'ubuntu' :P

---

### Post by Dynar on 2007-11-28
> **Takster said:**
> Awesome, great stuff.

I was pretty un-original and called my PC 'ubuntu' :P

Hehe.. :lolflag:

Anyway, after using this method, I do have direct rendering, but firefox, running movies and playing games seems to be flickering my screen. I cant watch movies in full screen. If it's small enough it will run.. perhaps my CPU is doing all the memory work.. Any possible way to solve that? 

For the rest, I'm quiet satisfied. Compiz seem to be working somewhat.

---

### Post by darolu on 2007-11-28
I made a fresh install, followed the tutorial posted in that blog using the newest driver (7-11) and didn't work, I got a white screen, I read in that blog a couple of guys had the same, but the solution proposed by the author didn't work for me, now after a low-res problem I'm finally running at normal resolution with the open driver, everywhere I read about ATI drivers most of the people say the open driver works better than the private one anyways, Is there anyway to run compiz with the default open driver?

---

### Post by Takster on 2007-11-29
> **Dynar said:**
> Hehe.. :lolflag:

Anyway, after using this method, I do have direct rendering, but firefox, running movies and playing games seems to be flickering my screen. I cant watch movies in full screen. If it's small enough it will run.. perhaps my CPU is doing all the memory work.. Any possible way to solve that? 

For the rest, I'm quiet satisfied. Compiz seem to be working somewhat.


[http://ubuntuforums.org/showpost.php?p=3852538&postcount=5](http://ubuntuforums.org/showpost.php?p=3852538&postcount=5) :)

If not, then  you must disable desktop effects (choose none, it will kill compiz) and you will be okay while playing movies and games.

---


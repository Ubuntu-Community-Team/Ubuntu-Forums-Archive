---
title: "i915 Enemy Territory screen size"
date: 2005-11-10
forum: Gaming &amp; Leisure
---

### Post by Burkey on 2005-11-10
Ok, not an awesome card but it is on my laptop and I have no choice ok!

I have 1 problem.. ET refuses to kick up 1024x768, it always changes back to 800x600 and then proceeds to run in the bottom left side of the screen instead of filling the whole screen.

If I start a match though it is fast and very playable, although running on a 12" screen and not using the whole panel blows so I need to find out what is up.

It is a Dell D410, glxinfo is all good, glxgears runs 1200+ fps and tuxracer pumps out around 40fps.  3D accel is on but the screen size is not... I posted a similar problem in the hardware section because I suspect the problem is going to be related to my x config or something, especially since Cedega runs WOW horribly slow (1fps?) when on Hoary it all ran fine.

Must be something changed.. a module missing?  Some X.Org change? what what what???

I am sorry but this is urgent, I am going to be travelling again soon for 4 weeks and will not have my athlon64 to game on... must kill noobs in WoW and ET...

---

### Post by slux on 2005-11-10
Just a guess, maybe you don't have enough video memory for 3d acceleration with the mode? Try dropping down to 16bit color maybe... Not sure of the symptoms but that's pretty much all I can think of. What's wrong with 800x600? Have you checked the logs? (Xorg, ET)

---

### Post by Burkey on 2005-11-10
Checked logs and nothing obvious shows apart from complaints that there was no 800x600 and 640x480 modes found!  But they are in xorg.conf so go figure

I would play at 800x600 if I really had to, but since it does not fill the screen frustrates me!

---

### Post by slux on 2005-11-11
It occurred to me that you might be experiencing the same issue that was (probably) solved here: [http://ubuntuforums.org/showthread.php?t=88876](http://ubuntuforums.org/showthread.php?t=88876)

I should've asked if you can actually change between the modes with Ctrl-Alt-+/- earlier.

---

### Post by Burkey on 2005-11-12
That is exactly the problem I suspect slux, but when I reconfigure it actually will only allow X to run in 640x480... so it seems to be reversed!  from reading that post it looks like I need to find some hsync and vsync values that allow all 3 modes (640x480, 800x600, 1024x768).

Some more google I guess.

---

### Post by Burkey on 2005-11-13
Ok, I got all 3 resolutions selectable but I think I broke something else the other day when I installed the latest i915 snapshot...

Enemy Territory comes up with sound but the display is black!

glxgears runs ok but when you press ESC to exit, it displays a glibc error of an invalid pointer :-O

---

### Post by Burkey on 2005-11-13
Ok, really pissed off now.  glxinfo says Direct Rendering is on, glxgears works fine but still Enemy Territory just sits at a blank screen, I can hear the intor music playing, press a key and it goes to the menu music but I cannot see a thing.

I am also trying to get Cedega to run World of Warcraft which is SLOOOOOWW, at least now when it runs the 3D tests the gears stutter and it says FAILED.  NFI why though... AAAAARRGHHHH!!!!  Surely there are others trying to use this kind of s51tty hardware.

The thing that REALLY get's on my goat is the fact I never had to do a thing to get it all working right on Hoary, so whats changed??  How can I get 3D working correctly..  /sigh

what a rant.. sorry but I have today only to get this working along with preparing presentations and packing my bags

---

### Post by Burkey on 2005-11-13
Ok, latest snapshots of xorg and dri are in and running, exactly the same crap.  glxinfo says fine glxgears runs fine but Enemy Territory has a black screen but is running, World of Warcraft puts out about 1fps.

I hope someone has advice because I am out of em.  Does this mean no gaming at all under Breezy on my laptop?  Coz that really sucks hard.

---

### Post by slux on 2005-11-13
Well, certainly sounds like an issue with the OpenGL driver installation. Does ET give any interesting errors on startup? You should check that your libGL.so in use is indeed the one that the intel accelerated drivers provide. There might be invalid libraries from f. ex. mesa lying around in /usr/lib and other dirs. The driver package should provide info about what libs should be in place (and anything else is probably unwanted then)

Unfortunately, you don't seem to be the only one experiencing these problems with intel 3d accelerators: [http://ubuntuforums.org/archive/index.php/t-80926.html](http://ubuntuforums.org/archive/index.php/t-80926.html)

---

### Post by Burkey on 2005-11-13
Yep, pretty sure it is screwed up... I wonder how to fix it now!!

glxinfo gives
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1,
    GL_APPLE_client_storage, GL_APPLE_packed_pixels,
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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

```

I am assuming the glx version mismatch is causing me grief.

Is there some way I can get a deb of this to re-install?  I went through some Cedega debug output and it is using Mesa GLX indirect.. no wonder why!  But how to fix is the question

---

### Post by MetalMusicAddict on 2005-11-13
Im having EXACTLY the same problem. 1st had a small screen then no screen. I havnt found a solution. Other games seem to work fine though. Im using a Dell Inspiron 2200.

---

### Post by Burkey on 2005-11-13
Maybe we should change this thread name to "My i915 was eaten by a badger"

This sucks, Hoary ran everything fine for me and it would just be painful to go back and re-install the whole system!

Did you try adding the HorizSync and VertRefresh settings?  

What I need is some good advice on properly installing the latest xorg snapshot complete with all DRI and GLX components.

I actually killed gdm, apt-get removed all my x.org and then re-installed it all, I have the same output from glxinfo but no longer get an error when running glxgears.

However it has netted me a gain of 0 when it comes to Cedega (which in debug mode is running with Mesa indirect!) or Enemy Territory which sits at a blank screen and forces me to kill gdm to recover from (if someone knows how to exit blindfolded tell me!)

I just ran planet-penguin racer and it is fine, so I can only assume OpenGL and DRI are good to go, but anything that uses GLX (Enemy Territory and Cedega) are screwed.

How do I install an updated GLX?  That is my question now.

---

### Post by tflovik on 2005-11-15
Yesterday i downloaded and burned the Mandriva2006 Livecd.
It uses the develop version of xorg 6.9.
When i ran glxgears the FPS was almost 1900, in Kubuntu i get around 1200 and having problems running several games including et.
By the way my machine is an Dell Inspiron 6000 with i915.
I have attached the xorg.conf produced by the livecd but i don't think it will help any in Kubuntu.

I am considering installing Mandriva now.

Hope this will be of interest.

---

### Post by no1wantdthisname on 2005-11-15
I have the same problem with i915.  Opengl doesn't seem to work well in Ubuntu.  When I try to play Warcraft III it just shows a black screen.  Video files also have distorted colors.

To see if this was a Ubuntu only issue, I started trying different distros.  The one that worked was Suse 10.0.  Warcraft III runs perfectly.  Video files still have the distorted color problem though.  

Of course I've gotten used to Ubuntu, so don't really want to switch. :???: I looked at the xorg.conf from suse, and tried modifying it for Ubuntu.  Nothing seems to work.  A black screen still shows up.  Running out of ideas.

---


---
title: "[SOLVED] Compiz Fusion Headache"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by rmx.dave on 2007-08-28
Okay, so I've spent about 7 hours today on this and I've decided to ask for help. I wanted to install Compiz Fusion, so I followed some guide (I've viewed so many now I can't remember which one) but I got it all installed and it ran fine. In fact, it ran perfectly. However, I tried changing settings in Compizconfig-Settings-Manager and nothing happened. Foolishly clicking around, I just enabled the Ubuntu desktop effects, and then everything went berserk. I then uninstalled everything Compiz-related via Synaptic, and reinstalled. Then, when attempting to run Compiz, I get this:

```

compiz: GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rendering context instead
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0

```

After searching the net and these forums, I was able to finally get Compiz running by typing this:

```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace gconf
```

But settings still do not change, and I cannot edit the window decoration theme. It's using the Compiz default. 

My question is, does anyone know how I can get Compiz working smoothly again, and allow my to modify settings via CCSM?

Sorry for such a long post, but I would really like to see this work.

Thanks,
rmx.dave

---

### Post by rmx.dave on 2007-08-29
Okay...so I know that all I have to do is reinstall whatever library is needed to satisfy the message:

```
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
```

Does anyone know what compiz is looking for here? I really don't want to do a fresh install...any help is appreciated. 

Thanks,
rmx.dave

---

### Post by michael37 on 2007-08-29
This error typically indicates a problem with your X configuration.  Please run command **glxinfo** and post output here.

---

### Post by rmx.dave on 2007-08-29
Here's the output:

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
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
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

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

I see that the "GLX_EXT_texture_from_pixmap" is there...any ideas on how to rectify this?

---

### Post by michael37 on 2007-08-29
> **rmx.dave said:**
> Here's the output:

I see that the "GLX_EXT_texture_from_pixmap" is there...any ideas on how to rectify this?

I saw this problem before with Intel video cards -- the GLX_EXT_texture_from_pixmap is clearly present from glxinfo, but compiz fails to detect it.  I don't have a computer with Intel card, so I can't reproduce it.  Just for sanity, please run this command to tell us your software versions:
```

sudo dpkg -l | egrep "decor|compiz"

```

Here is a post that resolved this problem: [http://ubuntuforums.org/showthread.php?t=515725](http://ubuntuforums.org/showthread.php?t=515725).  Try talking about your problem there.

---

### Post by rmx.dave on 2007-08-29
Here are my compiz versions. I compiled Compiz straight from compiz.org after having even less luck with repo versions.
```
ii  compiz                                        0.5.5~git20070828+3v1ubuntu0               OpenGL window and compositing manager
ii  compiz-core                                   0.5.5~git20070828+3v1ubuntu0               OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                   0.5.2+git20070817-0ubuntu1~ppa1            Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                    0.5.2-0ubuntu2~ppa1                        Collection of plugins from OpenCompositing f
ii  compiz-gnome                                  0.5.5~git20070828+3v1ubuntu0               OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                    0.3.6-1ubuntu13                            OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                                0.5.5~git20070828+3v1ubuntu0               OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager                 0.5.2+git20070814-0ubuntu1~ppa1            Compiz configuration settings manager
rc  gnome-compiz-manager                          0.10.3-0ubuntu1                            Compiz Gnome Manager
ii  libcompizconfig0                              0.5.2-0ubuntu1~ppa2                        Settings library for plugins - OpenCompositi
ii  libdecoration0                                0.5.5~git20070828+3v1ubuntu0               Compiz window decoration library
ii  libdivxdecore0-binary                         5.0.5-1duo1                                DivX MPEG-4 library (decoder)
ii  python-compizconfig                           0.5.2-0ubuntu1~ppa1                        Compiz configuration system bindings

```

I'm reading the thread you linked to, but it seems like the issue resolved there is slightly different, but I'm going to give it a shot. 

Thanks for your continued help.

---

### Post by Deived on 2007-08-29
I had the same problem.

Go to they synaptic package manager and search for compiz gconf (or something like that).  Install it and you should be good.  Took me 2 days to find that out.

---

### Post by rmx.dave on 2007-08-29
EDIT: I lied. The error message is still there, the terminal text just disappeared when I entered it. Compiz still did not start after installing that file. By the way, I searched in Synaptic for compiz gconf and all I found was libcompizconfig-backend-gconf or something really close to that. So that's the package I installed. Is it possible I need a different package or are we just getting off track?

---

### Post by Deived on 2007-08-29
I was getting that with emerald so I disabled it.

Make sure you have your window decoration plugin selected in compiz config.
I'm pretty sure my compiz was updated, but I havent had that problem.

---

### Post by Deived on 2007-08-29
> **rmx.dave said:**
> EDIT: I lied. The error message is still there, the terminal text just disappeared when I entered it. Compiz still did not start after installing that file. By the way, I searched in Synaptic for compiz gconf and all I found was libcompizconfig-backend-gconf or something really close to that. So that's the package I installed. Is it possible I need a different package or are we just getting off track?

No, that's it.  I couldnt update any compiz settings until I installed that package.
Also, earlier you mentioned that you enabled Desktop Effects.  Make sure that's off if it's still on.  In can mess with your windows... at least it did to me a while back.

---

### Post by rmx.dave on 2007-08-29
Yeah sorry, I quickly edited that post after discovering the Compiz actually didn't start after all.

---

### Post by rmx.dave on 2007-08-29
> **Deived said:**
> No, that's it.  I couldnt update any compiz settings until I installed that package.
Also, earlier you mentioned that you enabled Desktop Effects.  Make sure that's off if it's still on.  In can mess with your windows... at least it did to me a while back.

Well, I can't start compiz with compiz --replace still, it gives me the Pixmap error. If I start with LIBGL_ALWAYS_INDIRECT=1 compiz --replace gconf, then it works, but I still can't change any settings. For instance, I turn Wobbly Windows off in CCSM, and the windows still wobble, and so on.

---

### Post by michael37 on 2007-08-29
> **rmx.dave said:**
> Well, I can't start compiz with compiz --replace still, it gives me the Pixmap error. If I start with LIBGL_ALWAYS_INDIRECT=1 compiz --replace gconf, then it works, but I still can't change any settings. For instance, I turn Wobbly Windows off in CCSM, and the windows still wobble, and so on.

Start compiz with LIBGL_ALWAYS_INDIRECT=1 compiz --replace
and then go to CCSM, click on Preferences and switch "Backend" to "Flat file".

Restart X (Ctrl-Alt-Backspace), relogin and see if that works.

---

### Post by rmx.dave on 2007-08-29
It actually already is set at flat file. And when I start compiz without the gconf at the end of the command, nothing happens. Metacity crashes and I'm stuck with windows that wont move, resize, or minimize (until I restart metacity of course).

---

### Post by michael37 on 2007-08-29
> **rmx.dave said:**
> It actually already is set at flat file. And when I start compiz without the gconf at the end of the command, nothing happens. Metacity crashes and I'm stuck with windows that wont move, resize, or minimize (until I restart metacity of course).

If that's the case, your flat file is horribly corrupted.  Wipe it again... [http://ubuntuforums.org/showthread.php?t=533201](http://ubuntuforums.org/showthread.php?t=533201)

On the line where it tells you to "After removing all those packages, copy /home/.compizconfig and /home/.config/compiz and /home/.gconf/apps/compiz to some other location just in case.(your desktop for eg)", instead of copy, use move (mv command) so you start with a blank slate.

---

### Post by rmx.dave on 2007-08-29
Okay. Tried that, and I've got a couple of things. I completely removed compiz following the instructions on the thread you linked to, and I moved the configuration settings. Now compiz won't start at all, even by my previous method. Also, I did not have a home/david/.compizconfig file (or a home/.compizconfig file like you said, but I figured you meant my home folder, and yes, I was viewing hidden files) but I did have the other two, which I moved out to the desktop. 

I'm really baffled as to what is going on with my system. One minute compiz is great, and then I mess one thing up and its just messed up. Thank you for helping me though, I really appreciate it.

---

### Post by michael37 on 2007-08-29
> **rmx.dave said:**
> Okay. Tried that, and I've got a couple of things. I completely removed compiz following the instructions on the thread you linked to, and I moved the configuration settings. Now compiz won't start at all, even by my previous method. Also, I did not have a home/david/.compizconfig file (or a home/.compizconfig file like you said, but I figured you meant my home folder, and yes, I was viewing hidden files) but I did have the other two, which I moved out to the desktop. 

I'm really baffled as to what is going on with my system. One minute compiz is great, and then I mess one thing up and its just messed up. Thank you for helping me though, I really appreciate it.

Yeah, that should be /home/david/.compizconfig directory.

Sorry to take you through that again, but I think your best choice is to
1. uninstall compiz (you know the drill)
2. move configs out of all three locations
3. install compiz
4. start compiz

The sequence does matter, and I suspect you did it in a different sequence last time.

Hope it's great for you after that procedure.

---

### Post by rmx.dave on 2007-08-29
Unfortunately it didn't. I still didn't have a .compizconfig file or directory in my home folder. After reinstalling (from repos, and when that didn't work I compiled from source) Compiz still doesn't start at all, and I get the same errors. 

However, I have just come to a discovery. When I uninstall Compiz from apt/Synaptic, it is still installed on my system. I assumed this is from compiling from source. Does anyone know how to COMPLETELY remove Compiz from my computer if I compiled it from source?

Thank you!

---

### Post by rmx.dave on 2007-08-29
Nevermind, I figured out. I just did a search and removed everything that contained Compiz. I know that next time I can use make uninstall, but I deleted the source folder already. Now I am going to try a fresh install.

---

### Post by rmx.dave on 2007-08-29
At last! Compiz Fusion is now working! All I had to do was wipe EVERYTHING. I think my biggest problem was that I compiled from source and those files remained on the system, so I never was changing anything. Settings change, and its beautiful. Thank you to everyone who helped here, I'm a much happier geek! 

Again, thank you.
rmx.dave

---

### Post by michael37 on 2007-08-30
Woohoo!  Congratulations!

Spin that cube and get yourself a nice looking Skydome :)

---


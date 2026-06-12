---
title: "[SOLVED] Compiz only works partially."
date: 2007-10-01
forum: Desktop Effects &amp; Customization
---

### Post by atomicthumbs on 2007-10-01
I followed the guide here: [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

Anyway, when I run compiz (compiz --replace), the screen goes black and comes back, except that all of my window decorations are gone. Amarok is totally black. There are no 3D effects (due to the absence of anything to do with changing windows). The "wobbly" menus and the alt-tab work fine, but nothing else.

Info:

1.5ghz Pentium 4M CPU

256MB DDR

nVdia Geforce 2 Go graphics card, 32MB memory, nvidia driver

I really want this to work. I know that the 3D on my card works, as I can play Neverball and PPracer.

:confused:

---

### Post by Martje_001 on 2007-10-01
I think you need to upgrade you grapic card or try gutsy

---

### Post by Rupertronco on 2007-10-01
Upgrading to gutsy wouldn't help him at all. It sounds like you may not have 3-d acceleration configured correctly. Please post your xorg.conf file. That system is more than capable of running fusion, it may not be the smoothest, but it'll run it. I've got it running on a p3 notebook with some garbage integraded card. Also type "glxinfo" in a terminal and post the output of that. 

That guide uses trevino's repository. If you're having problems I'd suggest using Amaranth's repository as it is more stable. Installation guides for that can be found on this forum.

---

### Post by atomicthumbs on 2007-10-01
Output of glxinfo:

```
atomicthumbs@laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_EXT_texture_from_pixmap
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_EXT_texture_from_pixmap, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce2 MX/AGP/SSE2
OpenGL version string: 1.5.8 NVIDIA 96.31
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_pixel_buffer_object,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects,
    GL_ARB_shading_language_100, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shared_texture_palette,
    GL_EXT_stencil_wrap, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fence,
    GL_NV_fog_distance, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil,
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_register_combiners,
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4,
    GL_NV_texture_rectangle, GL_NV_vertex_array_range,
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_SGIS_generate_mipmap, GL_SGIS_multitexture, GL_SGIS_texture_lod,
    GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x39 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x3a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3d 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x42 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x43 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x44 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x45 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x46 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x47 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x48 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x49 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x4a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x4b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x4c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x4d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x4e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x4f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x50 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None

```

It works with other 3D things...

---

### Post by atomicthumbs on 2007-10-01
Okay, I started KDe-window-decorater, and now compiz mostly works. The problem is that som ewindows (namely the two I use most oftern, Opera and Amarok) just go black when I start them. Sometimes they are normal for a moment, but then they just go blank. In opera, the cursor still changes when I hover over a link (eve though I can't see the link). Any way to fix this?

---

### Post by atomicthumbs on 2007-10-01
I've figured out the problem: whenever the windows enlarge over a certain size, they become black.

In addition, starting ccsm doesn't work: it just acts like it's starting, then does nothing.

---

### Post by overlord.gaurav on 2007-10-01
Add compiz to startup. 
Run CCSM >> Preferences >> Backend >> Flat-file Backend.
This is how I got CCSM to work.

---

### Post by atomicthumbs on 2007-10-01
How do I add it to startup?

CCSM doesn't start with kwin or Compiz. :( I'm running KDE, so the GNOME instructions wont't work.

I'm thinking of waiting until most of the problems are fixed with Gutsy Gibbon to run compiz. Oh well. :(

---

### Post by overlord.gaurav on 2007-10-01
Then do one thing. Install fusion-icon.
Compiz Fusion Icon is a tray icon that provides quick access to CCSM, Emerald Theme Manager, and basic functions (eg. switching/reloading WMs or WDs). 

STEP 1
```
git clone git://anongit.opencompositing.org/users/crdlb/fusion-icon 
```

STEP 2
```
cd fusion-icon
```

STEP 3
```
sudo make install
```

Now you'll have to run ONLY fusion-icon.

---

### Post by atomicthumbs on 2007-10-01
Alright, I've done that. Unfortunatly, CCSM (Compiz settings) still doesn't work, even when launched from there. Emerald doesn't work either. When launched from a terminal:

```
atomicthumbs@laptop:~$ emerald
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

```

I think if I could get Emerald to work it would fix my problems.

---

### Post by overlord.gaurav on 2007-10-02
> **atomicthumbs said:**
> Alright, I've done that. Unfortunatly, CCSM (Compiz settings) still doesn't work, even when launched from there. Emerald doesn't work either. When launched from a terminal:

```
atomicthumbs@laptop:~$ emerald
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6254): Wnck-WARNING **: Unhandled action type (nil)

```

I think if I could get Emerald to work it would fix my problems.
Are you sure your Desktop Effects are enabled?
Go to system >> Preferences >> Desktop Effects >> Enable Desktop Effects

---

### Post by atomicthumbs on 2007-10-02
This is KDE, not GNOME. I fixed this (except for ccsmm) already. See my other thread.

---


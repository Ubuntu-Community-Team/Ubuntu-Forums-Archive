---
title: "Blender 3D Modeller won't launch."
date: 2006-07-01
forum: Desktop Environments
---

### Post by Shadow_ on 2006-07-01
Split from: [here](http://www.ubuntuforums.org/showthread.php?p=1202791#post1202791).

I tried to launch Blender 3D Modeller. It opens then quickly closes again...

I ran it from a terminal, as suggested in the original post, and got this:
```

Using Python version 2.4
Unable to load: libtiff.
Try setting the BF_TIFF_LIB environment variable if you want this support.
Example: setenv BF_TIFF_LIB /usr/lib/libtiff.so
Error: Rage 128 timed out... exiting
```

typed in the example code and got this:
```
nathan@ubuntu:~$ setenv BF_TIFF_LIB /usr/lib/libtiss.so
bash: setenv: command not found
```

Any suggestions would be appreciated :)

~Nathan

---

### Post by encompass on 2006-07-01
do you have 3d support?
run this
glxinfo
scroll up and see if it says you have Direct Rendering.
if so I haven't the foggiest idea how to help you.  Thats my best shot.  and IMO I wouldhave posted this to your original thread rather than confusing everyone.

---

### Post by darenw on 2006-07-01
> 
Unable to load: libtiff.



hmm, do you have libtiff installed?   i would assume Synaptic/ any package manager would have made sure it was, but nothing is perfect....

---

### Post by Shadow_ on 2006-07-02
Ok, I ran glxinfo and got this:
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
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: VA Linux Systems, Inc.
OpenGL renderer string: Mesa DRI Rage 128 Pro 20041026 AGP 1x
OpenGL version string: 1.2 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_compression, GL_ARB_texture_env_add,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_separate_specular_color, GL_EXT_subtexture, GL_EXT_texture,
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_object, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format,
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x26 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x2a 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x2b 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x2e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x2f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x32 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow

```

I'm not really sure what it means... I installed Easy Ubunutu (or what ever it's called) before upgrading to 6.06, and I think those changes might have been undone. I chose not to instal graphics drivers becasue my monitor was working :D

[quote=encompass]and IMO I wouldhave posted this to your original thread rather than confusing everyone.[/quote]

yeah, the other post was found through a search, and my post was a bit of a necro bump, plus it was support for x64 systems, mine is x32. Sorry for any confusion caused...

~Nathan

---

### Post by Shadow_ on 2006-07-02
Ok, I used synaptic to install all the libtiff* packages, and ran blender from a terminal. I gto this error message:
```

Using Python version 2.4
Error: Rage 128 timed out... exiting
```
I guess this is 'cause I haven't installed a drivers for my graphics card? If I remeber correctly it's an All-in-wonder Rage ATI 128 pro? I'll check Synaptic to see if there are any obvious drivers but a point or nudge in the right direction would be appreciated :)

~Nathan

---

### Post by Shadow_ on 2006-07-03
Yay!
All sorted, re-installed EasyUbuntu with graphics drivers and I got Blender to work :D

Now I must learn how to use it...

Thanks a lot,
~Nathan

---

### Post by yu_raider on 2007-04-12
Hi, can you tell me what driver did you install for your Rage 128 card, because I can't find any.

---


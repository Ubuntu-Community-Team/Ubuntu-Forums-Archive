---
title: "Intel 915 &amp; Aiglx"
date: 2006-11-09
forum: Desktop Environments
---

### Post by robbert on 2006-11-09
Hi,

I'm trying to get Beryl and Aiglx working on my laptop with an Intel card. But when i start Beryl i get the following error:
```

XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x5b
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

Glxinfo
```

name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x5b
display: :0  screen: 0
direct rendering: Yes
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.5.1
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
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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

Isn't this a little bit an old version? Is that normal (does it normally suppose to work with it)?
```

OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225

```

Essential parts of Xorg.conf
```

....

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dbe"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

....

Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "DRI"           "true"
        Option      "XAANoOffscreenPixmaps"
EndSection

Section "Extensions"
        Option  "Composite"     "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "Generic Monitor"
        Option "AddARGBGLXVisuals" "True"
        Option "DisableGLXRootClipping" "True"
        DefaultDepth    24
        ...
EndSection

Section "ServerLayout"
.....
        Option "AIGLX" "true"
EndSection

Section "DRI"
        Group   0
        Mode    0666
EndSection

```

Anyone an idea how to get it working? With beryl-xgl it is working by the way, but i wanna use aiglx...

Specs:
Intel i915 graphical card
Ubuntu Edgy
Beryl 0.1.1

---

### Post by Tinwood on 2006-11-10
There appears to be a bug:

[ https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/60726]("https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/60726")

No idea when it will be fixed.  Guess that's the end of my Beryl investigations for the moment!

Cheers
Alex.

---

### Post by robbert on 2006-11-10
Has this bug any relation with my bug, because beryl dont't give this error: "GL_ARB_fragment is not supported" on my computer. 
On my computer i get the following error:
libGL warning: 3D driver claims to not support visual 0x5b
beryl: glXBindTexImageEXT is missing

---

### Post by Tinwood on 2006-11-10
Interesting.  Looking at your glxinfo you really don't seem to have GL_ARB_fragment_program and it is needed for the water plugin which is enabled by default.

The bug I referenced indicated that this simply isn't supported at present for AIGLX in the i810 driver.

The bit about not supporting the visual is the GL driver (wrongly?) saying it can't support the 32 bit plane.

The "glXBindTexImageEXT" missing bit seems to be something to do with the OpenGL library not supporting this extension.  Is this a libGL.so problem?

---

### Post by robbert on 2006-11-10
Compiling Xorg with the patch above ;) hope it'll help...

---

### Post by robbert on 2006-11-10
> **Tinwood said:**
> Interesting.  Looking at your glxinfo you really don't seem to have GL_ARB_fragment_program and it is needed for the water plugin which is enabled by default.
The water plugin is working now with XGL after applying that patch. ;)

But AIGLX still isn't working.

> 
The bit about not supporting the visual is the GL driver (wrongly?) saying it can't support the 32 bit plane.
Can that cause the problem that AIGLX isn't working?

> 
The "glXBindTexImageEXT" missing bit seems to be something to do with the OpenGL library not supporting this extension.  Is this a libGL.so problem?
Hmm, any idea how to solve it? When searching with google i didn't find any useful information.

---

### Post by Tinwood on 2006-11-10
It may not help you, but mine is now working - I've shifted to Beryl 0.1.2 which I got from the beryl-project, by adding the following to my sources.list:

deb [http://ubuntu2.beryl-project.org/](http://ubuntu2.beryl-project.org/) edgy main


i.e. it replaced the original:
```

# for Beryl functionality
#deb http://ubuntu.beryl-project.org/ edgy main-edgy
deb http://ubuntu2.beryl-project.org/ edgy main

```However, I also had to make some changes to my xorg.conf (which I wasn't previously aware of):

xorg.conf:

```

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "XAANoOffscreenPixmaps" "true"
EndSection

```i.e. added the Option "XAAN..." bit

and at the end of the xorg.conf:

```

Section "Extensions"
Option  "Composite" "true"
EndSection

```However, I don't know if this is solving anything.  I still have Beryl complaining about not having a stencil buffer:

```

libGL warning: 3D driver claims to not support visual 0x5b
beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Initiating splash
Reloading all options.

```
It seems that the there is still a problem with the i810 driver not supporting the fragment stuff and, of course, there is the stencil buffer problem that isn't resolved.  It is very pretty though!

Hope that something in this helps!

---

### Post by robbert on 2006-11-10
Tried beryl 0.1.2, but it still isn't working. Still the same error: "beryl: glXBindTexImageEXT is missing" :(
I made those changes in my xorg.conf already, so that doesn't seem to be the problem either.

Can you post the output of your glxinfo please, than i could compare it with mine... maybe there are some differences who could explain my problem.

---

### Post by Tinwood on 2006-11-12
Okay, my glxinfo is shown at the end.

However, I still can't help wondering if your error is more to do with libGL.so?  The symbols from my libGL.so are:

```

$ objdump -T /usr/lib/libGL.so | grep glXBind
00014710 g    DF .text  00000007  Base        glXBindChannelToWindowSGIX
00014b30 g    DF .text  00000185  Base        glXBindTexImageEXT
00014770 g    DF .text  00000005  Base        glXBindSwapBarrierSGIX

```i.e. there it is on the 2nd line.  What does the above do on your system?

Cheers
Alex.



```

$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x5b
display: :0  screen: 0
direct rendering: Yes
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.5.1
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
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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

---

### Post by robbert on 2006-11-13
The objdump of libGL looks exactly the seem, so that doesn't seem to be the problem.
```

robbert@robbertmobile:~$ objdump -T /usr/lib/libGL.so | grep glXBind
00014710 g    DF .text  00000007  Base        glXBindChannelToWindowSGIX
00014b30 g    DF .text  00000185  Base        glXBindTexImageEXT
00014770 g    DF .text  00000005  Base        glXBindSwapBarrierSGIX

```

I did a diff between our glxinfo results:
```

17,21c16,19
<     GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
<     GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
<     GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
<     GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
<     GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
---
>     GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
>     GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
>     GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
>     GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
26,28c24,26
<     GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
<     GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
<     GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
---
>     GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
>     GLX_SGI_make_current_read, GLX_SGI_video_sync, GLX_SGIS_multisample, 
>     GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group

```
What makes the following differences:
In the 2nd part with extensions I don't have:
* GLX_MESA_copy_sub_buffer 
* GLX_EXT_texture_from_pixmap

In the 3rd part with extensions I don't have:
* GLX_MESA_copy_sub_buffer

I don't know where these extensions are responsible for, or they have anything to
do with my problem.

(btw,thanks for your help so far ;))

---

### Post by Tinwood on 2006-11-13
That's a bit strange.  Are you using Dapper or Edgy?  It looks like your mesa library might be different to mine?

What's your equivalent to:

```

[FONT=Courier New] $ dpkg -l '*mesa*' | grep '^ii'
ii  libgl1-mesa-dev     6.5.1~20060817-0ubuntu3 A free implementation of the OpenGL API -- GLX develop
ii  libgl1-mesa-dri     6.5.1~20060817-0ubuntu3 A free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx     6.5.1~20060817-0ubuntu3 A free implementation of the OpenGL API -- GLX runtime
ii  libglu1-mesa        6.5.1~20060817-0ubuntu3 The OpenGL utility library (GLU)
ii  libglu1-mesa-dev    6.5.1~20060817-0ubuntu3 The OpenGL utility library -- development support file
ii  mesa-common-dev     6.5.1~20060817-0ubuntu3 Developer documentation for Mesa
ii  mesa-utils          6.3.2-1ubuntu1          Miscellaneous Mesa GL utilities[/FONT]

```

---

### Post by robbert on 2006-11-13
I'm running Edgy.

Looks equivalent:
```
[FONT=Courier New]
robbert@robbertmobile:~$ dpkg -l '*mesa*' | grep '^ii'
ii  libgl1-mesa-dev     6.5.1~20060817-0ubuntu3 A free implementation of the OpenGL API -- GLX develop
ii  libgl1-mesa-dri     6.5.1~20060817-0ubuntu3 A free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx     6.5.1~20060817-0ubuntu3 A free implementation of the OpenGL API -- GLX runtime
ii  libglu1-mesa        6.5.1~20060817-0ubuntu3 The OpenGL utility library (GLU)
ii  libglu1-mesa-dev    6.5.1~20060817-0ubuntu3 The OpenGL utility library -- development support file
ii  mesa-common-dev     6.5.1~20060817-0ubuntu3 Developer documentation for Mesa
ii  mesa-utils          6.3.2-1ubuntu1          Miscellaneous Mesa GL utilities[/FONT]
```

Just did apt-get --reinstall for all those packages, but without succes... :(

---

### Post by Tinwood on 2006-11-13
Okay, one less thing to worry about!

Now, I guess, on to less obvious things.  Things that spring to mind are if there is another libGL.so on the system somewhere?

What is the output of:
```

alex@alex-laptop:~$ locate libGL.so
/usr/lib/libGL.so.1
/usr/lib/libGL.so.1.2
/usr/lib/libGL.so
alex@alex-laptop:~$ ls -al /usr/lib/libGL.so
lrwxrwxrwx 1 root root 10 2006-10-28 20:47 /usr/lib/libGL.so -> libGL.so.1

```(I'm now trying to work out if a different library is linking in with the Mesa library to provide the actual function.)

---

### Post by robbert on 2006-11-13
You're my hero!!

found a libGL.so in /usr/X11R6/lib I deleted it and it's working now ;)

---

### Post by Tinwood on 2006-11-13
Excellent!  Now all you need to do is find out which package put that file on and remove it (I know that you have deleted the file, but if the owning package gets updated the file WILL re-appear and break your system).

So, if you run:

```

$ dpkg -S /usr/X11R6/lib/libGL.so

```It will take a while, but should print out who owns the file.  Now, depending on what it is you might be able to just remove it or upgrade it.

Hope that this helps.
Cheers
Alex.

---

### Post by robbert on 2006-11-13
There is no package owning that file. I think it's from the freedesktop dri snapshots I installed once (think almost 2 years ago).

Thanks for your help again ;)

---


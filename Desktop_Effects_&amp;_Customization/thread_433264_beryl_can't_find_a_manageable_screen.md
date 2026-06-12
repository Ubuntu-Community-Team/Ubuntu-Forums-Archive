---
title: "beryl can't find a manageable screen"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by ubnewbie2 on 2007-05-04
When I try to start it, I get this

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
```

Is this related to my system using nvidia for legacy cards? see [http://ubuntuforums.org/showthread.php?t=433199](http://ubuntuforums.org/showthread.php?t=433199)

---

### Post by Pox on 2007-05-04
Try

```
beryl --use-copy
```

Tell me if it works.

---

### Post by ubnewbie2 on 2007-05-05
I just tried it.  

beryl --use-copy 

gives the same error

---

### Post by ubnewbie2 on 2007-05-05
I just looked at the out put of glxinfo

```
$glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: RIVA TNT2/AGP/SSE/3DNOW!
OpenGL version string: 1.5.3 NVIDIA 71.84
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_texture_env_add, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_compiled_vertex_array, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fog_distance, 
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_SGIS_multitexture, 
    GL_SUN_slice_accum
```

and there is no "GLX_EXT_texture_from_pixmap" - which is what it is complaining about.

So does this mean the legacy driver on my old nvidia card just doesn't have all the functions needed by beryl?  
The man page on beryl says  "It  will  run  anywhere that GLX_EXT_texture_from_pixmap is supported, which is currently on Xgl and aiglx"  so it's starting to look like I'm out of luck.

---

### Post by Pox on 2007-05-05
No, I just set up Beryl on my sister's legacy card, doesn't have TFP but runs with Copy fine.

---

### Post by ubnewbie2 on 2007-05-05
> **Pox said:**
> No, I just set up Beryl on my sister's legacy card, doesn't have TFP but runs with Copy fine.

So what is --use-copy ?  The man pages don't even mention it as an option.

---


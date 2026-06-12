---
title: "compiz - XGL or AIGLX howto know ?"
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by salvadorveiga on 2007-11-06
Hey guys... I've read a lot about this but the more i read the more conphused I get... I've heard AIGLX is easier/better and more stable to work with desktop effects... how can I know what i am running ? I don't know what I'm running since I'm a noob in these things...

I have an ati 9200 Radeon and in the console the output for glxinfo is 
```
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
OpenGL renderer string: Mesa DRI R200 20060602 AGP 8x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1
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
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

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
0x72 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

I don't have the package xserver-xgl installed if that's supposed to say something...

should I stay the way I am or should i configure it to AIGLX or something ? thanks

---

### Post by Forlong on 2007-11-07
If you haven't installed Xgl, you are using AIGLX (it's turned on in Ubuntu's X-server by default).

---

### Post by salvadorveiga on 2007-11-07
so im using aiglx ? nice... i've always heard it's a better combnation with compiz and that it was faster but it was a pain to make it work with ati... i have an ati and this came out of the box

---

### Post by Forlong on 2007-11-08
> **salvadorveiga said:**
> so im using aiglx ? nice... i've always heard it's a better combnation with compiz and that it was faster but it was a pain to make it work with ati... i have an ati and this came out of the box
Hehe, yeah great, isn't it? Same goes for me.
We are lucky because our graphics cards are supported by the open radeon driver. If you have to use the proprietary (restricted) fglrx driver it can be a PITA, for sure. :)

---

### Post by salvadorveiga on 2007-11-08
> **Forlong said:**
> Hehe, yeah great, isn't it? Same goes for me.
We are lucky because our graphics cards are supported by the open radeon driver. If you have to use the proprietary (restricted) fglrx driver it can be a PITA, for sure. :)

i was thinking of buying a new graphics card... if I buy one I should go with nVidia right ?

---

### Post by Forlong on 2007-11-08
Yes, that would be the best choice for now.

---

### Post by dirken on 2008-01-02
> **Forlong said:**
> Hehe, yeah great, isn't it? Same goes for me.
If you have to use the proprietary (restricted) fglrx driver it can be a PITA, for sure. :)

Not that difficult :)
Got it working just some minutes ago

Just download the latest fglrx driver from the debian website, jou'll find the links underneath ( i can't understand why ubuntu isn't supporting it :/) and remove the current fglrx driver using the restricted drivers manager.
Then uninstall xgl by invoking the command ```
sudo apt-get remove xserver-xgl
```
Next install the kernerl source package and afterwards the fglrx driver itself and reboot the computer.
The latetst driver should work withouth xgl and my compiz is running just fine


FGLRX kernel source: [http://packages.debian.org/sid/fglrx-kernel-src](http://packages.debian.org/sid/fglrx-kernel-src)
FGLRX driver: [http://packages.debian.org/sid/fglrx-driver](http://packages.debian.org/sid/fglrx-driver)

---

### Post by Mr Greencastle on 2008-01-02
I'm glad to see ATI is improving with their drivers... or at least making them available. I see a much cleaner more out-of-the-box Compiz-Fusion and Linux experience.

If my chip (radeon xpress 1100, pretty much a 200m) works without Xgl after a restricted driver install when Hardy is unleashed, I will be very pleased. 

I have it working with AIGLX right now, but I had to jump through a lot of hoops and edit a lot of text files to get it to work properly.

Mr Green

---


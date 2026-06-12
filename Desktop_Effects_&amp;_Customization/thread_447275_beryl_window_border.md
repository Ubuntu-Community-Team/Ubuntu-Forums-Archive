---
title: "beryl window border?"
date: 2007-05-17
forum: Desktop Effects &amp; Customization
---

### Post by em11488 on 2007-05-17
when I start beryl all my programs have no borders like how metacity has. (min max exit buttons) how do I get  this back so I could move the programs and stuff.

---

### Post by Hobo Joe on 2007-05-17
paste the output of:

```

glxinfo

```

---

### Post by em11488 on 2007-05-17
wow, id like to, but my terminal is all white, cant see anything, just a white box

---

### Post by Hobo Joe on 2007-05-17
When you boot up, before you click log in, click options, then sessions, then do 'failsafe gnome'

That *should* fix the no borders for now.

---

### Post by starcraft.man on 2007-05-17
> **em11488 said:**
> wow, id like to, but my terminal is all white, cant see anything, just a white box

Crap, you must have had a crash with Beryl.... Can you right click on the top right icon and go Select Window Manager > Metacity. That should get you back to standard manager temporarily, if not reboot your machine and see if that or the terminal works. If still bad ya might need to boot into the recovery mode (should be your second boot option in grub, right under standard kernel) to get things working again...

Edit: Hobo got to post button first, and btw... that cat just looks seriously freaky >.<.

---

### Post by Loki57701 on 2007-05-17
I had the same problem. Goto your system monitor>processes and end the Beryl process. That should get your terminal back atleast.  I have tried to use desktop effects but I have the same problem with the window borders disappearing and (no max, min, close) buttons. I still havent figured out how to fix it

---

### Post by Hobo Joe on 2007-05-17
I think the problem is that you don't have direct rendering, I've had something like that in the past.

But it could be something else.
Like I said, paste the output of:

```

glxinfo

```

---

### Post by dustigroove on 2007-05-17
[FONT=Arial][SIZE=2][COLOR=Black]Hey em11488...  What graphics card? ATI? NVIDIA? Are you using XGL?

Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by Loki57701 on 2007-05-17
Heres mine, but it says I have direct rendering?

glxinfo:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 7600/PCI/SSE2
OpenGL version string: 2.1.0 NVIDIA 97.55
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x22 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x2a 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x2b 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x2c 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x2d 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x2e 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x2f 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x30 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x31 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x32 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x33 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x34 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x35 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x36 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x37 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x38 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x39 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x3a 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x3b 16 dc  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x3c 16 dc  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x3d 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x3e 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x3f 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x40 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x41 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x42 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x43 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x44 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x45 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x46 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x47 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x48 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x10c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by Hobo Joe on 2007-05-17
> **Loki57701 said:**
> Heres mine, but it says I have direct rendering?



Like I said, the only experience I have in it is my own, so... I'm stumped. Sorry... :(

---

### Post by bung33 on 2007-05-17
I had a similar problem when I upgraded from 6.06 to 7.04. Beryl was installed before I upgraded the OS. It worked perfectly. However, after I upgraded, I began to experience a few problems with the display. One of the problems was the terminal being completely white. To fix the problem, I simply reinstalled Beryl. After that, everything worked perfectly again. Of course, you really don't even need Beryl on 7.04, since it comes with desktop effects that you can enable. However, the Beryl manager does have many more options.

---

### Post by dustigroove on 2007-05-17
[FONT=Arial][COLOR=Black][SIZE=2]Try adding this to your /etc/X11/xorg.conf under the &#8220;Device&#8221; section:

[/SIZE][/COLOR][/FONT][COLOR=Black]```
Option      "AddARGBGLXVisuals"      "True"
```[/COLOR][FONT=Arial][COLOR=Black][SIZE=2]
**EDIT:**  You will also need to ensure that your color depth is set to 24.

Cheers

[/SIZE][/COLOR][/FONT]

---

### Post by jgreenback on 2007-05-30
Thanks dusigroove,  you ROCK!  This worked like a charm for me.

I was having the problem in Ubuntu 7.04 w/ Beryl for those having the same issues with the same OS version and Beryl.

> **dustigroove said:**
> [FONT=Arial][SIZE=2]Try adding this to your /etc/X11/xorg.conf under the “Device” section:

[/SIZE][/FONT]```
Option      "AddARGBGLXVisuals"      "True"
```[FONT=Arial][SIZE=2]
**EDIT:**  You will also need to ensure that your color depth is set to 24.

Cheers,

[/SIZE][/FONT]

---

### Post by Arppa on 2007-05-31
i had this problem myself and it occured becouse my xorg.conf wasnät properly configred for beryl. what graphics card you are using? can you paste your xorg.conf?

---

### Post by nemesis5 on 2007-07-21
thanks for this post, I had the same problem (Ubuntu 7.10  - the Gutsy Gibbon -tribe 3)

:KS:KS:KS:KS:KS

edit: GeForce Go 7600 by NVIDIA
on a HP pavilion dv9000

---


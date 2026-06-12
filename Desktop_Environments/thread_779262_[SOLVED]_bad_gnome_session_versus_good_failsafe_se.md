---
title: "[SOLVED] bad gnome session versus good failsafe session"
date: 2008-05-02
forum: Desktop Environments
---

### Post by Julianito on 2008-05-02
Hello,

Since I upgraded to Hardy, my gnome default session fails whereas the failsafe session is ok (except missing locale in wine).

Running the default gnome session, I have lot of issues (some I successfully fixed, others not) :
- bad screen resolution (fixed)
- blank screen/cube with compiz
- I had many difficulties to configure nvidia properly, having glx enabled, ...

The failsafe session is nice : compiz working (no blank screen/cube), glx enabled, game WoW working nice under wine, ...
Except that the keyboard under wine is qwerty instead of azerty.

I attached ~/.xsession-errors
How could I analyze this file logs and compare between default gnome session and failsafe session ?
I should have a bad initialization script somewhere but which one ?

Many thanks for help,
Julien

---

### Post by Julianito on 2008-05-03
Using default gnome session I have 
glxinfo | grep "direct rendering"
direct rendering: No

Using failsafe I have
glxinfo | grep "direct rendering"
direct rendering: Yes

```
glxinfo 
name of display: :3.0
display: :3  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8600 GTS/PCI/SSE2
OpenGL version string: 1.2 (2.1.2 NVIDIA 169.12)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_program, 
    GL_ARB_fragment_program, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_EXT_framebuffer_object, GL_ATI_texture_mirror_once, 
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_NV_texture_env_combine4, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0 808467811 1634493998 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0 4705 1751607660 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0 779447909 1294600805 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0 1869902965 1114992229 Ncon

```

```
lspci | grep VGA
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
```

Doing this :
```

~$ glxinfo | grep direct
direct rendering: No
~$ export DISPLAY=:0.0
~$ glxinfo | grep direct
direct rendering: Yes

```

---

### Post by Julianito on 2008-05-03
solved removing xserver-xgl :-D

---


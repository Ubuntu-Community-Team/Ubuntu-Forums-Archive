---
title: "gDesklets"
date: 2008-08-17
forum: Desktop Environments
---

### Post by eggie9001 on 2008-08-17
When I try to install gDesklets and the gDesklets data, everything goes smoothly. But, when I try to run gDesklets it fades to black and then I have to 'force quit'.

Any solutions?

---

### Post by eggdeng on 2008-08-17
I found both awn and gesklets to be very buggy. A much better option is to install cairo-dock. You can get .deb packages from
[http://developer.berlios.de/project/showfiles.php?group_id=8724]("http://developer.berlios.de/project/showfiles.php?group_id=8724")
The packages you need are
cairo-dock_v1.6.1.2_i686.deb and
cairo-dock-plug-ins_v1.6.1.2_i686.deb
Just download to your desktop, click on the packages and gdebi will do the rest.
Cairo-dock provides the mac type dock but with detachable widgets so really it gives you the funcionality of both of awn and gdesklets. It's more or less bug-free and very configurable. Screenshot attached.
It's also possible to install from the repos, see [https://help.ubuntu.com/community/CairoDock]("https://help.ubuntu.com/community/CairoDock")

---

### Post by eggie9001 on 2008-08-17
Thanks a lot!

I installed the dock itself and the plugins but, I can't seem to get the dock running.

I go to applications, system tools and click on cairo dock and nothing seems to happen.

---

### Post by eggie9001 on 2008-08-17
Does anyone have a solution to this?

---

### Post by eggdeng on 2008-08-18
Can you supply some info about your graphics set up? Are you using 8.04 (Hardy)? What graphics card have you got? Which graphics driver & how did you install it? Are you running Compiz?
The following commands will provide useful output.

```
lspci | grep VGA
cat /etc/X11/xorg.conf | grep Driver
glxinfo 
top | grep Xorg
```

---

### Post by eggie9001 on 2008-08-18
I am currently not on the Ubuntu OS, but once I get on it I will edit this post with the results.

---

### Post by fabounet on 2008-08-18
launch it in a terminal to get the output.
the next version (1.6.2) will be in the repositories by the way ;-)

---

### Post by eggie9001 on 2008-08-18
Ok, well here are the results.

```
joe@joe-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]

```

```
joe@joe-laptop:~$ cat /etc/X11/xorg.conf | grep Driver
	Driver		"kbd"
	Driver		"mouse"
	Driver		"synaptics"
	Driver		"fglrx"

```

```
joe@joe-laptop:~$ glxinfo 
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
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
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
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
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x85 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  8 1 Ncon

```

```
joe@joe-laptop:~$ top | grep Xorg
 5498 root      20   0  313m  83m  29m S   34  9.5   0:25.14 Xorg               
 5498 root      20   0  313m  83m  29m S    2  9.5   0:25.20 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:25.24 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:25.28 Xorg               
 5498 root      20   0  313m  83m  29m S   25  9.5   0:26.04 Xorg               
 5498 root      20   0  313m  83m  29m S    4  9.5   0:26.16 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.18 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.22 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.26 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.30 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.34 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.38 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.42 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.46 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.50 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.54 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.58 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.60 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.64 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.68 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.72 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.76 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.80 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.84 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.88 Xorg               
 5498 root      20   0  313m  83m  29m S    1  9.5   0:26.90 Xorg               
 5498 root      20   0  313m  83m  29m S   19  9.5   0:27.48 Xorg               
 5498 root      20   0  313m  83m  29m R   14  9.5   0:27.90 Xorg               
 5498 root      20   0  313m  83m  29m S   17  9.5   0:28.40 Xorg               
 5498 root      20   0  313m  83m  29m S    5  9.5   0:28.54 Xorg               
 5498 root      20   0  313m  83m  29m S    5  9.6   0:28.70 Xorg               
 5498 root      20   0  313m  83m  29m S    7  9.6   0:28.90 Xorg               
 5498 root      20   0  313m  83m  29m S    9  9.6   0:29.16 Xorg               
 5498 root      20   0  313m  83m  29m R   11  9.6   0:29.48 Xorg               
 5498 root      20   0  313m  83m  29m S    9  9.6   0:29.76 Xorg               
 5498 root      20   0  313m  83m  29m S   23  9.6   0:30.46 Xorg               
 5498 root      20   0  313m  83m  29m S   26  9.6   0:31.24 Xorg               
 5498 root      20   0  313m  83m  29m S    7  9.6   0:31.46 Xorg               
 5498 root      20   0  313m  83m  29m S   12  9.6   0:31.82 Xorg               
 5498 root      20   0  313m  83m  29m R   17  9.6   0:32.34 Xorg               
 5498 root      20   0  313m  83m  29m S    7  9.6   0:32.54 Xorg               
 5498 root      20   0  313m  83m  29m S   24  9.6   0:33.26 Xorg               
 5498 root      20   0  313m  83m  29m S    7  9.6   0:33.48 Xorg               
 5498 root      20   0  313m  83m  29m S    9  9.6   0:33.74 Xorg               

```

---

### Post by eggdeng on 2008-08-19
Sorry for taking so long to get back, I guess we're in different time zones. From what you've posted, everything looks to be in order. The only thing I can suggest is that you try using xgl in place of Xorg. I have both (on an ATI X1400) & alternate betwen them.
The basic procedure is as follows. First, install xgl
```
sudo apt-get install xserver-xgl
```
Now create a little script to start xgl
```
gksudo gedit /usr/bin/startxgl.sh
```
Assuming you are using gnome, paste the following into the file
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
dbus-launch --exit-with-session gnome-session 

```
Save & exit. Make the file executable.
```
sudo chmod +x /usr/bin/startxgl.sh
```
You need to create one more file which will give you the option to log into an xgl session
```
gksudo gedit /usr/share/xsessions/xgl.desktop
```
Paste the following into the file
```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
```
Save & exit. Now log out. At the login window, you should now have the additional option of choosing an xgl session. Choose xgl, then choose *Just for this session* and log back in. If you have problems, you can just log back out and log in again to your normal session.
All this is explained in detail at [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")

---


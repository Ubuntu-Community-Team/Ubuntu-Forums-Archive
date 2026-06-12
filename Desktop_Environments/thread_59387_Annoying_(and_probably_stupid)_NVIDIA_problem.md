---
title: "Annoying (and probably stupid) NVIDIA problem"
date: 2005-08-23
forum: Desktop Environments
---

### Post by REBELinBLUE on 2005-08-23
I have installed the NVIDIA drivers, changed xorg.conf and restarted X11. Then it works.

Once I restart how ever X doesn't load. The only error I see on screen is

```
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
```

My complete xorg log is below

Now if I run the installer again and then startx it works, this leads me to believe there is a module not being loaded as the installer loads the modules and run time and so when I reboot they are gone. Problem is I can't figure out how to tell which module I missing, if any.


Any ideas?

Here is the output of glxinfo
> stephen@shuttle:~$ glxinfo
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
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 MX Integrated GPU/AGP/SSE/3DNOW!
OpenGL version string: 1.5.3 NVIDIA 76.76
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr,
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
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
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x33 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x39 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3a 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3b 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3d 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None

glxgears (seems low)
> stephen@shuttle:~$ glxgears
3234 frames in 5.0 seconds = 646.800 FPS
6894 frames in 5.0 seconds = 1378.800 FPS
7644 frames in 5.0 seconds = 1528.800 FPS

---

### Post by skoal on 2005-08-23
something amiss there...
> 
skoal@morpheus:///data/ubuntu/dev $ dpkg-query -S libfb.a
xserver-xorg: /usr/X11R6/lib/modules/libfb.a
so, somehow that file from a standard xorg package install got wankered. I use nvidia binary drivers as well and that file exists.  Maybe 'apt-get -f install' is what you need...

\\//_

---

### Post by REBELinBLUE on 2005-08-23
[QUOTE=skoal]something amiss there...

so, somehow that file from a standard xorg package install got wankered. I use nvidia binary drivers as well and that file exists.  Maybe 'apt-get -f install' is what you need...

\\//_[/QUOTE]

 Well thats definately done something. I now get the NVIDIA splash flashing on and off 4/5 times then the computer freezes

Just reinstalling all the X related packages

---

### Post by Dolphin on 2005-08-23
GF4 MX?  That FPS seems about right.  That's not a terribly powerful card by today's standards.

I get 9800FPS with my x800xt.

---

### Post by skoal on 2005-08-23
oops! I makey mistakey earlier, so I delelted my post.  I thought you were missing the libfb.a file, but you are not.  That "error" you posted is just some xorg debugging hooey and not important (in your case here).

It looks like you're using the Nvidia binary driver installer.  Right?  Not the deb package.  If so, what you are experiencing is typical when you had already installed the deb package and then try the nvidia installer.  Just remove all those nvidia deb packages you once installed and redo the Nvidia supplied installer again.  There are threads running around here on how to clean those old deb packages.

If I'm off base here (and my sol'n doesn't fix it for you), please add me to your /ignore list for my stupidity shown by my prior post...

sorry 'bout that mate...

\\//_

---

### Post by REBELinBLUE on 2005-08-23
[QUOTE=skoal]oops! I makey mistakey earlier, so I delelted my post.  I thought you were missing the libfb.a file, but you are not.  That "error" you posted is just some xorg debugging hooey and not important (in your case here).

It looks like you're using the Nvidia binary driver installer.  Right?  Not the deb package.  If so, what you are experiencing is typical when you had already installed the deb package and then try the nvidia installer.  Just remove all those nvidia deb packages you once installed and redo the Nvidia supplied installer again.  There are threads running around here on how to clean those old deb packages.

If I'm off base here (and my sol'n doesn't fix it for you), please add me to your /ignore list for my stupidity shown by my prior post...

sorry 'bout that mate...

\\//_[/QUOTE]
 Hmm, I did remove them all previously. Will reinstall them and then remove them again

---

### Post by REBELinBLUE on 2005-08-24
[QUOTE=REBELinBLUE]Hmm, I did remove them all previously. Will reinstall them and then remove them again[/QUOTE]
 I had forgotten the kernel-restricted package, removed that and reinstalled but it made no difference :(

---

### Post by REBELinBLUE on 2005-08-26
[QUOTE=REBELinBLUE]I had forgotten the kernel-restricted package, removed that and reinstalled but it made no difference :([/QUOTE]
 Just a quick post to say I've fixed it, personally I hate looking through a problem and finding a topic with no resolution. So for anyone else that has theses problems here is how I fixed it

1) Set the display driver back to nv from nvidia
2) Removed the offical nvidia drivers by adding the command line parameter --uninstall to the installer
3) Purged the apt cache of all the nvidia related modules (kernel-restricted, nvidia-common, nvidia-glx, nvidia-settings) by selecting the package in Synaptic and choosing "Remove completely"
4) Located an left over modules by running "locate nvidia" (you may need to run sudo updatebd first) and then deleted any modules found (backing up of course). I have nvidia.ko and agp_nvidia.ko
5) Reinstalled the packages from the repo through Synaptic
6) Ran sudo nvidia-glx-config enable
7) Restarted X

Everything is happy :D The average frame rate has gone up to about 1400 fps which is more like I was expecting, much better than the 600. UT2K4 runs and doesn't sigfault.

Thanks for your help skoal

---


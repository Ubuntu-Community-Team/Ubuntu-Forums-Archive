---
title: "7800 GTX Driver Issue?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by Loomy on 2006-07-03
Alright my video card is a Nvidia XFX 7800 GTX.  I don't think I have my drivers set up correctly.  My first question is how do I know if my Nvidia Drivers I installed are working?  My second is does anyone know if there is a compatability issue with this card?

---

### Post by encompass on 2006-07-03
if you have installed the driver from the nvidia website.  it should be the same driver for all the cards.
As for checking it.  heck, just play a 3d game.  or better, run glxinfo and scroll up to see the line of direct redering.  if it says yes, I think your good to go.
if it is not working, what howto did you use.  or, what steps did you take to install the driver.

---

### Post by Loomy on 2006-07-03
I used Automatix to install them.  Also where is this GLX thing?  This is only my second day using linux. :-?

---

### Post by Loomy on 2006-07-03
Here is the glxinfo, not sure what it means.
> brian@Brians:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
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
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGI_make_current_read,
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_EXT_texture_from_pixmap
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7800 GTX/PCI/SSE2/3DNOW!
OpenGL version string: 1.4 (2.0.2 NVIDIA 87.62)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program,
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_HP_occlusion_test,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_NV_blend_square,
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fog_distance,
    GL_NV_fragment_program_option, GL_NV_fragment_program2,
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint,
    GL_NV_texgen_reflection, GL_NV_texture_compression_vtc,
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle,
    GL_NV_vertex_program2_option, GL_NV_vertex_program3,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SUN_multi_draw_arrays, GL_SUN_slice_accum
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
0x32 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x42 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x46 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x4a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4b 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x5d 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x61 24 dc  0 32  0 r  y  .  8  8  8  0   24  8 16 16 16 16  2 1 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x65 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x69 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x6d 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
brian@Brians:~$



---

### Post by kpkeerthi on 2006-07-03
Since you have used automatix, you can try the below quick and dirty checks:

1. Open terminal and run ```
cat /etc/X11/xorg.conf | grep nvidia
```
It should show ```
Driver "nvidia"
```

2. Open System -> Preferences -> Screensaver and select 'Ant spotlight'. it should not stutter.

If none of the above works, do let me know and we can continue from here. Otherwise you are good.

As for the compatibility with 7800 GTX, I see no issues so far. Its been a smooth sail since day one.

---

### Post by encompass on 2006-07-03
I didn't like the driver that came with the system... it may not work with your card... which would be weird. as a last resort try this thread... it works perfect with my old 5200
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)
Hope this helps... if you don't do any gaming... you may even like the 3d effects for your desktop... but that for another time. :D

---

### Post by Loomy on 2006-07-03
[QUOTE=kpkeerthi]Since you have used automatix, you can try the below quick and dirty checks:

1. Open terminal and run ```
cat /etc/X11/xorg.conf | grep nvidia
```
It should show ```
Driver "nvidia"
```

2. Open System -> Preferences -> Screensaver and select 'Ant spotlight'. it should not stutter.

If none of the above works, do let me know and we can continue from here. Otherwise you are good.

As for the compatibility with 7800 GTX, I see no issues so far. Its been a smooth sail since day one.[/QUOTE]
Alright I did both of those things and Druver "Nvidia" showed up also the 'AntSpotlight' did not stutter.  Does this mean my video card is configured correctly?

The reasons I thought it was not working correctly is the highest resolution I can select is 1024X768 and I could not get XGL to work following the Nvidia guide step by step.  Perhaps I did something else wrong?

---

### Post by Ramses de Norre on 2006-07-03
Your glxinfo shows that direct rendering is disabled, so you don't have hardware 3D acceleration.. You'll want to check out [this]("http://doc.gwos.org/index.php/Install_Nvidia_driver").

---

### Post by Loomy on 2006-07-03
[QUOTE=Ramses de Norre]Your glxinfo shows that direct rendering is disabled, so you don't have hardware 3D acceleration.. You'll want to check out [this]("http://doc.gwos.org/index.php/Install_Nvidia_driver").[/QUOTE]

Here's what I got...
> brian@Brians:~$ sudo apt-get install nvidia-glx
Password:
Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brian@Brians:~$ sudo apt-get install nvidia-settings
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  nvidia-glx
The following NEW packages will be installed:
  nvidia-settings
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/504kB of archives.
After unpacking 11.5MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 86898 files and directories currently installed.)
Removing nvidia-glx ...
Selecting previously deselected package nvidia-settings.
(Reading database ... 86854 files and directories currently installed.)
Unpacking nvidia-settings (from .../nvidia-settings_1.0-3ubuntu7_i386.deb) ...
Setting up nvidia-settings (1.0-3ubuntu7) ...

brian@Brians:~$ sudo nvidia-glx-config enable
sudo: nvidia-glx-config: command not found
brian@Brians:~$


---

### Post by tseliot on 2006-07-03
[QUOTE=Loomy]Here's what I got...[/QUOTE]
Please read Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by Loomy on 2006-07-03
[QUOTE=tseliot]Please read Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)[/QUOTE]
I don't need to get the legacy drivers do I?

Edit: I followed the guide, but how do I know if it worked?

---

### Post by encompass on 2006-07-04
it would also be important to note that the nvidia logo, big and bright shows up on the screen too.  When the nvidia driver is loaded.

---

### Post by RawMustard on 2006-07-04
I have the same card, and it works great under Dapper with XGL as well.
It would appear you have a problem with your xorg.conf file.
Did you try to run nvidia-xconfig?

Post your xorg.conf file.

---

### Post by tseliot on 2006-07-04
[QUOTE=Loomy]I don't need to get the legacy drivers do I?

Edit: I followed the guide, but how do I know if it worked?[/QUOTE]
Try with:
```
dmesg | grep NVIDIA
```

and
```
glxinfo | grep direct
```

---


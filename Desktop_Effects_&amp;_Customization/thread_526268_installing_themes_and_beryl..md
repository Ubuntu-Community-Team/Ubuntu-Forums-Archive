---
title: "installing themes and beryl."
date: 2007-08-15
forum: Desktop Effects &amp; Customization
---

### Post by damansandhu on 2007-08-15
what should i do to install themes , as i see themes in emerald theme manager but dont know how to apply them and i installed beryl from adept manager , its doing nothing , no cubes . when i open beryl manager , nothing hapens except thengs dont move of desktop until i turn it off.

---

### Post by Criminosis on 2007-08-15
hmm...this one is going to go over my head, i know it. But i'll help for as long as i can :popcorn:

You did set up direct rendering first, right?

---

### Post by damansandhu on 2007-08-15
i think no , how to do direct rendering?

---

### Post by damansandhu on 2007-08-15
i am getting this error

daman@Ultimate:~$ beryl-manager
daman@Ultimate:~$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by nelamvr6 on 2007-08-15
You can download beryl themes [here](http://gnomelook.org/index.php?xcontentmode=103&PHPSESSID=56363ea8824c0fdbc4be81c110a35331).

Don't extract them, leave them in compressed format, and them within the Emerald theme manager select "Import" (or words to that effect, I'm stuck in window$ at work so I can't provide the exact wording or options) and navigate to where you've downloaded the theme file. Select the file and then choose the theme.

It's just that easy!

---

### Post by damansandhu on 2007-08-15
ok , i have imported that themes to emerald , but how to apply them , there is no apply option.

---

### Post by Criminosis on 2007-08-15
> **damansandhu said:**
> i think no , how to do direct rendering?

Sorry, left to eat. :lolflag:

do a glxinfo command in your console, and put the output here

And for bonus points, do you know what your video card / integrated GPU is?

---

### Post by damansandhu on 2007-08-15
i have geforce 7600 gs

daman@Ultimate:~$ glxinfo
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
OpenGL renderer string: GeForce 7600 GS/AGP/SSE2/3DNOW!
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
0x32 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x42 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x46 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
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
0x59 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5d 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x61 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x65 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x69 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6d 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
daman@Ultimate:~$

---

### Post by Criminosis on 2007-08-15
> **damansandhu said:**
> 

direct rendering: Yes


Good man, we got that hill overcome now. 

Now with beryl not launching...that's a tricky one. I didn't have that issue when i set up. Did you ever consider just using using Compiz Fusion? Beryl is dying out since the two projects are merging up. it ran easy mode after i used synaptic to install it.

---

### Post by damansandhu on 2007-08-15
ok , i just want good visuals and 3d effects on ubuntu , i am willing to install compiz fusion for it , do i have to uninstall beryl first?

---

### Post by Criminosis on 2007-08-15
Woah, wait, time out. Are you using kubuntu by chance?

---

### Post by Criminosis on 2007-08-15
> **damansandhu said:**
> ok , i just want good visuals and 3d effects on ubuntu , i am willing to install compiz fusion for it , do i have to uninstall beryl first?

wait nvm, that answered my kubuntu question.

---

### Post by damansandhu on 2007-08-15
i dont know what i am using , when i start my pc , its boots with kubuntu written on it , but i have download ubuntu 7.04 fiesty but it turned out to be kubuntu.

---

### Post by damansandhu on 2007-08-15
what is difference between ubuntu and kubuntu ?? ,

---

### Post by damansandhu on 2007-08-15
anyways , what should i do to install compiz fusion?

---

### Post by Criminosis on 2007-08-15
ubuntu and kubuntu are the same thing at their core. They just have different desktop environments between them.  

I found something that might help [http://ubuntuforums.org/showthread.php?p=1762954](http://ubuntuforums.org/showthread.php?p=1762954)

They point to this place for a fix [http://kubuntuforums.net/forums/index.php?topic=7964.0;topicseen](http://kubuntuforums.net/forums/index.php?topic=7964.0;topicseen)

Tell us how it goes

I'll help you with compiz fusion if you want to change after we fix this. But I figure this needs to be cleared up first, as this might cause more problems later on.

---

### Post by damansandhu on 2007-08-15
how to do that? , how to comment these lines in /etc/X11/xorg.conf file.

---

### Post by Criminosis on 2007-08-15
Open it up :

```
sudo gedit /etc/X11/xorg.conf
```

Navigate to where they dictate you to and place a "#" (without quotation marks :lolflag:) infront of that line of text. This makes the Xserver skip over / ignore that line.

---

### Post by damansandhu on 2007-08-15
daman@Ultimate:~$ sudo gedit /etc/X11/xorg.conf
sudo: gedit: command not found
daman@Ultimate:~$

---

### Post by Criminosis on 2007-08-15
:oops::oops::oops::oops::oops: I goofed, forgot kubuntu doesn't have gedit by default (gedit = gnome edit, i guess. lol) 

I think the kde equivalent is kwrite. sorry :lolflag:

---

### Post by damansandhu on 2007-08-15
ok a blank page opened by using daman@Ultimate:~$ sudo kwrite /etc/x11/xorg.conf
, then i filled it with stuff that is written on that website , now my problem is that i cant save this file , error i am getting is

"the document could not be saved as it was not possible to write to file :///etc/x11/xorg.conf
check that you have write access to that file or that enough disk space is available"

---

### Post by Criminosis on 2007-08-15
> **damansandhu said:**
> ok a blank page opened by using daman@Ultimate:~$ sudo kwrite /etc/x11/xorg.conf
, then i filled it with stuff that is written on that website , now my problem is that i cant save this file , error i am getting is

"the document could not be saved as it was not possible to write to file :///etc/x11/xorg.conf
check that you have write access to that file or that enough disk space is available"

your "x" in "x11" has to be capitalized. Linux is case-sensitive :razz:

---

### Post by damansandhu on 2007-08-15
ok there is something wriiten on the opened page

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "L1515S"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "L1515S"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by damansandhu on 2007-08-15
should i replace it with the stuff that is written on that website.

---

### Post by Criminosis on 2007-08-15
ohh no way. Just modify what they instruct. That file is the .conf (configuration file) of your display server. If you mess with it like that you could (well more like _will_) crash it to the point where it has to boot up into a text console..and i can't help you too easily after that. It is kinda easy to get out of, but it isn't too smart to experiment if you are beginning and/or don't have another system with internet access.

---

### Post by damansandhu on 2007-08-15
ok , i have done as written there , now i am getting this

daman@Ultimate:~$ beryl-manager
daman@Ultimate:~$ **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

---

### Post by Criminosis on 2007-08-15
Oi, i feel stupid...that might have been a major part of it from the start.

At the bottom add this to your xorg.conf :

```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Luckily, both you and I have Nvidia...ATI i've heard is a nightmare (gave up trying to do this stuff on my desktop](*,))

Tell us how it goes!

---

### Post by EXCiD3 on 2007-08-15
> Checking for XComposite extension : failed

I'm pretty sure this just means you don't have the XComposite extension enabled in your xorg.conf.

Add this to the very end of your xorg.conf file: ```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Make sure your default screen screen depth is set to 24, not 16 which is the default. And you will probably also need to add: ```
Option         "AddARGBGLXVisuals" "true"
``` into your Device section (which contains your graphics card) in order to have Window decorations display. Good luck!

**EDIT:** BTW, you may check out [http://compiz.org/NVidia]("http://compiz.org/NVidia") as Beryl is actually a split of the Compiz project. If you have any problems after adding the above options to your xorg.conf, just read through that page and double check that you have everything it does.

---

### Post by damansandhu on 2007-08-15
yo , beryl is working now , thanks bro

---

### Post by Criminosis on 2007-08-15
Nice call on that Visuals. Forgot about that one.

No problem mate. Think about Compiz though. I upgraded to it from Beryl. They have some cool advancements on there.

---

### Post by joshuachad on 2007-08-15
I agree. I first installed Beryl but i like Compiz better since i installed it. For me it was less buggy.You can still use emerald and auquamarine themes provided you install and specify to use them.

---

### Post by EXCiD3 on 2007-08-15
Once Compiz Fusion has an official release, its gonna blow both Compiz and Beryl out of the water ;) Ive tried it already and love it, but I find Compositing window managers to actually make me less productive as i tend to spin the cube around and play with the wobbly windows too often ;)

---

### Post by damansandhu on 2007-08-15
ok , my beryl problem is solved now , but the problem which i face now is how to apply themes from emeral theme manager???

---

### Post by Criminosis on 2007-08-15
> **damansandhu said:**
> ok , my beryl problem is solved now , but the problem which i face now is how to apply themes from emeral theme manager???

oh, right. lol. forgot about that :lolflag:.  ok i'm going to give you a generic guide and see how far (or if you finish) you get.

1. Install emerald (and emerald-themes) (I think you already did this)

2. Modify your compiz command (in your sessions window) to 

```
compiz --replace -c emerald --replace
```

This will make both compiz and emerald-themes start after you login. Your sessions are at System --> Preferences ---> Sessions.  (reboot here, or do something to the point of restarting the X server)

3. Run 

```
emerald-theme-manager 
```

4. Pick a theme 

and the effects should be instantaneous

(as in : don't look for an apply button. there isn't one. :D)

---

### Post by Criminosis on 2007-08-15
> **EXCiD3 said:**
> ...but I find Compositing window managers to actually make me less productive as i tend to spin the cube around and play with the wobbly windows too often ;)


*raises hand for being guilty as well* :lolflag:

---

### Post by damansandhu on 2007-08-15
daman@Ultimate:~$ emerald-theme-manager
daman@Ultimate:~$ compiz --replace -c emerald --replace
[: 222: Failsafe: unexpected operator
Checking for Xgl: not present.
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Converting gconf plugin list: ''
Checking for nVidia: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'
Backend     : kconfig
Integration : true
Profile     : default
Adding plugin svg (svg)
Adding plugin png (png)
Adding plugin ring (ring)
Adding plugin cube (cube)
Adding plugin inotify (inotify)
Adding plugin neg (neg)
Adding plugin showdesktop (showdesktop)
Adding plugin mblur (mblur)
Adding plugin addhelper (addhelper)
Adding plugin wall (wall)
Adding plugin expo (expo)
Adding plugin scale (scale)
Adding plugin clone (clone)
Adding plugin screenshot (screenshot)
Adding plugin wobbly (wobbly)
Adding plugin move (move)
Adding plugin reflex (reflex)
Adding plugin fade (fade)
Adding plugin switcher (switcher)
Adding plugin group (group)
Adding plugin rotate (rotate)
Adding plugin firepaint (firepaint)
Adding plugin water (water)
Adding plugin resizeinfo (resizeinfo)
Adding plugin minimize (minimize)
Adding plugin place (place)
Adding plugin crashhandler (crashhandler)
Adding plugin scaleaddon (scaleaddon)
Adding plugin animation (animation)
Adding plugin annotate (annotate)
Adding plugin snap (snap)
Adding plugin blur (blur)
Adding plugin fadedesktop (fadedesktop)
Adding plugin text (text)
Adding plugin bench (bench)
Adding plugin decoration (decoration)
Adding plugin regex (regex)
Adding plugin winrules (winrules)
Adding plugin resize (resize)
Adding plugin extrawm (extrawm)
Adding plugin cubereflex (cubereflex)
Adding plugin video (video)
Adding plugin vpswitch (vpswitch)
Adding plugin thumbnail (thumbnail)
Adding plugin put (put)
Adding plugin dbus (dbus)
Adding plugin glib (glib)
Adding plugin splash (splash)
Adding plugin imgjpeg (imgjpeg)
Adding plugin opacify (opacify)
Adding plugin zoom (zoom)
Adding plugin plane (plane)
Adding plugin fs (fs)
Adding core settings (General Options)
Adding plugin trailfocus (trailfocus)
Initializing core options...done
Initializing neg options...done
Initializing move options...done
Initializing place options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing resize options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing zoom options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
Segmentation fault (core dumped)
kwin: Unknown option '-c'.
kwin: Use --help to get a list of available command line options.
daman@Ultimate:~$

---

### Post by damansandhu on 2007-08-15
my pc is now partially freezed , i cant

---

### Post by Criminosis on 2007-08-15
I said change your session (follow the menu guide : Your sessions are at System --> Preferences ---> Sessions) 
*reboot*

then do emerald-theme-manager

EDIT : dang it i did it again. You've got beryl, not compiz. and you have KDE. One sec, lemme find you a guild; i haven't ventured into KDE too much.

---

### Post by damansandhu on 2007-08-15
after this my pc was partially freezed , i wasn't able to move or close termianal and other applications.

---

### Post by Criminosis on 2007-08-15
> **damansandhu said:**
> after this my pc was partially freezed , i wasn't able to move or close termianal and other applications.
 
yeah, that my fault, i was trying to force it to use a program that wasn't there.

---

### Post by Criminosis on 2007-08-15
ok, i think i have a workaround (bear with me, I've honestly only used KDE for like 5 minutes).

Can you right click on the desktop and create a "launcher"? if you can it should bring something up asking for

Type
Name
Command 
Comment

---

### Post by damansandhu on 2007-08-15
what should i do now?


and i have a doubt , when i use beryl , the top window options line close , maximize and minimize disappears .

---

### Post by Criminosis on 2007-08-15
check out what i posted above yours. And don't worry about that. That is because emerald is trying to take command of the desktop effects, but it didn't succeed because i goofed up >.<

---

### Post by damansandhu on 2007-08-15
there is no launcer option

---

### Post by Criminosis on 2007-08-15
> **damansandhu said:**
> there is no launcer option

that's alright. I found a different way.

[http://languor.us/node/68](http://languor.us/node/68)

   1. Open up Konqueror. Navigate to your home folder.
   2. Click on View. Select Show Hidden Files.
   3. Look for a folder named .kde and open it.
   4. Look for a folder named Autostart and open it.
   5. Right click inside Konqueror. Select Create New and Text File.
   6. Give the text file the name of the program you would like to autostart.
   7. Open the file using Kate or the text editor of your choice.
   8. Type #!/bin/bash on the first line.
   9. Type the command to launch your program along with any necessary switches.
  10. Save the file.
  11. Right click on the file, select Properties and the Permissions tab.
  12. Finally, check the is executable box and click OK to complete the process.

Ok, that's what we'll do.

Try putting

```
 beryl-manager --replace -c emerald --replace
```

for number 9.

*Reboot*

Then after that type emerald-theme-manager into the konsole. Then pick your theme. 

I *think*:-k that'll do it.

---

### Post by damansandhu on 2007-08-15
which is the program that i would like to autostart?

---

### Post by damansandhu on 2007-08-15
i mean what name should i give to text file.

---

### Post by Criminosis on 2007-08-15
Hmm good question. I don't think it affects the way the program boots, so just call it Desktop Effects or similar. I think it is more for user reference than it is for the OS.

---

### Post by damansandhu on 2007-08-15
is there any other way ?

---

### Post by Criminosis on 2007-08-15
> **damansandhu said:**
> is there any other way ?

didn't work?:confused:

post what you typed for number 9

---


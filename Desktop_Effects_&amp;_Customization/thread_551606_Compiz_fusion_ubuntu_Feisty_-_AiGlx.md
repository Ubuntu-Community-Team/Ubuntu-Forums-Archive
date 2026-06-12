---
title: "Compiz fusion: ubuntu Feisty - AiGlx"
date: 2007-09-15
forum: Desktop Effects &amp; Customization
---

### Post by vampire666eng on 2007-09-15
Once again I have to ask for your help guys.:oops:

Pleased with the overall experience of ubuntu (installed it just 2 days ago ;)), I wanted to give the compiz fusion a try (it looks really cool).

I read countless tutorials-threads and posts but I have some doubts that I wish to clear before proceeding with the installation.

-I understood that I need a CompositeManager: I have to chose between  Xgl and AiGlx. I believe that AiGlx is more stable but Xgl "is the future".
I prefer stability so I should choose AiGlx. But how to install it? Maybe AiGlx it's already installed in ubuntu Feisty? But if that is the case the compiz fusion doesn't work on my pc as I followed this tutorial 
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)
without any success.

-I have a AMD64+ 3000, 2GB RAM, Geforce 6600GT.
-I checked in the restricted drivers manager and the card is running.

What should I do?

Thanks.

---

### Post by CowzRule on 2007-09-15
AiGLX is already installed and is more stable than XGL.
For more info see the links in the following:
[http://ubuntuforums.org/showthread.php?t=272104]("http://ubuntuforums.org/showthread.php?t=272104")

---

### Post by Rupertronco on 2007-09-15
AiGLX and XGL enable 3d OpenGL acceleration. The composite managers are compiz/beryl. It can be very confusing at first, especially with so many similar names (aiglx, xgl, glx, fglrx, etc)

If you have nVidia, you will not need XGL, and may not even need AiGLX (the newest nVidia drivers have built in OpenGL support).

Also type the following into a terminal:
glxgears - what happens?
glxinfo - copy and paste the output of this
gedit /etc/X11/xorg.conf - copy and paste text file

---

### Post by vampire666eng on 2007-09-15
> **CowzRule said:**
> AiGLX is already installed and is more stable than XGL.
For more info see the links in the following:
[http://ubuntuforums.org/showthread.php?t=272104]("http://ubuntuforums.org/showthread.php?t=272104")
Thanks for the reply...I gave all that thread a look, but I'm even more confused now.:)
> **Rupertronco said:**
> AiGLX and XGL enable 3d OpenGL acceleration. The composite managers are compiz/beryl. It can be very confusing at first, especially with so many similar names (aiglx, xgl, glx, fglrx, etc)

If you have nVidia, you will not need XGL, and may not even need AiGLX (the newest nVidia drivers have built in OpenGL support).

Also type the following into a terminal:
glxgears - what happens?
glxinfo - copy and paste the output of this
gedit /etc/X11/xorg.conf - copy and paste text file
Thank you for your help. So:

-with **glxgears** there are 3 gears moving and some benchmarks
```
alain@VAMPIRE666:~$ glxgears
35476 frames in 5.0 seconds = 7095.078 FPS
38103 frames in 5.0 seconds = 7620.437 FPS
38343 frames in 5.0 seconds = 7668.507 FPS
38401 frames in 5.0 seconds = 7680.134 FPS
38375 frames in 5.0 seconds = 7674.969 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
alain@VAMPIRE666:~$ 
alain@VAMPIRE666:~$ 
```
-**glxinfo**:
```
alain@VAMPIRE666:~$ glxinfo
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
OpenGL renderer string: GeForce 6600 GT/PCI/SSE2/3DNOW!
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
alain@VAMPIRE666:~$ 
```
-**the output of  gedit /etc/X11/xorg.conf**:
```
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
    Option         "XkbLayout" "it"
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
    Identifier     "SAMTRON"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "SAMTRON"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```
> If you have nVidia, you will not need XGL, and may not even need AiGLX (the newest nVidia drivers have built in OpenGL support).
Maybe I have to install these?
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by Forlong on 2007-09-15
Please post the output of
```
compiz --replace
```
in a terminal


edit: oh, OK, you have to _enable_ composite in your xorg.conf

Open it in a text editor being root:
```
sudo gedit /etc/X11/xorg.conf
```
And change this:
```
Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```
to
```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by vampire666eng on 2007-09-15
I'm not sure if you still need it but I'll post it anyway.:)
```
compiz --replacealain@VAMPIRE666:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by Forlong on 2007-09-15
Yeah, that's just the confirmation ;)

Change the xorg.conf as I told you and don't forget to restart your X-Server afterwards by pressing [Ctrl]+[Alt]+[Backspace]

---

### Post by vampire666eng on 2007-09-15
bender...ehm, I meant Forlong,:D now it works! Thanks a lot!!!8)

P.S. Just to be sure in the log-in section I should run 
1. Run x client script
and not
2. GNOME
right?

I'm so astonished by the great support of this community! Immediate response and immediate problems solved! 

I wish that one day I could know just a fraction of what you guys know so that I can help other guys and somehow return the favor.;)

---

### Post by Forlong on 2007-09-15
> **vampire666eng said:**
> P.S. Just to be sure in the log-in section I should run 
1. Run x client script
and not
2. GNOME
right?
No, GNOME is the right choice.


I'm glad that it works for you. If you have any further questions, you can use [this thread](http://ubuntuforums.org/showthread.php?t=536149) so I will notice it right away.

---

### Post by vampire666eng on 2007-09-15
Ok, cool.:) Thanks again.

---

### Post by faceless-21 on 2007-09-15
Ok...  Well I am going to copy and paste a tutorial that my friend wrote me and hope it helps you(I tried other tuts and none worked except his...)  So here it is, minus the pics he gave me.

  OH!  use envy to DL your nvidia drivers FIRST envy located here [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
and I used gdebi to install the package(use adept manager to install gdebi)
  and after you install your nvidia drivers go to Kmenu>settings>nvidia settings and make SURE that the color depth is set to "32bit millions" and then save it to your Xorg.conf file.  And if it gives an error when you try to save it, click on the "preview changes" button that will pop up.  It will give you a preview of what your xorg.conf file will look like after the changes.  Then back up your original xorg.conf file and copy that "preview" into your running xorg.conf  Then save it and reboot your system.  
  I kept trying and trying and treying to get it working properly until I finaly figured out(on my own) that the colors had to be 32bit millions before compiz and emerald worked together...  Ok so install envy/nvidia drivers and then try this tutorial...
  BTW I looked at that tutorial you linked too, and that guy had the amaranth repositories...  And maybe those work for some people, but we have had much better luck with the tuxfamily ones...
  anyhoo GOODLUCK!!   and if you have problems message me and I can IM with you or something.  


"Installing Compiz Fusion
	Under Kubuntu Feisty Fawn 7.04.

1.  Open the K Menu (Kubuntu&#8217;s version of the Start Menu. Navigate to 
System -> Konsole



2. Remove Old Files
In Konsole, type 
	sudo apt-get remove compiz* && sudo apt-get autoremove
	(Copy the above text and paste into Konsole with Shift + Insert)



After the Konsole does its thing, and you see your usr@comp:~$ prompt again, type this in:
	sudo apt-get remove beryl* emerald* && sudo apt-get autoremove

These two commands will remove any instances of Compiz and/or Beryl and Emerald Decs.


3. Add Repositories
Now, after reaching the prompt again, type all of this in:

sudo su -c 'echo deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy >> /etc/apt/sources.list'

Now this:

sudo su -c 'echo deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy >> /etc/apt/sources.list'

Now update the package info:

sudo apt-get update


4. INSTALL COMPIZ FUSION &#8211; DON&#8217;T JUMP TO THIS STEP WITHOUT DOING THE ABOVE OR YOU WILL FRAKK YOUR SYSTEM

To install Compiz and all of its components, type into the Konsole (all as one copy/paste):

sudo apt-get install compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra compizconfig-settings-manager sexy-python

After installing, and reaching the prompt yet again, type:

sudo apt-get install emerald emerald-themes

5. Remove the annoying Update Notice (optional)

Open the Konsole and type:

sudo kate /etc/apt/sources.list

Now scroll down to where you see these lines:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

And place a pound sign in front of them so that they now read:

# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

Yay.



(Cont&#8217;d)


6. Configuring Compiz

Run the &#8216;CompizConfig Settings Manager&#8217; by pressing Alt + F2 and typing &#8220;ccsm&#8221; without quotes and pressing enter.

Click on preferences at the bottom left and choose &#8220;Flat-file&#8221; as your backend.

Create a profile if you wish by pressing the Plus sign.

Click the back button.

Scroll down the plugins list until you see the Window Decoration plugin. Make sure its Checked and click on the actual name to configure it.



In this window, add this to the Command field (as seen in screenshot):

emerald --replace

Press Back to save changes and close ALL windows.

Open a fresh Konsole and type in:

kate ~/compiz_start





Now type this into the blank document:

#!/bin/bash
compiz --replace &#8211;indirect-rendering &
sleep 5
emerald --replace 


Save the file and exit. 

In Konsole type:

konqueror ~/

Now find that compiz_start file you just made. Right click on it and click properties.

Click the Permissions Tab.

Check the Is Executable box and press Ok.

Back in the file manager (in which you right clicked the file), now, LEFT click the compiz_start file to execute it.

If all goes well, you should now be running Compiz Fusion with ALL Decs.

---

### Post by Rupertronco on 2007-09-15
So did enabling your composite extension work? What's it say when you run the compiz replace command?

---

### Post by vampire666eng on 2007-09-16
Wow faceless-21! Thanks a lot for your step-by-step tutorial!8-) I'm really speechless.:o
I'm pretty happy with the result so I don't want to try another method and maybe mess things up. Don't get me wrong, I'm not saying that if I use your method I will get things messed up (far from saying that), I'm just saying that now the compiz-fusion works, so I'm afraid of doing other changes or re-do the whole process if I had everything worked out.;) I have solved the problem thanks to Forlong (and his blog), but if I need to re-do the whole process I'll for sure try your method (page bookmarked). No doubt about it! ;) Thanks again!

> **Rupertronco said:**
> So did enabling your composite extension work? What's it say when you run the compiz replace command?

I just enabled the Composite option in xorg.conf as Forlong suggested and now the Compiz Fusion works like a charm.

Before enabling the composite option I had (compiz --replace):

```
compiz --replacealain@VAMPIRE666:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity
```

After enabling the composite option I had (compiz --replace):

```
alain@VAMPIRE666:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5675): Wnck-WARNING **: Unhandled action type (nil)
```

I don't know what are all those warnings...but everything is working as far as I can tell.

---

### Post by Porpoise on 2007-09-16
I've been following this thread looking for inspiration. I recently installed Ubuntu Feisty Fawn and I love it. (The sooner I can get rid of my Win2k the better). I love the look and feel of it but I am still having a few issues (I&#314;l handle them 1 at a time as they are not related).

As far as this thread is concerned, the main issue I'm having is that I have a Radeon All-In-Wonder 7500 card installed coupled to a Samsung SyncMaster 225MW and have been unable to get the system to set the screen size to the full resolution of the panel (1680X1050). I installed Compiz in the hope that I could get the correct screen res through using that. Unfortunately, I got loads of great other features - except, I still can't get the correct screen resolution for my panel!!@@!!

Can you (or someone here) help? Please! Please! I love Ubuntu - Don't want to go back to Windoze!!

---


---
title: "OpenGL problem"
date: 2006-02-02
forum: Gaming &amp; Leisure
---

### Post by nemrod on 2006-02-02
I have a slightly annoying problem with OpenGL. Actually it's more than just slightly annoying, because I can't play any games using OpenGL (that I know of, and have tried).
The error I get when trying to start Stemania is this:```
Error: There was an error while initializing your video card.

   PLEASE DO NOT FILE THIS ERROR AS A BUG!

Video Driver: OpenGL

Initializing OpenGL...
SetVideoMode failed: X11 driver not configured with OpenGL
```For gltron and some other things I've tried I get this:```
[system] Couldn't set GL mode: X11 driver not configured with OpenGL
```
Might as well post my xorg.conf and the output of glxinfo, to spare you from asking :p
```
#Section "InputDevice"
#       Identifier      "Configured Mouse"
#       Driver          "mouse"
#       Option          "CorePointer"
#       Option          "Device"                "/dev/input/mice"
#       Option          "Protocol"              "ImPS/2"
#       Option          "Emulate3Buttons"       "true"
#       Option          "ZAxisMapping"          "4 5"
#EndSection
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Files"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Protocol" "evdev"
    Option         "Dev Name" "Logitech USB-PS/2 Optical Mouse"
    Option         "Dev Phys" "usb-0000:00:10.1-2/input0"
    Option         "Buttons" "10"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "NoLogo"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768"
    EndSubSection
EndSection
```
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/AGP/SSE2/3DNOW!
OpenGL version string: 2.0.1 NVIDIA 81.78
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
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query,
    GL_EXT_vertex_array, GL_HP_occlusion_test, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence,
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program,
    GL_NV_fragment_program_option, GL_NV_fragment_program2, GL_NV_half_float,
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
0x61 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
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
```

The card I'm using is an nVidia 6600GT and I'm using the latest drivers from nVidias site following this guide: [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074) (method #2)

I'd really appreciate some help :)

---

### Post by Lord Illidan on 2006-02-02
Did the installation perform as expected? There were no issues experienced during the installation of the drivers?

Did you install the ubuntu nvidia drivers?

Also, could you play glx games in the past?

---

### Post by nemrod on 2006-02-02
[QUOTE=Lord Illidan]Did the installation perform as expected? There were no issues experienced during the installation of the drivers?

Did you install the ubuntu nvidia drivers?

Also, could you play glx games in the past?[/QUOTE]
1. Yep, it did, no issues.
2. No, if you read my post you would've seen that I installed according to method #2 of the HOWTO here. (nVidias own drivers)
3. Yes, I could, which is why I believe it is a driver problem. I posted this problem in the HOWTO-thread but the author recommended me to make a thread here instead.

---

### Post by handy on 2006-02-02
I let Automatix install the drivers for me, (a few times now) no problems, clean & easy.

It might be worth a try?

---

### Post by nemrod on 2006-02-18
I tried Automatix, and I got another problem. X wouldn't start. I removed the nvidia drivers installed by it and used the backupped xorg.conf and now X works as it should, however OpenGL still does not.
This time I'm getting a different error though, "Segmentation fault".

Any solution to this one?

edit: This time everything gets this error. Including glxgears, which worked before.

---

### Post by patrick295767 on 2006-02-19
I read:
> stemania
  By the way ... have you tried :
```
apt-get -f -y install hatari
```
  then, ```
hatari -f mydiskgame.msa
```
This ste/stf emulator works damn well...
  
Greetings

---


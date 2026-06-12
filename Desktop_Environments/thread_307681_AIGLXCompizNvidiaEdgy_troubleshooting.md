---
title: "AIGLX/Compiz/Nvidia/Edgy troubleshooting"
date: 2006-11-26
forum: Desktop Environments
---

### Post by dguido on 2006-11-26
In one short statement: Compiz segfaults when started and my windows end up missing their borders.

I have:

An NVIDIA 6600GT using the 96.29 drivers from [http://albertomilone.com/drivers/edgy/nonlegacy/32bit](http://albertomilone.com/drivers/edgy/nonlegacy/32bit) .  They are loaded successfully according to my Xorg.0.log

AIGLX from the official Edgy X.org (configuration options listed below).  AIGLX appears to be loaded successfully according to my Xorg.0.log.

Compiz from 'http://www.beerorkid.com/compiz edgy main-edgy'.  When started from the command line in gnome, Compiz says that XGL is not present, it is assuming AIGLX, and then it segfaults.

My xorg.conf contains the following AIGLX/Compiz related options:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    Option         "AIGLX" "true"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
# for AIGLX
    Load           "dbe"
    Load           "glx"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "NoLogo" "true"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "On"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RandRRotation" "true"
    Option         "NoPowerConnectorCheck" "1"
#    Option         "HwCursor" "0"
    Option         "XAANoOffscreenPixmaps" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Anyone know what I'm doing wrong?  I may have some extraneous entries in my xorg.conf.  If someone would like me to post my Xorg.0.log file please just ask.  Thanks!

---

### Post by dguido on 2006-11-26
On second thought, I figured I'd post my glxinfo and Xorg.0.log without anyone asking for it.

glxinfo:
```
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
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/AGP/SSE2
OpenGL version string: 2.1.0 NVIDIA 96.29
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
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
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

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x36 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3e 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x46 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x5a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x61 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x71 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x72 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x75 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x76 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x77 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x78 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x79 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x7e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x7f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x80 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x82 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x83 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x84 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x85 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x86 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x87 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x89 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x8a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x8b 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x8c 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x8d 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x8e 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x8f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x90 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x91 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x92 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x93 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x94 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x95 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x96 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x97 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x98 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
```

---

### Post by dguido on 2006-11-26
Xorg.0.log
```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 26 23:39:46 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to:
        /usr/share/X11/fonts/misc,
        /usr/share/X11/fonts/100dpi/:unscaled,
        /usr/share/X11/fonts/75dpi/:unscaled,
        /usr/share/X11/fonts/Type1,
        /usr/share/X11/fonts/100dpi,
        /usr/share/X11/fonts/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        /usr/share/fonts/X11/misc/,
        /usr/share/fonts/X11/TTF/,
        /usr/share/fonts/X11/OTF,
        /usr/share/fonts/X11/Type1/,
        /usr/share/fonts/X11/CID/,
        /usr/share/fonts/X11/100dpi/,
        /usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AIGLX" "true"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.0
        X.Org XInput driver : 0.6
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1043,80f2 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1043,80a6 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1043,80a6 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1043,80a6 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1043,80a6 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1043,80a6 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1043,810d rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,00f1 card 0000,0000 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:05:0: chip 8086,100e card 1043,80ee rev 02 class 02,00,00 hdr 00
(II) PCI: 02:0a:0: chip 14e4,4318 card 1737,0042 rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
        [0] -1  0       0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xf9000000 - 0xfbefffff (0x2f00000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xe0000000 - 0xf7ffffff (0x18000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [1] -1  0       0x0000e400 - 0x0000e4ff (0x100) IX[B]
        [2] -1  0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [3] -1  0       0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xfbf00000 - 0xfbffffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] rev 162, Mem @ 0xfa000000/24, 0xe0000000/28, 0xf9000000/24, BIOS @ 0xfbee0000/17
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd8000000 from 0xdfffffff to 0xd7ffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xfbfda000 - 0xfbfdbfff (0x2000) MX[B]
        [1] -1  0       0xfbfe0000 - 0xfbffffff (0x20000) MX[B]
        [2] -1  0       0xf8fff400 - 0xf8fff4ff (0x100) MX[B]
        [3] -1  0       0xf8fff800 - 0xf8fff9ff (0x200) MX[B]
        [4] -1  0       0xc4000000 - 0xc40003ff (0x400) MX[B]
        [5] -1  0       0xf8fffc00 - 0xf8ffffff (0x400) MX[B]
        [6] -1  0       0xd8000000 - 0xd7ffffff (0x0) MX[B]O
        [7] -1  0       0xfbee0000 - 0xfbefffff (0x20000) MX[B](B)
        [8] -1  0       0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
        [9] -1  0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [10] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [11] -1 0       0x0000e800 - 0x0000e83f (0x40) IX[B]
        [12] -1 0       0x0000b000 - 0x0000b03f (0x40) IX[B]
        [13] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [14] -1 0       0x00000400 - 0x0000041f (0x20) IX[B]
        [15] -1 0       0x00009400 - 0x0000940f (0x10) IX[B]
        [16] -1 0       0x00009800 - 0x00009803 (0x4) IX[B]
        [17] -1 0       0x0000a000 - 0x0000a007 (0x8) IX[B]
        [18] -1 0       0x0000a400 - 0x0000a403 (0x4) IX[B]
        [19] -1 0       0x0000a800 - 0x0000a807 (0x8) IX[B]
        [20] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [21] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [22] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [23] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [24] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xfbfda000 - 0xfbfdbfff (0x2000) MX[B]
        [1] -1  0       0xfbfe0000 - 0xfbffffff (0x20000) MX[B]
        [2] -1  0       0xf8fff400 - 0xf8fff4ff (0x100) MX[B]
        [3] -1  0       0xf8fff800 - 0xf8fff9ff (0x200) MX[B]
        [4] -1  0       0xc4000000 - 0xc40003ff (0x400) MX[B]
        [5] -1  0       0xf8fffc00 - 0xf8ffffff (0x400) MX[B]
        [6] -1  0       0xd8000000 - 0xd7ffffff (0x0) MX[B]O
        [7] -1  0       0xfbee0000 - 0xfbefffff (0x20000) MX[B](B)
        [8] -1  0       0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
        [9] -1  0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [10] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [11] -1 0       0x0000e800 - 0x0000e83f (0x40) IX[B]
        [12] -1 0       0x0000b000 - 0x0000b03f (0x40) IX[B]
        [13] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [14] -1 0       0x00000400 - 0x0000041f (0x20) IX[B]
        [15] -1 0       0x00009400 - 0x0000940f (0x10) IX[B]
        [16] -1 0       0x00009800 - 0x00009803 (0x4) IX[B]
        [17] -1 0       0x0000a000 - 0x0000a007 (0x8) IX[B]
        [18] -1 0       0x0000a400 - 0x0000a403 (0x4) IX[B]
        [19] -1 0       0x0000a800 - 0x0000a807 (0x8) IX[B]
        [20] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [21] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [22] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [23] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [24] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfbfda000 - 0xfbfdbfff (0x2000) MX[B]
        [5] -1  0       0xfbfe0000 - 0xfbffffff (0x20000) MX[B]
        [6] -1  0       0xf8fff400 - 0xf8fff4ff (0x100) MX[B]
        [7] -1  0       0xf8fff800 - 0xf8fff9ff (0x200) MX[B]
        [8] -1  0       0xc4000000 - 0xc40003ff (0x400) MX[B]
        [9] -1  0       0xf8fffc00 - 0xf8ffffff (0x400) MX[B]
        [10] -1 0       0xd8000000 - 0xd7ffffff (0x0) MX[B]O
        [11] -1 0       0xfbee0000 - 0xfbefffff (0x20000) MX[B](B)
        [12] -1 0       0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
        [13] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [14] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [15] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [16] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [17] -1 0       0x0000e800 - 0x0000e83f (0x40) IX[B]
        [18] -1 0       0x0000b000 - 0x0000b03f (0x40) IX[B]
        [19] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [20] -1 0       0x00000400 - 0x0000041f (0x20) IX[B]
        [21] -1 0       0x00009400 - 0x0000940f (0x10) IX[B]
        [22] -1 0       0x00009800 - 0x00009803 (0x4) IX[B]
        [23] -1 0       0x0000a000 - 0x0000a007 (0x8) IX[B]
        [24] -1 0       0x0000a400 - 0x0000a403 (0x4) IX[B]
        [25] -1 0       0x0000a800 - 0x0000a807 (0x8) IX[B]
        [26] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [27] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [28] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [29] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [30] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.1.1, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9629
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9629
        Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA dlloader X Driver  1.0-9629  Wed Nov  1 19:31:54 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfbfda000 - 0xfbfdbfff (0x2000) MX[B]
        [5] -1  0       0xfbfe0000 - 0xfbffffff (0x20000) MX[B]
        [6] -1  0       0xf8fff400 - 0xf8fff4ff (0x100) MX[B]
        [7] -1  0       0xf8fff800 - 0xf8fff9ff (0x200) MX[B]
        [8] -1  0       0xc4000000 - 0xc40003ff (0x400) MX[B]
        [9] -1  0       0xf8fffc00 - 0xf8ffffff (0x400) MX[B]
        [10] -1 0       0xd8000000 - 0xd7ffffff (0x0) MX[B]O
        [11] -1 0       0xfbee0000 - 0xfbefffff (0x20000) MX[B](B)
        [12] -1 0       0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
        [13] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [14] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [15] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [16] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [17] -1 0       0x0000e800 - 0x0000e83f (0x40) IX[B]
        [18] -1 0       0x0000b000 - 0x0000b03f (0x40) IX[B]
        [19] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [20] -1 0       0x00000400 - 0x0000041f (0x20) IX[B]
        [21] -1 0       0x00009400 - 0x0000940f (0x10) IX[B]
        [22] -1 0       0x00009800 - 0x00009803 (0x4) IX[B]
        [23] -1 0       0x0000a000 - 0x0000a007 (0x8) IX[B]
        [24] -1 0       0x0000a400 - 0x0000a403 (0x4) IX[B]
        [25] -1 0       0x0000a800 - 0x0000a807 (0x8) IX[B]
        [26] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [27] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [28] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [29] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [30] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfbfda000 - 0xfbfdbfff (0x2000) MX[B]
        [5] -1  0       0xfbfe0000 - 0xfbffffff (0x20000) MX[B]
        [6] -1  0       0xf8fff400 - 0xf8fff4ff (0x100) MX[B]
        [7] -1  0       0xf8fff800 - 0xf8fff9ff (0x200) MX[B]
        [8] -1  0       0xc4000000 - 0xc40003ff (0x400) MX[B]
        [9] -1  0       0xf8fffc00 - 0xf8ffffff (0x400) MX[B]
        [10] -1 0       0xd8000000 - 0xd7ffffff (0x0) MX[B]O
        [11] -1 0       0xfbee0000 - 0xfbefffff (0x20000) MX[B](B)
        [12] -1 0       0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
        [13] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [14] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [15] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [16] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [17] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [18] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [19] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [20] -1 0       0x0000e800 - 0x0000e83f (0x40) IX[B]
        [21] -1 0       0x0000b000 - 0x0000b03f (0x40) IX[B]
        [22] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [23] -1 0       0x00000400 - 0x0000041f (0x20) IX[B]
        [24] -1 0       0x00009400 - 0x0000940f (0x10) IX[B]
        [25] -1 0       0x00009800 - 0x00009803 (0x4) IX[B]
        [26] -1 0       0x0000a000 - 0x0000a007 (0x8) IX[B]
        [27] -1 0       0x0000a400 - 0x0000a403 (0x4) IX[B]
        [28] -1 0       0x0000a800 - 0x0000a807 (0x8) IX[B]
        [29] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [30] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [31] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [32] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [33] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[B]
        [34] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [35] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "NoPowerConnectorCheck" "1"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "On"
(**) NVIDIA(0): Option "RandRRotation" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Skipping Power Connector Check.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 GT at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.57.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 GT at PCI:1:0:0:
(--) NVIDIA(0):     HIQ L90D+ DVI (DFP-0)
(--) NVIDIA(0): HIQ L90D+ DVI (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): HIQ L90D+ DVI (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (87, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xf9000000 - 0xf9ffffff (0x1000000) MX[B]
        [1] 0   0       0xe0000000 - 0xefffffff (0x10000000) MX[B]
        [2] 0   0       0xfa000000 - 0xfaffffff (0x1000000) MX[B]
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xfbfda000 - 0xfbfdbfff (0x2000) MX[B]
        [8] -1  0       0xfbfe0000 - 0xfbffffff (0x20000) MX[B]
        [9] -1  0       0xf8fff400 - 0xf8fff4ff (0x100) MX[B]
        [10] -1 0       0xf8fff800 - 0xf8fff9ff (0x200) MX[B]
        [11] -1 0       0xc4000000 - 0xc40003ff (0x400) MX[B]
        [12] -1 0       0xf8fffc00 - 0xf8ffffff (0x400) MX[B]
        [13] -1 0       0xd8000000 - 0xd7ffffff (0x0) MX[B]O
        [14] -1 0       0xfbee0000 - 0xfbefffff (0x20000) MX[B](B)
        [15] -1 0       0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
        [16] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [17] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [18] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [19] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [20] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [21] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [22] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [23] -1 0       0x0000e800 - 0x0000e83f (0x40) IX[B]
        [24] -1 0       0x0000b000 - 0x0000b03f (0x40) IX[B]
        [25] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [26] -1 0       0x00000400 - 0x0000041f (0x20) IX[B]
        [27] -1 0       0x00009400 - 0x0000940f (0x10) IX[B]
        [28] -1 0       0x00009800 - 0x00009803 (0x4) IX[B]
        [29] -1 0       0x0000a000 - 0x0000a007 (0x8) IX[B]
        [30] -1 0       0x0000a400 - 0x0000a403 (0x4) IX[B]
        [31] -1 0       0x0000a800 - 0x0000a807 (0x8) IX[B]
        [32] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [33] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [34] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [35] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [36] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[B]
        [37] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [38] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "XAANoOffscreenPixmaps" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+us" };
    xkb_geometry             { include "pc(pc104)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
AUDIT: Sun Nov 26 23:39:50 2006: 11443 X: client 2 rejected from local host
AUDIT: Sun Nov 26 23:39:50 2006: 11443 X: client 3 rejected from local host
    xkb_types                { include "%" };
    xkb_compatibility        { include "%" };
    xkb_symbols              { include "%" };
    xkb_geometry             { include "%" };
(EE) Error loading keymap /var/lib/xkb/server-0.xkm
```

---

### Post by dguido on 2006-11-27
glxgears
8603 frames in 5.0 seconds = 1720.491 FPS
8491 frames in 5.0 seconds = 1698.112 FPS
8492 frames in 5.0 seconds = 1698.289 FPS
8493 frames in 5.0 seconds = 1698.488 FPS

Seems kind of low... I have a Pentium D 3.4 Ghz, Nvidia 6600GT, and 3 GB of RAM.  Is ~1700 fps normal or low?

---

### Post by halfvolle melk on 2006-11-27
Those logs look fine AFAICT. If got the same card and get higher FPS, but glxgears is no good for benchmarking. For instance, if I full screen the gears frame rate drops to 230. Check out GLobs for benchmarking:
[http://www.ubuntuforums.org/showthread.php?t=157429](http://www.ubuntuforums.org/showthread.php?t=157429)

---

### Post by tseliot on 2006-11-27
post the output of this command:
```
glxinfo | grep direct
```

---

### Post by kimro on 2006-11-27
I have a 6600GT 128mb and had the same problem. I just installed Beryl. I am very interested in a solution as well.

---

### Post by dguido on 2006-11-27
> **tseliot said:**
> post the output of this command:
```
glxinfo | grep direct
```

direct rendering: Yes

You can see the full output 4 posts up ^.

---


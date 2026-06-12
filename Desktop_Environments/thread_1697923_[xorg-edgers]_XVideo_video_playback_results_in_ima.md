---
title: "[xorg-edgers] XVideo video playback results in image corruption"
date: 2011-03-01
forum: Desktop Environments
---

### Post by Prodoc on 2011-03-01
Yesterday I added the [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) packages to my system repositories and upgrade the provided packages to try out the Gallium3D drivers.
It did successfully started using Gallium3D using the r300g drivers.

Both VLC and gstreamer, thus Totem, default to using Xv for video output. In this mode video playback happens with heavy image corruption. This can be seen in the attached image. The problem disappears when I switch to just 'X11 video output (XCB)' in VLC or 'X Window System (No Xv)' for gstreamer.
The strange thing with gstream is that the test does work fine. I.e. if I start 'gstreamer-properties' and set the default output to 'X Window System (X11/XShm/Xv)' and run the test, all is well.

Specs:
ATI Radeon X850XT
Ubuntu 10.10

I'm not sure what kind of details I should provide but here's at least some. Let me know if you need any more info.

Output of "glxinfo":
```
name of display: :0.0
r300: DRM version: 2.5.0, Name: ATI R481, ID: 0x4b49, GB: 4, Z: 1
r300: GART size: 509 MB, VRAM size: 256 MB
r300: AA compression: NO, Z compression: NO, HiZ: NO
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI R481
OpenGL version string: 2.1 Mesa 7.11-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_copy_buffer, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query2, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture3D, GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_EXT_vertex_array, GL_OES_EGL_image, 
    GL_OES_read_format, GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_texgen_reflection, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
```

Output of "dmesg | grep drm":
```
[    1.262048] [drm] Initialized drm 1.1.0 20060810
[    2.354546] [drm] radeon defaulting to kernel modesetting.
[    2.354549] [drm] radeon kernel modesetting enabled.
[    2.356507] [drm] initializing kernel modesetting (R420 0x1002:0x4B49).
[    2.356704] [drm] register mmio base: 0xFBE00000
[    2.356706] [drm] register mmio size: 65536
[    2.357771] [drm:radeon_agp_init] *ERROR* Unable to acquire AGP: -19
[    2.357773] [drm] Forcing AGP to PCI mode
[    2.357776] [drm] Generation 2 PCI interface, using max accessible memory
[    2.357844] [drm] radeon: irq initialized.
[    2.357951] [drm] Detected VRAM RAM=256M, BAR=128M
[    2.357956] [drm] RAM width 256bits DDR
[    2.358066] [drm] radeon: 256M of VRAM memory ready
[    2.358068] [drm] radeon: 512M of GTT memory ready.
[    2.358091] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    2.360636] [drm] radeon: 4 quad pipes, 1 z pipes initialized.
[    2.361355] [drm] Loading R400 Microcode
[    2.363033] [drm] radeon: ring at 0x00000000C8000000
[    2.363056] [drm] ring test succeeded in 2 usecs
[    2.363203] [drm] radeon: ib pool ready.
[    2.363275] [drm] ib test succeeded in 0 usecs
[    2.363306] [drm] Default TV standard: NTSC
[    2.363587] [drm] Default TV standard: NTSC
[    2.363871] [drm] Radeon Display Connectors
[    2.363873] [drm] Connector 0:
[    2.363875] [drm]   VGA
[    2.363877] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[    2.363879] [drm]   Encoders:
[    2.363881] [drm]     CRT1: INTERNAL_DAC1
[    2.363882] [drm] Connector 1:
[    2.363884] [drm]   S-video
[    2.363885] [drm]   Encoders:
[    2.363886] [drm]     TV1: INTERNAL_DAC2
[    2.363888] [drm] Connector 2:
[    2.363889] [drm]   DVI-I
[    2.363891] [drm]   HPD1
[    2.363893] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[    2.363895] [drm]   Encoders:
[    2.363897] [drm]     CRT2: INTERNAL_DAC2
[    2.363898] [drm]     DFP1: INTERNAL_TMDS1
[    2.500687] [drm] Possible lm63 thermal controller at 0x4c
[    2.707973] [drm] fb mappable at 0xE8040000
[    2.707977] [drm] vram apper at 0xE8000000
[    2.707979] [drm] size 5242880
[    2.707980] [drm] fb depth is 24
[    2.707982] [drm]    pitch is 5120
[    2.967437] fb0: radeondrmfb frame buffer device
[    2.967439] drm: registered panic notifier
[    2.967676] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
```

Output of "glxgears"
```
r300: DRM version: 2.5.0, Name: ATI R481, ID: 0x4b49, GB: 4, Z: 1
r300: GART size: 509 MB, VRAM size: 256 MB
r300: AA compression: NO, Z compression: NO, HiZ: NO
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
298 frames in 5.0 seconds = 59.535 FPS
...
```

What could be the cause of the problem and how can I fix it?
If it is a bug, where should it be reported?

---

### Post by zenon222 on 2011-03-04
Same here with the radeon driver and xorg-edgers.
There is a way to install the updated drivers and keep the mainline xorg sever... If nobody finds an answer, that's what I'll do.

Try running GIMP, if loading an image in gimp utterly corrupts your display.  I do have a simple fix for that.  Found it from the very helpful [email]xorg-driver-ati@lists.x.org[/email]

---

### Post by lext on 2011-09-02
Same with xorg-edgers + ubuntu 10.04 + radeon M6 (r100) 

worked nicely but very slow xv before (x-update) hope somebody works on a bugfix

---


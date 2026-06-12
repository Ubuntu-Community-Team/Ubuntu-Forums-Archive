---
title: "Call of Duty on laptop does not start"
date: 2005-11-24
forum: Gaming &amp; Leisure
---

### Post by telrúnya on 2005-11-24
Hi all

I'm trying to play Call of Duty on a Dell X300 Laptop with Ubuntu Breezy. Installation worked with the Loki installer but I can't start the game:

[PHP]
COD 1.3 build win-x86 Mar  2 2004
----- FS_Startup -----
Current language: english
Current search path:
H:\cod\main\pakb.pk3 (60 files)
H:\cod\main\paka.pk3 (41 files)
H:\cod\main\pak9.pk3 (149 files)
H:\cod\main\pak8.pk3 (235 files)
H:\cod\main\pak6.pk3 (3 files)
H:\cod\main\pak5.pk3 (4858 files)
H:\cod\main\pak4.pk3 (1668 files)
H:\cod\main\pak3.pk3 (1992 files)
H:\cod\main\pak2.pk3 (694 files)
H:\cod\main\pak1.pk3 (2642 files)
H:\cod\main\pak0.pk3 (12816 files)
H:\cod/main
H:\cod\main\localized_english_pak5.pk3 (46 files)
    localized assets pak file for english
H:\cod\main\localized_english_pak3.pk3 (7 files)
    localized assets pak file for english
H:\cod\main\localized_english_pak2.pk3 (9 files)
    localized assets pak file for english
H:\cod\main\localized_english_pak1.pk3 (3736 files)
    localized assets pak file for english
H:\cod\main\localized_english_pak0.pk3 (1204 files)
    localized assets pak file for english

File Handles:
----------------------
30160 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec config.cfg
couldn't exec autoexec.cfg
========= autoconfigure
configure.csv: using configuration 0 cpu MHz 512 sys MB 64 vid MB
execing configure.cfg
fs_basepath is write protected.
fs_homepath is write protected.
Hunk_Clear: reset the hunk ok
...detecting CPU, found Intel Pentium III
Measured CPU speed is 0.60 GHz
System memory is 622 MB (capped at 1 GB)
Video card memory is 64 MB
Streaming SIMD Extensions (SSE) supported

----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
Initializing OpenGL subsystem
...initializing QGL
...calling LoadLibrary( 'c:\windows\system32\opengl32.dll' ): succeeded
...setting mode 4: 800 600 FS
...using colorbits of 32
...calling CDS: failed, bad mode
...trying next higher resolution: ok
...registered window class
...created window@0,0 (800x600)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 32, 24, 8 )
...15 PFDs found
...MCD acceleration found
...PIXELFORMAT 3 selected
...creating GL context: succeeded
...making context current: succeeded
Initializing OpenGL extensions

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 6.5
GL_EXTENSIONS:  GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
----- CL_Shutdown -----
RE_Shutdown( 1 )
Shutting down OpenGL subsystem
...wglMakeCurrent( NULL, NULL ): success
...deleting GL context: success
...releasing DC: success
...destroying window
...resetting display
...shutting down QGL
...unloading OpenGL DLL
-----------------------
Hunk_Clear: reset the hunk ok
Your video card appears to be missing one or more features required to run Call of Duty.

You should install the latest drivers for your video card, being sure to uninstall the old drivers first.  If you already have the latest drivers, you should completely uninstall the drivers and then reinstall them.  This fixes most problems.  If the game still doesn't work, it may be that your video card does not have the minimum features required.  Please check the readme for more information, including a list of supported video cards.
[/PHP]

glxgears results in about 1150 FPS, so DRI is enabled (video card is a integrated Intel 855GM).

Please help!

Greetings
telrúnya

---

### Post by telrúnya on 2005-11-25
I just installed and configured the 855resolution package and the situation improved. Well, I get another error message:

```

COD 1.3 build win-x86 Mar  2 2004
----- FS_Startup -----
Current language: english
Current search path:
H:\cod\main\pakb.pk3 (60 files)
H:\cod\main\paka.pk3 (41 files)
H:\cod\main\pak9.pk3 (149 files)
H:\cod\main\pak8.pk3 (235 files)
H:\cod\main\pak6.pk3 (3 files)
H:\cod\main\pak5.pk3 (4858 files)
H:\cod\main\pak4.pk3 (1668 files)
H:\cod\main\pak3.pk3 (1992 files)
H:\cod\main\pak2.pk3 (694 files)
H:\cod\main\pak1.pk3 (2642 files)
H:\cod\main\pak0.pk3 (12816 files)
H:\cod/main
H:\cod\main\localized_english_pak5.pk3 (46 files)
    localized assets pak file for english
H:\cod\main\localized_english_pak3.pk3 (7 files)
    localized assets pak file for english
H:\cod\main\localized_english_pak2.pk3 (9 files)
    localized assets pak file for english
H:\cod\main\localized_english_pak1.pk3 (3736 files)
    localized assets pak file for english
H:\cod\main\localized_english_pak0.pk3 (1204 files)
    localized assets pak file for english

File Handles:
----------------------
30160 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec config.cfg
couldn't exec autoexec.cfg
========= autoconfigure
configure.csv: using configuration 0 cpu MHz 512 sys MB 64 vid MB
execing configure.cfg
fs_basepath is write protected.
fs_homepath is write protected.
Hunk_Clear: reset the hunk ok
...detecting CPU, found Intel Pentium III
Measured CPU speed is 0.60 GHz
System memory is 622 MB (capped at 1 GB)
Video card memory is 64 MB
Streaming SIMD Extensions (SSE) supported

----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
Initializing OpenGL subsystem
...initializing QGL
...calling LoadLibrary( 'c:\windows\system32\opengl32.dll' ): succeeded
...setting mode 4: 800 600 FS
...using colorbits of 32
...calling CDS: failed, bad mode
...trying next higher resolution: ok
...registered window class
...created window@0,0 (800x600)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 32, 24, 8 )
...15 PFDs found
...MCD acceleration found
...PIXELFORMAT 3 selected
...creating GL context: succeeded
...making context current: succeeded
video card cannot set mode 800x600 because GL_MAX_TEXTURE_SIZE is only 512
...restoring display settings
...WARNING: could not set the given mode (4)
...shutting down QGL
...unloading OpenGL DLL
Forcing 640x480 resolution to allow OpenGL to run in fullscreen
...initializing QGL
...calling LoadLibrary( 'c:\windows\system32\opengl32.dll' ): succeeded
...setting mode 3: 640 480 FS
...using colorbits of 32
...calling CDS: failed, bad mode
...trying next higher resolution: ok
...created window@0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 32, 24, 8 )
...15 PFDs found
...MCD acceleration found
...PIXELFORMAT 3 selected
...creating GL context: succeeded
...making context current: succeeded
video card cannot set mode 640x480 because GL_MAX_TEXTURE_SIZE is only 512
...restoring display settings
...WARNING: could not set the given mode (3)
...shutting down QGL
...unloading OpenGL DLL
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Hunk_Clear: reset the hunk ok
Could not load OpenGL.  Make sure that you have the latest drivers for your video card from the manufacturer's web site.

```

The problem seems to be "video card cannot set mode 800x600 because GL_MAX_TEXTURE_SIZE is only 512". Any ideas?

glxinfo:

```


name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20050225 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

Thank you!

---


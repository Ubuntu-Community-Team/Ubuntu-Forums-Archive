---
title: "Doom 3 troubles on amd64 and ATI"
date: 2006-07-03
forum: Gaming &amp; Leisure
---

### Post by thedaemon666 on 2006-07-03
I have been trying to get Doom 3 to run in native Ubuntu 6.06 amd64. I have installed the Ati proprietary linux driver version 8.26.18 and have all the proper pk4 files copied to my base directory for doom 3. I have googled and searched many linux forums and have came to no solution for my problem. I have verified that my system is running in 24 bit color depth. Below is the outputs from doom 3, glxinfo, and fglrxinfo. Any help is appreciated.

Doom 3 output
```

DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth1 - 192.168.1.103/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/daemonx/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 49
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 53
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 54
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL

```

glxinfo output
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5879 (8.26.18)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3,
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None

```

fglrxinfo output
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5879 (8.26.18)

```

Anybody have any idea or direction that they can point me in to find a solution? Or is it hopeless? I would like to avoid booting into the plague that is known as windows as much as possible and getting Doom 3 running in linux will help me to do so haha, and yes I do realise that Doom 3 will not run amazingly on my system but its something I want to see happen.

---


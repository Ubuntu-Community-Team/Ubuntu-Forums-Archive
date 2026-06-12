---
title: "Can't play Quake 4!"
date: 2006-08-30
forum: Gaming &amp; Leisure
---

### Post by linuxpenguin on 2006-08-30
I want to play Quake 4.  I installed id's patch, copied the files from the CD, and I already had the nVidia drivers installed, but still when I try to play Quake 4 I get errors:

```
t@darkrider:~$ quake4
Quake4 Final V1.3.0.2393 Build 2393.0 linux-x86 Aug  7 2006
found interface lo - loopback
found interface eth0 - 172.16.0.170/255.255.240.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0x1e246dd2
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x7d4d8d2a
Loaded pk4 /usr/local/games/quake4/q4base/game200.pk4 with checksum 0x46f04342
Loaded pk4 /usr/local/games/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /usr/local/games/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /usr/local/games/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /usr/local/games/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /usr/local/games/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /usr/local/games/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /usr/local/games/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /usr/local/games/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /usr/local/games/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /usr/local/games/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /usr/local/games/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /usr/local/games/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /usr/local/games/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /usr/local/games/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /usr/local/games/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /usr/local/games/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /usr/local/games/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /usr/local/games/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /usr/local/games/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /usr/local/games/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Current search path:
/home/scott/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/usr/local/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/usr/local/games/quake4/q4base/pak020.pk4 (11 files)
/usr/local/games/quake4/q4base/pak019.pk4 (1206 files)
/usr/local/games/quake4/q4base/pak018.pk4 (3 files)
/usr/local/games/quake4/q4base/pak017.pk4 (3 files)
/usr/local/games/quake4/q4base/pak016.pk4 (193 files)
/usr/local/games/quake4/q4base/pak015.pk4 (34 files)
/usr/local/games/quake4/q4base/pak014.pk4 (552 files)
/usr/local/games/quake4/q4base/pak013.pk4 (239 files)
/usr/local/games/quake4/q4base/pak012.pk4 (1081 files)
/usr/local/games/quake4/q4base/pak011.pk4 (5620 files)
/usr/local/games/quake4/q4base/pak010.pk4 (5539 files)
/usr/local/games/quake4/q4base/pak009.pk4 (1284 files)
/usr/local/games/quake4/q4base/pak008.pk4 (1289 files)
/usr/local/games/quake4/q4base/pak007.pk4 (1330 files)
/usr/local/games/quake4/q4base/pak006.pk4 (1343 files)
/usr/local/games/quake4/q4base/pak005.pk4 (1395 files)
/usr/local/games/quake4/q4base/pak004.pk4 (2249 files)
/usr/local/games/quake4/q4base/pak003.pk4 (1281 files)
/usr/local/games/quake4/q4base/pak002.pk4 (313 files)
/usr/local/games/quake4/q4base/pak001.pk4 (5837 files)
/usr/local/games/quake4/q4base/game200.pk4 (9 files)
/usr/local/games/quake4/q4base/game100.pk4 (2 files)
/usr/local/games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 64 loaded
WARNING: file materials/mappack1.mtr, line 175: material 'models/mapobjects/multiplayer/jump_pad/jump_pad_color' previously defined at materials/mapobjects_mp2.mtr:1
WARNING: file materials/mappack1.mtr, line 199: material 'models/mapobjects/multiplayer/jump_pad/jump_pad_color_glow' previously defined at materials/mapobjects_mp2.mtr:29
WARNING: file materials/mappack1.mtr, line 224: material 'models/mapobjects/multiplayer/acceleration_pad/acceleration_pad_color' previously defined at materials/mapobjects_mp2.mtr:53
WARNING: file materials/mappack1.mtr, line 242: material 'models/mapobjects/multiplayer/acceleration_pad/arrows_color' previously defined at materials/mapobjects_mp2.mtr:78
WARNING: file materials/stroyent_mp.mtr, line 10: material 'textures/stroyent/mp/stroy_pillar1_orange' previously defined at materials/mappack1.mtr:1
WARNING: file materials/stroyent_mp.mtr, line 18: material 'textures/stroyent/mp/stroy_pillar1_green' previously defined at materials/mappack1.mtr:12
WARNING: file materials/stroyent_mp.mtr, line 26: material 'textures/stroyent/mp/tun6_green' previously defined at materials/mappack1.mtr:20
WARNING: file materials/stroyent_mp.mtr, line 34: material 'textures/stroyent/mp/tun6small_green' previously defined at materials/mappack1.mtr:28
WARNING: file materials/stroyent_mp.mtr, line 42: material 'textures/stroyent/mp/tunbump_green' previously defined at materials/mappack1.mtr:36
WARNING: file materials/stroyent_mp.mtr, line 50: material 'textures/stroyent/mp/tunpipe_green' previously defined at materials/mappack1.mtr:44
WARNING: file materials/stroyent_mp.mtr, line 58: material 'textures/stroyent/mp/tunpipe_orange' previously defined at materials/mappack1.mtr:52
WARNING: file materials/stroyent_mp.mtr, line 66: material 'textures/stroyent/mp/tunpipe2_orange' previously defined at materials/mappack1.mtr:60
WARNING: file materials/stroyent_mp.mtr, line 74: material 'textures/stroyent/mp/tunpipe2_green' previously defined at materials/mappack1.mtr:68
WARNING: file materials/stroyent_mp.mtr, line 92: material 'textures/stroyent/mp/tunwall12_orange' previously defined at materials/mappack1.mtr:76
WARNING: file materials/stroyent_mp.mtr, line 100: material 'textures/stroyent/mp/tunwall12_green' previously defined at materials/mappack1.mtr:94
WARNING: file materials/stroyent_mp.mtr, line 108: material 'textures/stroyent/mp/tunwall15_orange' previously defined at materials/mappack1.mtr:102
WARNING: file materials/stroyent_mp.mtr, line 116: material 'textures/stroyent/mp/tunwall15_green' previously defined at materials/mappack1.mtr:110
WARNING: file materials/stroyent_mp.mtr, line 139: material 'textures/stroyent/mp/concrete09asmooth' previously defined at materials/mappack1.mtr:118
WARNING: file materials/stroyent_mp.mtr, line 140: material 'textures/stroyent/mp/concrete09smooth' previously defined at materials/mappack1.mtr:141
WARNING: file materials/stroyent_mp.mtr, line 141: material 'textures/stroyent/mp/concrete04smooth' previously defined at materials/mappack1.mtr:142
521ms to load 1125k of material
113ms to load 43k of skin
283ms to load 722k of sound
4ms to load 1k of materialType
483ms to load 2889k of lipSync
78ms to load 105k of playback
1184ms to load 1687k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' without VO
.... found additional language 'italian' without VO
.... found additional language 'spanish' without VO
688 strings read from strings/english_code.lang
1776 strings read from strings/english_guis.lang
1779 strings read from strings/english_mappack.lang
2255 strings read from strings/english_maps.lang
3 strings read from strings/french_mappack.lang
3 strings read from strings/italian_mappack.lang
3 strings read from strings/spanish_mappack.lang
Couldn't open journal files
execing default.cfg
couldn't exec editor.cfg
couldn't exec Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1440x900 SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1440x900 SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL

```

What should I do?

---

### Post by atriste on 2006-08-30
is your direct rendering working? 

what does $glxinfo say? 

i also noticed that during the startup it mentioned it was looking in your home folder as well as your usr folder

---

### Post by linuxpenguin on 2006-08-31
> **atriste said:**
> is your direct rendering working? 

what does $glxinfo say? 
```
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
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
OpenGL renderer string: GeForce Go 7400/PCI/SSE2
OpenGL version string: 2.0.2 NVIDIA 87.62
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
    GL_EXT_stencil_clear_tag, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
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
0x21 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x22 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x2a 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  2 1 Ncon
0x2b 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  4 1 Ncon
0x2c 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  2 1 Ncon
0x2d 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  4 1 Ncon
0x2e 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  2 1 Ncon
0x2f 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  4 1 Ncon
0x30 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  2 1 Ncon
0x31 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  4 1 Ncon
0x32 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  2 1 Ncon
0x33 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  4 1 Ncon
0x34 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  2 1 Ncon
0x35 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  4 1 Ncon
0x36 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x37 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x38 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x39 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x3a 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x3b 16 dc  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x3c 16 dc  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x3d 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  2 1 Ncon
0x3e 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  4 1 Ncon
0x3f 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  2 1 Ncon
0x40 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  4 1 Ncon
0x41 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  2 1 Ncon
0x42 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  4 1 Ncon
0x43 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  2 1 Ncon
0x44 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  4 1 Ncon
0x45 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  2 1 Ncon
0x46 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  4 1 Ncon
0x47 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  2 1 Ncon
0x48 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  4 1 Ncon

```

> i also noticed that during the startup it mentioned it was looking in your home folder as well as your usr folder
I don't know about Quake 4, but I remember DOOM3 looks for mods in your home folder.

---


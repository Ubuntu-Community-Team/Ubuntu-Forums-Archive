---
title: "Enemy Territory Quake Wars Crashes"
date: 2009-03-25
forum: Gaming &amp; Leisure
---

### Post by GSZX1337 on 2009-03-25
For some reason, I can't get Enemy Territory Quake Wars to run without having it crash after a few minutes. It used to run fine, but eventually it stopped running well. I figured it was my updated drivers, so I rolled them back to the last working version. No dice. I know my video card is not overheating or anything because I can play games like FEAR Combat and S.T.A.L.K.E.R. (in Winedohs at least).

I'm not on my Ubuntu computer right now, so I can't run ETQW in the terminal. Any help will be appreciated.

---

### Post by GSZX1337 on 2009-03-27
I got to my Ubuntu computer, here's the terminal output:
```
gszx1337@GMan:~$ /usr/local/games/etqw/etqw
ETQW 1.5.12663.12663  linux-x86 May  9 2008 13:50:52
found interface lo - loopback
found interface eth0 - 192.168.0.4/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /usr/local/games/etqw/base/game000.pk4 with checksum 0x3efd73a5
Loaded pk4 /usr/local/games/etqw/base/game001.pk4 with checksum 0xa02f1c18
Loaded pk4 /usr/local/games/etqw/base/game002.pk4 with checksum 0x87457e61
Loaded pk4 /usr/local/games/etqw/base/pak000.pk4 with checksum 0x442eb08b
Loaded pk4 /usr/local/games/etqw/base/pak001.pk4 with checksum 0x10e16e6
Loaded pk4 /usr/local/games/etqw/base/pak002.pk4 with checksum 0x8dbe7353
Loaded pk4 /usr/local/games/etqw/base/pak003.pk4 with checksum 0x99dfcabb
Loaded pk4 /usr/local/games/etqw/base/pak004.pk4 with checksum 0x7e49f838
Loaded pk4 /usr/local/games/etqw/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /usr/local/games/etqw/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /usr/local/games/etqw/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /usr/local/games/etqw/base/pak008.pk4 with checksum 0x71a93b80
Loaded pk4 /usr/local/games/etqw/base/zpak_english000.pk4 with checksum 0x977c7bd0
Loaded pk4 /usr/local/games/etqw/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /usr/local/games/etqw/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /usr/local/games/etqw/base/zpak_english003.pk4 with checksum 0xc2d7ed49
Loaded pk4 /usr/local/games/etqw/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /usr/local/games/etqw/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /usr/local/games/etqw/base/zpak_french003.pk4 with checksum 0x8f315c7b
Loaded pk4 /usr/local/games/etqw/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /usr/local/games/etqw/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /usr/local/games/etqw/base/zpak_german003.pk4 with checksum 0x370e6186
Loaded pk4 /usr/local/games/etqw/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /usr/local/games/etqw/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /usr/local/games/etqw/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /usr/local/games/etqw/base/zpak_korean003.pk4 with checksum 0x4f8dfac1
Loaded pk4 /usr/local/games/etqw/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /usr/local/games/etqw/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /usr/local/games/etqw/base/zpak_polish003.pk4 with checksum 0x8d9af876
Loaded pk4 /usr/local/games/etqw/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /usr/local/games/etqw/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /usr/local/games/etqw/base/zpak_russian003.pk4 with checksum 0x7e90b040
Loaded pk4 /usr/local/games/etqw/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /usr/local/games/etqw/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Loaded pk4 /usr/local/games/etqw/base/zpak_spanish003.pk4 with checksum 0xe7d989bc
Current search path:
/home/gszx1337/.etqwcl/base
/usr/local/games/etqw/base
/usr/local/games/etqw/base/zpak_spanish003.pk4 (6 files)
/usr/local/games/etqw/base/zpak_spanish002.pk4 (119 files)
/usr/local/games/etqw/base/zpak_spanish001.pk4 (13 files)
/usr/local/games/etqw/base/zpak_russian003.pk4 (5 files)
/usr/local/games/etqw/base/zpak_russian002.pk4 (119 files)
/usr/local/games/etqw/base/zpak_russian001.pk4 (13 files)
/usr/local/games/etqw/base/zpak_polish003.pk4 (6 files)
/usr/local/games/etqw/base/zpak_polish002.pk4 (119 files)
/usr/local/games/etqw/base/zpak_polish001.pk4 (13 files)
/usr/local/games/etqw/base/zpak_korean003.pk4 (5 files)
/usr/local/games/etqw/base/zpak_korean002.pk4 (12 files)
/usr/local/games/etqw/base/zpak_korean001.pk4 (12 files)
/usr/local/games/etqw/base/zpak_korean000.pk4 (6 files)
/usr/local/games/etqw/base/zpak_german003.pk4 (5 files)
/usr/local/games/etqw/base/zpak_german002.pk4 (119 files)
/usr/local/games/etqw/base/zpak_german001.pk4 (13 files)
/usr/local/games/etqw/base/zpak_french003.pk4 (14 files)
/usr/local/games/etqw/base/zpak_french002.pk4 (119 files)
/usr/local/games/etqw/base/zpak_french001.pk4 (13 files)
/usr/local/games/etqw/base/zpak_english003.pk4 (7 files)
/usr/local/games/etqw/base/zpak_english002.pk4 (117 files)
/usr/local/games/etqw/base/zpak_english001.pk4 (9 files)
/usr/local/games/etqw/base/zpak_english000.pk4 (1018 files)
/usr/local/games/etqw/base/pak008.pk4 (1496 files)
/usr/local/games/etqw/base/pak007.pk4 (1510 files)
/usr/local/games/etqw/base/pak006.pk4 (3 files)
/usr/local/games/etqw/base/pak005.pk4 (2172 files)
/usr/local/games/etqw/base/pak004.pk4 (72 files)
/usr/local/games/etqw/base/pak003.pk4 (1133 files)
/usr/local/games/etqw/base/pak002.pk4 (1637 files)
/usr/local/games/etqw/base/pak001.pk4 (1067 files)
/usr/local/games/etqw/base/pak000.pk4 (9350 files)
/usr/local/games/etqw/base/game002.pk4 (3 files)
/usr/local/games/etqw/base/game001.pk4 (11 files)
/usr/local/games/etqw/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
Decompressing the global token cache...3566Kb
------------------------------
execing 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
execing 'etqwbinds.cfg'
couldn't exec 'autoexec.cfg'
Vendor: Device:
thread priority set to 1
couldn't exec '/home/gszx1337/.etqwcl/sdnet/gszx1337/base/autoexec.cfg'
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1680x1050
SDL_ListModes:
1680x1050 1600x1024 1440x900 1400x1050 1360x768 1280x1024 1280x960 1152x864 1024x768 960x600 960x540 
840x525 832x624 800x600 800x512 720x450 680x384 640x512 640x480 640x400 576x432 
512x384 416x312 400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
vsync: SDL reports -3002360 - broken?
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_ARB_texture_rectangle
X..GL_EXT_texture_rectangle not found
...using GL_EXT_stencil_wrap
...using GL_EXT_stencil_two_side
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using GL_EXT_depth_bounds_test
...using GL_ARB_point_sprite
...using GL_ARB_occlusion_query
...using GL_EXT_framebuffer_object
...using GL_EXT_packed_depth_stencil
...using GL_EXT_blend_minmax
...using GL_ARB_multisample
...using GL_ARB_shader_objects
...using GL_ARB_vertex_shader
...using GL_ARB_fragment_shader
...using GL_ARB_fragment_program_shadow
...using GL_ARB_shadow
...using GL_ARB_depth_texture
...using GL_EXT_gpu_program_parameters
...using GL_EXT_timer_query
X..GL_GREMEDY_string_marker not found
X..GL_EXT_texture_compression_latc not found
---------- R_ARB2_Init ----------
Cg available.
---------------------------------
thread priority set to 2
thread priority set to 2
using ARB_vertex_buffer_object memory
renderSystem initialized.
--------------------------------------
72 strings read from localization/english/strings/bindings.lang
486 strings read from localization/english/strings/chat.lang
884 strings read from localization/english/strings/code.lang
2187 strings read from localization/english/strings/game.lang
3208 strings read from localization/english/strings/guis.lang
3384 strings read from localization/english/strings/lifestats.lang
3522 strings read from localization/english/strings/loadtips.lang
3861 strings read from localization/english/strings/locations.lang
4386 strings read from localization/english/strings/maps.lang
4453 strings read from localization/english/strings/tasks.lang
/proc/cpuinfo CPU frequency: 1800 MHz
Couldn't open journal files
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.17a
opened Alsa PCM device plug:dmix:0 for playback
device buffer size: 5644 frames (22576 bytes)
allocated a mix buffer of 16384 bytes
--------------------------------------
-------- ALSA Microphone Init --------
ALSA lib ../../../src/pcm/pcm_dmix.c:947:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
snd_pcm_open SND_PCM_STREAM_CAPTURE 'plug:dmix:0' failed: Invalid argument
WARNING: microphone is diabled
--------------------------------------
initializating SDL Joysticks
initialized 0 controller(s)
-------- Initializing Session --------
----------------- BSE Init ------------------
--------- BSE Created Successfully ----------
session initialized
--------------------------------------
found DLL in pak file: /usr/local/games/etqw/base/game002.pk4/gamex86.so
copy gamex86.so to /home/gszx1337/.etqwcl/base/gamex86.so
game using generic code for SIMD processing
enabled Flush-To-Zero mode
--------- Initializing Game ----------
gamename: baseETQW-1
gamedate: May  8 2008
Initializing global UI namespaces
...23 namespaces
...240 properties
Initializing event system
...903 event definitions
Initializing class hierarchy
...163 classes, 397320 bytes for event callbacks
WARNING: Couldn't load sound 'video/intro_1024x512.theora', defaulting
WARNING: idDeclLocal::ParseLocal Failed to Parse decl 'video/intro' in file 'sounds/cinematics.sndshd' line 0
game initialized.
--------------------------------------
------------- Initialized in 14 -------------
--- Common Initialization Complete ---
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 9553
1800 MHz CPU
3024 MB System Memory
detecting video ram (set sys_videoRam on command line to override) ..
found XNVCtrl extension 1.16
256 MB Video Memory
Async thread started
execing /home/gszx1337/.etqwcl/sdnet/gszx1337/base/profile.cfg 
execing 'localization/english/defaultbinds.cfg'
execing /home/gszx1337/.etqwcl/sdnet/gszx1337/base/bindings.cfg 
PunkBuster Client: Attempting to resolve master5.evenbalance.com
PunkBuster Client: Resolved to [66.36.231.175] (14)
PunkBuster Client: PunkBuster Client (v2.114 | A0) Enabled
Opening IP socket: localhost:-1
PunkBuster Client: Game Version [ETQW 1.5.12663.12663  linux-x86 May  9 2008 13:50:52]
PunkBuster Client: Not Connected to a Server
Opening IP socket: localhost:27733
Server spawned on port 27733.
client 0 connected.
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
--------- Map Initialization ---------
Map: maps/area22.entities
----------- Game Map Init ------------
found DLL in pak file: /usr/local/games/etqw/base/game002.pk4/compiledscriptx86.so
copy compiledscriptx86.so to /home/gszx1337/.etqwcl/base/compiledscriptx86.so
Loaded '/home/gszx1337/.etqwcl/base/compiledscriptx86.so'
  266 classes
  84 global functions
----------- Loading Map AAS ------------
[Load AAS Binary]
loading 'maps/area22.aas_playerb'
[Load AAS Binary]
loading 'maps/area22.aas_vehicleb'
collision data:
   172 models
315499 vertices (3697 kB)
435308 edges (8502 kB)
170480 polygons (10655 kB)
586942 polygon edges (1146 kB)
  7068 brushes (220 kB)
 42932 brush planes (670 kB)
 89240 nodes (2440 kB)
367113 polygon refs (2868 kB)
  8019 brush refs (62 kB)
118381 internal edges
   912 sharp edges
     0 contained polygons removed
     0 polygons merged
 30657 kB total memory used
803 msec to load collision data.
    9 KB passage memory used to build PVS
    6 msec to calculate PVS
   72 areas
  176 portals
    8 areas visible on average
  864 bytes PVS data
Spawning entities
Loaded 'stuff/area22/stuff.clustb' in 1.2 seconds
...1064 entities spawned, 0 inhibited

----------- Loading Map Bot Actions ------------
--------------------------------------
thread priority set to 2
----- idRenderModelManagerLocal::EndLevelLoad -----
    0 purged from previous
 1152 kept from previous
  423 new loaded
all models loaded in   0.0 seconds
---------------------------------------------------
----- idImageManager::EndLevelLoad -----
    0 purged from previous
   76 kept from previous
 1291 new loaded
    0 megaTextures purged from previous
    1 megaTextures kept from previous
all images loaded in   1.8 seconds
----------------------------------------
----- idSoundCache::EndLevelLoad -----
44183k referenced
    0k purged
----------------------------------------
-----------------------------------
 24752 msec to load maps/area22.entities
interactionTable size: 1119580 bytes
0 interaction take 0 bytes
Loaded map in    25 seconds
SpawnPlayer: 0
gszx1337 entered the game.
client 1 connected.
SpawnPlayer: 1
Streifel entered the game.
Streifel joined the Strogg
gszx1337 joined the Strogg
Segmentation fault

```

glxinfo:
```
gszx1337@GMan:~$ glxinfo
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
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7900 GT/GTO/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 173.14.12
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
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

120 GLX Visuals
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
0x33 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x46 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
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
0x5a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x61 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x71 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
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
0x81 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x82 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x83 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x84 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x85 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x86 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x87 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x89 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8b 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x8c 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x8d 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8e 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x90 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x91 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x92 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x93 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x94 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x95 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x96 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x97 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x98 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon

179 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x99  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x9a  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x9b  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x9c  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x9d  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x9e  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x9f  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xa0  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xa1  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xa2  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xa3  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xa4  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xa5  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xa6  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xa7  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xa8  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xa9  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0xaa  0 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0xab  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0xac  0 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0xad  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0xae  0 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0xaf  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0xb0  0 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0xb1  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb2  0 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb3  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb4  0 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb5  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb6  0 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb7  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb8  0 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb9  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xba  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xbb  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xbc  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xbd  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xbe  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xbf  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xc0  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xc1  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xc2  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xc3  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xc4  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xc5  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xc6  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xc7  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xc8  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xc9  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xca  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xcb  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xcc  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xcd  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xce  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xcf  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xd0  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xd1  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xd2  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xd3  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xd4  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xd5  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xd6  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xd7  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xd8  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xd9  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0xda  0 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0xdb  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0xdc  0 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0xdd  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0xde  0 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0xdf  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0xe0  0 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0xe1  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0xe2  0 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0xe3  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0xe4  0 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0xe5  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0xe6  0 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0xe7  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0xe8  0 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0xe9  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0xea  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xeb  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0xec  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xed  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xee  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xef  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xf0  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xf1  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0xf2  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0xf3  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0xf4  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0xf5  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xf6  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xf7  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xf8  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xf9  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xfa  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xfb  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xfc  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xfd  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xfe  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xff  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x100  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x101  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x102  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x103  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x104  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x105  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x106  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x107  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x108  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x109  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x10a  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x10b  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x10c  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x10d  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x10e  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x10f  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x110  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x111  0 sg  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x112  0 sg  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x113  0 sg  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x114  0 sg  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x115  0 sg  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x116  0 sg  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x117  0 sg  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x118  0 sg  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x119  0 sg  0  0  0 r  .  .  0  0  0  0  4 16  0 16 16 16 16  0 0 None
0x11a  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  0 16 16 16 16  0 0 None
0x11b  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  8 16 16 16 16  0 0 None
0x11c  0 sg  0 32  0 r  .  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0x11d  0 sg  0 32  0    .  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0x11e  0 sg  0 32  0 r  y  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0x11f  0 sg  0 32  0    y  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0x120  0 sg  0 32  0 r  .  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0x121  0 sg  0 32  0    .  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0x122  0 sg  0 32  0 r  y  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0x123  0 sg  0 32  0    y  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0x124  0 sg  0 64  0 r  .  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0x125  0 sg  0 64  0    .  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0x126  0 sg  0 64  0 r  y  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0x127  0 sg  0 64  0    y  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0x128  0 sg  0 128  0 r  .  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0x129  0 sg  0 128  0    .  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0x12a  0 sg  0 128  0 r  y  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0x12b  0 sg  0 128  0    y  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0x12c  0 sg  0 32  0 r  .  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0x12d  0 sg  0 32  0    .  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0x12e  0 sg  0 32  0 r  y  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0x12f  0 sg  0 32  0    y  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0x130  0 sg  0 32  0 r  .  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0x131  0 sg  0 32  0    .  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0x132  0 sg  0 32  0 r  y  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0x133  0 sg  0 32  0    y  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0x134  0 sg  0 32  0 r  .  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0x135  0 sg  0 32  0    .  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0x136  0 sg  0 32  0 r  y  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0x137  0 sg  0 32  0    y  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0x138  0 sg  0 32  0 r  .  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0x139  0 sg  0 32  0    .  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0x13a  0 sg  0 32  0 r  y  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0x13b  0 sg  0 32  0    y  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0x13c  0 sg  0 64  0 r  .  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0x13d  0 sg  0 64  0    .  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0x13e  0 sg  0 64  0 r  y  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0x13f  0 sg  0 64  0    y  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0x140  0 sg  0 64  0 r  .  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0x141  0 sg  0 64  0    .  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0x142  0 sg  0 64  0 r  y  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0x143  0 sg  0 64  0    y  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0x144  0 sg  0 128  0 r  .  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0x145  0 sg  0 128  0    .  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0x146  0 sg  0 128  0 r  y  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0x147  0 sg  0 128  0    y  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0x148  0 sg  0 128  0 r  .  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x149  0 sg  0 128  0    .  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x14a  0 sg  0 128  0 r  y  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x14b  0 sg  0 128  0    y  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None

```

---

### Post by GSZX1337 on 2009-03-28
bumpzorz

---

### Post by Naiki Muliaina on 2009-03-28
Fraid i dont know much about these things, but could you post up whats in your PC? Graphics card etc. Pretty sure there was something about ATI's crashing with Quake in Linux, but that was a while ago.

---

### Post by GSZX1337 on 2009-03-29
GeForce 7900 GT
AMD Opteron 165 (it was OCed, but I clocked it back to stock)
3 GB RAM
Gigabyte GA-K8N-Pro-SLI motherboard
700 Watt OCZ Power Supply

---

### Post by change_mode on 2009-03-29
The error message suggests that it's somehow related to the memory.

---

### Post by OliW on 2009-09-23
I'm getting similar phantom crashes. Some maps crash really fast, others take a few minutes. All I know is it's really annoying.

Did you ever manage to fix your problem?

I'm running 64bit karmic on an i7 with a 8800gts (185 nvidia driver).

---

### Post by Technophobia on 2009-09-24
I have had something similar happen to be in the past. I just disabled Compiz and everything seemed ok after that. I'm not sure if this helps at all.

---

### Post by MichiganMan on 2009-11-11
> **OliW said:**
> I'm getting similar phantom crashes. Some maps crash really fast, others take a few minutes. All I know is it's really annoying.

Did you ever manage to fix your problem?

I'm running 64bit karmic on an i7 with a 8800gts (185 nvidia driver).

I've had two incidences of difficult to diagnose crashes with Quake Wars.  The first was a memory simm going bad.  The defect only manifested itself in Quake Wars, guess I didn't push the RAM enough anywhere else.  The symptoms were very similar to what you're experiencing OliW.  I finally identified it by running memtest from a LiveCD.  You can also run memtest from Grub.

Second instance happed recently after I formatted for Karmic and couldn't get the microphone working.  Trying would produce a crash.  (GSZX1337, I notice your terminal output shows possible problems with your microphone settings.  Don't know if it matters if you even *have* a mic or not)  I found the solution in [this]("http://community.enemyterritory.com/forums/showthread.php?t=30686&highlight=linux+microphone") thread.

---


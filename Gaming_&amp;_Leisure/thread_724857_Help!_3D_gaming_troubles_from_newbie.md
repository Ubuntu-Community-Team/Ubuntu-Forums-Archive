---
title: "Help! 3D gaming troubles from newbie"
date: 2008-03-15
forum: Gaming &amp; Leisure
---

### Post by Screwtape on 2008-03-15
Hi, All-
I have just installed the Quake 4 demo on my brand new Toshiba satellite and when I try to run the program, it changes my resolution to 640x480 and that's it. No game, no nothing. I have an Intel GM965/960 graphics card, 2 gigs of memory, and a fairly fast centrino dual core processor so I'm hoping tech specs aren't the problem.

I've used GLEW to download GL extensions, but it's been suggested to me that not having the proper extensions might still be the problem. I can run Darwinia just fine.

Any takers?
Thanks in advance.

---

### Post by Screwtape on 2008-03-15
anybody know the particular GL extensions required to run this game? Or if there's another problem I'm not aware of? Or is there further information I should post about my computer?

---

### Post by Screwtape on 2008-03-15
some more information for the potentially helpful: this is the script I get when I try to run Quake 4:
> 
sam@sam-laptop:~/quake4$ sh quake4
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface wlan0 - 192.168.1.109/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/sam/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /home/sam/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /home/sam/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
Loaded pk4 /home/sam/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /home/sam/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /home/sam/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /home/sam/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /home/sam/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /home/sam/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /home/sam/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /home/sam/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /home/sam/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /home/sam/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /home/sam/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /home/sam/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /home/sam/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /home/sam/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /home/sam/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Addon pk4 /home/sam/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/sam/.quake4/q4base
/home/sam/quake4/q4base
/home/sam/quake4/q4base/zpak_english_04.pk4 (3 files)
/home/sam/quake4/q4base/zpak_english_03.pk4 (4 files)
/home/sam/quake4/q4base/zpak_english_02.pk4 (21 files)
/home/sam/quake4/q4base/zpak_english_01.pk4 (1 files)
/home/sam/quake4/q4base/pak022.pk4 (14 files)
/home/sam/quake4/q4base/pak021.pk4 (89 files)
/home/sam/quake4/q4base/pak020.pk4 (11 files)
/home/sam/quake4/q4base/pak019.pk4 (1206 files)
/home/sam/quake4/q4base/pak018.pk4 (3 files)
/home/sam/quake4/q4base/pak017.pk4 (3 files)
/home/sam/quake4/q4base/pak016.pk4 (193 files)
/home/sam/quake4/q4base/pak015.pk4 (34 files)
/home/sam/quake4/q4base/pak014.pk4 (552 files)
/home/sam/quake4/q4base/pak013.pk4 (239 files)
/home/sam/quake4/q4base/game200.pk4 (9 files)
/home/sam/quake4/q4base/game100.pk4 (2 files)
/home/sam/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
/home/sam/quake4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 55 loaded
42ms to load 243k of material
1ms to load 4k of skin
63ms to load 378k of sound
0ms to load 0k of materialType
310ms to load 2889k of lipSync
0ms to load 0k of playback
8ms to load 25k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' without VO
.... found additional language 'italian' without VO
.... found additional language 'spanish' without VO
696 strings read from strings/english_code.lang
1794 strings read from strings/english_guis.lang
1797 strings read from strings/english_mappack.lang
2273 strings read from strings/english_maps.lang
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
1280x800 1280x768 1024x768 800x600 640x480 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.14a
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 22576 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
...using GL_ARB_texture_non_power_of_two
...using GL_NV_blend_square
...using GL_ARB_texture_compression
X..GL_EXT_texture_compression_s3tc not found
Fatal Error: Texture compression unavailable
Shutting down SDL subsystem
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Texture compression unavailable
and this is my GLXinfo script:> 
sam@sam-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays

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
0x64 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
sam@sam-laptop:~$ 

---

### Post by reston5 on 2008-03-15
just letting you know if you do get it up and running i would highly recommend an addon graphics card because your onboard will run the game very choppy and slow I was lucky to get 10fps on mine when i ran the game at 800*600:)

---


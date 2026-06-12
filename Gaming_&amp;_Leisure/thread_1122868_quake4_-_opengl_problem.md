---
title: "quake4 - opengl problem"
date: 2009-04-11
forum: Gaming &amp; Leisure
---

### Post by queBurro on 2009-04-11
heh 

I'm trying to get quake4 running on my laptop under ubuntu, but I'm hitting an error with opengl, glxgears works, the game works on my laptop under vista but I can't get it to work under ubuntu, I'm using the integrated graphics...
 
see below for the error report on running quake and below that for my glxinfo, 

any help would be appreciated :)

@queBurro:~$ quake
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface wlan0 - 192.168.1.102/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /usr/local/games/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
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
Loaded pk4 /usr/local/games/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /usr/local/games/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Addon pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/tb/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_english_04.pk4 (3 files)
/usr/local/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/usr/local/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/usr/local/games/quake4/q4base/zpak_english.pk4 (3457 files)
/usr/local/games/quake4/q4base/pak022.pk4 (14 files)
/usr/local/games/quake4/q4base/pak021.pk4 (89 files)
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
/usr/local/games/quake4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 64 loaded
307ms to load 1125k of material
106ms to load 43k of skin
265ms to load 723k of sound
4ms to load 1k of materialType
467ms to load 2889k of lipSync
87ms to load 105k of playback
973ms to load 1690k of effect
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
5756 strings read from strings/english_lips.lang
5759 strings read from strings/english_mappack.lang
6235 strings read from strings/english_maps.lang
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
1280x800 SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.17a
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5461 frames ( 21844 bytes )
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



-------------------


@queBurro:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2
OpenGL shading language version string: 1.10
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, 
    GL_ATI_separate_stencil, GL_IBM_multimode_draw_arrays, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_program_debug, 
    GL_MESA_resize_buffers, GL_MESA_texture_array, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_fragment_program, 
    GL_NV_light_max_exponent, GL_NV_point_sprite, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

2 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x3a 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

32 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x3b  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x3c  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x3d  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x3e  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x3f  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x40  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x41  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x42  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x43  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x44  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x45  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x46  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x47  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x49  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x4a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x4b  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x4c  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x4d  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x4e  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x4f  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x50  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x51  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x52  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x53  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x54  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x55  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x56  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x57  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x59  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5a  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

@queBurro:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by rizzeh on 2009-04-11
Fatal Error: Texture compression unavailable
Shutting down SDL subsystem

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)


I dont think you can play Quake4 with Intel graphics.

---

### Post by hikaricore on 2009-04-11
You might be able to on Windows with D3D, but Intel chipsets are notorious for their lacking OpenGL support which is the only way to run it on Linux.

---

### Post by queBurro on 2009-04-14
> **hikaricore said:**
> You might be able to on Windows with D3D, but Intel chipsets are notorious for their lacking OpenGL support which is the only way to run it on Linux.

I thought maybe the opengl version 1.2? I've got didn't support the textures q4 was trying to use and that the windows one did because it was a later version 1.4? 

thanks for the replies :)

---

### Post by queBurro on 2009-04-23
ok,
just tried this on 9.04/jaunty and it's working, really slow but that's the next step :)

---

### Post by wolfyking2 on 2009-04-24
Try turning all the graphics settings to the lowest, and set the fullscreen off and screen resolution to 800x600.  Trust me, it works

---


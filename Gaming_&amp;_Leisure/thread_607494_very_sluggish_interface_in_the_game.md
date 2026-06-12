---
title: "very sluggish interface in the game"
date: 2007-11-09
forum: Gaming &amp; Leisure
---

### Post by bharadwaj on 2007-11-09
I installed sauerbraten, Alien Arena, Enemy territory. 
Every thing runs fine the all the games start perfectly but don't know what went wrong is that my graphics driver problem that I am unable to play games like I used to in windows? I mean the interface of the game is very sluggish when ever I try to aim anything it doesn't go it's like doing job on a hung system.
My motherboard is i845G 

think this piece of info would help you a bit. This comes when ever i try to close the sauerbraten:

"bharadwaj@runfree:~/Backups/games/sauerbraten$ ./sauerbraten_unix 
init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2 (Tungsten Graphics, Inc)
Driver: 1.3 Mesa 7.0.1
WARNING: No vertex_buffer_object extension! (geometry heavy maps will be SLOW)
WARNING: Using floating point vertexes. (use "/floatvtx 0" to disable)
WARNING: No shader support! Using fixed function fallback. (no fancy visuals for you)
WARNING: No occlusion query support! (large maps may be SLOW)
WARNING: No framebuffer object support. (reflective water may be slow)
WARNING: Non-power-of-two textures not supported!
init: console
init: world
init: sound
init: cfg
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.2 seconds)
Mining Station by metlslime
game mode is ffa/default
quad damage will spawn in 10 seconds!
+10 health will spawn in 10 seconds!
read map packages/base/mpsp6a.ogz (1.5 seconds)"


When I close Enemy Territory I get

"anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/home/bharadwaj/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaf448f40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader levelshots/supply
^3WARNING: Couldn't find image for shader levelshots/stalingrad
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
78.47.212.218:27960 resolved to 78.47.212.218:27960
********************
ERROR: PunkBuster must be Enabled before joining this server. PunkBuster can be Enabled/Disabled on the Play Online (Server Browser) screen. Visit [www.evenbalance.com](www.evenbalance.com) for PunkBuster support.

********************
Sys_LoadDll(/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/home/bharadwaj/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaf448f40  
Sys_LoadDll(ui) succeeded!
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 7.0.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_packed_pixels GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays 
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_group GLX_EXT_texture_from_pixmap 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/home/bharadwaj/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaf448f40  
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
78.47.212.218:27960 resolved to 78.47.212.218:27960
********************
ERROR: PunkBuster must be Enabled before joining this server. PunkBuster can be Enabled/Disabled on the Play Online (Server Browser) screen. Visit [www.evenbalance.com](www.evenbalance.com) for PunkBuster support.

********************
Sys_LoadDll(/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/home/bharadwaj/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaf448f40  
Sys_LoadDll(ui) succeeded!
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 7.0.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_packed_pixels GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays 
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_group GLX_EXT_texture_from_pixmap 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/bharadwaj/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/home/bharadwaj/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaf448f40  
Sys_LoadDll(ui) succeeded!
^5PunkBuster Client: PunkBuster Client (v1.152 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60 linux-i386 Mar 10 2005]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
78.47.212.218:27960 resolved to 78.47.212.218:27960
^5PunkBuster Client: File /home/bharadwaj/.etwolf/etmain/etkey Deleted due to Empty CDKey
^5PunkBuster Client: Cdkey Registration Request sent to GuidAuth Master at 192.246.40.62:27960 (2010939450)
^5PunkBuster Client: Connected to Server 78.47.212.218:27960
^5PunkBuster Client: File /home/bharadwaj/.etwolf/etmain/etkey Deleted due to Empty CDKey
^5PunkBuster Client: Cdkey/GUID Registration successful (/home/bharadwaj/.etwolf/etmain/etkey)
----- FS_Startup -----
Current search path:
/home/bharadwaj/enemy-territory/etmain/pak2.pk3 (22 files)
    on the pure list
/home/bharadwaj/enemy-territory/etmain/pak1.pk3 (10 files)
    on the pure list
/home/bharadwaj/enemy-territory/etmain/pak0.pk3 (3725 files)
    on the pure list
/home/bharadwaj/enemy-territory/etmain/mp_bin.pk3 (6 files)
    on the pure list
/home/bharadwaj/.etwolf/etpub
/home/bharadwaj/enemy-territory/etpub
/home/bharadwaj/.etwolf/etmain
/home/bharadwaj/enemy-territory/etmain

----------------------
7526 files in pk3 files
Need paks: etpub/z&z_killspreesounds.pk3
etpub/z&z_everything_in_1_download_psl.pk3
etpub/etpub_client-20070801.pk3
etmain/StarGate_1945.pk3

Need paks: @etpub/z&z_killspreesounds.pk3@etpub/z&z_killspreesounds.pk3@etpub/z&z_everything_in_1_download_psl.pk3@etpub/z&z_everything_in_1_download_psl.pk3@etpub/etpub_client-20070801.pk3@etpub/etpub_client-20070801.pk3@etmain/StarGate_1945.pk3@etmain/StarGate_1945.pk3
Need paks: @etpub/z&z_killspreesounds.pk3@etpub/z&z_killspreesounds.pk3@etpub/z&z_everything_in_1_download_psl.pk3@etpub/z&z_everything_in_1_download_psl.pk3@etpub/etpub_client-20070801.pk3@etpub/etpub_client-20070801.pk3@etmain/StarGate_1945.pk3@etmain/StarGate_1945.pk3
execing profiles/bharadwaj/etconfig.cfg
Client download subsystem initialized
^5PunkBuster Client: Master Query Sent to (ID2.EVENBALANCE.COM) 192.246.40.80
^5PunkBuster Client: Received Master Security Information
----- FS_Startup -----
Current search path:
/home/bharadwaj/.etwolf/etpub/z&z_killspreesounds.pk3 (29 files)
    on the pure list
/home/bharadwaj/.etwolf/etpub/z&z_everything_in_1_download_psl.pk3 (179 files)
    on the pure list
/home/bharadwaj/.etwolf/etpub/etpub_client-20070801.pk3 (71 files)
    on the pure list
/home/bharadwaj/.etwolf/etmain/StarGate_1945.pk3 (217 files)
    on the pure list
/home/bharadwaj/enemy-territory/etmain/pak2.pk3 (22 files)
    on the pure list
/home/bharadwaj/enemy-territory/etmain/pak1.pk3 (10 files)
    on the pure list
/home/bharadwaj/enemy-territory/etmain/pak0.pk3 (3725 files)
    on the pure list
/home/bharadwaj/enemy-territory/etmain/mp_bin.pk3 (6 files)
    on the pure list
/home/bharadwaj/.etwolf/etpub
/home/bharadwaj/enemy-territory/etpub
/home/bharadwaj/.etwolf/etmain
/home/bharadwaj/enemy-territory/etmain

----------------------
11785 files in pk3 files
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 7.0.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_packed_pixels GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays 
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_group GLX_EXT_texture_from_pixmap 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
copy /home/bharadwaj/enemy-territory/etmain/ui.mp.i386.so to /home/bharadwaj/.etwolf/etpub/ui.mp.i386.so
Sys_LoadDll(/home/bharadwaj/.etwolf/etpub/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae3709e4  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/flameguards_logo
^3Warning: file ui/wm_quickmessageAlt.menu, line 51: redefinition of ORIGIN_QUICKMESSAGE
^3Warning: file ui/wm_quickmessageAlt.menu, line 53: redefinition of QM_MENU_GRADIENT_START_OFFSET
^3Warning: file ui/wm_quickmessageAlt.menu, line 55: redefinition of QM_MENU_START
^3Warning: file ui/wm_quickmessageAlt.menu, line 94: redefinition of QM_MENU_END
^1Error: file ui/ingame_vote.menu, line 98: can't evaluate CV_SVF_PUTSPEC, not defined
^1ERROR: ui/ingame_vote.menu, line 98: couldn't parse menu item keyword voteFlag
^1ERROR: ui/ingame_vote.menu, line 98: couldn't parse menu keyword itemDef
^1ERROR: ui/ingame_vote_misc.menu, line 66: expected integer but found CV_SVF_SHUFFLENORESTART

^1ERROR: ui/ingame_vote_misc.menu, line 66: couldn't parse menu item keyword voteFlag
^1ERROR: ui/ingame_vote_misc.menu, line 66: couldn't parse menu keyword itemDef
^1ERROR: ui/ingame_vote_players.menu, line 77: expected integer but found CV_SVF_PUTSPEC

^1ERROR: ui/ingame_vote_players.menu, line 77: couldn't parse menu item keyword voteFlag
^1ERROR: ui/ingame_vote_players.menu, line 77: couldn't parse menu keyword itemDef
^1ERROR: ui/fg_ingame_servers.menu, line 20: expected integer but found WINDOW_STYLE_FILLED

^1ERROR: ui/fg_ingame_servers.menu, line 20: couldn't parse menu keyword style
copy /home/bharadwaj/enemy-territory/etmain/cgame.mp.i386.so to /home/bharadwaj/.etwolf/etpub/cgame.mp.i386.so
Sys_LoadDll(/home/bharadwaj/.etwolf/etpub/cgame.mp.i386.so)... ok
Sys_LoadDll(cgame) found **vmMain** at  0xaa9e0ab8  
Sys_LoadDll(cgame) succeeded!
LOADING... collision map
LOADING... sounds
Com_sprintf: overflow of 64 bytes buffer
Com_sprintf: overflow of 64 bytes buffer
voice chat memory size = 0

.........................
Initializing Sound Scripts
...loading 'sound/scripts/vo_allies.sounds'
...loading 'sound/scripts/vo_axis.sounds'
...loading 'sound/scripts/oasis.sounds'
done.
LOADING... graphics
LOADING... maps/oasis.bsp
stitched 0 LoD cracks
...loaded 19509 faces, 178 meshes, 1005 trisurfs, 0 flares 0 foliage
LOADING... entities
LOADING... game media
LOADING...  - textures
LOADING...  - models
LOADING...  - weapons
^3WARNING: R_FindImageFile could not find 'models/multiplayer/Wrench/wrench.tga' in shader 'models/multiplayer/pliers/pliers'
^3Shader models/multiplayer/pliers/pliers has a stage with no image
LOADING...  - items
LOADING...  - inline models
LOADING...  - server models
LOADING...  - particles
LOADING...  - classes
LOADING...  - game media done
LOADING... flamechunks
LOADING... clients
^3WARNING: Couldn't find image for shader watermark/
profiles/bharadwaj/-hud.dat
^2No HUD specified, default HUD loaded
^3client: detected etpub server 0.8.1 (2049)
RestoreProfile: no backup profiles/bharadwaj/etconfig.cfg.etpub found
.CL_InitCGame: 39.73 seconds
Com_TouchMemory: 1 msec
unknown cmd userinfo
unknown cmd userinfo
^d|^7Amalia^d|^7 disconnected
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
^d|^7Maxima^d|^7^7 was owned ^7by ^d|^7Potter^d|^7^7's MP40.
Axis reclaim the Old City!
^7Binoc Masters: ^d|^7Potter^d|^7: 2, ^d|^7Perkamentus^d|^7: 2, ^d|^7Maxima^d|^7: 2
^7Active Killing Sprees: ^d|^7Potter^d|^7: 5, ^d|^7Clinton^d|^7: 1, ^d|^7Maxima^d|^7: 1
^8Longest Killing Spree: ^65^8 kills by ^7^d|^7Potter^d|^8.
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
^d|^7Maxima^d|^7^7 was owned ^7by ^d|^7Potter^d|^7^7's Thompson.
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
^d|^7MC^d|^7^7 was owned ^7by ^d|^7Maxima^d|^7^7's Luger.
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
^d|^7Clinton^d|^7^7 was owned ^7by ^d|^7Snicker^d|^7^7's Thompson.
^d|^7Perkamentus^d|^7^7 was owned ^7by ^d|^7Snicker^d|^7^7's Thompson.
^3server: detected etpubclient 20070801
^5PunkBuster Client: WARNING: ^7PB Kicks for Name Spamming and Name Stealing and All PB Restrictions on this Server
Axis reclaim the Old City!
^5PunkBuster Client: PB Server assigned guid = c0f1632d93e5837e3b573023085416fc
^5PunkBuster Client: Receiving from PB Server (l v1.285 | A1382 C1.738)
Allies capture the Old City!
^5PunkBuster Client: 0 Current Cvar Violations
^d[^7sukkel^d]^7^7 was owned ^7by ^d|^7Perkamentus^d|^7^7's MP40.
Allies capture the Old City!
^d|^7Maxima^d|^7^7 was owned ^7by ^d|^7Perkamentus^d|^7^7's MP40.
Axis reclaim the Old City!
Allies capture the Old City!
^d|^7Perkamentus^d|^7^7 was owned ^7by ^d|^7Snicker^d|^7^7's deagle.
Axis reclaim the Old City!
^d[^7sukkel^d]^7^7 was owned ^7by ^d|^7Perkamentus^d|^7^7's MP40.
Allies capture the Old City!
^d|^7Potter^d|^7^7 was sliced ^7by ^d|^7Maxima^d|^7^7's combat knife.
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
^d|^7Clinton^d|^7^7 was owned ^7by ^d|^7MC^d|^7^7's Thompson.
Allies capture the Old City!
Axis reclaim the Old City!
^d|^7MC^d|^7^7 was owned ^7by ^d|^7Maxima^d|^7^7's Luger.
Allies capture the Old City!
Axis reclaim the Old City!
^d|^7Potter^d|^7^7 was owned ^7by ^d|^7Potter^d|^7^7's deagle.
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
^d|^7Perkamentus^d|^7^7 was mown down by ^d[^7sukkel^d]^7^7's Mobile MG42.
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
^d|^7Clinton^d|^7^7 was owned ^7by ^d|^7Maxima^d|^7^7's Thompson.
^7Binoc Masters: ^d|^7Clinton^d|^7: 3, ^d|^7Potter^d|^7: 3, ^d|^7Potter^d|^7: 2
^7Active Killing Sprees: ^d|^7Potter^d|^7: 8, ^d|^7Snicker^d|^7: 5, ^d|^7Maxima^d|^7: 2
^8Longest Killing Spree: ^68^8 kills by ^7^d|^7Potter^d|^8.
Axis reclaim the Old City!
^d|^7Potter^d|^7^7 was owned ^7by ^d|^7Potter^d|^7^7's Thompson.
Allies capture the Old City!
^d|^7Perkamentus^d|^7^7 was owned ^7by ^d|^7Maxima^d|^7^7's Thompson.
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
^d|^7Maxima^d|^7^7 was mown down by ^d[^7sukkel^d]^7^7's Mobile MG42.
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
Axis reclaim the Old City!
Allies capture the Old City!
^d|^7MC^d|^7^7 was owned ^7by ^d|^7Perkamentus^d|^7^7's MP40.
^d|^7Perkamentus^d|^7^7 was owned ^7by ^d|^7Maxima^d|^7^7's Thompson.
EventHandling: 0
----- CL_Shutdown -----
copy /home/bharadwaj/enemy-territory/etmain/ui.mp.i386.so to /home/bharadwaj/.etwolf/etpub/ui.mp.i386.so
Sys_LoadDll(/home/bharadwaj/.etwolf/etpub/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaeecaf40  
Sys_LoadDll(ui) succeeded!
^3Warning: file ui/wm_quickmessageAlt.menu, line 51: redefinition of ORIGIN_QUICKMESSAGE
^3Warning: file ui/wm_quickmessageAlt.menu, line 53: redefinition of QM_MENU_GRADIENT_START_OFFSET
^3Warning: file ui/wm_quickmessageAlt.menu, line 55: redefinition of QM_MENU_START
^3Warning: file ui/wm_quickmessageAlt.menu, line 94: redefinition of QM_MENU_END
^1Error: file ui/ingame_vote.menu, line 98: can't evaluate CV_SVF_PUTSPEC, not defined
^1ERROR: ui/ingame_vote.menu, line 98: couldn't parse menu item keyword voteFlag
^1ERROR: ui/ingame_vote.menu, line 98: couldn't parse menu keyword itemDef
^1ERROR: ui/ingame_vote_misc.menu, line 66: expected integer but found CV_SVF_SHUFFLENORESTART

^1ERROR: ui/ingame_vote_misc.menu, line 66: couldn't parse menu item keyword voteFlag
^1ERROR: ui/ingame_vote_misc.menu, line 66: couldn't parse menu keyword itemDef
^1ERROR: ui/ingame_vote_players.menu, line 77: expected integer but found CV_SVF_PUTSPEC

^1ERROR: ui/ingame_vote_players.menu, line 77: couldn't parse menu item keyword voteFlag
^1ERROR: ui/ingame_vote_players.menu, line 77: couldn't parse menu keyword itemDef
^1ERROR: ui/fg_ingame_servers.menu, line 20: expected integer but found WINDOW_STYLE_FILLED

^1ERROR: ui/fg_ingame_servers.menu, line 20: couldn't parse menu keyword style
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console"


Please need some help

---

### Post by mbradlcu on 2007-11-11
sorry I may have missed it but what vid-card are you using?,,

---

### Post by bharadwaj on 2007-11-13
"GL_RENDERER: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2" as found by the game and thats true ;)

---

### Post by Mblackwell on 2007-11-13
Try lowering your settings. And disable desktop effects.

---

### Post by mbradlcu on 2007-11-13
hopefully I'm wrong about this but my laptop with the same vid chipset is pretty slow compared to the MS counterpart ; (
I've run open arena and it was not to bad.
what numbers do you get running 'glxgears'?

---


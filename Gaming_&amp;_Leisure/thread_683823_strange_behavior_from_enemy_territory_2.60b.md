---
title: "strange behavior from enemy territory 2.60b"
date: 2008-01-31
forum: Gaming &amp; Leisure
---

### Post by harmonizedmc9 on 2008-01-31
so i've been playing et for at least a year now with minimal problems.. there must have been an update in the last day or two that did something to it though... the deployment screen and all HUD graphics have little horizontal rainbow blips flashing all over, and the framerate is reduced by more than half... other than an update i didn't modify my system at all, and i already tried reinstalling the game and the same problems persist... and unfortunately this isn't the type of thing that left any error messages, sorry...
one thing it could be is the other day i accidentally let my hard drive get full while streaming a movie, perhaps this ended up corrupting some random files... but i'm pretty sure i played it with no problem between then and the update... just included this information to be on the safe side...
so anyway if there is anyone out there who has ANY idea of what the problem is and how to solve it, i would be incredibly grateful.
later and thanks for checking this out!

in case it contains a clue, here is the bash script from starting the game and immediately exiting... after that i'll add the portion from connecting to a server (if i try both at once i lose the first part of the startup script)

ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/rich/.etwolf/etmain/z_pak_directplay_01.pk3 (3 files)
/home/rich/.etwolf/etmain/z_fieldopsincompl.pk3 (16 files)
/home/rich/.etwolf/etmain/xposed.pk3 (75 files)
/home/rich/.etwolf/etmain/xf5u_fix2.pk3 (4 files)
/home/rich/.etwolf/etmain/xf5u_3_0_fix2.pk3 (3 files)
/home/rich/.etwolf/etmain/xf5u_3_0_fix.pk3 (3 files)
/home/rich/.etwolf/etmain/xf5u_3_0.pk3 (339 files)
/home/rich/.etwolf/etmain/xf5u.pk3 (315 files)
/home/rich/.etwolf/etmain/WTF_AXIS-INFANTARY.pk3 (170 files)
/home/rich/.etwolf/etmain/whoreage.pk3 (44 files)
/home/rich/.etwolf/etmain/weed6.pk3 (1 files)
/home/rich/.etwolf/etmain/Warbell.pk3 (242 files)
/home/rich/.etwolf/etmain/vio_grail.pk3 (142 files)
/home/rich/.etwolf/etmain/vesuvius_b1.pk3 (140 files)
/home/rich/.etwolf/etmain/vesuvius.pk3 (168 files)
/home/rich/.etwolf/etmain/venice_ne4.pk3 (325 files)
/home/rich/.etwolf/etmain/venice.pk3 (330 files)
/home/rich/.etwolf/etmain/venice.2d111d78.pk3 (330 files)
/home/rich/.etwolf/etmain/vengeance_te_final.pk3 (108 files)
/home/rich/.etwolf/etmain/vengeance_final.pk3 (103 files)
/home/rich/.etwolf/etmain/v2_factory.pk3 (151 files)
/home/rich/.etwolf/etmain/v2base.pk3 (22 files)
/home/rich/.etwolf/etmain/v1_drakir.pk3 (436 files)
/home/rich/.etwolf/etmain/v1rocket_b2.pk3 (108 files)
/home/rich/.etwolf/etmain/UJE_flat_sniper.pk3 (111 files)
/home/rich/.etwolf/etmain/UJE_bridge_sniper.pk3 (62 files)
/home/rich/.etwolf/etmain/UJE_00.pk3 (208 files)
/home/rich/.etwolf/etmain/tiger_110.pk3 (295 files)
/home/rich/.etwolf/etmain/the_moskeeB1.pk3 (306 files)
/home/rich/.etwolf/etmain/temple_sniper2.pk3 (23 files)
/home/rich/.etwolf/etmain/temple_final.pk3 (57 files)
/home/rich/.etwolf/etmain/tc_venice_rc2.pk3 (324 files)
/home/rich/.etwolf/etmain/tc_base.pk3 (63 files)
/home/rich/.etwolf/etmain/tankbuster_160.pk3 (102 files)
/home/rich/.etwolf/etmain/sw_oasis_b3.pk3 (45 files)
/home/rich/.etwolf/etmain/sw_cathedral_b7.pk3 (82 files)
/home/rich/.etwolf/etmain/supplydepot3.pk3 (51 files)
/home/rich/.etwolf/etmain/supplydepot2.pk3 (46 files)
/home/rich/.etwolf/etmain/supply.pk3 (44 files)
/home/rich/.etwolf/etmain/SuperGoldrush_Final.pk3 (170 files)
/home/rich/.etwolf/etmain/subway.pk3 (174 files)
/home/rich/.etwolf/etmain/starbase_beta.pk3 (223 files)
/home/rich/.etwolf/etmain/standards23.pk3 (2 files)
/home/rich/.etwolf/etmain/standards21.pk3 (2 files)
/home/rich/.etwolf/etmain/sot_b2.pk3 (111 files)
/home/rich/.etwolf/etmain/sniperion_b1.pk3 (18 files)
/home/rich/.etwolf/etmain/SG_1945_final.pk3 (217 files)
/home/rich/.etwolf/etmain/saberpeak_final.pk3 (243 files)
/home/rich/.etwolf/etmain/rttr_b2.pk3 (36 files)
/home/rich/.etwolf/etmain/ROP_River4.pk3 (77 files)
/home/rich/.etwolf/etmain/rocketrace_final2.pk3 (144 files)
/home/rich/.etwolf/etmain/rochelle_b2.pk3 (159 files)
/home/rich/.etwolf/etmain/rhine_bridge3.pk3 (368 files)
/home/rich/.etwolf/etmain/rhine2.pk3 (117 files)
/home/rich/.etwolf/etmain/resurrection_final.pk3 (306 files)
/home/rich/.etwolf/etmain/resurrection.pk3 (305 files)
/home/rich/.etwolf/etmain/reactor_final.pk3 (115 files)
/home/rich/.etwolf/etmain/raw_b3.pk3 (121 files)
/home/rich/.etwolf/etmain/raiders.pk3 (261 files)
/home/rich/.etwolf/etmain/radar_summer_101.pk3 (69 files)
/home/rich/.etwolf/etmain/praetoria_one.pk3 (380 files)
/home/rich/.etwolf/etmain/pha_horus.pk3 (184 files)
/home/rich/.etwolf/etmain/penemuende_b2.pk3 (143 files)
/home/rich/.etwolf/etmain/parisbastille_b3.pk3 (116 files)
/home/rich/.etwolf/etmain/pak05.pk3 (2 files)
/home/rich/.etwolf/etmain/over_the_top.pk3 (144 files)
/home/rich/.etwolf/etmain/nqpten10.pk3 (1 files)
/home/rich/.etwolf/etmain/northpole.pk3 (112 files)
/home/rich/.etwolf/etmain/normandy_final.pk3 (63 files)
/home/rich/.etwolf/etmain/norman016.pk3 (1 files)
/home/rich/.etwolf/etmain/neuschwaben_final2.pk3 (210 files)
/home/rich/.etwolf/etmain/nemorosuspb4.pk3 (88 files)
/home/rich/.etwolf/etmain/navarone.pk3 (105 files)
/home/rich/.etwolf/etmain/mp_theriver_2nd.pk3 (131 files)
/home/rich/.etwolf/etmain/mp_sub_rc1.pk3 (155 files)
/home/rich/.etwolf/etmain/mp_rocket_et_a1.pk3 (203 files)
/home/rich/.etwolf/etmain/mp_forum_b1.pk3 (98 files)
/home/rich/.etwolf/etmain/mp_beach.pk3 (176 files)
/home/rich/.etwolf/etmain/mml_minastirith_fp3_sp1.pk3 (97 files)
/home/rich/.etwolf/etmain/mml_minastirith_fp3.pk3 (90 files)
/home/rich/.etwolf/etmain/mml_helmsdeep_b4.pk3 (185 files)
/home/rich/.etwolf/etmain/mml_helmsdeep_a3_sp1.pk3 (4 files)
/home/rich/.etwolf/etmain/mml_helmsdeep_a3.pk3 (125 files)
/home/rich/.etwolf/etmain/mml_church_et_v1.pk3 (107 files)
/home/rich/.etwolf/etmain/mlb_temple.pk3 (83 files)
/home/rich/.etwolf/etmain/mlb_starbase.pk3 (197 files)
/home/rich/.etwolf/etmain/mlb_hotchkiss.pk3 (130 files)
/home/rich/.etwolf/etmain/mlb_egypt_fixed.pk3 (195 files)
/home/rich/.etwolf/etmain/mlb_egypt.pk3 (195 files)
/home/rich/.etwolf/etmain/mlb_daybreak.pk3 (158 files)
/home/rich/.etwolf/etmain/mlb_bayraid.pk3 (140 files)
/home/rich/.etwolf/etmain/mars.pk3 (57 files)
/home/rich/.etwolf/etmain/marketgarden_et_r2.pk3 (275 files)
/home/rich/.etwolf/etmain/mapki31.pk3 (1 files)
/home/rich/.etwolf/etmain/ludendorff_110.pk3 (188 files)
/home/rich/.etwolf/etmain/loffys_tram1.pk3 (173 files)
/home/rich/.etwolf/etmain/lmsm_final.pk3 (377 files)
/home/rich/.etwolf/etmain/lighthouse2.pk3 (101 files)
/home/rich/.etwolf/etmain/lighthouse.pk3 (110 files)
/home/rich/.etwolf/etmain/leningrad_b2.pk3 (135 files)
/home/rich/.etwolf/etmain/karsiah.pk3 (40 files)
/home/rich/.etwolf/etmain/isle.pk3 (60 files)
/home/rich/.etwolf/etmain/industry2.pk3 (85 files)
/home/rich/.etwolf/etmain/HoG_b12_dt.pk3 (136 files)
/home/rich/.etwolf/etmain/hide.pk3 (69 files)
/home/rich/.etwolf/etmain/haunted_mansion.pk3 (93 files)
/home/rich/.etwolf/etmain/gsk6.pk3 (2 files)
/home/rich/.etwolf/etmain/greenlee_et.pk3 (60 files)
/home/rich/.etwolf/etmain/graverob_b1.pk3 (95 files)
/home/rich/.etwolf/etmain/goldrush-ga.pk3 (36 files)
/home/rich/.etwolf/etmain/goldendunk_a2.pk3 (76 files)
/home/rich/.etwolf/etmain/glider_251.pk3 (52 files)
/home/rich/.etwolf/etmain/GA_El_Kef.pk3 (39 files)
/home/rich/.etwolf/etmain/Gardenn_b3.pk3 (52 files)
/home/rich/.etwolf/etmain/fun_beach_final.pk3 (72 files)
/home/rich/.etwolf/etmain/frost_final.pk3 (51 files)
/home/rich/.etwolf/etmain/Frostbite.pk3 (99 files)
/home/rich/.etwolf/etmain/Fata_Morgana.pk3 (73 files)
/home/rich/.etwolf/etmain/falcon2.pk3 (67 files)
/home/rich/.etwolf/etmain/facility31_b1.pk3 (212 files)
/home/rich/.etwolf/etmain/exodus_a4b.pk3 (55 files)
/home/rich/.etwolf/etmain/et_mor2.pk3 (86 files)
/home/rich/.etwolf/etmain/et_ice.pk3 (61 files)
/home/rich/.etwolf/etmain/et_dam_b1.pk3 (85 files)
/home/rich/.etwolf/etmain/et_beach.pk3 (177 files)
/home/rich/.etwolf/etmain/etmapcycle.pk3 (3 files)
/home/rich/.etwolf/etmain/etdo_f1.pk3 (137 files)
/home/rich/.etwolf/etmain/escape2.pk3 (82 files)
/home/rich/.etwolf/etmain/eagles_2ways_b3.pk3 (264 files)
/home/rich/.etwolf/etmain/eagles2_a6.pk3 (285 files)
/home/rich/.etwolf/etmain/eagles2_a4.pk3 (255 files)
/home/rich/.etwolf/etmain/ds_bunkers_b2.pk3 (137 files)
/home/rich/.etwolf/etmain/ds_bunkers_b2.74e99cc3.pk3 (130 files)
/home/rich/.etwolf/etmain/dojo3.pk3 (2 files)
/home/rich/.etwolf/etmain/dojo2.pk3 (2 files)
/home/rich/.etwolf/etmain/dojo1.pk3 (2 files)
/home/rich/.etwolf/etmain/deltaforce_b.pk3 (78 files)
/home/rich/.etwolf/etmain/darji2.pk3 (220 files)
/home/rich/.etwolf/etmain/ctf_pool_v2.pk3 (136 files)
/home/rich/.etwolf/etmain/cortexbeta_who.pk3 (166 files)
/home/rich/.etwolf/etmain/cortexbeta_who.baada64e.pk3 (165 files)
/home/rich/.etwolf/etmain/complete.pk3 (2 files)
/home/rich/.etwolf/etmain/colosseum_b5.pk3 (76 files)
/home/rich/.etwolf/etmain/cherbourg.pk3 (79 files)
/home/rich/.etwolf/etmain/chartwell_121.pk3 (241 files)
/home/rich/.etwolf/etmain/chartwell_120.pk3 (241 files)
/home/rich/.etwolf/etmain/chariot_120.pk3 (295 files)
/home/rich/.etwolf/etmain/cathedral_final.pk3 (82 files)
/home/rich/.etwolf/etmain/castleattack_b5.pk3 (156 files)
/home/rich/.etwolf/etmain/carnage2.pk3 (41 files)
/home/rich/.etwolf/etmain/canyon3.pk3 (131 files)
/home/rich/.etwolf/etmain/campv3.pk3 (2 files)
/home/rich/.etwolf/etmain/caha_tavern_b2.pk3 (145 files)
/home/rich/.etwolf/etmain/caen2.pk3 (85 files)
/home/rich/.etwolf/etmain/caen.pk3 (82 files)
/home/rich/.etwolf/etmain/byzantine.pk3 (216 files)
/home/rich/.etwolf/etmain/bunker1298.pk3 (1 files)
/home/rich/.etwolf/etmain/bunker1296.pk3 (1 files)
/home/rich/.etwolf/etmain/bunker1280.pk3 (1 files)
/home/rich/.etwolf/etmain/bunker1278.pk3 (1 files)
/home/rich/.etwolf/etmain/bulldog_160.pk3 (50 files)
/home/rich/.etwolf/etmain/breakout_360.pk3 (103 files)
/home/rich/.etwolf/etmain/braundorf_b4.pk3 (51 files)
/home/rich/.etwolf/etmain/bot_campaign.pk3 (2 files)
/home/rich/.etwolf/etmain/beta_low_mount_***.pk3 (71 files)
/home/rich/.etwolf/etmain/beta_flame-guards.pk3 (157 files)
/home/rich/.etwolf/etmain/berserk_te.pk3 (88 files)
/home/rich/.etwolf/etmain/bergen_fixed.pk3 (182 files)
/home/rich/.etwolf/etmain/beerrun_b7a.pk3 (120 files)
/home/rich/.etwolf/etmain/baserace_beta2.pk3 (94 files)
/home/rich/.etwolf/etmain/baserace_b3c.pk3 (141 files)
/home/rich/.etwolf/etmain/baserace_b3a.pk3 (139 files)
/home/rich/.etwolf/etmain/baserace_b1b.pk3 (56 files)
/home/rich/.etwolf/etmain/baserace.pk3 (129 files)
/home/rich/.etwolf/etmain/axislab_final.pk3 (172 files)
/home/rich/.etwolf/etmain/am_hydro_dam_fix.pk3 (4 files)
/home/rich/.etwolf/etmain/am_hydro_dam.pk3 (66 files)
/home/rich/.etwolf/etmain/alleys.pk3 (89 files)
/home/rich/.etwolf/etmain/alchemy125b.pk3 (5 files)
/home/rich/.etwolf/etmain/AFD_Beta5.pk3 (38 files)
/home/rich/.etwolf/etmain/1944_siegfried.pk3 (50 files)
/home/rich/.etwolf/etmain/1944_beach.pk3 (60 files)
/home/rich/.etwolf/etmain/110_factory_170.pk3 (279 files)
/home/rich/.etwolf/etmain/10mash2007_15.pk3 (2 files)
/home/rich/.etwolf/etmain/10mash2007_14.pk3 (2 files)
/home/rich/.etwolf/etmain/10maap.pk3 (2 files)
/home/rich/.etwolf/etmain/0729bbanq8.pk3 (1 files)
/home/rich/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
25861 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/harmonized/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Rage 128 Pro 20051027 AGP 1x x86/MMX/SSE
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
... GL_EXT_texture_filter_anisotropic not found
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: VA Linux Systems, Inc.
GL_RENDERER: Mesa DRI Rage 128 Pro 20051027 AGP 1x x86/MMX/SSE
GL_VERSION: 1.2 Mesa 7.0.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_compression GL_ARB_texture_env_add GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_object GL_EXT_vertex_array GL_APPLE_packed_pixels GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_swap_control GLX_MESA_swap_frame_usage GLX_OML_swap_method GLX_SGI_swap_control GLX_SGI_video_sync GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_group 
GL_MAX_TEXTURE_SIZE: 512
GL_MAX_ACTIVE_TEXTURES_ARB: 2

PIXELFORMAT: color(16-bits) Z(16-bit) stencil(0-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 2
texture bits: 16
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
11025 speed
0x0xae45f000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/rich/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/rich/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/rich/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac8cdf40  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: rich-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: Attempting to resolve master8.evenbalance.com
^5PunkBuster Client: Resolved to [66.180.170.20]
^5PunkBuster Client: PunkBuster Client (v2.036 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60b linux-i386 May  8 2006]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

and here's from connecting to a server to exiting:

]/connect et3.kernwaffe.de
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
et3.kernwaffe.de resolved to 83.141.24.114:27960
^5PunkBuster Client: Connected to Server 83.141.24.114:27960
----- FS_Startup -----
Current search path:
/home/rich/.etwolf/noquarter/z_kw_skmaps_standard006.pk3 (2 files)
    on the pure list
/home/rich/.etwolf/noquarter/z_kw_skmaps_standard005.pk3 (4 files)
    on the pure list
/home/rich/.etwolf/noquarter/z_kw_skmaps_standard004.pk3 (98 files)
    on the pure list
/home/rich/.etwolf/noquarter/z_kw_extrapack_001.pk3 (22 files)
    on the pure list
/home/rich/.etwolf/noquarter/z_kwbig_cmpgn_1.37.pk3 (3 files)
    on the pure list
/home/rich/.etwolf/noquarter/nq_bin_b1.1.0.pk3 (6 files)
    on the pure list
/home/rich/.etwolf/noquarter/noquarter_b1.1.0.pk3 (1037 files)
    on the pure list
/home/rich/.etwolf/etmain/z_pak_directplay_01.pk3 (3 files)
    on the pure list
/home/rich/.etwolf/etmain/Warbell.pk3 (242 files)
    on the pure list
/home/rich/.etwolf/etmain/vesuvius.pk3 (168 files)
    on the pure list
/home/rich/.etwolf/etmain/sw_oasis_b3.pk3 (45 files)
    on the pure list
/home/rich/.etwolf/etmain/supply.pk3 (44 files)
    on the pure list
/home/rich/.etwolf/etmain/pha_horus.pk3 (184 files)
    on the pure list
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
    on the pure list
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
    on the pure list
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
    on the pure list
/home/rich/.etwolf/etmain/mp_theriver_2nd.pk3 (131 files)
    on the pure list
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
    on the pure list
/home/rich/.etwolf/etmain/mml_minastirith_fp3.pk3 (90 files)
    on the pure list
/home/rich/.etwolf/etmain/mlb_hotchkiss.pk3 (130 files)
    on the pure list
/home/rich/.etwolf/etmain/mlb_egypt.pk3 (195 files)
    on the pure list
/home/rich/.etwolf/etmain/mlb_bayraid.pk3 (140 files)
    on the pure list
/home/rich/.etwolf/etmain/haunted_mansion.pk3 (93 files)
    on the pure list
/home/rich/.etwolf/etmain/goldendunk_a2.pk3 (76 files)
    on the pure list
/home/rich/.etwolf/etmain/et_beach.pk3 (177 files)
    on the pure list
/home/rich/.etwolf/etmain/eagles2_a6.pk3 (285 files)
    on the pure list
/home/rich/.etwolf/etmain/colosseum_b5.pk3 (76 files)
    on the pure list
/home/rich/.etwolf/etmain/chartwell_121.pk3 (241 files)
    on the pure list
/home/rich/.etwolf/etmain/chariot_120.pk3 (295 files)
    on the pure list
/home/rich/.etwolf/etmain/cathedral_final.pk3 (82 files)
    on the pure list
/home/rich/.etwolf/etmain/castleattack_b5.pk3 (156 files)
    on the pure list
/home/rich/.etwolf/etmain/caen.pk3 (82 files)
    on the pure list
/home/rich/.etwolf/etmain/bulldog_160.pk3 (50 files)
    on the pure list
/home/rich/.etwolf/etmain/baserace.pk3 (129 files)
    on the pure list
/home/rich/.etwolf/etmain/am_hydro_dam.pk3 (66 files)
    on the pure list
/home/rich/.etwolf/noquarter/z_T2D-campaigns.pk3 (9 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_MLB_scripts.pk3 (9 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_menu.pk3 (3 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_mashsounds_beta9.pk3 (80 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_kw_watermark_1.00.pk3 (5 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_kw_sound_04.pk3 (141 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_kw_sound_03.pk3 (115 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_kw_sound_02.pk3 (85 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_kw_skmaps_standard003.pk3 (8 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_kw_skmaps_standard002.pk3 (16 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_kw_skmaps_standard001.pk3 (66 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_kw_skmaps_010.pk3 (65 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_kw_skmaps_008.pk3 (2 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_kw_skmaps_007.pk3 (4 files)
    not on the pure list
/home/rich/.etwolf/noquarter/z_kw_skmaps_006.pk3 (17 file----- finished R_Init -----
copy /usr/local/games/enemy-territory/etmain/ui.mp.i386.so to /home/rich/.etwolf/noquarter/ui.mp.i386.so
Sys_LoadDll(/home/rich/.etwolf/noquarter/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xab02e320  
Sys_LoadDll(ui) succeeded!
copy /usr/local/games/enemy-territory/etmain/cgame.mp.i386.so to /home/rich/.etwolf/noquarter/cgame.mp.i386.so
Sys_LoadDll(/home/rich/.etwolf/noquarter/cgame.mp.i386.so)... ok
Sys_LoadDll(cgame) found **vmMain** at  0xa6f64820  
Sys_LoadDll(cgame) succeeded!
LOADING... :collision map:
LOADING... :sounds:
voice chat memory size = 0

.........................
Initializing Sound Scripts
...loading 'sound/scripts/vo_allies.sounds'
...loading 'sound/scripts/vo_axis.sounds'
...loading 'sound/scripts/mp_theriver_2nd.sounds'
done.
LOADING... :graphics:
LOADING... maps/mp_theriver_2nd.bsp
^3WARNING: Couldn't find image for shader textures/river2nd_r/rv2nd_wallins01_base_2
^3WARNING: Couldn't find image for shader textures/river2nd_r/rv2nd_wallins01_base_2
^3WARNING: Couldn't find image for shader textures/river2nd_r/rv2nd_wallins01_base_2
stitched 0 LoD cracks
...loaded 13727 faces, 0 meshes, 333 trisurfs, 0 flares 0 foliage
LOADING... :entities:
LOADING... :game media:
LOADING... :textures:
LOADING... :models:
WARNING: reused image ui/assets/filter_antilag.tga with mixed glWrapClampMode parm
LOADING... :weapons:
LOADING... :items:
LOADING... :inline models:
LOADING... :server models:
LOADING... :particles:
LOADING... :classes:
LOADING... :game media done:
LOADING... :flamechunks:
LOADING... :clients:
^dLoadLocations: ^3Warning: ^9No location data found for map ^2mp_theriver_2nd^9.
CL_InitCGame: 44.89 seconds
Com_TouchMemory: 1 msec
execing profiles/harmonized/etconfig.cfg
[skipnotify]^3server: retrieved xp save state from 10 mins ago
^1Note: ^3class ^7SOLDIER^3 with ^7MORTAR^3 is now ^2available
Axis Command Post constructed: charge speed increased!
XP-Shuffle / Map Restart / Swap Teams  / Match Reset and New Campaign votings are now DISABLED.
^5PunkBuster Client: PB Server assigned guid = d07e669ef91e25a397abb2dfcfdc6b3f
^5PunkBuster Client: Receiving from PB Server (l v1.638 | A1382 C2.036)
^5PunkBuster Client: WARNING: ^7PB Kicks for Name Stealing and Non-standard Characters and All PB Restrictions on this Server
wiwex^7 was blasted by urban^7's rifle grenade
^5PunkBuster Client: rate = "25000" : must be EQUAL to 25000 (OK)
^5PunkBuster Client: snaps = "20" : must be INSIDE 20 to 40 (OK)
^5PunkBuster Client: cl_maxpackets = "30" : must be INSIDE 30 to 100 (OK)
^5PunkBuster Client: cl_timenudge = "0" : must be EQUAL to 0 (OK)
^5PunkBuster Client: cg_bobup = "0.005" : must be INSIDE 0 to 0.005 (OK)
^5PunkBuster Client: r_picmip = "2" : must be INSIDE 0 to 3 (OK)
^5PunkBuster Client: r_overbrightbits = "0" : must be INSIDE 0 to 4 (OK)
^5PunkBuster Client: r_mapoverbrigtbits = "" : must be INSIDE 0 to 4 (OK)
^5PunkBuster Client: cg_shadows = "0" : must be INSIDE 0 to 1 (OK)
^5PunkBuster Client: r_rmse = "0.0" : must be EQUAL to 0 (OK)
^5PunkBuster Client: 0 Current Cvar Violations
^5PunkBuster Client: CvarList truncated; Use pb_cvarlist to see entire list
----- CL_Shutdown -----
copy /usr/local/games/enemy-territory/etmain/ui.mp.i386.so to /home/rich/.etwolf/noquarter/ui.mp.i386.so
Sys_LoadDll(/home/rich/.etwolf/noquarter/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac5c2f40  
Sys_LoadDll(ui) succeeded!
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

---

### Post by harmonizedmc9 on 2008-02-01
wow ok nevermind got it working... if you want to know what the problem was, ask me, but frankly i am far too embarrassed to post it here. in fact i'd just delete this thread if i could but with my er formidable technical savvy i can't figure out how at the moment and i'm too impatient to play et now that it's working again to find out how.  sorry.

---


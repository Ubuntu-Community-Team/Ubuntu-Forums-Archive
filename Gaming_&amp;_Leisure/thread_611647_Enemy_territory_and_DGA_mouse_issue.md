---
title: "Enemy territory and DGA mouse issue"
date: 2007-11-13
forum: Gaming &amp; Leisure
---

### Post by frodon on 2007-11-13
Since i upgraded to gutsy i have an issue with enemy territory.

When i first tried to play ET after my upgrade i noticed that once i join a server my mouse go down and will make like a washing machine if i move it, so impossible to play.
After some research i found out that disabling the dga mouse support in ET (put the in_dgamouse parameter to 0) fully solve the issue.

However without the dga mouse support my 2000 dpi mouse behave like a 1000 dpi mouse, i mean it is less accurate.

Now checking my ET log i found out that XF86DGA Mouse driver is just not initialized which explain why i get problems when i set ET to use dga mouse support within ET :
```
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/frodon/.etwolf/etmain/z_[FL]_ExtraSound.pk3 (3 files)
/home/frodon/.etwolf/etmain/z_baserfin_scobo.pk3 (22 files)
/home/frodon/.etwolf/etmain/zz_et6mapcycle.pk3 (3 files)
/home/frodon/.etwolf/etmain/zuz30maps.pk3 (3 files)
/home/frodon/.etwolf/etmain/xlabs1.pk3 (75 files)
/home/frodon/.etwolf/etmain/WhaleClient_CompassShaders.pk3 (2 files)
/home/frodon/.etwolf/etmain/whaleclient-1_4_beta1.pk3 (98 files)
/home/frodon/.etwolf/etmain/Warbell.pk3 (242 files)
/home/frodon/.etwolf/etmain/venice_tcrc2_v1_lt.pk3 (1 files)
/home/frodon/.etwolf/etmain/venice.pk3 (330 files)
/home/frodon/.etwolf/etmain/v2base.pk3 (22 files)
/home/frodon/.etwolf/etmain/trickjumptemple3.pk3 (40 files)
/home/frodon/.etwolf/etmain/trick.pk3 (2 files)
/home/frodon/.etwolf/etmain/transmitter.pk3 (143 files)
/home/frodon/.etwolf/etmain/toiletmanfinal.pk3 (72 files)
/home/frodon/.etwolf/etmain/test_008.pk3 (1 files)
/home/frodon/.etwolf/etmain/temple_final.pk3 (57 files)
/home/frodon/.etwolf/etmain/tc_venice_rc2.pk3 (324 files)
/home/frodon/.etwolf/etmain/tc_base.pk3 (63 files)
/home/frodon/.etwolf/etmain/sw_oasis_b3.pk3 (45 files)
/home/frodon/.etwolf/etmain/supplydepot3.pk3 (51 files)
/home/frodon/.etwolf/etmain/supplydepot2.pk3 (46 files)
/home/frodon/.etwolf/etmain/supply.pk3 (44 files)
/home/frodon/.etwolf/etmain/Stonehenge_KOTH.pk3 (37 files)
/home/frodon/.etwolf/etmain/snatch3.pk3 (34 files)
/home/frodon/.etwolf/etmain/snakejumps_b1.pk3 (14 files)
/home/frodon/.etwolf/etmain/snake2.pk3 (36 files)
/home/frodon/.etwolf/etmain/saberpeak_final.pk3 (243 files)
/home/frodon/.etwolf/etmain/ROP_River4.pk3 (77 files)
/home/frodon/.etwolf/etmain/rommel_final_supplement.pk3 (5 files)
/home/frodon/.etwolf/etmain/rommel_final_1107.pk3 (126 files)
/home/frodon/.etwolf/etmain/resurrection.pk3 (305 files)
/home/frodon/.etwolf/etmain/reactor_final.pk3 (115 files)
/home/frodon/.etwolf/etmain/raw_final.pk3 (118 files)
/home/frodon/.etwolf/etmain/password2.pk3 (100 files)
/home/frodon/.etwolf/etmain/parisbastille_b3.pk3 (116 files)
/home/frodon/.etwolf/etmain/oilraid.pk3 (101 files)
/home/frodon/.etwolf/etmain/night_crawlers.pk3 (108 files)
/home/frodon/.etwolf/etmain/nejijump5_b5.pk3 (37 files)
/home/frodon/.etwolf/etmain/nejijump5_b4.pk3 (50 files)
/home/frodon/.etwolf/etmain/nejijump4.pk3 (39 files)
/home/frodon/.etwolf/etmain/nejijump3.pk3 (44 files)
/home/frodon/.etwolf/etmain/mrmen_gamma_final.pk3 (119 files)
/home/frodon/.etwolf/etmain/mml_minastirith_fp2.pk3 (75 files)
/home/frodon/.etwolf/etmain/mlb_hotchkiss.pk3 (130 files)
/home/frodon/.etwolf/etmain/marketgarden_et_r2.pk3 (300 files)
/home/frodon/.etwolf/etmain/makemejump-b3.pk3 (16 files)
/home/frodon/.etwolf/etmain/LNATrickjump.pk3 (16 files)
/home/frodon/.etwolf/etmain/lnatjhard2.pk3 (16 files)
/home/frodon/.etwolf/etmain/ldtj_b1.pk3 (40 files)
/home/frodon/.etwolf/etmain/KxKGamma.pk3 (23 files)
/home/frodon/.etwolf/etmain/karsiah_te2.pk3 (41 files)
/home/frodon/.etwolf/etmain/island.pk3 (134 files)
/home/frodon/.etwolf/etmain/industry2_final.pk3 (85 files)
/home/frodon/.etwolf/etmain/ikkigammas.pk3 (24 files)
/home/frodon/.etwolf/etmain/HoG_b12_dt.pk3 (136 files)
/home/frodon/.etwolf/etmain/hankjump7.pk3 (9 files)
/home/frodon/.etwolf/etmain/GTOv4.pk3 (6 files)
/home/frodon/.etwolf/etmain/goldrush-ga.pk3 (36 files)
/home/frodon/.etwolf/etmain/GA_El_Kef.pk3 (39 files)
/home/frodon/.etwolf/etmain/fun_testing.pk3 (1 files)
/home/frodon/.etwolf/etmain/funjumpsmap-b4.pk3 (105 files)
/home/frodon/.etwolf/etmain/frost_final.pk3 (51 files)
/home/frodon/.etwolf/etmain/Frostbite.pk3 (99 files)
/home/frodon/.etwolf/etmain/FLY-Xtrem-Arena.pk3 (199 files)
/home/frodon/.etwolf/etmain/fg3_playervote2.pk3 (3 files)
/home/frodon/.etwolf/etmain/fg3_passion.pk3 (6 files)
/home/frodon/.etwolf/etmain/fg3_future_v3.pk3 (6 files)
/home/frodon/.etwolf/etmain/fg3_fixed.pk3 (3 files)
/home/frodon/.etwolf/etmain/fg1_100_beta4.pk3 (5 files)
/home/frodon/.etwolf/etmain/et_village.pk3 (58 files)
/home/frodon/.etwolf/etmain/et_mor2.pk3 (86 files)
/home/frodon/.etwolf/etmain/et_mor2.c1ae225d.pk3 (86 files)
/home/frodon/.etwolf/etmain/et_ice.pk3 (61 files)
/home/frodon/.etwolf/etmain/equ2_009.pk3 (1 files)
/home/frodon/.etwolf/etmain/equ2_006.pk3 (1 files)
/home/frodon/.etwolf/etmain/equ1_044.pk3 (1 files)
/home/frodon/.etwolf/etmain/equ1_043.pk3 (1 files)
/home/frodon/.etwolf/etmain/equ1_042.pk3 (1 files)
/home/frodon/.etwolf/etmain/equ1_041.pk3 (1 files)
/home/frodon/.etwolf/etmain/equ1_040.pk3 (1 files)
/home/frodon/.etwolf/etmain/equ1_027.pk3 (1 files)
/home/frodon/.etwolf/etmain/equ1_026.pk3 (1 files)
/home/frodon/.etwolf/etmain/equ1_023.pk3 (2 files)
/home/frodon/.etwolf/etmain/equ1_022.pk3 (2 files)
/home/frodon/.etwolf/etmain/equ1_021.pk3 (3 files)
/home/frodon/.etwolf/etmain/equ1_020.pk3 (3 files)
/home/frodon/.etwolf/etmain/equ1_011.pk3 (2 files)
/home/frodon/.etwolf/etmain/equ1_010.pk3 (2 files)
/home/frodon/.etwolf/etmain/equ1_009.pk3 (2 files)
/home/frodon/.etwolf/etmain/equ1_008.pk3 (2 files)
/home/frodon/.etwolf/etmain/equ1_007.pk3 (1 files)
/home/frodon/.etwolf/etmain/eftetpub1206.pk3 (2 files)
/home/frodon/.etwolf/etmain/dubrovnik_final.pk3 (186 files)
/home/frodon/.etwolf/etmain/ds_bunkers_b2.pk3 (137 files)
/home/frodon/.etwolf/etmain/Divinejumps.pk3 (29 files)
/home/frodon/.etwolf/etmain/ctrljumps_2_final.pk3 (18 files)
/home/frodon/.etwolf/etmain/cpu_arena_b1.pk3 (33 files)
/home/frodon/.etwolf/etmain/complete.pk3 (2 files)
/home/frodon/.etwolf/etmain/chocojump1_3.pk3 (142 files)
/home/frodon/.etwolf/etmain/cathedral_final.pk3 (82 files)
/home/frodon/.etwolf/etmain/caen2_rev1.pk3 (73 files)
/home/frodon/.etwolf/etmain/caen2.pk3 (85 files)
/home/frodon/.etwolf/etmain/caen.pk3 (82 files)
/home/frodon/.etwolf/etmain/bunker1258.pk3 (2 files)
/home/frodon/.etwolf/etmain/bunker1256.pk3 (2 files)
/home/frodon/.etwolf/etmain/bunker1254.pk3 (2 files)
/home/frodon/.etwolf/etmain/bridges.pk3 (153 files)
/home/frodon/.etwolf/etmain/bremen_b2.pk3 (82 files)
/home/frodon/.etwolf/etmain/braundorf_b4.pk3 (51 files)
/home/frodon/.etwolf/etmain/bp_valhalla.pk3 (55 files)
/home/frodon/.etwolf/etmain/beejump-b2.pk3 (45 files)
/home/frodon/.etwolf/etmain/battery_recharged_130.pk3 (58 files)
/home/frodon/.etwolf/etmain/baserace_b1b.pk3 (56 files)
/home/frodon/.etwolf/etmain/base47.pk3 (67 files)
/home/frodon/.etwolf/etmain/base12_b6.pk3 (88 files)
/home/frodon/.etwolf/etmain/adlernest.pk3 (113 files)
/home/frodon/.etwolf/etmain/1944_beach.pk3 (60 files)
/home/frodon/.etwolf/etmain
/mnt/fatboy/Jeux/enemi_terrictory/etmain/pak2.pk3 (22 files)
/mnt/fatboy/Jeux/enemi_terrictory/etmain/pak1.pk3 (10 files)
/mnt/fatboy/Jeux/enemi_terrictory/etmain/pak0.pk3 (3725 files)
/mnt/fatboy/Jeux/enemi_terrictory/etmain/mp_bin.pk3 (6 files)
/mnt/fatboy/Jeux/enemi_terrictory/etmain

----------------------
10904 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/frodon/etconfig.cfg
com_zoneMegs will be changed upon restarting.
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
...setting mode 8: 1280 1024
Using XFree86-VidModeExtension Version 2.2
XFree86-VidModeExtension Activated at 1280x1024
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 7600 GT/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 7600 GT/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.0 NVIDIA 96.39
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_texture_from_pixmap GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_ARB_get_proc_address 
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 8, 1280 x 1024 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Forcing glFinish
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
48000 speed
0x0xa7968000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/frodon/.etwolf/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa4fbc0ea  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: trax
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: Attempting to resolve master7.evenbalance.com
^5PunkBuster Client: Resolved to [216.240.146.139]
^5PunkBuster Client: Master Query Sent to (MASTER4.EVENBALANCE.COM) 66.180.170.20
^5PunkBuster Client: PunkBuster Client (v1.738 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60b linux-i386 May  8 2006]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
]/exec lg
execing lg
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
85.214.123.186:27960 resolved to 85.214.123.186:27960
^5PunkBuster Client: Connected to Server 85.214.123.186:27960
^5PunkBuster Client: Received Master Security Information
----- FS_Startup -----
Current search path:
/home/frodon/.etwolf/noquarter/nq_bin_b1.1.1.pk3 (6 files)
    on the pure list
/home/frodon/.etwolf/noquarter/noquarter_b1.1.1.pk3 (68 files)
    on the pure list
/home/frodon/.etwolf/noquarter/noquarter_b1.1.0.pk3 (1037 files)
    on the pure list
/home/frodon/.etwolf/etmain/venice.pk3 (330 files)
    on the pure list
/home/frodon/.etwolf/etmain/sw_oasis_b3.pk3 (45 files)
    on the pure list
/home/frodon/.etwolf/etmain/supplydepot3.pk3 (51 files)
    on the pure list
/home/frodon/.etwolf/etmain/snatch3.pk3 (34 files)
    on the pure list
/home/frodon/.etwolf/etmain/saberpeak_final.pk3 (243 files)
    on the pure list
/mnt/fatboy/Jeux/enemi_terrictory/etmain/pak2.pk3 (22 files)
    on the pure list
/mnt/fatboy/Jeux/enemi_terrictory/etmain/pak1.pk3 (10 files)
    on the pure list
/mnt/fatboy/Jeux/enemi_terrictory/etmain/pak0.pk3 (3725 files)
    on the pure list
/mnt/fatboy/Jeux/enemi_terrictory/etmain/mp_bin.pk3 (6 files)
    on the pure list
/home/frodon/.etwolf/etmain/goldrush-ga.pk3 (36 files)
    on the pure list
/home/frodon/.etwolf/etmain/et_mor2.c1ae225d.pk3 (86 files)
    on the pure list
/home/frodon/.etwolf/etmain/dubrovnik_final.pk3 (186 files)
    on the pure list
/home/frodon/.etwolf/etmain/caen2.pk3 (85 files)
    on the pure list
/home/frodon/.etwolf/etmain/1944_beach.pk3 (60 files)
    on the pure list
/home/frodon/.etwolf/noquarter/z_kw_watermark_1.00.pk3 (5 files)
    not on the pure list
/home/frodon/.etwolf/noquarter/z_kw_mines.pk3 (6 files)
    not on the pure list
/home/frodon/.etwolf/noquarter/x_sounds_10.pk3 (225 files)
    not on the pure list
/home/frodon/.etwolf/noquarter/Spring.pk3 (71 files)
    not on the pure list
/home/frodon/.etwolf/noquarter/nq_bin_b1.0.2.pk3 (6 files)
    not on the pure list
/home/frodon/.etwolf/noquarter/noquarter_b1.0.2.pk3 (958 files)
    not on the pure list
/home/frodon/.etwolf/noquarter/fun_04.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/noquarter/chat_sound[ZUZ].pk3 (123 files)
    not on the pure list
/home/frodon/.etwolf/noquarter
/mnt/fatboy/Jeux/enemi_terrictory/noquarter
/home/frodon/.etwolf/etmain/z_[FL]_ExtraSound.pk3 (3 files)
    not on the pure list
/home/frodon/.etwolf/etmain/z_baserfin_scobo.pk3 (22 files)
    not on the pure list
/home/frodon/.etwolf/etmain/zz_et6mapcycle.pk3 (3 files)
    not on the pure list
/home/frodon/.etwolf/etmain/zuz30maps.pk3 (3 files)
    not on the pure list
/home/frodon/.etwolf/etmain/xlabs1.pk3 (75 files)
    not on the pure list
/home/frodon/.etwolf/etmain/WhaleClient_CompassShaders.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/whaleclient-1_4_beta1.pk3 (98 files)
    not on the pure list
/home/frodon/.etwolf/etmain/Warbell.pk3 (242 files)
    not on the pure list
/home/frodon/.etwolf/etmain/venice_tcrc2_v1_lt.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/v2base.pk3 (22 files)
    not on the pure list
/home/frodon/.etwolf/etmain/trickjumptemple3.pk3 (40 files)
    not on the pure list
/home/frodon/.etwolf/etmain/trick.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/transmitter.pk3 (143 files)
    not on the pure list
/home/frodon/.etwolf/etmain/toiletmanfinal.pk3 (72 files)
    not on the pure list
/home/frodon/.etwolf/etmain/test_008.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/temple_final.pk3 (57 files)
    not on the pure list
/home/frodon/.etwolf/etmain/tc_venice_rc2.pk3 (324 files)
    not on the pure list
/home/frodon/.etwolf/etmain/tc_base.pk3 (63 files)
    not on the pure list
/home/frodon/.etwolf/etmain/supplydepot2.pk3 (46 files)
    not on the pure list
/home/frodon/.etwolf/etmain/supply.pk3 (44 files)
    not on the pure list
/home/frodon/.etwolf/etmain/Stonehenge_KOTH.pk3 (37 files)
    not on the pure list
/home/frodon/.etwolf/etmain/snakejumps_b1.pk3 (14 files)
    not on the pure list
/home/frodon/.etwolf/etmain/snake2.pk3 (36 files)
    not on the pure list
/home/frodon/.etwolf/etmain/ROP_River4.pk3 (77 files)
    not on the pure list
/home/frodon/.etwolf/etmain/rommel_final_supplement.pk3 (5 files)
    not on the pure list
/home/frodon/.etwolf/etmain/rommel_final_1107.pk3 (126 files)
    not on the pure list
/home/frodon/.etwolf/etmain/resurrection.pk3 (305 files)
    not on the pure list
/home/frodon/.etwolf/etmain/reactor_final.pk3 (115 files)
    not on the pure list
/home/frodon/.etwolf/etmain/raw_final.pk3 (118 files)
    not on the pure list
/home/frodon/.etwolf/etmain/password2.pk3 (100 files)
    not on the pure list
/home/frodon/.etwolf/etmain/parisbastille_b3.pk3 (116 files)
    not on the pure list
/home/frodon/.etwolf/etmain/oilraid.pk3 (101 files)
    not on the pure list
/home/frodon/.etwolf/etmain/night_crawlers.pk3 (108 files)
    not on the pure list
/home/frodon/.etwolf/etmain/nejijump5_b5.pk3 (37 files)
    not on the pure list
/home/frodon/.etwolf/etmain/nejijump5_b4.pk3 (50 files)
    not on the pure list
/home/frodon/.etwolf/etmain/nejijump4.pk3 (39 files)
    not on the pure list
/home/frodon/.etwolf/etmain/nejijump3.pk3 (44 files)
    not on the pure list
/home/frodon/.etwolf/etmain/mrmen_gamma_final.pk3 (119 files)
    not on the pure list
/home/frodon/.etwolf/etmain/mml_minastirith_fp2.pk3 (75 files)
    not on the pure list
/home/frodon/.etwolf/etmain/mlb_hotchkiss.pk3 (130 files)
    not on the pure list
/home/frodon/.etwolf/etmain/marketgarden_et_r2.pk3 (300 files)
    not on the pure list
/home/frodon/.etwolf/etmain/makemejump-b3.pk3 (16 files)
    not on the pure list
/home/frodon/.etwolf/etmain/LNATrickjump.pk3 (16 files)
    not on the pure list
/home/frodon/.etwolf/etmain/lnatjhard2.pk3 (16 files)
    not on the pure list
/home/frodon/.etwolf/etmain/ldtj_b1.pk3 (40 files)
    not on the pure list
/home/frodon/.etwolf/etmain/KxKGamma.pk3 (23 files)
    not on the pure list
/home/frodon/.etwolf/etmain/karsiah_te2.pk3 (41 files)
    not on the pure list
/home/frodon/.etwolf/etmain/island.pk3 (134 files)
    not on the pure list
/home/frodon/.etwolf/etmain/industry2_final.pk3 (85 files)
    not on the pure list
/home/frodon/.etwolf/etmain/ikkigammas.pk3 (24 files)
    not on the pure list
/home/frodon/.etwolf/etmain/HoG_b12_dt.pk3 (136 files)
    not on the pure list
/home/frodon/.etwolf/etmain/hankjump7.pk3 (9 files)
    not on the pure list
/home/frodon/.etwolf/etmain/GTOv4.pk3 (6 files)
    not on the pure list
/home/frodon/.etwolf/etmain/GA_El_Kef.pk3 (39 files)
    not on the pure list
/home/frodon/.etwolf/etmain/fun_testing.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/funjumpsmap-b4.pk3 (105 files)
    not on the pure list
/home/frodon/.etwolf/etmain/frost_final.pk3 (51 files)
    not on the pure list
/home/frodon/.etwolf/etmain/Frostbite.pk3 (99 files)
    not on the pure list
/home/frodon/.etwolf/etmain/FLY-Xtrem-Arena.pk3 (199 files)
    not on the pure list
/home/frodon/.etwolf/etmain/fg3_playervote2.pk3 (3 files)
    not on the pure list
/home/frodon/.etwolf/etmain/fg3_passion.pk3 (6 files)
    not on the pure list
/home/frodon/.etwolf/etmain/fg3_future_v3.pk3 (6 files)
    not on the pure list
/home/frodon/.etwolf/etmain/fg3_fixed.pk3 (3 files)
    not on the pure list
/home/frodon/.etwolf/etmain/fg1_100_beta4.pk3 (5 files)
    not on the pure list
/home/frodon/.etwolf/etmain/et_village.pk3 (58 files)
    not on the pure list
/home/frodon/.etwolf/etmain/et_mor2.pk3 (86 files)
    not on the pure list
/home/frodon/.etwolf/etmain/et_ice.pk3 (61 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ2_009.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ2_006.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_044.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_043.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_042.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_041.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_040.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_027.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_026.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_023.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_022.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_021.pk3 (3 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_020.pk3 (3 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_011.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_010.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_009.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_008.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/equ1_007.pk3 (1 files)
    not on the pure list
/home/frodon/.etwolf/etmain/eftetpub1206.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/ds_bunkers_b2.pk3 (137 files)
    not on the pure list
/home/frodon/.etwolf/etmain/Divinejumps.pk3 (29 files)
    not on the pure list
/home/frodon/.etwolf/etmain/ctrljumps_2_final.pk3 (18 files)
    not on the pure list
/home/frodon/.etwolf/etmain/cpu_arena_b1.pk3 (33 files)
    not on the pure list
/home/frodon/.etwolf/etmain/complete.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/chocojump1_3.pk3 (142 files)
    not on the pure list
/home/frodon/.etwolf/etmain/cathedral_final.pk3 (82 files)
    not on the pure list
/home/frodon/.etwolf/etmain/caen2_rev1.pk3 (73 files)
    not on the pure list
/home/frodon/.etwolf/etmain/caen.pk3 (82 files)
    not on the pure list
/home/frodon/.etwolf/etmain/bunker1258.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/bunker1256.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/bunker1254.pk3 (2 files)
    not on the pure list
/home/frodon/.etwolf/etmain/bridges.pk3 (153 files)
    not on the pure list
/home/frodon/.etwolf/etmain/bremen_b2.pk3 (82 files)
    not on the pure list
/home/frodon/.etwolf/etmain/braundorf_b4.pk3 (51 files)
    not on the pure list
/home/frodon/.etwolf/etmain/bp_valhalla.pk3 (55 files)
    not on the pure list
/home/frodon/.etwolf/etmain/beejump-b2.pk3 (45 files)
    not on the pure list
/home/frodon/.etwolf/etmain/battery_recharged_130.pk3 (58 files)
    not on the pure list
/home/frodon/.etwolf/etmain/baserace_b1b.pk3 (56 files)
    not on the pure list
/home/frodon/.etwolf/etmain/base47.pk3 (67 files)
    not on the pure list
/home/frodon/.etwolf/etmain/base12_b6.pk3 (88 files)
    not on the pure list
/home/frodon/.etwolf/etmain/adlernest.pk3 (113 files)
    not on the pure list
/home/frodon/.etwolf/etmain
/mnt/fatboy/Jeux/enemi_terrictory/etmain

----------------------
24314 files in pk3 files
Com_TrackProfile: Deleting old pid file [etmain] [profiles/frodon/profile.pid]
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 7600 GT/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.0 NVIDIA 96.39
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_texture_from_pixmap GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_ARB_get_proc_address 
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 8, 1280 x 1024 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Forcing glFinish
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/frodon/.etwolf/noquarter/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa73a3000  
Sys_LoadDll(ui) succeeded!
Sys_LoadDll(/home/frodon/.etwolf/noquarter/cgame.mp.i386.so)... ok
Sys_LoadDll(cgame) found **vmMain** at  0x9f984b80  
Sys_LoadDll(cgame) succeeded!
CG_ParseWolfinfo(1)
LOADING... :collision map:
LOADING... :sounds:
voice chat memory size = 0

.........................
Initializing Sound Scripts
...loading 'sound/scripts/vo_allies.sounds'
...loading 'sound/scripts/vo_axis.sounds'
...loading 'sound/scripts/saberpeak_final.sounds'
done.
LOADING... :graphics:
LOADING... maps/saberpeak_final.bsp
stitched 16 LoD cracks
...loaded 11792 faces, 182 meshes, 333 trisurfs, 0 flares 0 foliage
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
^dLoadLocations: ^3Warning: ^9No location data found for map ^2saberpeak_final^9.
CL_InitCGame: 12.93 seconds
Com_TouchMemory: 0 msec
execing profiles/frodon/etconfig.cfg
com_hunkMegs will be changed upon restarting.
r_customwidth will be changed upon restarting.
com_soundMegs will be changed upon restarting.
com_zoneMegs will be changed upon restarting.
[skipnotify]^3server: retrieved xp save state from 1 days ago
[BOT]Bullseye^7 disconnected
Allies have stolen the Ammo!
----- CL_Shutdown -----
Sys_LoadDll(/home/frodon/.etwolf/noquarter/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa73a3000  
Sys_LoadDll(ui) succeeded!
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

```

In a standard ET log you should notice something like :
```
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
...setting mode 8: 1280 1024
Using XFree86-VidModeExtension Version 2.2
[B][COLOR="Red"]XF86DGA Mouse (Version 2.0) initialized[/COLOR]
[/B]XFree86-VidModeExtension Activated at 1280x1024
```

So my question is :
Does anyone know what i can do to make ET initializing XF86DGA Mouse driver on startup like it was the case when i was using feisty ?

If it helps here is my xorg.conf :
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database. 
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	#Load    "GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"on"
	Option 		"AllowGLXWithComposite" "true"
	Option		"backingstore" 		"true"
	Option		"NoLogo"
	Option 		"AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
	Identifier	"700S"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
	Modeline "1280x1024" 109.62  1280 1336 1472 1720  1024 1024 1026 1062 
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"700S"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

#Section "Extensions"
#	Option 	"Composite" "Enable"
#EndSection

```

---

### Post by frodon on 2008-05-15
Just in case someone had the same issue i found a solution.

I just renamed my .etwolf directory and started ET so that the game recreate it in default state. Then to not download all again i put back the datas from my old .etwolf directory **except** all "profile" directories which i left in default state as it is were the configuration issue is.

Once that done my mouse is working great again with full dga support.

---


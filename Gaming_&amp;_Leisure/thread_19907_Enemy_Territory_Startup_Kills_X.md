---
title: "Enemy Territory Startup Kills X"
date: 2005-03-14
forum: Gaming &amp; Leisure
---

### Post by AmeTsuchi on 2005-03-14
My apologies; I had originally posted this in the FAQ but this would probably be a better place to state my problem.

When running Enemy Territory, the game begins to start up and switches resolution. However, it then kills the X server and gdm restarts. glxgears works fine for me at 4600 FPS and ET was actually running fine on a previous install of Ubuntu (I had Warty, then upgraded to Hoary, then did a full wipe and reinstall because Hoary caused problems). Here's the output of et (and you'll also notice that /dev/dsp wasn't found, even though it does exist, but I'd like to at least get the game running first!)

I'm running the 2.6.8.1-5-k7 packaged kernel, but I had the same problems with the stock kernel.

Output:
```

ET 2.56 linux-i386 Sep 10 2003
----- FS_Startup -----
Current search path:
/home/enso/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/etmain

----------------------
3739 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Cvar_Set2: arch linux i386
Cvar_Set2: username enso

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
Cvar_Set2: cl_paused 0
Cvar_Set2: cl_running 1
Can't find scripts/translation.cfg
----- Client Initialization Complete -----
Cvar_Set2: r_uiFullScreen 1
----- R_Init -----
Warning: cvar "r_uifullscreen" given initial values: "1" and "0"
Cvar_Set2: r_flareFade 5
Cvar_Set2: com_hunkused 2022432
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce FX 5700 Ultra/AGP/SSE/3DNOW!
Cvar_Set2: r_previousglDriver libGL.so.1
Cvar_Set2: r_textureMode GL_LINEAR_MIPMAP_NEAREST
Cvar_Set2: r_picmip 1
Cvar_Set2: r_lastValidRenderer GeForce FX 5700 Ultra/AGP/SSE/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
Cvar_Set2: r_ext_NV_fog_dist 0
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce FX 5700 Ultra/AGP/SSE/3DNOW!
GL_VERSION: 1.5.1 NVIDIA 61.11
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
NV distance fog: disabled
Cvar_Set2: r_intensity 1
Warning: cvar "r_gamma" given initial values: "1.3" and "1.0"
Can't find image.cache
Initializing Shaders
^1...loading 'scripts/alpha.shader'
^1...loading 'scripts/alpha_sd.shader'
^1...loading 'scripts/assault.shader'
^1...loading 'scripts/assault_rock.shader'
^1...loading 'scripts/awf_props.shader'
^1...loading 'scripts/battery.shader'
^1...loading 'scripts/battery_wall.shader'
^1...loading 'scripts/bbmodels_mapobjects.shader'
^1...loading 'scripts/blimp.shader'
^1...loading 'scripts/bunker_sd.shader'
^1...loading 'scripts/castle_door.shader'
^1...loading 'scripts/castle_floor.shader'
^1...loading 'scripts/castle_window.shader'
^1...loading 'scripts/castle_wood.shader'
^1...loading 'scripts/chat.shader'
^1...loading 'scripts/chateau.shader'
^1...loading 'scripts/chat_window.shader'
^1...loading 'scripts/chat_wood.shader'
^1...loading 'scripts/common.shader'
^1...loading 'scripts/decals.shader'
^1...loading 'scripts/doors.shader'
^1...loading 'scripts/eerie.shader'
^1...loading 'scripts/egypt_door_sd.shader'
^1...loading 'scripts/egypt_floor_sd.shader'
^1...loading 'scripts/egypt_props_sd.shader'
^1...loading 'scripts/egypt_rock_sd.shader'
^1...loading 'scripts/egypt_trim_sd.shader'
^1...loading 'scripts/egypt_walls_sd.shader'
^1...loading 'scripts/egypt_windows_sd.shader'
^1...loading 'scripts/egypt_wood_sd.shader'
^1...loading 'scripts/factory_sd.shader'
^1...loading 'scripts/fueldump.shader'
^1...loading 'scripts/gfx_2d.shader'
^1...loading 'scripts/gfx_clipboard.shader'
^1...loading 'scripts/gfx_damage.shader'
^1...loading 'scripts/gfx_hud.shader'
^1...loading 'scripts/gfx_limbo.shader'
^1...loading 'scripts/gfx_misc.shader'
^1...loading 'scripts/goldrush.shader'
^1...loading 'scripts/icons.shader'
^1...loading 'scripts/levelshots.shader'
^1...loading 'scripts/lights.shader'
^1...loading 'scripts/liquids.shader'
^1...loading 'scripts/liquids_sd.shader'
^1...loading 'scripts/mapfx.shader'
^1...loading 'scripts/metals_sd.shader'
^1...loading 'scripts/metal_misc.shader'
^1...loading 'scripts/miltary_door.shader'
^1...loading 'scripts/miltary_trim.shader'
^1...loading 'scripts/miltary_wall.shader'
^1...loading 'scripts/models_ammo.shader'
^1...loading 'scripts/models_foliage.shader'
^1...loading 'scripts/models_furniture.shader'
^1...loading 'scripts/models_mapobjects.shader'
^1...loading 'scripts/models_multiplayer.shader'
^1...loading 'scripts/models_players.shader'
^1...loading 'scripts/models_shards.shader'
^1...loading 'scripts/models_weapons2.shader'
^1...loading 'scripts/mp_goldrush.shader'
^1...loading 'scripts/mp_guns.shader'
^1...loading 'scripts/mp_railgun.shader'
^1...loading 'scripts/mp_rocket.shader'
^1...loading 'scripts/mp_seawall.shader'
^1...loading 'scripts/mp_siwa.shader'
^1...loading 'scripts/mp_wurzburg.shader'
^1...loading 'scripts/props.shader'
^1...loading 'scripts/props_sd.shader'
^1...loading 'scripts/radar.shader'
^1...loading 'scripts/railgun_props.shader'
^1...loading 'scripts/railway_sd.shader'
^1...loading 'scripts/rock.shader'
^1...loading 'scripts/rubble.shader'
^1...loading 'scripts/seawall_wall.shader'
^1...loading 'scripts/sfx.shader'
^1...loading 'scripts/shadows.shader'
^1...loading 'scripts/siwa_fx_sd.shader'
^1...loading 'scripts/siwa_props_sd.shader'
^1...loading 'scripts/siwa_skyboxes_sd.shader'
^1...loading 'scripts/skies.shader'
^1...loading 'scripts/skies_sd.shader'
^1...loading 'scripts/snow.shader'
^1...loading 'scripts/snow_sd.shader'
^1...loading 'scripts/sprites.shader'
^1...loading 'scripts/stone.shader'
^1...loading 'scripts/swf.shader'
^1...loading 'scripts/temperate_sd.shader'
^1...loading 'scripts/terrain.shader'
^1...loading 'scripts/textures.shader'
^1...loading 'scripts/tobruk_wall_sd.shader'
^1...loading 'scripts/tobruk_windows_sd.shader'
^1...loading 'scripts/town_props.shader'
^1...loading 'scripts/town_roof.shader'
^1...loading 'scripts/town_wall.shader'
^1...loading 'scripts/town_window.shader'
^1...loading 'scripts/town_wood.shader'
^1...loading 'scripts/tree.shader'
^1...loading 'scripts/ui_assets.shader'
^1...loading 'scripts/ui_assets2.shader'
^1...loading 'scripts/village.shader'
^1...loading 'scripts/villa_sd.shader'
^1...loading 'scripts/wood.shader'
^1...loading 'scripts/xlab_door.shader'
^1...loading 'scripts/xlab_props.shader'
^1...loading 'scripts/xlab_wall.shader'
^1...loading 'scripts/_unsorted.shader'
Cvar_Set2: com_hunkused 2499968
Can't find gfx/misc/sunflare1.tga
Can't find shader.cache
Can't find model.cache
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: No such device
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/enso/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/enso/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/enso/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0x4a11abfc  
Sys_LoadDll(ui) succeeded!
Warning: cvar "cg_drawCrosshair" given initial values: "1" and "4"
Warning: cvar "bot_enable" given initial values: "0" and "1"
Cvar_Set2: ui_blackout 0
Cvar_Set2: ui_menuFiles ui/menus.txt
Parsing menu file: ui/global.menu
Parsing menu file: ui/main.menu
Parsing menu file: ui/profile.menu
Parsing menu file: ui/profile_create.menu
Parsing menu file: ui/profile_create_initial.menu
Parsing menu file: ui/profile_rename.menu
Parsing menu file: ui/profile_delete.menu
Parsing menu file: ui/profile_delete_error.menu
Parsing menu file: ui/profile_create_error.menu
Parsing menu file: ui/playonline.menu
Parsing menu file: ui/playonline_connecttoip.menu
Parsing menu file: ui/playonline_serverinfo.menu
Parsing menu file: ui/playonline_disablepb.menu
Parsing menu file: ui/playonline_enablepb.menu
Parsing menu file: ui/hostgame.menu
Parsing menu file: ui/hostgame_advanced.menu
Parsing menu file: ui/hostgame_advanced_default.menu
Parsing menu file: ui/hostgame_dedicated_warning.menu
Parsing menu file: ui/viewreplay.menu
Parsing menu file: ui/viewreplay_delete.menu
Parsing menu file: ui/options.menu
Parsing menu file: ui/options_customise_game.menu
Parsing menu file: ui/options_customise_hud.menu
Parsing menu file: ui/options_controls.menu
Parsing menu file: ui/options_controls_default.menu
Parsing menu file: ui/options_system.menu
Parsing menu file: ui/options_system_gamma.menu
Parsing menu file: ui/credits_splashdamage.menu
Parsing menu file: ui/credits_idsoftware.menu
Parsing menu file: ui/credits_activision.menu
Parsing menu file: ui/credits_additional.menu
Parsing menu file: ui/credits_quit.menu
Parsing menu file: ui/quit.menu
Parsing menu file: ui/popup_errormessage.menu
Parsing menu file: ui/popup_errormessage_pb.menu
Parsing menu file: ui/popup_hostgameerrormessage.menu
Parsing menu file: ui/popup_autoupdate.menu
Parsing menu file: ui/popup_password.menu
Parsing menu file: ui/vid_restart.menu
Parsing menu file: ui/vid_confirm.menu
Parsing menu file: ui/rec_restart.menu
Parsing menu file: ui/wm_quickmessage.menu
Parsing menu file: ui/wm_quickmessageAlt.menu
Parsing menu file: ui/wm_ftquickmessage.menu
Parsing menu file: ui/wm_ftquickmessageAlt.menu
Parsing menu file: ui/ingame_main.menu
Parsing menu file: ui/ingame_vote.menu
Parsing menu file: ui/ingame_vote_disabled.menu
Parsing menu file: ui/ingame_vote_misc.menu
Parsing menu file: ui/ingame_vote_misc_refrcon.menu
Parsing menu file: ui/ingame_vote_map.menu
Parsing menu file: ui/ingame_vote_players.menu
Parsing menu file: ui/ingame_vote_players_warn.menu
Parsing menu file: ui/ingame_serverinfo.menu
Parsing menu file: ui/ingame_disconnect.menu
Parsing menu file: ui/ingame_messagemode.menu
Parsing menu file: ui/ingame_tapout.menu
Parsing menu file: ui/ingame_tapoutlms.menu
UI menu load time = 3017 milli seconds
Cvar_Set2: ui_mousePitch 0
Cvar_Set2: s_volume 0.8
Cvar_Set2: s_musicvolume 0.5
Cvar_Set2: ui_TeamArenaFirstRun 1
Found high quality video and normal CPU
Cvar_Set2: com_recommended 1
Cvar_Set2: com_recommendedSet 1
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Cvar_Set2: net_port 27960
Hostname: localhost.localdomain
Alias: localhost
Alias: krystal
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
Cvar_Set2: developer 1
execing preset_normal.cfg
Cvar_Set2: r_subdivisions 12
r_subdivisions will be changed upon restarting.
Cvar_Set2: r_lodbias 0
Cvar_Set2: r_colorbits 0
Cvar_Set2: r_depthbits 24
r_depthbits will be changed upon restarting.
Cvar_Set2: r_picmip 1
Cvar_Set2: r_mode 4
Cvar_Set2: r_texturebits 32
r_texturebits will be changed upon restarting.
Cvar_Set2: r_ext_compressed_textures 1
Cvar_Set2: r_dynamiclight 1
Cvar_Set2: r_fastSky 0
Cvar_Set2: r_inGameVideo 1
Cvar_Set2: cg_shadows 1
Cvar_Set2: cg_brassTime 2500
Cvar_Set2: r_texturemode GL_LINEAR_MIPMAP_NEAREST
Cvar_Set2: r_detailtextures 0
r_detailtextures will be changed upon restarting.
RE_Shutdown( 1 )
DGA Mouse - Disabling DGA DirectVideo
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 135
  Minor opcode of failed request: 10
  Serial number of failed request: 289
Cvar_Set2: cl_paused 0
Cvar_Set2: com_hunkused 0
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
Cvar_Set2: cl_paused 0
----- R_Init -----
Cvar_Set2: r_detailtextures 0
Cvar_Set2: r_texturebits 32
Cvar_Set2: r_depthbits 24
Warning: cvar "r_uifullscreen" given initial values: "1" and "0"
Cvar_Set2: r_subdivisions 12
Cvar_Set2: r_flareFade 5
Cvar_Set2: com_hunkused 2022432
Cvar_Set2: r_glDriver libGL.so.1
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
X connection to :0.0 broken (explicit kill or server shutdown).


```

---

### Post by AmeTsuchi on 2005-03-14
Argh... sound mysteriously no longer works in any apps in Ubuntu... I'll look more into that.

Edit: actually it works in xine...

---

### Post by DDL on 2005-03-14
The following link may helps.

[http://ubuntuforums.org/showpost.php?p=35109&postcount=23](http://ubuntuforums.org/showpost.php?p=35109&postcount=23)

Indeed ET seems not working while using a virtual screen size higher than the deskstop screen size.


DDL

---

### Post by AmeTsuchi on 2005-03-14
Yes! That worked for me. Thanks! Now I just need to get audio working again.

---

### Post by DDL on 2005-03-15
[QUOTE=AmeTsuchi]Yes! That worked for me. Thanks! Now I just need to get audio working again.[/QUOTE]

Yelcome ;-)

Concerning the sound problem, have a look to following links:
[http://ubuntuforums.org/showthread.php?t=5246](http://ubuntuforums.org/showthread.php?t=5246)
or there
[http://ubuntuforums.org/showthread.php?t=17490&highlight=Enemy+sound](http://ubuntuforums.org/showthread.php?t=17490&highlight=Enemy+sound)
or there
[http://ubuntuforums.org/search.php?searchid=363753](http://ubuntuforums.org/search.php?searchid=363753)

DDL.

---


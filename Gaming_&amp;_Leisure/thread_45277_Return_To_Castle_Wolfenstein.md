---
title: "Return To Castle Wolfenstein"
date: 2005-06-29
forum: Gaming &amp; Leisure
---

### Post by DarkKnight on 2005-06-29
Ehlo peeps.

Does anyone have this up and running? 

Every time I go to play SP, it quits as soon as it is about to start a cut scene... On top of this, it has -zero- sound, I suspect it isn't playing nice with ALSA. 

Any idea's anyone? 

Here's the output: 
```
stevie@Steel:/usr/games/wolf$ wolfsp
Wolf 1.4 linux-i386 Nov  5 2002
----- FS_Startup -----
Current search path:
/home/stevie/.wolf/main
/usr/games/wolf/main/sp_pak4.pk3 (21 files)
/usr/games/wolf/main/sp_pak3.pk3 (14 files)
/usr/games/wolf/main/sp_pak2.pk3 (232 files)
/usr/games/wolf/main/sp_pak1.pk3 (1342 files)
/usr/games/wolf/main/pak0.pk3 (4775 files)
/usr/games/wolf/main

----------------------
6384 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing wolfconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Bypassing CD checks
----- Client Initialization -----
Cmd_AddCommand: map_restart already defined
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce4 Ti 4200 with AGP8X/AGP/SSE/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...using GL_NV_fog_distance
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 Ti 4200 with AGP8X/AGP/SSE/3DNOW!
GL_VERSION: 1.5.3 NVIDIA 71.74
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
picmip2: 2
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
ATI truform: disabled
NV distance fog: enabled
Fog Mode: GL_EYE_RADIAL_NV
Initializing Shaders
...loading 'scripts/ai.shader'
...loading 'scripts/alpha.shader'
...loading 'scripts/blacksmokeanim.shader'
...loading 'scripts/blacksmokeanimb.shader'
...loading 'scripts/characters.shader'
...loading 'scripts/clipboard.shader'
...loading 'scripts/common.shader'
...loading 'scripts/cursorhints.shader'
...loading 'scripts/decals.shader'
...loading 'scripts/eerie.shader'
...loading 'scripts/expblue.shader'
...loading 'scripts/explode1.shader'
...loading 'scripts/fijets.shader'
...loading 'scripts/firest.shader'
...loading 'scripts/flamethrower.shader'
...loading 'scripts/funnel.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/heat.shader'
...loading 'scripts/lights.shader'
...loading 'scripts/liquid.shader'
...loading 'scripts/maxx.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/metal.shader'
...loading 'scripts/models.shader'
...loading 'scripts/netest.shader'
...loading 'scripts/oldwolf.shader'
...loading 'scripts/organics.shader'
...loading 'scripts/particle.shader'
...loading 'scripts/q3view.shader'
...loading 'scripts/sfx.shader'
...loading 'scripts/signs.shader'
...loading 'scripts/skin.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/solo.shader'
...loading 'scripts/surfaces.shader'
...loading 'scripts/terrain.shader'
...loading 'scripts/test.shader'
...loading 'scripts/twiltb.shader'
...loading 'scripts/twiltb2.shader'
...loading 'scripts/ui.shader'
...loading 'scripts/ui_hud.shader'
...loading 'scripts/ui_notebook.shader'
...loading 'scripts/ui_wolf.shader'
...loading 'scripts/viewflames.shader'
...loading 'scripts/walls.shader'
...loading 'scripts/z_light.shader'
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/usr/games/wolf/main/uii386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaf435778
Sys_LoadDll(ui) succeeded!
Parsing menu file:ui/main.menu
r_rmse of 0.000000 has saved 12kb
Parsing menu file:ui/setup.menu
Parsing menu file:ui/controls.menu
Parsing menu file:ui/cdkey.menu
Parsing menu file:ui/system.menu
Parsing menu file:ui/options.menu
Parsing menu file:ui/credit.menu
r_rmse of 0.000000 has saved 204kb
r_rmse of 0.000000 has saved 252kb
r_rmse of 0.000000 has saved 264kb
Parsing menu file:ui/connect.menu
Parsing menu file:ui/quit.menu
Parsing menu file:ui/vid_restart.menu
Parsing menu file:ui/snd_restart.menu
Parsing menu file:ui/rec_restart.menu
Parsing menu file:ui/default.menu
Parsing menu file:ui/error.menu
Parsing menu file:ui/serverinfo.menu
Parsing menu file:ui/quitcredit.menu
Parsing menu file:ui/resetscore.menu
Parsing menu file:ui/buy_pop.menu
Parsing menu file:ui/multiplayer_pop.menu
Parsing menu file:ui/play.menu
Parsing menu file:ui/load.menu
Parsing menu file:ui/mods.menu
Parsing menu file:ui/briefing.menu
UI menu load time = 661 milli seconds
Parsing menu file:ui/ingame.menu
Parsing menu file:ui/ingame_controls.menu
Parsing menu file:ui/ingame_options.menu
Parsing menu file:ui/ingame_system.menu
Parsing menu file:ui/ingame_leave.menu
Parsing menu file:ui/ingame_player.menu
Parsing menu file:ui/ingame_load.menu
Parsing menu file:ui/ingame_save.menu
Parsing menu file:ui/in_vid_restart.menu
Parsing menu file:ui/in_snd_restart.menu
Parsing menu file:ui/in_rec_restart.menu
Parsing menu file:ui/notebook.menu
Parsing menu file:ui/clipboard.menu
Parsing menu file:ui/bookz.menu
Parsing menu file:ui/bookv.menu
Parsing menu file:ui/bookp.menu
Parsing menu file:ui/pregame.menu
Parsing menu file:ui/test.menu
Parsing menu file:ui/ingame_help.menu
UI menu load time = 681 milli seconds
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: Steel
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
sv_maxclients will be changed upon restarting.
------ Server Initialization ------
Server: cutscene1
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- FS_Startup -----
Current search path:
/home/stevie/.wolf/main
/usr/games/wolf/main/sp_pak4.pk3 (21 files)
/usr/games/wolf/main/sp_pak3.pk3 (14 files)
/usr/games/wolf/main/sp_pak2.pk3 (232 files)
/usr/games/wolf/main/sp_pak1.pk3 (1342 files)
/usr/games/wolf/main/pak0.pk3 (4775 files)
/usr/games/wolf/main

----------------------
12768 files in pk3 files
Sys_LoadDll(/usr/games/wolf/main/qagamei386.so)... ok
Sys_LoadDll(qagame) found **vmMain** at  0xae28232c
Sys_LoadDll(qagame) succeeded!
Gametype changed, clearing session data.
------- BotLib Initialization -------
------------ Map Loading ------------
trying to load maps/cutscene1_b0.aas
loaded maps/cutscene1_b0.aas
trying to load maps/cutscene1_b1.aas
loaded maps/cutscene1_b1.aas
-------------------------------------
AAS initialized.
AAS initialized.
-----------------------------------
RE_Shutdown( 0 )
----- R_Init -----

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 Ti 4200 with AGP8X/AGP/SSE/3DNOW!
GL_VERSION: 1.5.3 NVIDIA 71.74
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
picmip2: 2
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
ATI truform: disabled
NV distance fog: enabled
Fog Mode: GL_EYE_RADIAL_NV
Initializing Shaders
...loading 'scripts/ai.shader'
...loading 'scripts/alpha.shader'
...loading 'scripts/blacksmokeanim.shader'
...loading 'scripts/blacksmokeanimb.shader'
...loading 'scripts/characters.shader'
...loading 'scripts/clipboard.shader'
...loading 'scripts/common.shader'
...loading 'scripts/cursorhints.shader'
...loading 'scripts/decals.shader'
...loading 'scripts/eerie.shader'
...loading 'scripts/expblue.shader'
...loading 'scripts/explode1.shader'
...loading 'scripts/fijets.shader'
...loading 'scripts/firest.shader'
...loading 'scripts/flamethrower.shader'
...loading 'scripts/funnel.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/heat.shader'
...loading 'scripts/lights.shader'
...loading 'scripts/liquid.shader'
...loading 'scripts/maxx.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/metal.shader'
...loading 'scripts/models.shader'
...loading 'scripts/netest.shader'
...loading 'scripts/oldwolf.shader'
...loading 'scripts/organics.shader'
...loading 'scripts/particle.shader'
...loading 'scripts/q3view.shader'
...loading 'scripts/sfx.shader'
...loading 'scripts/signs.shader'
...loading 'scripts/skin.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/solo.shader'
...loading 'scripts/surfaces.shader'
...loading 'scripts/terrain.shader'
...loading 'scripts/test.shader'
...loading 'scripts/twiltb.shader'
...loading 'scripts/twiltb2.shader'
...loading 'scripts/ui.shader'
...loading 'scripts/ui_hud.shader'
...loading 'scripts/ui_notebook.shader'
...loading 'scripts/ui_wolf.shader'
...loading 'scripts/viewflames.shader'
...loading 'scripts/walls.shader'
...loading 'scripts/z_light.shader'
----- finished R_Init -----
Sys_LoadDll(/usr/games/wolf/main/uii386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xad831778
Sys_LoadDll(ui) succeeded!
Parsing menu file:ui/main.menu
r_rmse of 0.000000 has saved 276kb
Parsing menu file:ui/setup.menu
Parsing menu file:ui/controls.menu
Parsing menu file:ui/cdkey.menu
Parsing menu file:ui/system.menu
Parsing menu file:ui/options.menu
Parsing menu file:ui/credit.menu
r_rmse of 0.000000 has saved 468kb
r_rmse of 0.000000 has saved 516kb
r_rmse of 0.000000 has saved 528kb
Parsing menu file:ui/connect.menu
Parsing menu file:ui/quit.menu
Parsing menu file:ui/vid_restart.menu
Parsing menu file:ui/snd_restart.menu
Parsing menu file:ui/rec_restart.menu
Parsing menu file:ui/default.menu
Parsing menu file:ui/error.menu
Parsing menu file:ui/serverinfo.menu
Parsing menu file:ui/quitcredit.menu
Parsing menu file:ui/resetscore.menu
Parsing menu file:ui/buy_pop.menu
Parsing menu file:ui/multiplayer_pop.menu
Parsing menu file:ui/play.menu
Parsing menu file:ui/load.menu
Parsing menu file:ui/mods.menu
Parsing menu file:ui/briefing.menu
UI menu load time = 658 milli seconds
Parsing menu file:ui/ingame.menu
Parsing menu file:ui/ingame_controls.menu
Parsing menu file:ui/ingame_options.menu
Parsing menu file:ui/ingame_system.menu
Parsing menu file:ui/ingame_leave.menu
Parsing menu file:ui/ingame_player.menu
Parsing menu file:ui/ingame_load.menu
Parsing menu file:ui/ingame_save.menu
Parsing menu file:ui/in_vid_restart.menu
Parsing menu file:ui/in_snd_restart.menu
Parsing menu file:ui/in_rec_restart.menu
Parsing menu file:ui/notebook.menu
Parsing menu file:ui/clipboard.menu
Parsing menu file:ui/bookz.menu
Parsing menu file:ui/bookv.menu
Parsing menu file:ui/bookp.menu
Parsing menu file:ui/pregame.menu
Parsing menu file:ui/test.menu
Parsing menu file:ui/ingame_help.menu
UI menu load time = 676 milli seconds
Sys_LoadDll(/usr/games/wolf/main/cgamei386.so)... ok
Sys_LoadDll(cgame) found **vmMain** at  0xabc53264
Sys_LoadDll(cgame) succeeded!
LOADING... collision map
LOADING... sounds

.........................
Initializing Sound Scripts
...loading 'sound/scripts/cutscene1.sounds'
...loading 'sound/scripts/cutscene6.sounds'
...loading 'sound/scripts/cutscene9.sounds'
...loading 'sound/scripts/cutscene11.sounds'
...loading 'sound/scripts/cutscene14.sounds'
...loading 'sound/scripts/cutscene19.sounds'
...loading 'sound/scripts/escape1.sounds'
...loading 'sound/scripts/escape2.sounds'
...loading 'sound/scripts/tram.sounds'
...loading 'sound/scripts/village1.sounds'
...loading 'sound/scripts/crypt1.sounds'
...loading 'sound/scripts/crypt2.sounds'
...loading 'sound/scripts/church.sounds'
...loading 'sound/scripts/boss1.sounds'
...loading 'sound/scripts/forest.sounds'
...loading 'sound/scripts/rocket.sounds'
...loading 'sound/scripts/assault.sounds'
...loading 'sound/scripts/sfm.sounds'
...loading 'sound/scripts/factory.sounds'
...loading 'sound/scripts/trainyard.sounds'
...loading 'sound/scripts/swf.sounds'
...loading 'sound/scripts/norway.sounds'
...loading 'sound/scripts/xlabs.sounds'
...loading 'sound/scripts/boss2.sounds'
...loading 'sound/scripts/dam.sounds'
...loading 'sound/scripts/village2.sounds'
...loading 'sound/scripts/chateau.sounds'
...loading 'sound/scripts/dark.sounds'
...loading 'sound/scripts/castle.sounds'
...loading 'sound/scripts/end.sounds'
...loading 'sound/scripts/ai.sounds'
...loading 'sound/scripts/general.sounds'
...loading 'sound/scripts/combat.sounds'
...loading 'sound/scripts/movers.sounds'
done.
LOADING... graphics
LOADING... maps/cutscene1.bsp
stitched 0 LoD cracks
...loaded 2413 faces, 25 meshes, 147 trisurfs, 17 flares
LOADING... game media
LOADING...  - textures
r_rmse of 0.000000 has saved 720kb
r_rmse of 0.000000 has saved 768kb
r_rmse of 0.000000 has saved 780kb
LOADING...  - models
r_rmse of 0.000000 has saved 828kb
r_rmse of 0.000000 has saved 840kb
LOADING...  - weapons
LOADING...  - items
LOADING...  - inline models
LOADING...  - server models
LOADING...  - particles
r_rmse of 0.000000 has saved 852kb
LOADING...  - game media done
LOADING... flamechunks
LOADING... clients
LOADING... WolfPlayer
UI menu load time = 4 milli seconds
Shutdown tty console

```

I'm sorry, I didn't see the sound problem thread. 

It was all a sound problem. 
(Why can't more games play nice with ALSA?)

---

### Post by Bloke on 2005-06-29
I just now installed the game. 

01) wolf-linux-1.4-full.x86.run
02) copied .pak files from a windows installation
03) changed .pak files from read only to r/w (copied off a cd) - not that it would make any difference
04) started the game

---

### Post by DarkKnight on 2005-06-30
[QUOTE=Bloke]I just now installed the game. 

01) wolf-linux-1.4-full.x86.run
02) copied .pak files from a windows installation
03) changed .pak files from read only to r/w (copied off a cd) - not that it would make any difference
04) started the game[/QUOTE]
 How did you get sound working? o_O

And I used GOTY since I have GOTY.

---

### Post by Bloke on 2005-06-30
I have the latest Hoary install, and have not dorked with my audio drivers other that changing to alsa in multimedia selector.

FYI : My computer has a SBLive! soundcard, and kernel 2.6.10-5-686. The RTCW I run is **not** GOTY though.

---

### Post by davyike on 2007-11-30
For anyone that has been trying to get this going recently (i.e. Ubuntu 7.x), because I found a lot of different advice on the internet that didn't work. It used to work fine, maybe it was getting rid of my SoundBlaster and using onboard sound that killed it, rather than the newer Ubuntu. But either way I got this error when I tried to start it:

```

/dev/dsp: Input/output error
Could not mmap /dev/dsp

```

Then when trying to start the actual game it would crash out during the first cut scene. First thing I tried was going to System > Preferences > Sound. Under sounds, untick 'Enable software mixing'. This didn't help, but may have contributed to the second part working. Become root and type:

```

echo 'wolfsp.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss

```

Note that sudo didn't work, I had to 'sudo su'. Change wolfsp.x86 to wolfmp.x86 if that's what you're using. You can add this line to your /etc/rc.local file before the 'exit 0' to have it execute every logon (got this from [here]("https://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfensteinEnemyTerritory")).

Hope this helps someone.

---

### Post by fantapants on 2009-10-19
hey, how do you get the maps downloaded/working because whenever I go on a server it like never loads the maps, How can I fix this?
:(

---


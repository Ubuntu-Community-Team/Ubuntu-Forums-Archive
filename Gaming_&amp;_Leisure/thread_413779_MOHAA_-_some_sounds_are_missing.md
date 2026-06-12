---
title: "MOHAA - some sounds are missing"
date: 2007-04-19
forum: Gaming &amp; Leisure
---

### Post by escom on 2007-04-19
In game I can`t hear some sounds, for example: my shots are loud and clear, but I can`t hear commander talk, explosions are also silent or almost silent. In game audio settings output is set on "stereo speakers", and I can`t change this to another. Game was installed on M$, and then copied on to linux partition, and launched under linux(without WINE).Output from terminal:


--- Common Initialization ---
Medal of Honor Allied Assault 1.11 linux-i386 Sep  3 2004
----- FS_Startup -----
Current search path:
/home/dzidek/.mohaa/main
/home/dzidek/EA GAMES/mohaa/main
/home/dzidek/EA GAMES/mohaa/main/Pak5.pk3 (259 files)
/home/dzidek/EA GAMES/mohaa/main/Pak4.pk3 (593 files)
/home/dzidek/EA GAMES/mohaa/main/Pak3.pk3 (669 files)
/home/dzidek/EA GAMES/mohaa/main/Pak2.pk3 (4722 files)
/home/dzidek/EA GAMES/mohaa/main/Pak1.pk3 (772 files)
/home/dzidek/EA GAMES/mohaa/main/Pak0.pk3 (11175 files)

----------------------
18190 files in pk3 files
execing default.cfg
execing menu.cfg
execing newconfig.cfg
Config: unnamedsoldier.cfg
STUB: wtf in unix/linux_general_extras.c line 95.
STUB: wtf in unix/linux_general_extras.c line 101.
execing configs/unnamedsoldier.cfg
couldn't exec localized.cfg
execing autoexec.cfg
Unknown command "fov"
couldn't exec custom.cfg
You are now setup for easy mode.
----- Client Initialization -----
Called FadeSound with: 0.000000
----- Initializing Renderer ----
----- R_Init -----
...loading libGL.so: Initializing SDL OpenGL display
...setting mode 3: 640 480
Attempting 4/4/4 Color bits, 24 depth, 0 stencil display...
libGL warning: 3D driver claims to not support visual 0x4b
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
STUB: missing hardware detection in unix/linux_glimp_sdl.c line 985.
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array

GL_VENDOR: VA Linux Systems, Inc.
GL_RENDERER: Mesa DRI Rage 128 Pro 20051027 AGP 2x
GL_VERSION: 1.2 Mesa 6.5.1
GL_EXTENSIONS: [...omitted...]
GL_MAX_TEXTURE_SIZE: 1024
GL_MAX_ACTIVE_TEXTURES_ARB: 2

PIXELFORMAT: color(16-bits) Z(24-bit) stencil(0-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: software w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 16
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
Setting up Shaders
----- finished R_Init -----
------- profiling DrawBackground methods -------
glDrawPixels w/ BGR: 0 clocks
glDrawPixels w/ RGB: 0 clocks
glTexSubImage2D w/ BGR: 0 clocks
glTexSubImage2D w/ RGB: 0 clocks
DrawBackground: using glDrawPixels with BGR data
-------------------------------
Opening IP socket: localhost:12203
Hostname: dzidek.lwsk.net.pl
IP: 192.168.5.30
------- Sound Initialization (full) -------
OpenAL: Opening device {default}...
OpenAL: Device opened successfully.
OpenAL: Creating AL context...
OpenAL: Context created successfully.
AL_VENDOR: J. Valenzuela
AL_VERSION: 0.0.7
AL_RENDERER: Software
AL_EXTENSIONS: AL_LOKI_quadriphonic AL_LOKI_play_position AL_LOKI_WAVE_format AL_LOKI_IMA_ADPCM_format AL_LOKI_buffer_data_callback ALC_LOKI_audio_channel 
AL extension: Looking up required symbol "alutLoadMP3_LOKI"......found.
AL extension: Looking up symbol "alReverbScale_LOKI"......found.
AL extension: Looking up symbol "alReverbDelay_LOKI"......found.
Loading global/sound0.txt
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
----- Sound Info -----
device - {default}
reverb - OFF
samplebits - 16
speed - 11025
----------------------
------- Sound Initialization Complete ------- 109 ms
Setting up Shaders
Loading inventory...
----- Client Initialization Complete ----- 3256 ms
--- Common Initialization Complete --- 5276 ms
--- Localization: I see 0 localization files
--- Localization: reading file global/localization.txt
Loading Localization File global/localization.txt
Loaded 515 localization entries
------- Sound Initialization (full) -------
Cmd_AddCommand: play already defined
Cmd_AddCommand: soundlist already defined
Cmd_AddCommand: soundinfo already defined
Cmd_AddCommand: sounddump already defined
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
----- Sound Info -----
device - {default}
reverb - OFF
samplebits - 16
speed - 11025
----------------------
------- Sound Initialization Complete ------- 2 ms
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
FIXME: Allow reverb toggle at runtime in OpenAL code.
You are now setup for medium mode.
------ Server Initialization ------
Server: briefing/briefing1
Called FadeSound with: 0.000000
Called FadeSound with: 0.000000
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
Called FadeSound with: 0.000000
Setting up Shaders
UI_DrawConnect called
------ Unloading fgame.so ------
------- Attempting to load ./fgame.so -------
^~^~^ Add the following line to the *_precache.scr map script:
cache models/player/american_army.tik
------ Server Initialization Complete ------  3.33 seconds
Called FadeSound with: 0.000000
------- Sound Begin Registration -------
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
------- Sound Begin Registration Complete -------
------- Attempting to load ./cgame.so -------


-----------PARSING UBERSOUND------------
Any SetCurrentTiki errors means that tiki wasn't prefetched and tiki-specific sounds for it won't work. To fix prefetch the tiki. Ignore if you don't use that tiki on this level.
Parse/Load time: 0.283000 seconds.
-------------UBERSOUND DONE---------------



-----------PARSING UBERDIALOG------------
Any SetCurrentTiki errors means that tiki wasn't prefetched and tiki-specific sounds for it won't work. To fix prefetch the tiki. Ignore if you don't use that tiki on this level.
Parse/Load time: 0.371000 seconds.
-------------UBERDIALOG DONE---------------

stitched 0 LoD cracks
...loaded 6 faces, 0 meshes, 0 trisurfs, 0 flares
R_LevelMarksLoad: maps/briefing/briefing1.dcl not found
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_paper_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_paper_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_wood_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_wood_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_metal_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_metal_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_stone_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_stone_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_dirt_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_dirt_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_grass_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_grass_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_mud_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_mud_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_water_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_water_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_glass_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_glass_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_sand_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_sand_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_foliage_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_foliage_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_snow_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_snow_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_carpet_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_carpet_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_human_uniform_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_human_uniform_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/water_trail_bubble.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_base.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bazookaexp_base.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_paper.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_wood.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_metal.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_stone.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_dirt.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_grass.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_mud.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_water.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_gravel.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_sand.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_foliage.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_snow.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_carpet.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/water_ripple_still.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/water_ripple_moving.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_oil_leak_big.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_oil_leak_medium.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_oil_leak_small.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_oil_leak_splat.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_water_leak_big.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_water_leak_medium.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_water_leak_small.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_water_leak_splat.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_light_dust.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_heavy_dust.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_dirt.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_grass.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_mud.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_puddle.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_sand.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_snow.tik
------- Sound End Registration -------
------- Sound End Registration Complete -------
CL_EndRegistration:  0.07 seconds
CL_InitCGame:  3.00 seconds
Saving to briefing_briefing10011 (autosave)...
Game Saved
Done.
Called FadeSound with: 0.000000

ERROR PlaySound: snd_step_metal needs an alias in ubersound.scr or uberdialog.scr - Please fix.

ERROR PlaySound: snd_step_equipment needs an alias in ubersound.scr or uberdialog.scr - Please fix.
^~^~^ Add the following line to the *_precache.scr map script:
cache models/player/american_army_fps.tik

ERROR PlaySound: snd_landing_metal needs an alias in ubersound.scr or uberdialog.scr - Please fix.
------ Server Initialization ------
Server: m1l1
Called FadeSound with: 0.000000
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
Called FadeSound with: 0.000000
Setting up Shaders
UI_DrawConnect called
------ Unloading fgame.so ------
------- Attempting to load ./fgame.so -------
------ Server Initialization Complete ------ 13.37 seconds
Called FadeSound with: 0.000000
------- Sound Begin Registration -------
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
------- Sound Begin Registration Complete -------
------- Attempting to load ./cgame.so -------


-----------PARSING UBERSOUND------------
Any SetCurrentTiki errors means that tiki wasn't prefetched and tiki-specific sounds for it won't work. To fix prefetch the tiki. Ignore if you don't use that tiki on this level.
Parse/Load time: 5.206000 seconds.
-------------UBERSOUND DONE---------------



-----------PARSING UBERDIALOG------------
Any SetCurrentTiki errors means that tiki wasn't prefetched and tiki-specific sounds for it won't work. To fix prefetch the tiki. Ignore if you don't use that tiki on this level.
Parse/Load time: 1.338000 seconds.
-------------UBERDIALOG DONE---------------

stitched 48 LoD cracks
...loaded 3655 faces, 615 meshes, 0 trisurfs, 0 flares
Cmd_AddCommand: ter_restart already defined
R_LevelMarksLoad: maps/m1l1.dcl not found
------- Sound End Registration -------
------- Sound End Registration Complete -------
CL_EndRegistration:  0.56 seconds
CL_InitCGame: 16.61 seconds
Saving to m1l10019 (autosave)...
Game Saved
Done.
Called FadeSound with: 0.000000
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_loop_block in client/snd_openal_new.cpp line 3930.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
----- Server Shutdown -----
------ Unloading fgame.so ------
---------------------------
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
Called FadeSound with: 0.000000
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
----- CL_Shutdown -----
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
Called FadeSound with: 0.000000
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
------- Sound Shutdown (full) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
OpenAL: Destroying channels...
OpenAL: Channels destroyed successfully.
OpenAL: Destroying context...
OpenAL: Context destroyed successfully.
OpenAL: Closing device...
OpenAL: Device closed successfully.
------- Sound Shutdown Complete -------
RE_Shutdown( 1 )
-----------------------



Can anybody help me?Thank`s

---

### Post by etherealremnant on 2007-04-20
You would probably get more responses if you put the full game name in the title. I do not, however, know how to solve your problem.

---


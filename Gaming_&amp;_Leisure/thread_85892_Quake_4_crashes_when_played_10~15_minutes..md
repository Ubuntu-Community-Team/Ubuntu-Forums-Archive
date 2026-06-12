---
title: "Quake 4 crashes when played 10~15 minutes."
date: 2005-11-03
forum: Gaming &amp; Leisure
---

### Post by Yuma on 2005-11-03
Hello! (first post)

I have just bought my copy of Quake 4 and I have some troubles. I have experienced sound problems while using Alsa, but using +set s_driver oss I solved that problem. But I can't mend the crash when I play for some minutes. I mean, I play fine for a while, but suddently the screen goes black and returns me to the desktop. It works smooth in the graphics I'm using. I wonder if this happens to anyone else. Some of my specs,

GNU/Linux: Breezy 5.10
Kernel: 2.6.12-9-368
Graphics: Nvidia 6600GT 128
Sound: Via integrated VT8233 or equivalent
OpenGL: version string: 2.0.0 NVIDIA 76.67 (from glxinfo)
SDL: libsdl1.2-debian-alsa or libsdl1.2-debian-oss (I have experienced the same problem with both)

Thanks for the help!
--
Alejandro Cámara Iglesias

---

### Post by kidcharles on 2005-11-03
I've experienced occasional crashes of this nature myself.  My crashes completely freeze my system and require a hard reboot.  I experienced them with the repository drivers (7667). I've since gone to using older nvidia drivers (7174) and haven't experienced any crashes, but I haven't tested much. I got stuttering in opengl using 7667, much improved with 7174 drivers. I've gotten this same type of freeze-up in World of Warcraft using Cedega, I believe only with the 7667 drivers. I'm inclined to think it is the video drivers rather than some other cause. I have the same card (6600 GT).

*edited for clarity*

---

### Post by Yuma on 2005-11-04
Thanks for the help!

Well, I have installed the new version of the nvidia drivers. Now I have the 7676 version and I get the same error. I've got a segmentation fault each time it kicks me out the game. I think it has to be some incompatibility with the SDL libraries or something like that... If any ideas, please! I'll post the exit of the game, without setting the developer flag (you know "+set developer 1"), if someone thinks it would be of help if I write the whole console log with that flag, just say so.

#############################################

yuma@asimov:~$ quake4 +set s_driver oss
Quake4 Final V1.0.0.0 Build 2147.12 linux-x86 Oct 20 2005
found interface lo - loopback
found interface eth0 - 192.168.1.128/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x6f346a2
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
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /usr/local/games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /usr/local/games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /usr/local/games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Current search path:
/home/yuma/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/usr/local/games/quake4/q4base/zpak_italian.pk4 (3500 files)
/usr/local/games/quake4/q4base/zpak_french.pk4 (3462 files)
/usr/local/games/quake4/q4base/zpak_english.pk4 (3457 files)
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
/usr/local/games/quake4/q4base/game100.pk4 (2 files)
/usr/local/games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 59 loaded
426ms to load 1071k of material
247ms to load 43k of skin
257ms to load 716k of sound
30ms to load 1k of materialType
464ms to load 2078k of lipSync
165ms to load 105k of playback
2282ms to load 1665k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
632 strings read from strings/english_code.lang
1654 strings read from strings/english_guis.lang
5616 strings read from strings/english_lips.lang
6085 strings read from strings/english_maps.lang
632 strings read from strings/french_code.lang
1654 strings read from strings/french_guis.lang
5616 strings read from strings/french_lips.lang
6085 strings read from strings/french_maps.lang
632 strings read from strings/italian_code.lang
1654 strings read from strings/italian_guis.lang
5616 strings read from strings/italian_lips.lang
6085 strings read from strings/italian_maps.lang
632 strings read from strings/spanish_code.lang
1654 strings read from strings/spanish_guis.lang
5616 strings read from strings/spanish_lips.lang
6085 strings read from strings/spanish_maps.lang
Couldn't open journal files
execing default.cfg
"ALT" isn't a valid key
"CTRL" isn't a valid key
couldn't exec editor.cfg
execing Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother.
/dev/dsp - bit rate: 16, channels: 2, frequency: 44100
allocated a mix buffer of 16384 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
...using GL_ARB_texture_non_power_of_two
...using GL_NV_blend_square
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_draw_range_elements
...using GL_EXT_blend_minmax
...using GL_NV_float_buffer
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
...using GL_NV_register_combiners
...using NV_vertex_program
...using NV_fragment_program
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using GL_ARB_shader_objects
...using GL_ARB_fragment_shader
...using GL_ARB_vertex_shader
...using GL_ARB_shading_language_100
...using EXT_depth_bounds_test
---------------- R_NV20_Init ----------------
---------------------------------------------
----------------- R200_Init -----------------
Not available.
---------------- R_ARB2_Init ----------------
Available.
---------------------------------------------
------------ R_ReloadARBPrograms ------------
glprogs/test.vfp
glprogs/test.vfp
glprogs/interaction.vfp
glprogs/interaction.vfp
glprogs/bumpyEnvironment.vfp
glprogs/bumpyEnvironment.vfp
glprogs/ambientLight.vfp
glprogs/ambientLight.vfp
glprogs/SimpleInteraction.vfp
glprogs/SimpleInteraction.vfp
glprogs/shadow.vp
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp
glprogs/nv20_diffuseColor.vp
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
glprogs/arbVP_glasswarp.txt
glprogs/arbFP_glasswarp.txt
glprogs/arbVP_depth.vp
glprogs/arbFP_depth.fp
glprogs/arbFP_depth_coc.fp
---------------------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
reloading textures/common/debuggraph.
reloading makeIntensity( gfx/lights/squarelight1a).
reloading gfx/lights/squarelight1.
reloading gfx/lights/round.
reloading gfx/guis/mainmenu/splash.
reloading gfx/2d/bigchars.
reloading gfx/guis/soundmeter/audiobg.
reloading gfx/guis/white.
reloading gfx/guis/guicursor_arrow.
reloading gfx/guis/guicursor_hand.
reloading gfx/guis/scrollbarh.
reloading gfx/guis/scrollbarv.
reloading gfx/guis/scrollbar_thumb.
reloading gfx/guis/scrollbar_right.
reloading gfx/guis/scrollbar_left.
reloading gfx/guis/scrollbar_up.
reloading gfx/guis/scrollbar_down.
found DLL in pak file: /usr/local/games/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/yuma/.quake4/q4base/gamex86.so
enabled Flush-To-Zero mode
------------- Initializing Game -------------
gamename: baseQUAKE4-1
gamedate: Oct 19 2005
722ms to load 634k of entityDef
147ms to load 177k of articulatedFigure
Initializing event system
...527 event definitions
Initializing class hierarchy
...242 classes, 586024 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 1463.62 MHz
Compiled '/home/yuma/.quake4/q4base/scripts/main.script': 11731.9 ms
-------------- Compile stats ----------------

Memory usage:
     Strings: 54, 8464 bytes
  Statements: 84406, 1688120 bytes
   Functions: 3361, 380380 bytes
   Variables: 324172 bytes
    Mem used: 3531952 bytes
 Static data: 4948144 bytes
   Allocated: 6313652 bytes
 Thread size: 7072 bytes

...5 aas types
game initialized.
---------------------------------------------
Loading viseme file: annosoft
----------- Initializing Session ------------
----------------- BSE Init ------------------
--------- BSE Created Successfully ----------
WARNING: idChoiceWindow::InitVars: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_system_val' references undefined cvar 's_useOpenAL'
WARNING: idChoiceWindow::InitVars: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_device_val' references undefined cvar 's_deviceName'
WARNING: idChoiceWindow::InitVars: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_eax_val' references undefined cvar 's_useEAXReverb'
session initialized
---------------------------------------------
Opening IP socket: localhost:-1
------ Common Initialization Complete -------
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 9885
detecting video ram ( set sys_videoRam to force ) ..
found XNVCtrl extension 1.6
1464 MHz CPU
752 MB System Memory
128 MB Video Memory
Async thread started
guid set to IQoIy0H1OZE
idUsercmdGenLocal::MouseMove: Ignoring ridiculous mouse delta.
------------ Game Map Shutdown --------------
---------------------------------------------
Asset log: assetlogs/maps/game/hub2
WARNING: idChoiceWindow::InitVars: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_system_val' references undefined cvar 's_useOpenAL'
WARNING: idChoiceWindow::InitVars: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_device_val' references undefined cvar 's_deviceName'
WARNING: idChoiceWindow::InitVars: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_eax_val' references undefined cvar 's_useEAXReverb'
reloading guis/mainmenu.gui.
reloading guis/restart.gui.
reloading guis/gameover.gui.
reloading guis/msg.gui.
reloading guis/takeNotes2.gui.
reloading guis/takeNotes.gui.
reloading guis/takeNotesQA.gui.
reloading guis/editcvars.gui.
reloading guis/spawn.gui.
reloading guis/intro.gui.
reloading guis/netmenu.gui.
idUsercmdGenLocal::MouseMove: Ignoring ridiculous mouse delta.
------------ Map Initialization -------------
Map: game/hub2
---------- Game Map Init SaveGame -----------
collision data:
   596 models
 54480 vertices (1276 KB)
107868 edges (3792 KB)
 45119 polygons (3877 KB)
178391 polygon edges (696 KB)
  5494 brushes (257 KB)
 32978 brush planes (515 KB)
 32744 nodes (895 KB)
107208 polygon refs (837 KB)
 27032 brush refs (211 KB)
 40084 internal edges
  6042 sharp edges
     0 contained polygons removed
     0 polygons merged
 12360 KB total memory used
1400 msec to load collision data.
map bounds are (7472.0, 10688.0, 4600.0)
max clip sector is (0.0, 0.0, 0.0)
    9 KB passage memory used to build PVS
   11 msec to calculate PVS
   97 areas
  212 portals
   17 areas visible on average
    1 KB PVS data
[Load AAS]
loading maps/game/hub2.aas32
done loading maps/game/hub2.aas32 (size 1791120).
[Load AAS]
loading maps/game/hub2.aas48
done loading maps/game/hub2.aas48 (size 1622964).
[Load AAS]
loading maps/game/hub2.aas96
done loading maps/game/hub2.aas96 (size 133300).
[Load AAS]
loading maps/game/hub2.aas250
[Load AAS]
loading maps/game/hub2.aas128
glprogs/heatHazeWithMask.vfp
glprogs/heatHazeWithMask.vfp
glprogs/heatHaze.vfp
glprogs/heatHaze.vfp
removed 6 degenerate triangles
WARNING: Couldn't load sound 'vo_1_2_20_50_1.ogg' using default
--------------------------------------
-- idRenderModelManagerLocal::EndLevelLoad --
    0 models purged from previous level,  1082 models kept.
---------------------------------------------
----- idImageManagerLocal::EndLevelLoad -----
    0 purged from previous
  112 kept from previous
 1347 new loaded
all images loaded in  19.5 seconds
    0 deferred loading
---------------------------------------------
-------- idSoundCache::EndLevelLoad ---------
3.11 seconds to expand oggs
15836k referenced
    0k purged
---------------------------------------------
---------------------------------------------
 45355 msec to load game/hub2
idRenderWorld::GenerateAllInteractions, msec = 19, staticAllocCount = 0.
Saved 'Quick1'
Saved 'Quick2'
Saved 'Quick3'
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
------------ Game Map Shutdown --------------
---------------------------------------------
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()
Shutting down SDL subsystem
--------------- Game Shutdown ---------------
rvStatAllocator:  dump of usage stats
        1800 total bytes handed out in 90 requests
        begin game:      0;  end game:        0
        player hit:     90;  player kill:     0
        player death:    0;
        damage dealt:    0;  damage taken:    0
        stat team:       0
        flag capture:    0;
        flag drop:       0;  flag return:     0
------------ Game Map Shutdown --------------
---------------------------------------------
Shutdown event system
---------------------------------------------
shutdown terminal support


############################################

See you. And thanks again.

---


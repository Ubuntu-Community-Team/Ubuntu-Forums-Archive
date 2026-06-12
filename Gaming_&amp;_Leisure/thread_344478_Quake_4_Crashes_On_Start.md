---
title: "Quake 4 Crashes On Start"
date: 2007-01-23
forum: Gaming &amp; Leisure
---

### Post by janascii on 2007-01-23
I've tried installing quake 4 several times in Edgy with no success.  Each time I try to run quake the screen resolution begins to change like most full screen games do but then crashes and I am left with a useless X session and have to restart X.  I think I have followed every possible way to install the game.  

Here is the output I'm getting from the terminal.

```
Quake4 Final V1.3.0.2393 Build 2393.0 linux-x86 Aug  7 2006
found interface lo - loopback
found interface eth0 - 131.151.188.228/255.255.254.0
found interface vmnet1 - 172.16.198.1/255.255.255.0
found interface vmnet8 - 192.168.18.1/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0x1e246dd2
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x7d4d8d2a
Loaded pk4 /usr/local/games/quake4/q4base/game200.pk4 with checksum 0x46f04342
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
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /usr/local/games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /usr/local/games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /usr/local/games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Current search path:
/home/janascii/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/usr/local/games/quake4/q4base/zpak_italian.pk4 (3500 files)
/usr/local/games/quake4/q4base/zpak_french.pk4 (3462 files)
/usr/local/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/usr/local/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/usr/local/games/quake4/q4base/zpak_english.pk4 (3457 files)
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
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 64 loaded
WARNING: file materials/mappack1.mtr, line 175: material 'models/mapobjects/multiplayer/jump_pad/jump_pad_color' previously defined at materials/mapobjects_mp2.mtr:1
WARNING: file materials/mappack1.mtr, line 199: material 'models/mapobjects/multiplayer/jump_pad/jump_pad_color_glow' previously defined at materials/mapobjects_mp2.mtr:29
WARNING: file materials/mappack1.mtr, line 224: material 'models/mapobjects/multiplayer/acceleration_pad/acceleration_pad_color' previously defined at materials/mapobjects_mp2.mtr:53
WARNING: file materials/mappack1.mtr, line 242: material 'models/mapobjects/multiplayer/acceleration_pad/arrows_color' previously defined at materials/mapobjects_mp2.mtr:78
WARNING: file materials/stroyent_mp.mtr, line 10: material 'textures/stroyent/mp/stroy_pillar1_orange' previously defined at materials/mappack1.mtr:1
WARNING: file materials/stroyent_mp.mtr, line 18: material 'textures/stroyent/mp/stroy_pillar1_green' previously defined at materials/mappack1.mtr:12
WARNING: file materials/stroyent_mp.mtr, line 26: material 'textures/stroyent/mp/tun6_green' previously defined at materials/mappack1.mtr:20
WARNING: file materials/stroyent_mp.mtr, line 34: material 'textures/stroyent/mp/tun6small_green' previously defined at materials/mappack1.mtr:28
WARNING: file materials/stroyent_mp.mtr, line 42: material 'textures/stroyent/mp/tunbump_green' previously defined at materials/mappack1.mtr:36
WARNING: file materials/stroyent_mp.mtr, line 50: material 'textures/stroyent/mp/tunpipe_green' previously defined at materials/mappack1.mtr:44
WARNING: file materials/stroyent_mp.mtr, line 58: material 'textures/stroyent/mp/tunpipe_orange' previously defined at materials/mappack1.mtr:52
WARNING: file materials/stroyent_mp.mtr, line 66: material 'textures/stroyent/mp/tunpipe2_orange' previously defined at materials/mappack1.mtr:60
WARNING: file materials/stroyent_mp.mtr, line 74: material 'textures/stroyent/mp/tunpipe2_green' previously defined at materials/mappack1.mtr:68
WARNING: file materials/stroyent_mp.mtr, line 92: material 'textures/stroyent/mp/tunwall12_orange' previously defined at materials/mappack1.mtr:76
WARNING: file materials/stroyent_mp.mtr, line 100: material 'textures/stroyent/mp/tunwall12_green' previously defined at materials/mappack1.mtr:94
WARNING: file materials/stroyent_mp.mtr, line 108: material 'textures/stroyent/mp/tunwall15_orange' previously defined at materials/mappack1.mtr:102
WARNING: file materials/stroyent_mp.mtr, line 116: material 'textures/stroyent/mp/tunwall15_green' previously defined at materials/mappack1.mtr:110
WARNING: file materials/stroyent_mp.mtr, line 139: material 'textures/stroyent/mp/concrete09asmooth' previously defined at materials/mappack1.mtr:118
WARNING: file materials/stroyent_mp.mtr, line 140: material 'textures/stroyent/mp/concrete09smooth' previously defined at materials/mappack1.mtr:141
WARNING: file materials/stroyent_mp.mtr, line 141: material 'textures/stroyent/mp/concrete04smooth' previously defined at materials/mappack1.mtr:142
313ms to load 1125k of material
275ms to load 43k of skin
165ms to load 722k of sound
16ms to load 1k of materialType
406ms to load 2889k of lipSync
120ms to load 105k of playback
2242ms to load 1687k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
688 strings read from strings/english_code.lang
1776 strings read from strings/english_guis.lang
5738 strings read from strings/english_lips.lang
5741 strings read from strings/english_mappack.lang
6217 strings read from strings/english_maps.lang
632 strings read from strings/french_code.lang
1654 strings read from strings/french_guis.lang
5616 strings read from strings/french_lips.lang
5619 strings read from strings/french_mappack.lang
6088 strings read from strings/french_maps.lang
632 strings read from strings/italian_code.lang
1654 strings read from strings/italian_guis.lang
5616 strings read from strings/italian_lips.lang
5619 strings read from strings/italian_mappack.lang
6088 strings read from strings/italian_maps.lang
632 strings read from strings/spanish_code.lang
1654 strings read from strings/spanish_guis.lang
5616 strings read from strings/spanish_lips.lang
5619 strings read from strings/spanish_mappack.lang
6088 strings read from strings/spanish_maps.lang
Couldn't open journal files
execing default.cfg
"ALT" isn't a valid key
"CTRL" isn't a valid key
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
1280x1024 1280x960 1280x800 1280x768 1152x864 1152x768 1024x768 960x600 840x525 832x624 800x600 
800x512 720x450 640x512 640x480 640x400 640x384 576x432 576x384 512x384 416x312 
400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.11
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
---------------------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
reloading textures/common/debuggraph.
reloading makeIntensity( gfx/lights/squarelight1a).
reloading gfx/lights/squarelight1.
reloading gfx/lights/round.
reloading gfx/guis/mainmenu/splash.
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
reloading fonts/english/bigchars.
found DLL in pak file: /usr/local/games/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/janascii/.quake4/q4base/gamex86.so
WARNING: idFileSystemLocal::OpenFileRead: fs_caseSensitiveOS 1 could not open /home/janascii/.quake4/q4base/gamex86.so
Regenerated world, staticAllocCount = 0.
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
Sys_Error: could not create destination file /home/janascii/.quake4/q4base/gamex86.so


```

If it is any help..  I'm running Edgy with all the latest updates on a machine with an AMD Athlon 2800+, gig of ram, and an Nvidia 7300GT graphics card.  I know I have the right driver because Beryl and True Combat: Elite run without a hitch.

---

### Post by conjur3r on 2007-01-23
What are the permissions on /home/janascii/.quake4/q4base?  Make sure you have write access to everything in the .quake4 folder.

---

### Post by janascii on 2007-01-23
That was it.... apparently when I changed the parent folder... it didn't change the ones inside of it.  

Thanks

---


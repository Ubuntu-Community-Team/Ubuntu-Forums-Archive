---
title: "Quake 4 Fails To Run"
date: 2006-10-29
forum: Gaming &amp; Leisure
---

### Post by TigerWolf on 2006-10-29
Ive searched google but the results where of no help. All of the permissions should be set properly. Here is the console output:

```
Quake4 Final V1.3.0.2393 Build 2393.0 linux-x86 Aug  7 2006
found interface lo - loopback
found interface eth1 - 192.168.1.5/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/tigerwolf/quake4/q4base/game000.pk4 with checksum 0x1e246dd2
Loaded pk4 /home/tigerwolf/quake4/q4base/game100.pk4 with checksum 0x7d4d8d2a
Loaded pk4 /home/tigerwolf/quake4/q4base/game200.pk4 with checksum 0x46f04342
Loaded pk4 /home/tigerwolf/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /home/tigerwolf/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /home/tigerwolf/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /home/tigerwolf/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /home/tigerwolf/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /home/tigerwolf/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /home/tigerwolf/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /home/tigerwolf/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /home/tigerwolf/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /home/tigerwolf/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /home/tigerwolf/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /home/tigerwolf/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /home/tigerwolf/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /home/tigerwolf/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /home/tigerwolf/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /home/tigerwolf/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /home/tigerwolf/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /home/tigerwolf/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /home/tigerwolf/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /home/tigerwolf/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /home/tigerwolf/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /home/tigerwolf/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /home/tigerwolf/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Current search path:
/home/tigerwolf/.quake4/q4base
/home/tigerwolf/quake4/q4base
/home/tigerwolf/quake4/q4base/zpak_english_03.pk4 (4 files)
/home/tigerwolf/quake4/q4base/zpak_english_02.pk4 (21 files)
/home/tigerwolf/quake4/q4base/zpak_english_01.pk4 (1 files)
/home/tigerwolf/quake4/q4base/zpak_english.pk4 (3457 files)
/home/tigerwolf/quake4/q4base/pak020.pk4 (11 files)
/home/tigerwolf/quake4/q4base/pak019.pk4 (1206 files)
/home/tigerwolf/quake4/q4base/pak018.pk4 (3 files)
/home/tigerwolf/quake4/q4base/pak017.pk4 (3 files)
/home/tigerwolf/quake4/q4base/pak016.pk4 (193 files)
/home/tigerwolf/quake4/q4base/pak015.pk4 (34 files)
/home/tigerwolf/quake4/q4base/pak014.pk4 (552 files)
/home/tigerwolf/quake4/q4base/pak013.pk4 (239 files)
/home/tigerwolf/quake4/q4base/pak012.pk4 (1081 files)
/home/tigerwolf/quake4/q4base/pak011.pk4 (5620 files)
/home/tigerwolf/quake4/q4base/pak010.pk4 (5539 files)
/home/tigerwolf/quake4/q4base/pak009.pk4 (1284 files)
/home/tigerwolf/quake4/q4base/pak008.pk4 (1289 files)
/home/tigerwolf/quake4/q4base/pak007.pk4 (1330 files)
/home/tigerwolf/quake4/q4base/pak006.pk4 (1343 files)
/home/tigerwolf/quake4/q4base/pak005.pk4 (1395 files)
/home/tigerwolf/quake4/q4base/pak004.pk4 (2249 files)
/home/tigerwolf/quake4/q4base/pak003.pk4 (1281 files)
/home/tigerwolf/quake4/q4base/pak002.pk4 (313 files)
/home/tigerwolf/quake4/q4base/game200.pk4 (9 files)
/home/tigerwolf/quake4/q4base/game100.pk4 (2 files)
/home/tigerwolf/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 55 loaded
WARNING: file materials/hardwareshaders.mtr, line 239: Guide name 'depthSpriteAlphaBlend' not found in 'gfx/effects/smoke/smoke_alpha_depth'
WARNING: file materials/hardwareshaders.mtr, line 240: expected '{' but found ','
WARNING: file materials/hardwareshaders.mtr, line 241: expected '{' but found ')'
WARNING: file materials/hardwareshaders.mtr, line 243: Guide name 'depthSpriteAlphaBlend' not found in 'gfx/effects/smoke/cloud_alpha_depth'
WARNING: file materials/hardwareshaders.mtr, line 244: expected '{' but found ','
WARNING: file materials/hardwareshaders.mtr, line 245: expected '{' but found ')'
WARNING: file materials/hardwareshaders.mtr, line 247: Guide name 'depthSpriteAlphaBlend' not found in 'gfx/effects/smoke/cloud_alpha_depth2'
WARNING: file materials/hardwareshaders.mtr, line 248: expected '{' but found ','
WARNING: file materials/hardwareshaders.mtr, line 248: material 'gfx/effects/depth/cloud_alpha_depth.tga' previously defined at materials/hardwareshaders.mtr:243
WARNING: file materials/hardwareshaders.mtr, line 249: expected '{' but found ')'
WARNING: file materials/hardwareshaders.mtr, line 249: material '120' previously defined at materials/hardwareshaders.mtr:240
WARNING: file materials/hardwareshaders.mtr, line 251: Guide name 'depthSpriteAdditive' not found in 'gfx/effects/weapons/muzzleflash2_depth'
WARNING: file materials/hardwareshaders.mtr, line 252: expected '{' but found ','
WARNING: file materials/hardwareshaders.mtr, line 253: expected '{' but found ')'
WARNING: file materials/hardwareshaders.mtr, line 255: Guide name 'depthSpriteAlphaBlend' not found in 'gfx/effects/particles_shapes/dirt3_depth'
WARNING: file materials/hardwareshaders.mtr, line 256: expected '{' but found ','
WARNING: file materials/hardwareshaders.mtr, line 257: expected '{' but found ')'
WARNING: file materials/hardwareshaders.mtr, line 259: Guide name 'depthSpriteAlphaBlend' not found in 'gfx/effects/particles_shapes/dirt2_depth'
WARNING: file materials/hardwareshaders.mtr, line 260: expected '{' but found ','
WARNING: file materials/hardwareshaders.mtr, line 261: expected '{' but found ')'
WARNING: file materials/hardwareshaders.mtr, line 263: Guide name 'depthSpriteAlphaBlend' not found in 'gfx/effects/smoke/steam_alpha_depth'
WARNING: file materials/hardwareshaders.mtr, line 264: expected '{' but found ','
WARNING: file materials/hardwareshaders.mtr, line 265: expected '{' but found ')'
WARNING: file materials/hardwareshaders.mtr, line 265: material '40' previously defined at materials/hardwareshaders.mtr:252
WARNING: file materials/hardwareshaders.mtr, line 267: Guide name 'depthSpriteAlphaBlend' not found in 'gfx/effects/smoke/steam_white_depth'
WARNING: file materials/hardwareshaders.mtr, line 268: expected '{' but found ','
WARNING: file materials/hardwareshaders.mtr, line 269: expected '{' but found ')'
WARNING: file materials/hardwareshaders.mtr, line 269: material '60' previously defined at materials/hardwareshaders.mtr:244
WARNING: file materials/hardwareshaders.mtr, line 271: Guide name 'depthSpriteAdditive' not found in 'gfx/effects/energy_sparks/bombard_focus_depth'
WARNING: file materials/hardwareshaders.mtr, line 272: expected '{' but found ','
WARNING: file materials/hardwareshaders.mtr, line 273: expected '{' but found ')'
WARNING: file materials/hardwareshaders.mtr, line 273: material '100' previously defined at materials/hardwareshaders.mtr:260
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
WARNING: file materials/test.mtr, line 1404: Guide name 'refractiveGlass' not found in 'models/mapobjects/test/sphere'
250ms to load 1123k of material
59ms to load 43k of skin
141ms to load 722k of sound
3ms to load 1k of materialType
342ms to load 2889k of lipSync
58ms to load 105k of playback
21ms to load 22k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
WARNING: Couldn't load image: makeIntensity( gfx/lights/squarelight1a)
WARNING: Couldn't load image: gfx/lights/squarelight1
WARNING: Couldn't load image: gfx/lights/squarelight1
WARNING: Couldn't load image: gfx/lights/round
WARNING: Couldn't load image: gfx/guis/mainmenu/splash
WARNING: Couldn't load image: gfx/guis/soundmeter/audiobg
WARNING: Couldn't load image: gfx/guis/white
WARNING: Couldn't load image: gfx/guis/guicursor_arrow
WARNING: Couldn't load image: gfx/guis/guicursor_hand
WARNING: Couldn't load image: gfx/guis/scrollbarh
WARNING: Couldn't load image: gfx/guis/scrollbarv
WARNING: Couldn't load image: gfx/guis/scrollbar_thumb
WARNING: Couldn't load image: gfx/guis/scrollbar_right
WARNING: Couldn't load image: gfx/guis/scrollbar_left
WARNING: Couldn't load image: gfx/guis/scrollbar_up
WARNING: Couldn't load image: gfx/guis/scrollbar_down
Spawning back end thread...
...ok
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' without VO
.... found additional language 'italian' without VO
.... found additional language 'spanish' without VO
688 strings read from strings/english_code.lang
1776 strings read from strings/english_guis.lang
5738 strings read from strings/english_lips.lang
5741 strings read from strings/english_mappack.lang
6217 strings read from strings/english_maps.lang
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
1280x1024 1280x960 1152x864 1024x768 832x624 800x600 640x480 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.11
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
glprogs/test.vfp: File not found
glprogs/test.vfp: File not found
glprogs/interaction.vfp: File not found
glprogs/interaction.vfp: File not found
glprogs/bumpyEnvironment.vfp: File not found
glprogs/bumpyEnvironment.vfp: File not found
glprogs/ambientLight.vfp: File not found
glprogs/ambientLight.vfp: File not found
glprogs/SimpleInteraction.vfp: File not found
glprogs/SimpleInteraction.vfp: File not found
glprogs/shadow.vp: File not found
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp: File not found
glprogs/nv20_diffuseColor.vp: File not found
glprogs/nv20_specularColor.vp: File not found
glprogs/nv20_diffuseAndSpecularColor.vp: File not found
glprogs/environment.vfp: File not found
glprogs/environment.vfp: File not found
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
---------------------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
reloading textures/common/debuggraph.
reloading makeIntensity( gfx/lights/squarelight1a).
WARNING: Couldn't load image: makeIntensity( gfx/lights/squarelight1a)
reloading gfx/lights/squarelight1.
WARNING: Couldn't load image: gfx/lights/squarelight1
reloading gfx/lights/squarelight1.
WARNING: Couldn't load image: gfx/lights/squarelight1
reloading gfx/lights/round.
WARNING: Couldn't load image: gfx/lights/round
reloading gfx/guis/mainmenu/splash.
WARNING: Couldn't load image: gfx/guis/mainmenu/splash
reloading gfx/guis/soundmeter/audiobg.
WARNING: Couldn't load image: gfx/guis/soundmeter/audiobg
reloading gfx/guis/white.
WARNING: Couldn't load image: gfx/guis/white
reloading gfx/guis/guicursor_arrow.
WARNING: Couldn't load image: gfx/guis/guicursor_arrow
reloading gfx/guis/guicursor_hand.
WARNING: Couldn't load image: gfx/guis/guicursor_hand
reloading gfx/guis/scrollbarh.
WARNING: Couldn't load image: gfx/guis/scrollbarh
reloading gfx/guis/scrollbarv.
WARNING: Couldn't load image: gfx/guis/scrollbarv
reloading gfx/guis/scrollbar_thumb.
WARNING: Couldn't load image: gfx/guis/scrollbar_thumb
reloading gfx/guis/scrollbar_right.
WARNING: Couldn't load image: gfx/guis/scrollbar_right
reloading gfx/guis/scrollbar_left.
WARNING: Couldn't load image: gfx/guis/scrollbar_left
reloading gfx/guis/scrollbar_up.
WARNING: Couldn't load image: gfx/guis/scrollbar_up
reloading gfx/guis/scrollbar_down.
WARNING: Couldn't load image: gfx/guis/scrollbar_down
reloading fonts/english/bigchars.
Could not register font fonts/chain [fonts/english/chain]
found DLL in pak file: /home/tigerwolf/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/tigerwolf/.quake4/q4base/gamex86.so
enabled Flush-To-Zero mode
------------- Initializing Game -------------
gamename: baseQUAKE4-1
gamedate: Jul 21 2006
60ms to load 117k of entityDef
3ms to load 0k of articulatedFigure
Initializing event system
...531 event definitions
Initializing class hierarchy
...247 classes, 598968 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 2009.44 MHz
Compiled '/home/tigerwolf/.quake4/q4base/scripts/main.script': 3398.0 ms
-------------- Compile stats ----------------

Memory usage:
     Strings: 54, 8464 bytes
  Statements: 84435, 1688700 bytes
   Functions: 3361, 380380 bytes
   Variables: 324172 bytes
    Mem used: 3532564 bytes
 Static data: 4948144 bytes
   Allocated: 6313684 bytes
 Thread size: 7072 bytes

TODO: Sys_SetClipboardData
------------ Game Map Shutdown --------------
---------------------------------------------
********************
ERROR: Unable to find entityDef for 'aas_types'
********************
Sys_Error: Error during initialization

```

---

### Post by TigerWolf on 2006-10-30
anyone?

---

### Post by tommcd on 2006-10-30
Did yo copy all the *.pk4 files from the CDs? If not, use this command:
sudo cp /cdrom/Setup/Data/base/*.pk4 /usr/local/games/quake4/base/
If you have trouble accessing the files on CDs 2-4, first unmount them, then mount them using the -o norock extension. For example:
sudo mount -o norock /dev/hdc
[http://zerowing.idsoftware.com/linux/quake4/#head-55969ff8b38fad088ee915b4e7da3480efcf5046](http://zerowing.idsoftware.com/linux/quake4/#head-55969ff8b38fad088ee915b4e7da3480efcf5046)
From what I have read, if you try to launch the game after you type in the CD key it screws up the file permissions, and you will have to launch the game with sudo (I made that mistake, and I had to chmod 2 files in the .quake4 folder to make it work without sudo).
Can you launch the game with sudo? I dont recognize the errors from your post. Sorry if this seems redundant, but I thought I would reply with how I did it.

---

### Post by TigerWolf on 2006-10-30
Ive copied the pk4 files. They seem to be fine.
My permissions are as follows:

> tigerwolf@tigerwolf-desktop:/media/hdb2/games/quake4$ ls -l
total 23192
drwxr-xr-x 7 tigerwolf tigerwolf    4096 2006-10-29 06:13 Docs
-rwxr-xr-x 1 tigerwolf tigerwolf  214919 2006-10-29 06:13 libgcc_s.so.1
-rwxr-xr-x 1 tigerwolf tigerwolf 3326045 2006-10-29 06:13 libSDL-1.2.id.so.0
-rwxr-xr-x 1 tigerwolf tigerwolf 4043221 2006-10-29 06:13 libstdc++.so.6
-rw-r--r-- 1 tigerwolf tigerwolf   18903 2006-10-29 06:13 License.txt
-rw-r--r-- 1 tigerwolf tigerwolf     271 2006-10-29 06:13 openurl.sh
drwxr-xr-x 3 tigerwolf tigerwolf    4096 2006-10-29 06:13 pb
drwxr-xr-x 3 tigerwolf tigerwolf    4096 2006-10-31 09:58 q4base
-rwxr-xr-x 1 tigerwolf tigerwolf 5149908 2006-10-29 06:13 q4ded.x86
-rw-r--r-- 1 tigerwolf tigerwolf    6966 2006-10-29 06:13 q4icon.bmp
-rwxr-xr-x 1 tigerwolf tigerwolf     143 2006-10-29 06:13 quake4
-rwxr-xr-x 1 tigerwolf tigerwolf     143 2006-10-29 06:13 quake4-dedicated
-rwxr-xr-x 1 tigerwolf tigerwolf     143 2006-10-29 06:13 quake4-smp
-rwxr-xr-x 1 tigerwolf tigerwolf 5421624 2006-10-29 06:13 quake4smp.x86
-rwxr-xr-x 1 tigerwolf tigerwolf 5416184 2006-10-29 06:13 quake4.x86
-rw-r--r-- 1 tigerwolf tigerwolf    3101 2006-10-29 06:13 README
-rw-r--r-- 1 tigerwolf tigerwolf   32170 2006-10-29 06:13 README-1.3.htm
-rw-r--r-- 1 tigerwolf tigerwolf   10148 2006-10-29 06:13 sdl.patch.1.2.10
-rw-r--r-- 1 tigerwolf tigerwolf       9 2006-10-29 06:13 version.info



> tigerwolf@tigerwolf-desktop:/media/hdb2/games/quake4/q4base$ ls -l
total 207364
-rw-r--r-- 1 tigerwolf tigerwolf      2740 2006-10-29 06:13 arena_ctf.cfg
-rw-r--r-- 1 tigerwolf tigerwolf      2721 2006-10-29 06:13 ctf.cfg
drwxr-xr-x 2 tigerwolf tigerwolf      4096 2006-10-29 06:13 demos
-rw-r--r-- 1 tigerwolf tigerwolf      2775 2006-10-29 06:13 dm.cfg
-rw-r--r-- 1 tigerwolf tigerwolf   1706451 2006-10-29 06:13 game000.pk4
-rw-r--r-- 1 tigerwolf tigerwolf   2325248 2006-10-29 06:13 game100.pk4
-rw-r--r-- 1 tigerwolf tigerwolf   5818299 2006-10-29 06:13 game200.pk4
-rw-r--r-- 1 tigerwolf tigerwolf      4568 2006-10-29 06:13 mapcycle-mp1.scriptcfg
-rw-r--r-- 1 tigerwolf tigerwolf      5102 2006-10-29 06:13 mapcycle-mp2.scriptcfg
-rw-r--r-- 1 tigerwolf tigerwolf      6949 2006-10-29 06:13 mapcycle-mp3.scriptcfg
-rw-r--r-- 1 tigerwolf tigerwolf      3990 2006-10-29 06:13 mapcycle.scriptcfg
-rw-r--r-- 1 tigerwolf tigerwolf  17391934 2006-10-29 06:13 pak013.pk4
-rw-r--r-- 1 tigerwolf tigerwolf  21404183 2006-10-29 06:13 pak014.pk4
-rw-r--r-- 1 tigerwolf tigerwolf    512986 2006-10-29 06:13 pak015.pk4
-rw-r--r-- 1 tigerwolf tigerwolf  45360121 2006-10-29 06:13 pak016.pk4
-rw-r--r-- 1 tigerwolf tigerwolf     17759 2006-10-29 06:13 pak017.pk4
-rw-r--r-- 1 tigerwolf tigerwolf     80946 2006-10-29 06:13 pak018.pk4
-rw-r--r-- 1 tigerwolf tigerwolf 116026927 2006-10-29 06:13 pak019.pk4
-rw-r--r-- 1 tigerwolf tigerwolf     32710 2006-10-29 06:13 pak020.pk4
-rwxrwxrwx 1 tigerwolf tigerwolf        26 2005-12-15 18:30 quake4key
-rw-r--r-- 1 tigerwolf tigerwolf      2799 2006-10-29 06:13 teamdm.cfg
-rw-r--r-- 1 tigerwolf tigerwolf      2950 2006-10-29 06:13 tourney.cfg
-rw-r--r-- 1 tigerwolf tigerwolf     23713 2006-10-29 06:13 zpak_czech_01.pk4.off
-rw-r--r-- 1 tigerwolf tigerwolf      7885 2006-10-29 06:13 zpak_english_01.pk4
-rw-r--r-- 1 tigerwolf tigerwolf    229965 2006-10-29 06:13 zpak_english_02.pk4
-rw-r--r-- 1 tigerwolf tigerwolf     29317 2006-10-29 06:13 zpak_english_03.pk4
-rw-r--r-- 1 tigerwolf tigerwolf      8636 2006-10-29 06:13 zpak_french_01.pk4.off
-rw-r--r-- 1 tigerwolf tigerwolf    287505 2006-10-29 06:13 zpak_french_02.pk4.off
-rw-r--r-- 1 tigerwolf tigerwolf     23865 2006-10-29 06:13 zpak_french_03.pk4.off
-rw-r--r-- 1 tigerwolf tigerwolf      8422 2006-10-29 06:13 zpak_italian_01.pk4.off
-rw-r--r-- 1 tigerwolf tigerwolf    218076 2006-10-29 06:13 zpak_italian_02.pk4.off
-rw-r--r-- 1 tigerwolf tigerwolf     23786 2006-10-29 06:13 zpak_italian_03.pk4.off
-rw-r--r-- 1 tigerwolf tigerwolf     25044 2006-10-29 06:13 zpak_polish_01.pk4.off
-rw-r--r-- 1 tigerwolf tigerwolf    133982 2006-10-29 06:13 zpak_russian_01.pk4.off
-rw-r--r-- 1 tigerwolf tigerwolf      8758 2006-10-29 06:13 zpak_spanish_01.pk4.off
-rw-r--r-- 1 tigerwolf tigerwolf    227372 2006-10-29 06:13 zpak_spanish_02.pk4.off
-rw-r--r-- 1 tigerwolf tigerwolf     24106 2006-10-29 06:13 zpak_spanish_03.pk4.off


---

### Post by tinkernub on 2006-10-30
I am having this same problem, I didn't type the CD key in after launching the game either.



[http://www.wulfram.com?mkid=892](http://www.wulfram.com?mkid=892)

---

### Post by TigerWolf on 2006-10-30
None of the suggested fixes help at all. I have no idea what the problem is. I doesnt work with sudo at all - same error.

---

### Post by dmn_clown on 2006-10-30
It looks like you are missing pak001.pk4.

---

### Post by TigerWolf on 2006-10-31
I looked in the directory and it isnt missing at all.

---

### Post by dmn_clown on 2006-10-31
But when you try to start the game pak001.pk4 is not being called as evidenced here

```
Loaded pk4 /home/tigerwolf/quake4/q4base/game200.pk4 with checksum 0x46f04342
Loaded pk4 /home/tigerwolf/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
```

It skipped completely over pak001.pk4.

As you say it is in the directory then it is either a bug in Q4

or

a permissions issue.  I would say that it is a permissions issue with pak001.pk4.  What is happening is that the game engine is trying to find the first level that is contained in that particular pk4 and then whigs out when it doesn't find it.

```
********************
ERROR: Unable to find entityDef for 'aas_types'
********************
```

It can't find the entity definition for the aas_types, essentially it can't find the ai for all of the strog that are seeking to stop you from invading their home planet in your imperialistic goals of universal domination ;)

---

### Post by TigerWolf on 2006-11-03
Thats extremely wierd -

-rwxrwxrwx 1 tigerwolf tigerwolf  55549952 2006-10-29 22:00 pak001.pk4

BTW: YAY! 100 posts

---

### Post by dmn_clown on 2006-11-03
> **TigerWolf said:**
> Thats extremely wierd -

-rwxrwxrwx 1 tigerwolf tigerwolf  55549952 2006-10-29 22:00 pak001.pk4

BTW: YAY! 100 posts

That is weird.  I guess you could always try deleting your .quake4 directory if that doesn't fix it, then delete the game, recopy the files from the CD's/DVD and re-run the installer.

Something has got to fix that...

---

### Post by robert@debian on 2006-12-14
Well I'm getting the same error. I also checked the md5sum's just to be sure.
Furthermore, my screen gets black a sec and I right back at the logon screen.
This just with my new Computer, no probs with the old one. 
I've also tried point release 1.3 and 1.3.2 doesn't solve it though.

---

### Post by adrenaline_nz on 2007-05-05
I'm getting the same error as the original poster, has anyone got a fix for this?

Running Fiesty.

Thanks

---


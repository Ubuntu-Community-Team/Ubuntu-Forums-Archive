---
title: "Quake 4 crashing on start."
date: 2007-02-08
forum: Gaming &amp; Leisure
---

### Post by andy- on 2007-02-08
Used idSoftware installer, ran the game after install and I get this:

> andy@home:~$ sudo quake4
Password:
Quake4 Final V1.3.0.2393 Build 2393.0 linux-x86 Aug  7 2006
found interface lo - loopback
found interface eth0 - 192.168.1.69/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0x1e246dd2
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x7d4d8d2a
Loaded pk4 /usr/local/games/quake4/q4base/game200.pk4 with checksum 0x46f04342
Loaded pk4 /usr/local/games/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /usr/local/games/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /usr/local/games/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /usr/local/games/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /usr/local/games/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /usr/local/games/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /usr/local/games/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /usr/local/games/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Current search path:
/home/andy/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/usr/local/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/usr/local/games/quake4/q4base/pak020.pk4 (11 files)
/usr/local/games/quake4/q4base/pak019.pk4 (1206 files)
/usr/local/games/quake4/q4base/pak018.pk4 (3 files)
/usr/local/games/quake4/q4base/pak017.pk4 (3 files)
/usr/local/games/quake4/q4base/pak016.pk4 (193 files)
/usr/local/games/quake4/q4base/pak015.pk4 (34 files)
/usr/local/games/quake4/q4base/pak014.pk4 (552 files)
/usr/local/games/quake4/q4base/pak013.pk4 (239 files)
/usr/local/games/quake4/q4base/game200.pk4 (9 files)
/usr/local/games/quake4/q4base/game100.pk4 (2 files)
/usr/local/games/quake4/q4base/game000.pk4 (2 files)
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
143ms to load 243k of material
2ms to load 4k of skin
143ms to load 378k of sound
1ms to load 0k of materialType
411ms to load 2889k of lipSync
1ms to load 0k of playback
9ms to load 22k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
WARNING: Invalid folder for map 'lights/defaultpointlight'
WARNING: Couldn't load image: lights/defaultpointlight
WARNING: Invalid folder for map 'lights/defaultprojectedlight'
WARNING: Couldn't load image: lights/defaultprojectedlight
WARNING: Invalid folder for map 'lights/muzzleflash'
WARNING: Couldn't load image: lights/muzzleflash
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
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' without VO
.... found additional language 'italian' without VO
.... found additional language 'spanish' without VO
688 strings read from strings/english_code.lang
1776 strings read from strings/english_guis.lang
1779 strings read from strings/english_mappack.lang
2255 strings read from strings/english_maps.lang
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
1280x1024 1280x1024 1280x1024 1280x720 1152x864 1152x864 1024x768 1024x768 1024x768 1024x768 1024x768
1024x768 960x720 864x648 856x480 800x600 800x600 800x600 800x600 800x600 800x600
800x600 800x600 800x600 720x480 704x480 640x480 640x480 640x480 640x480 640x480
640x480 640x480 640x400 640x400 512x384 512x384 400x150 400x150 320x120 320x120
320x100 320x100
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
1 pixels multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.10
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 15052 frames ( 60208 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
...using GL_NV_blend_square
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_draw_range_elements
...using GL_EXT_blend_minmax
X..GL_NV_float_buffer not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
X..NV_vertex_program not found
X..GL_EXT_stencil_two_side not found
...using GL_ATI_separate_stencil
...using GL_ATI_fragment_shader
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using GL_ARB_shader_objects
...using GL_ARB_fragment_shader
...using GL_ARB_vertex_shader
...using GL_ARB_shading_language_100
X..EXT_depth_bounds_test not found
---------------- R_NV20_Init ----------------
Not available.
----------------- R200_Init -----------------
GL_NUM_FRAGMENT_REGISTERS_ATI: 6
GL_NUM_FRAGMENT_CONSTANTS_ATI: 8
GL_NUM_PASSES_ATI: 2
GL_NUM_INSTRUCTIONS_PER_PASS_ATI: 8
GL_NUM_INSTRUCTIONS_TOTAL_ATI: 16
GL_COLOR_ALPHA_PAIRING_ATI: 1
GL_NUM_LOOPBACK_COMPONENTS_ATI: 3
GL_NUM_INPUT_INTERPOLATOR_COMPONENTS_ATI: 3
FPROG_FAST_PATH
---------------------
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
reloading lights/defaultpointlight.
WARNING: Invalid folder for map 'lights/defaultpointlight'
WARNING: Couldn't load image: lights/defaultpointlight
reloading lights/defaultprojectedlight.
WARNING: Invalid folder for map 'lights/defaultprojectedlight'
WARNING: Couldn't load image: lights/defaultprojectedlight
reloading lights/muzzleflash.
WARNING: Invalid folder for map 'lights/muzzleflash'
WARNING: Couldn't load image: lights/muzzleflash
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
found DLL in pak file: /usr/local/games/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/andy/.quake4/q4base/gamex86.so
enabled Flush-To-Zero mode
------------- Initializing Game -------------
gamename: baseQUAKE4-1
gamedate: Jul 21 2006
78ms to load 117k of entityDef
0ms to load 0k of articulatedFigure
Initializing event system
...531 event definitions
Initializing class hierarchy
...247 classes, 598968 bytes for event callbacks
Initializing scripts
TODO: Sys_SetClipboardData
------------ Game Map Shutdown --------------
---------------------------------------------
********************
ERROR: Couldn't load scripts/main.script

********************
Sys_Error: Error during initialization
andy@home:~$

Do I have to setup permissions or something? That's just too many files not found and not loading, help a noob out :)

---

### Post by Sqwishy on 2007-02-08
what! no don't run it with sudo! you don't ... no! lol ... only use sudo for installing stuffs, or when it asks you to, or when it says that you need to. but DON"T play games with sudo! O_o you probobly need to run the install with sudo

---

### Post by meng on 2007-02-08
What video card do you have? Is it set up for 3d acceleration?

---

### Post by conjur3r on 2007-02-09
Did you copy the extra paks from your CD after installation?

[http://zerowing.idsoftware.com/linux/quake4/#head-3b5b3c3dcae4463b33ba18cb3086ab8b7e19c85b](http://zerowing.idsoftware.com/linux/quake4/#head-3b5b3c3dcae4463b33ba18cb3086ab8b7e19c85b)

---

### Post by nrgtek on 2007-04-21
Where did you get the Id Software installer for Quake 4?

---

### Post by noerrorsfound on 2007-04-21
> **nrgtek said:**
> Where did you get the Id Software installer for Quake 4?
Probably from here:
[ftp://ftp.idsoftware.com/idstuff/quake4/linux](ftp://ftp.idsoftware.com/idstuff/quake4/linux)

---

### Post by lakersforce on 2007-04-21
I could be wrong, but it looks like you only have the binaries, and not the game installed.

---

### Post by nrgtek on 2007-04-21
> **noerrorsfound said:**
> Probably from here:
[ftp://ftp.idsoftware.com/idstuff/quake4/linux](ftp://ftp.idsoftware.com/idstuff/quake4/linux)

I own a copy of Q4, this link looks like it's just a demo. I'd like to know how to install the full game on Fiesty.

---

### Post by nrgtek on 2007-04-21
So i got it running from the link conjur3r posted. However, when I boot into Q4, it's in spanish! is there a file to edit to boot in with English as default?

---

### Post by lakersforce on 2007-04-22
> **nrgtek said:**
> I own a copy of Q4, this link looks like it's just a demo. I'd like to know how to install the full game on Fiesty.

Nope, it is the full version.

---


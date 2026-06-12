---
title: "Quake 4 Startup Crash"
date: 2007-05-16
forum: Gaming &amp; Leisure
---

### Post by di0de on 2007-05-16
Hi guys,
Just moved from WinXP to Ubuntu and I have to say I am loving it, but I have just tried to install Quake4 and received the following error:

Quake4  V1.4.1 linux-x86 Apr  2 2007
found interface lo - loopback
found interface eth0 - 192.168.13.111/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /media/sda5/quake4/q4base/game000.pk4 with checksum 0xae4eae32
Loaded pk4 /media/sda5/quake4/q4base/game100.pk4 with checksum 0x2dc1ddd1
Loaded pk4 /media/sda5/quake4/q4base/game200.pk4 with checksum 0x1787dbd9
Loaded pk4 /media/sda5/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /media/sda5/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /media/sda5/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /media/sda5/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /media/sda5/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /media/sda5/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /media/sda5/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /media/sda5/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /media/sda5/quake4/q4base/pak021.pk4 with checksum 0xd166cbf7
Loaded pk4 /media/sda5/quake4/q4base/pak022.pk4 with checksum 0x54a80682
Loaded pk4 /media/sda5/quake4/q4base/q4cmp_pak001.pk4 with checksum 0x961944b2
Loaded pk4 /media/sda5/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /media/sda5/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /media/sda5/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /media/sda5/quake4/q4base/zpak_english_04.pk4 with checksum 0xac1d3432
Addon pk4 /media/sda5/quake4/q4base/q4cmp_pak001.pk4 with checksum 0x961944b2 is on addon list
Current search path:
/home/aaron/.quake4/q4base
/media/sda5/quake4/q4base
/media/sda5/quake4/q4base/zpak_english_04.pk4 (3 files)
/media/sda5/quake4/q4base/zpak_english_03.pk4 (4 files)
/media/sda5/quake4/q4base/zpak_english_02.pk4 (21 files)
/media/sda5/quake4/q4base/zpak_english_01.pk4 (1 files)
/media/sda5/quake4/q4base/pak022.pk4 (14 files)
/media/sda5/quake4/q4base/pak021.pk4 (59 files)
/media/sda5/quake4/q4base/pak020.pk4 (11 files)
/media/sda5/quake4/q4base/pak019.pk4 (1206 files)
/media/sda5/quake4/q4base/pak018.pk4 (3 files)
/media/sda5/quake4/q4base/pak017.pk4 (3 files)
/media/sda5/quake4/q4base/pak016.pk4 (193 files)
/media/sda5/quake4/q4base/pak015.pk4 (34 files)
/media/sda5/quake4/q4base/pak014.pk4 (552 files)
/media/sda5/quake4/q4base/pak013.pk4 (239 files)
/media/sda5/quake4/q4base/game200.pk4 (9 files)
/media/sda5/quake4/q4base/game100.pk4 (2 files)
/media/sda5/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
/media/sda5/quake4/q4base/q4cmp_pak001.pk4 (103 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 55 loaded
103ms to load 244k of material
2ms to load 4k of skin
145ms to load 378k of sound
0ms to load 0k of materialType
579ms to load 2889k of lipSync
1ms to load 0k of playback
7ms to load 22k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' without VO
.... found additional language 'italian' without VO
.... found additional language 'spanish' without VO
696 strings read from strings/english_code.lang
1793 strings read from strings/english_guis.lang
1796 strings read from strings/english_mappack.lang
2272 strings read from strings/english_maps.lang
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
1440x900 1280x1024 1280x720 1152x864 1024x768 1024x480 960x720 864x648 856x480 848x480 800x600 
720x576 720x480 704x480 640x480 640x400 640x350 512x384 400x300 320x240 320x200 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
1 pixels multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.13
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
reloading lights/defaultprojectedlight.
reloading lights/muzzleflash.
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
Could not register font fonts/chain [fonts/english/chain]
found DLL in pak file: /media/sda5/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/aaron/.quake4/q4base/gamex86.so
enabled Flush-To-Zero mode
------------- Initializing Game -------------
gamename: baseQUAKE4-1
gamedate: Apr  2 2007
52ms to load 118k of entityDef
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
pure virtual method called
terminate called after throwing an instance of 'idException'
Aborted (core dumped)


Any ideas off the top of your collective heads what the issue may be? I copied the .pk4 files off the dvd into the one directory but I tried to copy it to a different dir than the tutorial suggests /media/sda5/quake4

Surely I should be able to copy it to another drive with more space though?

---

### Post by Nehvrook on 2007-05-16
You have to copy the files from the DVD into your Quake 4 instalation folder 
<path to your install>/Quake4/q4base
If you copied them anywhere other than there it won't be able to find them and so won't load.

---

### Post by dilb on 2007-05-17
I had a similar problem. If Nehvrook's solution doesn't work, I found it was a permissions issue. You need to make sure you have read, write and execute permissions for the quake 4 files (by default in /usr/local/games/quake4/ but you've obviously saved them somewhere else) and also your saved files (which is a hidden file in your home directory).
That solved it for me anyway. Good luck.

---

### Post by dilb on 2007-05-17
Try running Quake 4 as root:
sudo quake4
in the terminal. If Quake 4 runs it's a permissions problem.

---

### Post by dilb on 2007-05-17
Forgot to say, don't run Quake 4 as root other than to test this problem!

Sorry for broken replies.

---

### Post by Nehvrook on 2007-05-17
Yes good point. Permissions can skrew things up. Make sure you don't installt he game with the sudo command. Otherwise all folders created will be owned by root and you won't be able to edit or delete them (I broke my Doom 3 installation twice by doing this before I realised what it was XD)

---

### Post by rajeev1204 on 2009-07-21
One very important point is,

if you have moved the quake 4 pak files to the home folder, install the game in home folder and **not** in /usr/local/bin or whatever default location the installer says or the game wont run.

Important point is '[B]Install to folder where the quake 4 data files are'
[/B] or
You will probably have a pure virtual exception error or a system initialization error.



Cheers

rajeev

---


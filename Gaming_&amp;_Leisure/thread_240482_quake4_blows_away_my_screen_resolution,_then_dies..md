---
title: "quake4 blows away my screen resolution, then dies..."
date: 2006-08-20
forum: Gaming &amp; Leisure
---

### Post by hotani on 2006-08-20
I could run the demo fine. Now that I have the game it won't start. Not only that, but it changes my screen res to 640 or some crap and I have to change it *twice* to get it back to normal. 

I installed like so:
- copied all pk4 files to /usr/local/games/quake4/q4base/
- ran installer
- ran installer as root
- ran installer pointing to q4base directory
- ran installer a few more times just to be sure.

Same problem.

here is the output:

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
found DLL in pak file: /usr/local/games/quake4/q4base/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/hotani/.quake4/q4base/gamex86.so
enabled Flush-To-Zero mode
------------- Initializing Game -------------
gamename: baseQUAKE4-1
gamedate: Jul 21 2006
50ms to load 117k of entityDef
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


](*,)

---

### Post by hotani on 2006-08-20
ok, this is how it has to go down. Unfortunately, this was not explained in any of the installation texts I read which usually said: "just copy the pk4 files, run the installer and GO!" WHEE!! Yeah, no.

My new and improved installation instructions:

1- copy all pk4 files to: /usr/local/games/quake4/q4base
2- run installer and *VERY IMPORTANTLY* point the game dir (the one on top in the installer dialog) to /usr/local/games/quake4

I ran the installer like so: 'sudo quake4-linux....run'

---

### Post by chevett on 2006-09-17
I am having the exact same problem.  Can you explain to me what you did?  I don't understand your comments.  Let me know, thanks a lot.

---

### Post by hotani on 2006-09-20
When you run the installer, there is a pop-up dialog which asks where the bin and app directories are on the machine. Be sure to put the path to the quake4 directory (same directory that contains the q4base dir) like this:
[img]http://www.linux.com/blob.pl?id=c357fbdc741aea5add9b38e9ce5fbe9a[/img]

---

### Post by foamy3 on 2007-02-12
Sorry for the necropost, but I got the same problem.  I did the installation just like you said and it still does it.  I found a temporary fix that it will run as root, but I really wouldn't recommend that if you play online.

---

### Post by LordFu on 2007-02-12
You need to change the permission. sudo chmod -R 775 /usr/local/games/quake4/q4base
will get it, I think.

---

### Post by Dave18 on 2007-03-13
Maybe this thing resolve your problem!
 
You have to copy all pk4 files from **/usr/local/games/quake4/q4base/ to /usr/local/games/quake4/q4base/q4base/**. So the .run thing doesn't work good, that was the reason!

---

### Post by conjur3r on 2007-03-14
You install into the /usr/local folder only if you have multiple users on your linux system.  If it's just the one account you use, then it's perfectly fine to install into your home directory.  This way you do not have to worry about using sudo, changing permissions, etc.

---

### Post by Aninhumer on 2007-05-06
I have tried installing both as root (and chmoding the files) and as my own user but whatever I do I just get:

ERROR: Couldn't load scripts/main.script

I also tried moving things to q4base/q4base, and running the game as root

(I am just trying to run the demo version, and do not own the full version of this game)

---

### Post by blkno1 on 2007-07-05
Any lucky I'm getting same results.

```
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface eth1 - 192.168.1.110/255.255.255.0
found interface vmnet1 - 192.168.0.1/255.255.255.0
found interface vmnet8 - 192.168.149.1/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/jim/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /home/jim/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /home/jim/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
Loaded pk4 /home/jim/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /home/jim/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /home/jim/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /home/jim/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /home/jim/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /home/jim/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /home/jim/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /home/jim/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /home/jim/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /home/jim/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /home/jim/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /home/jim/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /home/jim/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /home/jim/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /home/jim/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Addon pk4 /home/jim/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/jim/.quake4/q4base
/home/jim/quake4/q4base
/home/jim/quake4/q4base/zpak_english_04.pk4 (3 files)
/home/jim/quake4/q4base/zpak_english_03.pk4 (4 files)
/home/jim/quake4/q4base/zpak_english_02.pk4 (21 files)
/home/jim/quake4/q4base/zpak_english_01.pk4 (1 files)
/home/jim/quake4/q4base/pak022.pk4 (14 files)
/home/jim/quake4/q4base/pak021.pk4 (89 files)
/home/jim/quake4/q4base/pak020.pk4 (11 files)
/home/jim/quake4/q4base/pak019.pk4 (1206 files)
/home/jim/quake4/q4base/pak018.pk4 (3 files)
/home/jim/quake4/q4base/pak017.pk4 (3 files)
/home/jim/quake4/q4base/pak016.pk4 (193 files)
/home/jim/quake4/q4base/pak015.pk4 (34 files)
/home/jim/quake4/q4base/pak014.pk4 (552 files)
/home/jim/quake4/q4base/pak013.pk4 (239 files)
/home/jim/quake4/q4base/game200.pk4 (9 files)
/home/jim/quake4/q4base/game100.pk4 (2 files)
/home/jim/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
/home/jim/quake4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 55 loaded
39ms to load 243k of material
0ms to load 4k of skin
59ms to load 378k of sound
1ms to load 0k of materialType
283ms to load 2889k of lipSync
0ms to load 0k of playback
8ms to load 25k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
Spawning back end thread...
...ok
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' without VO
.... found additional language 'italian' without VO
.... found additional language 'spanish' without VO
696 strings read from strings/english_code.lang
1794 strings read from strings/english_guis.lang
1797 strings read from strings/english_mappack.lang
2273 strings read from strings/english_maps.lang
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
2560x1024 2048x768 1600x600 1280x480 1024x768 800x600 640x480 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.13
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
found DLL in pak file: /home/jim/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/jim/.quake4/q4base/gamex86.so
enabled Flush-To-Zero mode
------------- Initializing Game -------------
gamename: baseQUAKE4-1
gamedate: Jun 15 2007
40ms to load 118k of entityDef
0ms to load 0k of articulatedFigure
Initializing event system
...531 event definitions
Initializing class hierarchy
...247 classes, 598968 bytes for event callbacks
Initializing scripts
Error ERP_DROP: Couldn't load scripts/main.script

TODO: Sys_SetClipboardData
------------ Game Map Shutdown --------------
---------------------------------------------
********************
ERROR: Couldn't load scripts/main.script

********************
Sys_Error: Error during initialization
```

---

### Post by kerneloftruth on 2010-10-05
ok guys,

let's start with the instructions from the idsoftware site:

[http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

open up a terminal then:

mkdir -p /usr/local/games/quake4/q4base

cd /usr/local/games/quake4/q4base/

assuming /mnt/cdrom is the folder where the CD/DVD is mounted:

cp -r /mnt/cdrom/Setup/Data/pb/ .

cp -r /mnt/cdrom/Setup/Data/q4base/* .

then do:

chmod 775 /usr/local/games/quake4/q4base/


take a look at the permissions of the files:

they should be:

-rw-r--r--

so 

chmod +r /usr/local/games/quake4/q4base/


get yourself the quake4-linux-1.4.2.x86.run

make it executable:

chmod +x quake4-linux-1.4.2.x86.run

then run it

sudo ./quake4-linux-1.4.2.x86.run

make sure the install path is correct (/usr/local/games/quake4/)

also make sure you select the correct version (All versions / German edition), ...

click on "Begin to install"


--> go back to /usr/local/games/quake4/q4base

cd /usr/local/games/quake4/q4base

mkdir q4base

again run: chmod 775 /usr/local/games/quake4/q4base/

cd q4base

create symbolic links to the pk4-files:

ln -s ../*.pk4 .


at this point it might still not work:

chown -R root:games /usr/local/games/quake4/

(make sure you're in the games group)

or if all people in the group users should be able to execute:

chown -R root:users /usr/local/games/quake4/


execute quake4:

either:

quake4

quake4-smp

or

quake4-dedicated

---


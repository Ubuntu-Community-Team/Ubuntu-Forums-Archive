---
title: "Quake 4 Language change causes crash"
date: 2010-08-01
forum: Gaming &amp; Leisure
---

### Post by bigseb on 2010-08-01
Installed Quake 4 last night. Went VERY smoothly without any hassles whatsoever. Started it up and it was in spanish (which I expected as this happened before). I found my way round though and entered the license key and started the game. Up til this no hassles at all.

Then I wanted to change the language to english so I opened the Quake4Config.cfg (sudo gedit ~/.Quake4/Quake4Config.cfg) and changed the sys_lang to "english". Now it crashes immediately on starting the game. I changed the value back to spanish and it still crashes.

Here is the terminal output:

sebastian@sebastian-laptop:~$ quake4
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /usr/local/games/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
Loaded pk4 /usr/local/games/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /usr/local/games/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /usr/local/games/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /usr/local/games/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /usr/local/games/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /usr/local/games/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /usr/local/games/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /usr/local/games/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /usr/local/games/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /usr/local/games/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Addon pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/sebastian/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_english_04.pk4 (3 files)
/usr/local/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/usr/local/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/usr/local/games/quake4/q4base/pak022.pk4 (14 files)
/usr/local/games/quake4/q4base/pak021.pk4 (89 files)
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
/usr/local/games/quake4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 55 loaded
51ms to load 243k of material
1ms to load 4k of skin
77ms to load 378k of sound
0ms to load 0k of materialType
374ms to load 2889k of lipSync
0ms to load 0k of playback
11ms to load 25k of effect
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
1794 strings read from strings/english_guis.lang
1797 strings read from strings/english_mappack.lang
2273 strings read from strings/english_maps.lang
3 strings read from strings/french_mappack.lang
3 strings read from strings/italian_mappack.lang
3 strings read from strings/spanish_mappack.lang
Couldn't open journal files
execing default.cfg
couldn't exec editor.cfg
execing Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1440x900 1360x768 1152x864 1024x768 960x600 960x540 840x525 832x624 800x600 800x512 720x450 
720x400 700x525 680x384 640x512 640x480 640x400 640x350 576x432 512x384 416x312 
400x300 360x200 320x240 320x200 320x175 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.22
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5461 frames ( 65532 bytes )
allocated a mix buffer of 49152 bytes
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
found DLL in pak file: /usr/local/games/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/sebastian/.quake4/q4base/gamex86.so
Fatal Error: could not create destination file /home/sebastian/.quake4/q4base/gamex86.so

Shutting down SDL subsystem
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
Sys_Error: could not create destination file /home/sebastian/.quake4/q4base/gamex86.so

Please how do I fix this?

---

### Post by Cresho on 2010-08-01
delete the .quake4 directory and try again

---

### Post by bigseb on 2010-08-01
Just had a thought: the .quake4 folder hader a lock item over it. Does this mean I must change the folder's permissions? If so how do I do this? Not sure...

---

### Post by Perfect Storm on 2010-08-01
Sounds like you tried launching the game as superuser (either by running the game with sudo or launching the game from the installation window) which is a bad idea and will cause permission problems. Just deleted the .quake4 folder and it will generate a new one.

---

### Post by Brebs on 2010-08-02
You are missing lots of "pak" files. Should get:

Loaded pk4 /opt/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /opt/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /opt/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
Loaded pk4 /opt/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /opt/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /opt/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /opt/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /opt/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /opt/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /opt/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /opt/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /opt/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /opt/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /opt/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /opt/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /opt/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /opt/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /opt/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /opt/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /opt/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /opt/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /opt/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /opt/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /opt/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /opt/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /opt/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /opt/quake4/q4base/zpak_czech_01.pk4 with checksum 0xea048e9b
Loaded pk4 /opt/quake4/q4base/zpak_czech_02.pk4 with checksum 0x233bf78
Loaded pk4 /opt/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /opt/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /opt/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /opt/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /opt/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Loaded pk4 /opt/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /opt/quake4/q4base/zpak_french_01.pk4 with checksum 0xe909853f
Loaded pk4 /opt/quake4/q4base/zpak_french_02.pk4 with checksum 0x3e376694
Loaded pk4 /opt/quake4/q4base/zpak_french_03.pk4 with checksum 0x401e8396
Loaded pk4 /opt/quake4/q4base/zpak_french_04.pk4 with checksum 0x1d7cacce
Loaded pk4 /opt/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /opt/quake4/q4base/zpak_italian_01.pk4 with checksum 0xef0e1696
Loaded pk4 /opt/quake4/q4base/zpak_italian_02.pk4 with checksum 0xca9e1dbd
Loaded pk4 /opt/quake4/q4base/zpak_italian_03.pk4 with checksum 0x9263d0ca
Loaded pk4 /opt/quake4/q4base/zpak_italian_04.pk4 with checksum 0x7d4bc6f7
Loaded pk4 /opt/quake4/q4base/zpak_polish_01.pk4 with checksum 0xd66ba55c
Loaded pk4 /opt/quake4/q4base/zpak_polish_02.pk4 with checksum 0xfb37d2ec
Loaded pk4 /opt/quake4/q4base/zpak_russian_01.pk4 with checksum 0x9aac856d
Loaded pk4 /opt/quake4/q4base/zpak_russian_02.pk4 with checksum 0x7392289b
Loaded pk4 /opt/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Loaded pk4 /opt/quake4/q4base/zpak_spanish_01.pk4 with checksum 0xe829a04a
Loaded pk4 /opt/quake4/q4base/zpak_spanish_02.pk4 with checksum 0xc28f719d
Loaded pk4 /opt/quake4/q4base/zpak_spanish_03.pk4 with checksum 0xd77e701d
Loaded pk4 /opt/quake4/q4base/zpak_spanish_04.pk4 with checksum 0xd000f97e
Addon pk4 /opt/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list

Now would be a good time to reinstall using [my installer script](http://forums.fedoraforum.org/showthread.php?t=189064).

---

### Post by bigseb on 2010-08-02
> **Brebs said:**
> You are missing lots of "pak" files. 
  
What do they all do? I got mine off my disc, do I need all the others?

---

### Post by bigseb on 2010-08-02
> **Cresho said:**
> delete the .quake4 directory and try again
What is the best way to do this?

---

### Post by Brebs on 2010-08-02
> **bigseb said:**
> What do they all do? I got mine off my disc, do I need all the others?
Why are you even bothering to ask this question? You've only installed half the required game files! So don't be surprised that it doesn't work.

As for your other question:

rm -rf ~/.quake4

---

### Post by bigseb on 2010-08-02
> **Brebs said:**
> Why are you even bothering to ask this question? You've only installed half the required game files! So don't be surprised that it doesn't work.
I'm bothering to ask as I have all the files that were *on the disk*. I doubt ID Software are going to sell a game with only half the necessary data...

---

### Post by Brebs on 2010-08-02
"disk" - is that a CD or DVD?

Here's some useful info:

du -hs /opt/quake4
2.9G

That's installed from my DVD. I'm guessing that you need to search for CDs 2 and 3. In which case, unfortunately, my installer won't work - it was designed for the original DVD.

---

### Post by bigseb on 2010-08-02
I have the DVD. Thing is I installed Quake on my system before and it worked fine. In fact, you even helped me with it back then (about 6 or so months ago). This time the install went very smoothly, I copied everything over as I should have but it won't run. Last time it worked fine. I don't get it.

The difference between last time and now is that now I'm running Lucid x64 (last time was Karmic x64) but that shouldn't make a difference, should it?

"du -hs /opt/quake4"  <--- what does this mean?

---

### Post by Brebs on 2010-08-03
> **bigseb said:**
> what does this mean?
See for yourself:

man du

Regarding the pak files - I expect you've made some elementary mistake.

---

### Post by bigseb on 2010-08-03
> **Brebs said:**
> Regarding the pak files - I expect you've made some elementary mistake.
I copied the pak file over into the folders first, then ran the installer. Should I maybe do it the other way round?

---

### Post by Brebs on 2010-08-03
What? I don't understand what you're saying.

Anyway, if you have the, er, "standard" DVD, then run [my installer](http://forums.fedoraforum.org/showthread.php?t=189064).

Remove whatever Quake 4 crap you've put on your PC, first.

---

### Post by bigseb on 2010-08-03
du -hs /opt/quake4 gives me this:

sebastian@sebastian-laptop:~$ du -hs /opt/quake4
du: cannot access `/opt/quake4': No such file or directory
sebastian@sebastian-laptop:~$

I guess I'll have to uninstall and try again :(

---

### Post by bigseb on 2010-08-03
Ok, I reinstalled Quake4. Ran the installer, copied over the pak files and game starts fine. Only thing is its in spanish and the sound is messed but both of those were expected. And this is exactly what happened when I installed a few days ago. It was when I tried to change the language to english that it kept crashing on startup. So... where to from here?

Incidentally I installed Doom3 too just to see what would happen and that isn't giving me any problems.

---


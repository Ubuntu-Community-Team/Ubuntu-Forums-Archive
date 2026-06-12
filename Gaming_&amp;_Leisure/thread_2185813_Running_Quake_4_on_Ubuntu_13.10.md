---
title: "Running Quake 4 on Ubuntu 13.10"
date: 2013-11-04
forum: Gaming &amp; Leisure
---

### Post by garyzw on 2013-11-04
I get the following error

```
./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory
```

Urban Terror and Return to Castle Wolfenstein work fine with Ubuntu 13.10

---

### Post by Toz on 2013-11-04
```
[toz@xubu ~]$ apt-file search libSDL-1.2.so.0
libsdl1.2debian: /usr/lib/x86_64-linux-gnu/libSDL-1.2.so.0
libsdl1.2debian: /usr/lib/x86_64-linux-gnu/libSDL-1.2.so.0.11.4
[toz@xubu ~]$ apt-cache policy libsdl1.2debian
libsdl1.2debian:
  Installed: 1.2.15-5ubuntu2
  Candidate: 1.2.15-5ubuntu2
  Version table:
 *** 1.2.15-5ubuntu2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages
        100 /var/lib/dpkg/status
```

Do you have **libsdl1.2debian** installed? If so, have you tried re-installing it?
```
sudo apt-get install --reinstall libsdl1.2debian
```

Are you have a 32 or 64 bit?
```
uname -a
```

---

### Post by garyzw on 2013-11-04
I have 64 bit.   I did the sudo apt-get install --reinstall libsdl1.2debian and I stil have the same error

---

### Post by Toz on 2013-11-04
> **garyzw said:**
> I have 64 bit.   I did the sudo apt-get install --reinstall libsdl1.2debian and I stil have the same error

64 bit? You're probably running into the "app/game is 32-bit but I want to run it on 64-bit but the ia32-libs package is deprecated" problem. I'm going to install it on my system (been a while since I've played and all this talk about it is making me nostalgic) and I'll see what I can do. We're going to have to manually install the 32 bit libraries to get this to work, but first we're going to need to figure out which ones to install.

Running:
```
ldd /path/to/quake4.x86
```
...(change "/path/to" to be the real path to the executable), should help us to identify those libraries.

EDIT: Got it. You need to install the 32-bit version of libsdl1.2debian like this:
```
sudo apt-get install libsdl1.2debian:i386
```

Now, off to see what I can do about those pesky Strogg.

---

### Post by garyzw on 2013-11-04
Thanks Toz-- this was a simple fix

---

### Post by garyzw on 2013-11-05
Ok now i get no sound in Quake 4 any ideas? :(

Stange because Urban Terror and Return to Castle Wolfenstein all have sound

---

### Post by Toz on 2013-11-05
Hmmm, I have sound. Can you post back the results of:
```
ldd /path/to/quake4.x86
```
...where "/path/to" is the real path to quake4.x86 _and_ the information displayed on the terminal window when you run quake4 from the terminal?

---

### Post by garyzw on 2013-11-05
This is what I get

```
gary@gary-LinuxPC:~$ ldd "/home/gary/Linux Games/Quake 4/quake4.x86"
    linux-gate.so.1 =>  (0xf7766000)
    libSDL-1.2.so.0 => /usr/lib/i386-linux-gnu/libSDL-1.2.so.0 (0xf76b1000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf7696000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf7690000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf755b000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf7548000)
    libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf752e000)
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf7445000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf7401000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf73e4000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7230000)
    libasound.so.2 => /usr/lib/i386-linux-gnu/libasound.so.2 (0xf713a000)
    libpulse-simple.so.0 => /usr/lib/i386-linux-gnu/libpulse-simple.so.0 (0xf7135000)
    libpulse.so.0 => /usr/lib/i386-linux-gnu/libpulse.so.0 (0xf70e5000)
    libcaca.so.0 => /usr/lib/i386-linux-gnu/libcaca.so.0 (0xf7019000)
    /lib/ld-linux.so.2 (0xf7767000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf6ff8000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf6fef000)
    libpulsecommon-4.0.so => /usr/lib/i386-linux-gnu/pulseaudio/libpulsecommon-4.0.so (0xf6f7f000)
    libjson-c.so.2 => /lib/i386-linux-gnu/libjson-c.so.2 (0xf6f74000)
    libdbus-1.so.3 => /lib/i386-linux-gnu/libdbus-1.so.3 (0xf6f29000)
    libslang.so.2 => /lib/i386-linux-gnu/libslang.so.2 (0xf6dfa000)
    libncursesw.so.5 => /lib/i386-linux-gnu/libncursesw.so.5 (0xf6dc3000)
    libtinfo.so.5 => /lib/i386-linux-gnu/libtinfo.so.5 (0xf6da0000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf6d9c000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf6d95000)
    libwrap.so.0 => /lib/i386-linux-gnu/libwrap.so.0 (0xf6d8b000)
    libsndfile.so.1 => /usr/lib/i386-linux-gnu/libsndfile.so.1 (0xf6d19000)
    libasyncns.so.0 => /usr/lib/i386-linux-gnu/libasyncns.so.0 (0xf6d11000)
    libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xf6cf8000)
    libFLAC.so.8 => /usr/lib/i386-linux-gnu/libFLAC.so.8 (0xf6cc4000)
    libvorbisenc.so.2 => /usr/lib/i386-linux-gnu/libvorbisenc.so.2 (0xf6b4c000)
    libvorbis.so.0 => /usr/lib/i386-linux-gnu/libvorbis.so.0 (0xf6b20000)
    libogg.so.0 => /usr/lib/i386-linux-gnu/libogg.so.0 (0xf6b16000)
    libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xf6aff000)


```

---

### Post by Toz on 2013-11-05
Looks good. Open a terminal window and run quake like this:
```
quake4 | tee quake4.log
```

After startup, quit and post back the contents of quake4.log.

---

### Post by Toz on 2013-11-05
And also, what does the following return:
```
apt-cache policy libasound2:i386
```

---

### Post by garyzw on 2013-11-05
This is what I got-- but for some strange reason I also have sound now :P

```
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface eth0 - 192.168.2.10/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/game200.pk4 with checksum 0xa3c810d9
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /home/gary/Linux Games/Quake 4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Addon pk4 /home/gary/Linux Games/Quake 4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/gary/.quake4/q4base
/home/gary/Linux Games/Quake 4/q4base
/home/gary/Linux Games/Quake 4/q4base/zpak_english_04.pk4 (3 files)
/home/gary/Linux Games/Quake 4/q4base/zpak_english_03.pk4 (4 files)
/home/gary/Linux Games/Quake 4/q4base/zpak_english_02.pk4 (21 files)
/home/gary/Linux Games/Quake 4/q4base/zpak_english_01.pk4 (1 files)
/home/gary/Linux Games/Quake 4/q4base/zpak_english.pk4 (3457 files)
/home/gary/Linux Games/Quake 4/q4base/pak022.pk4 (14 files)
/home/gary/Linux Games/Quake 4/q4base/pak021.pk4 (89 files)
/home/gary/Linux Games/Quake 4/q4base/pak020.pk4 (11 files)
/home/gary/Linux Games/Quake 4/q4base/pak019.pk4 (1206 files)
/home/gary/Linux Games/Quake 4/q4base/pak018.pk4 (3 files)
/home/gary/Linux Games/Quake 4/q4base/pak017.pk4 (3 files)
/home/gary/Linux Games/Quake 4/q4base/pak016.pk4 (193 files)
/home/gary/Linux Games/Quake 4/q4base/pak015.pk4 (34 files)
/home/gary/Linux Games/Quake 4/q4base/pak014.pk4 (552 files)
/home/gary/Linux Games/Quake 4/q4base/pak013.pk4 (239 files)
/home/gary/Linux Games/Quake 4/q4base/pak012.pk4 (1081 files)
/home/gary/Linux Games/Quake 4/q4base/pak011.pk4 (5620 files)
/home/gary/Linux Games/Quake 4/q4base/pak010.pk4 (5539 files)
/home/gary/Linux Games/Quake 4/q4base/pak009.pk4 (1284 files)
/home/gary/Linux Games/Quake 4/q4base/pak008.pk4 (1289 files)
/home/gary/Linux Games/Quake 4/q4base/pak007.pk4 (1330 files)
/home/gary/Linux Games/Quake 4/q4base/pak006.pk4 (1343 files)
/home/gary/Linux Games/Quake 4/q4base/pak005.pk4 (1395 files)
/home/gary/Linux Games/Quake 4/q4base/pak004.pk4 (2249 files)
/home/gary/Linux Games/Quake 4/q4base/pak003.pk4 (1281 files)
/home/gary/Linux Games/Quake 4/q4base/pak002.pk4 (313 files)
/home/gary/Linux Games/Quake 4/q4base/pak001.pk4 (5837 files)
/home/gary/Linux Games/Quake 4/q4base/game200.pk4 (9 files)
/home/gary/Linux Games/Quake 4/q4base/game100.pk4 (2 files)
/home/gary/Linux Games/Quake 4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
/home/gary/Linux Games/Quake 4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 64 loaded
78ms to load 1125k of material
14ms to load 43k of skin
50ms to load 723k of sound
1ms to load 1k of materialType
131ms to load 2889k of lipSync
10ms to load 105k of playback
241ms to load 1690k of effect
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
5756 strings read from strings/english_lips.lang
5759 strings read from strings/english_mappack.lang
6235 strings read from strings/english_maps.lang
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
1920x1080 1680x1050 1440x900 1366x768 1280x1024 1280x800 1280x720 1024x768 800x600 640x480 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
16 pixels multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.27.2
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device plughw:0 for playback
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
found DLL in pak file: /home/gary/Linux Games/Quake 4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/gary/.quake4/q4base/gamex86.so
enabled Flush-To-Zero mode
------------- Initializing Game -------------
gamename: baseQUAKE4-1
gamedate: Jun 15 2007
93ms to load 644k of entityDef
15ms to load 177k of articulatedFigure
Initializing event system
...531 event definitions
Initializing class hierarchy
...247 classes, 598968 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 3801 MHz
Compiled '/home/gary/.quake4/q4base/scripts/main.script': 916.5 ms
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

...5 aas types
game initialized.
---------------------------------------------
Loading viseme file: annosoft
----------- Initializing Session ------------
----------------- BSE Init ------------------
--------- BSE Created Successfully ----------
session initialized
---------------------------------------------
Opening IP socket: localhost:-1
------ Common Initialization Complete -------
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 4578
detecting video ram ( set sys_videoRam to force ) ..
found XNVCtrl extension 1.29
3801 MHz CPU
7936 MB System Memory
2048 MB Video Memory
Async thread started
idUsercmdGenLocal::MouseMove: Ignoring ridiculous mouse delta.
------------ Game Map Shutdown --------------
---------------------------------------------
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
Shutting down SDL subsystem
--------------- Game Shutdown ---------------
rvStatAllocator:  dump of usage stats
    0 total bytes handed out in 0 requests
    begin game:      0;  end game:        0
    player hit:      0;  player kill:     0
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

```

---

### Post by garyzw on 2013-11-05
apt-cache policy libasound2:i386
libasound2:i386:
  Installed: 1.0.27.2-1ubuntu6
  Candidate: 1.0.27.2-1ubuntu6
  Version table:
 *** 1.0.27.2-1ubuntu6 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main i386 Packages
        100 /var/lib/dpkg/status

---

### Post by Toz on 2013-11-05
> **garyzw said:**
> This is what I got-- but for some strange reason I also have sound now :P
Good. Enjoy the game.

---

### Post by singing_fish on 2014-05-18
Just wanted to say thank you!

> sudo apt-get install libsdl1.2debian:i386

Made it for ET:QW on 64bit 14.04 :)

cheers,
rené

---

### Post by lars11 on 2015-04-30
thread bookmarked. Thanks for the great info!

---

### Post by Plasma_NZ on 2015-05-03
Im having problems with quake3 on ubuntu 14.04

Tried aoss and padsp - neither works for the sound... quake pukes out

------- sound initialization -------
Sorry but your soundcard can't do this
------------------------------------
Sound memory manager started


oss-compat / alsa-oss are installed

any ideas.?

---

### Post by garyzw on 2015-05-16
> **Plasma_NZ said:**
> Im having problems with quake3 on ubuntu 14.04

Tried aoss and padsp - neither works for the sound... quake pukes out

------- sound initialization -------
Sorry but your soundcard can't do this
------------------------------------
Sound memory manager started


oss-compat / alsa-oss are installed

any ideas.?

After running in to this problem in 15.04 I found this solution. It makes the sound in Quake 4 work for me in Ubuntu 15.04 so it should hopefully work in 14.04 also. I have seta s_driver "best" instead of seta s_driver "oss" in the Quake4Config.cfg. You need to install libasound2-plugins:i386

```
sudo apt-get install libasound2-plugins:i386
```

---

### Post by bryce4 on 2016-03-14
This is what I get when I try to rune Quake 4 right now. I'm running an Ubuntu fork, UberStudent, based on 14.04.
```
bryce@bryce-P55A-UD4P:~$ quake4
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface eth0 - 192.168.0.100/255.255.255.0
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
/home/bryce/.quake4/q4base
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
23ms to load 243k of material
1ms to load 4k of skin
35ms to load 378k of sound
0ms to load 0k of materialType
180ms to load 2889k of lipSync
0ms to load 0k of playback
4ms to load 25k of effect
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
couldn't exec Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1920x1080 1680x1050 1600x900 1280x1024 1280x800 1280x720 1152x864 1024x768 832x624 800x600 720x400 
640x480 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  33
  Current serial number in output stream:  34
pure virtual method called
terminate called without an active exception
signal caught: Aborted
si_code -6
Trying to exit gracefully..
pure virtual method called
terminate called recursively
double fault Aborted, bailing out
```

---


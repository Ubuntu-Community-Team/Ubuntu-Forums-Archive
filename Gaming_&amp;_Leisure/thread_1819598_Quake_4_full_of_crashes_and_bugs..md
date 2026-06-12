---
title: "Quake 4 full of crashes and bugs."
date: 2011-08-06
forum: Gaming &amp; Leisure
---

### Post by kaldor on 2011-08-06
Ubuntu 11.04 64 bit. AMD Radeon HD 6450 with Catalyst.

I used to play Quake 4 a while ago on an older laptop which couldn't really handle it. So, I decided to try it out on my new PC which it should just fly on. Sadly, I'm not having that luck.

I just did "create server" as a test to see if it would work. It crashes. Here's the message when run in Terminal:

```
---------------------------------------------
-------- Initializing renderSystem ----------
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
1920x1080 1680x1050 1600x1200 1600x900 1440x900 1400x1050 1280x1024 1280x960 1280x768 1280x720 1024x768 
800x600 640x480 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  130 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xaa
  Serial number of failed request:  141
  Current serial number in output stream:  143
pure virtual method called
terminate called without an active exception
signal caught: Aborted
si_code -6
Trying to exit gracefully..
pure virtual method called
terminate called recursively
double fault Aborted, bailing out
shutdown terminal support

```

Managed to load a Singleplayer game, but there is a half second delay between my keyboard/mouse controls. That's just unplayable:
```
---------------------------------------------
Opening IP socket: localhost:-1
------ Common Initialization Complete -------
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 12760
detecting video ram ( set sys_videoRam to force ) ..
guess failed, return default low-end VRAM setting ( 64MB VRAM )
2900 MHz CPU
8000 MB System Memory
64 MB Video Memory
Async thread started
guid set to YGS7jHuRWzo
idUsercmdGenLocal::MouseMove: Ignoring ridiculous mouse delta.
]sys_videoRam 
"sys_videoRam" is:"0" default:"0"
Texture memory on the video card (in megabytes) - 0: autodetect
Asset log: assetlogs/maps/game/airdefense1
------------ Game Map Shutdown --------------
---------------------------------------------
Asset log: assetlogs/maps/game/airdefense1
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
------------ Map Initialization -------------
Map: game/airdefense1
rvStatAllocator:  dump of usage stats
	16 total bytes handed out in 1 requests
	begin game:      0;  end game:        1
	player hit:      0;  player kill:     0
	player death:    0;
	damage dealt:    0;  damage taken:    0
	stat team:       0
	flag capture:    0;
	flag drop:       0;  flag return:     0
rvStatAllocator:  dump of usage stats
	0 total bytes handed out in 0 requests
	begin game:      0;  end game:        0
	player hit:      0;  player kill:     0
	player death:    0;
	damage dealt:    0;  damage taken:    0
	stat team:       0
	flag capture:    0;
	flag drop:       0;  flag return:     0
-------------- Game Map Init ----------------
collision data:
   606 models
 57187 vertices (1340 KB)
112706 edges (3962 KB)
 46640 polygons (4008 KB)
183402 polygon edges (716 KB)
  6161 brushes (288 KB)
 36855 brush planes (575 KB)
 21126 nodes (577 KB)
 97596 polygon refs (762 KB)
 22524 brush refs (175 KB)
 38181 internal edges
  4600 sharp edges
     0 contained polygons removed
     0 polygons merged
 12407 KB total memory used
457 msec to load collision data.
map bounds are (46336.0, 31936.0, 13760.0)
max clip sector is (0.0, 0.0, 0.0)
    1 KB passage memory used to build PVS
    1 msec to calculate PVS
   52 areas
   96 portals
    7 areas visible on average
  416 bytes PVS data
[Load AAS]
loading maps/game/airdefense1.aas32
done loading maps/game/airdefense1.aas32 (size 525484).
[Load AAS]
loading maps/game/airdefense1.aas48
done loading maps/game/airdefense1.aas48 (size 525196).
[Load AAS]
loading maps/game/airdefense1.aas96
[Load AAS]
loading maps/game/airdefense1.aas250
[Load AAS]
loading maps/game/airdefense1.aas128
Entering doom_main()
Exiting doom_main()
Spawning entities
glprogs/heatHazeWithMask.vfp
glprogs/heatHazeWithMask.vfp
...1777 entities spawned, 0 inhibited

------------ Processing events --------------
---------------------------------------------
-- idRenderModelManagerLocal::EndLevelLoad --
   17 models purged from previous level,  1130 models kept.
---------------------------------------------
----- idImageManagerLocal::EndLevelLoad -----
    0 purged from previous
  234 kept from previous
 1635 new loaded
all images loaded in  13.1 seconds
    0 deferred loading
---------------------------------------------
-------- idSoundCache::EndLevelLoad ---------
1.38 seconds to expand oggs
29174k referenced
    0k purged
---------------------------------------------
---------------------------------------------
 30295 msec to load game/airdefense1
idRenderWorld::GenerateAllInteractions, msec = 2, staticAllocCount = 0.
Saved 'Autosave game/airdefense1'
]fov
Unknown command 'fov'
]g_fov
"g_fov" is:"90" default:"90"
]g_fov 120
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
	32 total bytes handed out in 2 requests
	begin game:      1;  end game:        0
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

Now, I managed to get into a map with "devmap mp/q4dm1". Everything loads up fine, but I am moving super slow. It feels like I am constantly walking or something.

Never had these issues before. What should I do?

Edit: Reinstalled and things seem to have improved, albeit still full of issues. Going to try it for a bit then see what to do.

---

### Post by tkmn on 2011-08-06
Video RAM amount is not detected correctly.

Try forcing it.

```
seta sys_videoram 512
seta com_videoRam 512
```

I have the same issue with my Radeon HD 5750. Your card probably has 512 or 1024 MB.

---


---
title: "Doom3 Hangs on startup"
date: 2010-02-20
forum: Gaming &amp; Leisure
---

### Post by Paul Lynch on 2010-02-20
Hi, 
complete noob here, I am having difficulty running doom3. I have installed the game as instructed on a number of sites and copied the pk4 files (01,2,3,4) to the base folder. When I run the script file my monitor goes blank but I can hear the game over my system speakers (poor quality sound but that is another days problem!). I have spent a number of hours going through previous threads here and have not yet solved my prob. Any help would be appreciated at this stage!!

I am using a NV44A Geforce 6200 card and I have the Ubuntu proprietary drivers installed (Version 173)

My problem seems to be:

WARNING: Couldn't load image: textures/black
WARNING: Couldn't load image: textures/sfx/monitor_glass2

Just not sure where to start ...... HELP!


DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:53:29
found interface lo - loopback
found interface eth0 - 87.198.44.148/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/paul/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /home/paul/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /home/paul/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /home/paul/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /home/paul/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /home/paul/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /home/paul/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /home/paul/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/paul/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/paul/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /home/paul/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/paul/.doom3/base
/home/paul/doom3/base
/home/paul/doom3/base/pak008.pk4 (3 files)
/home/paul/doom3/base/pak007.pk4 (38 files)
/home/paul/doom3/base/pak006.pk4 (48 files)
/home/paul/doom3/base/pak005.pk4 (63 files)
/home/paul/doom3/base/pak003.pk4 (4676 files)
/home/paul/doom3/base/pak002.pk4 (6120 files)
/home/paul/doom3/base/pak001.pk4 (8972 files)
/home/paul/doom3/base/pak000.pk4 (2698 files)
/home/paul/doom3/base/game03.pk4 (2 files)
/home/paul/doom3/base/game02.pk4 (2 files)
/home/paul/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
WARNING: Couldn't load image: textures/black
Couldn't open journal files
execing editor.cfg
execing default.cfg
execing DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
Opening IP socket: localhost:27666
found DLL in pak file: /home/paul/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/paul/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Jan 16 2007
Initializing event system
...473 event definitions
Initializing class hierarchy
...142 classes, 382184 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 3060.66 MHz
Compiled 'weapon_machinegun::Lower': 1807.0 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67875, 1357500 bytes
   Functions: 2109, 250532 bytes
   Variables: 147376 bytes
    Mem used: 2479288 bytes
 Static data: 2277552 bytes
   Allocated: 3284544 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
WARNING: Couldn't load image: textures/sfx/monitor_glass2
session initialized
--------------------------------------
--- Common Initialization Complete ---
------------- Warnings ---------------
during DOOM 3 initialization...
WARNING: Couldn't load image: textures/black
WARNING: Couldn't load image: textures/sfx/monitor_glass2
2 warnings

Type 'help' for dedicated server info.

terminal support enabled ( use +set in_tty 0 to disabled )
pid: 2231
1008 MB System Memory
Async thread started

---

### Post by Brebs on 2010-02-20
> **Paul Lynch said:**
> Loaded pk4 /home/paul/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /home/paul/doom3/base/pak005.pk4 with checksum 0x8ffc3621

So where is:
-rw-r--r-- 1 root root 237752384 pak00**4**.pk4

---

### Post by Paul Lynch on 2010-02-20
BREBS
thanks for the quick reply, so looks like the 004.pk4 file didn't copy for me. I have now copied all the pk4 files again including the 004 file and still the same symptom, audio but no graphics when I run the script.

The terminal text below shows no errors/warnings but still no visual on start up.

Any help appreciated....

DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:53:29
found interface lo - loopback
found interface eth0 - 87.198.44.148/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/paul/doom3/base/game00.pk4 with checksum 0x7dafc4d4
Loaded pk4 /home/paul/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /home/paul/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /home/paul/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /home/paul/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /home/paul/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /home/paul/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /home/paul/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /home/paul/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /home/paul/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/paul/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/paul/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /home/paul/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/paul/.doom3/base
/home/paul/doom3/base
/home/paul/doom3/base/pak008.pk4 (3 files)
/home/paul/doom3/base/pak007.pk4 (38 files)
/home/paul/doom3/base/pak006.pk4 (48 files)
/home/paul/doom3/base/pak005.pk4 (63 files)
/home/paul/doom3/base/pak004.pk4 (5137 files)
/home/paul/doom3/base/pak003.pk4 (4676 files)
/home/paul/doom3/base/pak002.pk4 (6120 files)
/home/paul/doom3/base/pak001.pk4 (8972 files)
/home/paul/doom3/base/pak000.pk4 (2698 files)
/home/paul/doom3/base/game03.pk4 (2 files)
/home/paul/doom3/base/game02.pk4 (2 files)
/home/paul/doom3/base/game01.pk4 (2 files)
/home/paul/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
execing DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
Opening IP socket: localhost:27666
found DLL in pak file: /home/paul/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/paul/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Jan 16 2007
Initializing event system
...473 event definitions
Initializing class hierarchy
...142 classes, 382184 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 3060.64 MHz
Compiled 'weapon_machinegun::Lower': 2392.8 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67875, 1357500 bytes
   Functions: 2109, 250532 bytes
   Variables: 147376 bytes
    Mem used: 2479288 bytes
 Static data: 2277552 bytes
   Allocated: 3284544 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
session initialized
--------------------------------------
--- Common Initialization Complete ---

Type 'help' for dedicated server info.

terminal support enabled ( use +set in_tty 0 to disabled )
pid: 2388
1008 MB System Memory
Async thread started

---

### Post by Paul Lynch on 2010-02-21
So I have been searching for solutions for thse and I have come to the conclusion that my problem is the cheap wide-screen TV I am using doesn't like the Doom3 default resolution. To change this I need to open DoomConfig.cfg and change the full screen setting so the game runs in a window. Problem is when I locate the DoomConfig.cfg file in /,doom/ the file is empty?? no script to edit. Any ideas?

---

### Post by Brebs on 2010-02-21
Here's my ~/.doom3/base/DoomConfig.cfg
```
unbindall
bind "TAB" "_impulse19"
bind "ENTER" "_button2"
bind "ESCAPE" "togglemenu"
bind "SPACE" "_moveup"
bind "#" "_mlook"
bind "/" "_impulse14"
bind "0" "_impulse10"
bind "1" "_impulse0"
bind "2" "_impulse1"
bind "3" "_impulse2"
bind "4" "_impulse3"
bind "5" "_impulse4"
bind "6" "_impulse5"
bind "7" "_impulse6"
bind "8" "_impulse7"
bind "9" "_impulse8"
bind "[" "_impulse15"
bind "]" "_impulse14"
bind "a" "_moveRight"
bind "c" "_movedown"
bind "d" "_impulse11"
bind "f" "_impulse9"
bind "g" "spawn char_guardsentry_flashlight"
bind "h" "spawn char_marine_machinegun"
bind "i" "spawn char_marine_machinegun"
bind "j" "spawn char_marine_machinegun"
bind "q" "_moveLeft"
bind "r" "_impulse13"
bind "s" "_forward"
bind "t" "clientMessageMode"
bind "w" "_zoom"
bind "x" "_back"
bind "y" "clientMessageMode 1"
bind "z" "_impulse13"
bind "BACKSPACE" "clientDropWeapon"
bind "PAUSE" "pause"
bind "UPARROW" "_forward"
bind "DOWNARROW" "_back"
bind "LEFTARROW" "_left"
bind "RIGHTARROW" "_right"
bind "DEL" "_lookdown"
bind "PGDN" "_lookup"
bind "END" "_impulse18"
bind "F1" "_impulse28"
bind "F2" "_impulse29"
bind "F3" "_impulse17"
bind "F5" "savegame quick"
bind "F6" "_impulse20"
bind "F7" "_impulse22"
bind "F9" "loadgame quick"
bind "F10" "loadgame quick"
bind "F12" "toggle com_showFPS"
bind "MOUSE1" "_attack"
bind "MOUSE2" "_speed"
bind "MOUSE3" "_zoom"
bind "MWHEELDOWN" "_impulse14"
bind "MWHEELUP" "_impulse15"
seta com_product_lang_ext "1"
seta sv_punkbuster "0"
seta cl_punkbuster "0"
seta com_videoRam "512"
seta com_showFPS "0"
seta com_purgeAll "0"
seta com_machineSpec "2"
seta com_preloadDemos "0"
seta com_compressDemos "1"
seta m_strafeSmooth "2"
seta m_smooth "2"
seta m_strafeScale "6.25"
seta m_yaw "0.022"
seta m_pitch "0.022"
seta sensitivity "2"
seta in_toggleZoom "0"
seta in_toggleCrouch "1"
seta in_toggleRun "0"
seta in_alwaysRun "1"
seta in_freeLook "1"
seta in_anglespeedkey "1.5"
seta in_pitchspeed "140"
seta in_yawspeed "140"
seta gui_configServerRate "0"
seta com_guid "hbKlbIEQ4zo"
seta net_clientDownload "1"
seta net_master4 ""
seta net_master3 ""
seta net_master2 ""
seta net_master1 ""
seta net_clientMaxRate "16000"
seta net_serverMaxClientRate "16000"
seta gui_filter_game "0"
seta gui_filter_idle "0"
seta gui_filter_gameType "0"
seta gui_filter_players "0"
seta gui_filter_password "0"
seta image_downSizeLimit "256"
seta image_ignoreHighQuality "0"
seta image_downSizeBumpLimit "256"
seta image_downSizeSpecularLimit "64"
seta image_downSizeBump "0"
seta image_downSizeSpecular "0"
seta image_useCache "0"
seta image_cacheMegs "20"
seta image_cacheMinK "200"
seta image_usePrecompressedTextures "1"
seta image_useNormalCompression "0"
seta image_useAllFormats "1"
seta image_useCompression "1"
seta image_preload "1"
seta image_roundDown "1"
seta image_forceDownSize "0"
seta image_downSize "0"
seta image_lodbias "0"
seta image_anisotropy "1"
seta image_filter "GL_LINEAR_MIPMAP_LINEAR"
seta r_debugArrowStep "120"
seta r_debugLineWidth "1"
seta r_debugLineDepthTest "0"
seta r_cgFragmentProfile "best"
seta r_cgVertexProfile "best"
seta r_forceLoadImages "0"
seta r_shadows "1"
seta r_skipBump "0"
seta r_skipSpecular "0"
seta r_skipNewAmbient "0"
seta r_renderer "best"
seta r_brightness "1"
seta r_gamma "1"
seta r_swapInterval "1"
seta r_useIndexBuffers "0"
seta r_customHeight "1080"
seta r_customWidth "1920"
seta r_fullscreen "1"
seta r_mode "-1"
seta r_multiSamples "0"
seta gui_mediumFontLimit "0.60"
seta gui_smallFontLimit "0.30"
seta s_libOpenAL "openal32.dll"
seta s_numberOfSpeakers "2"
seta s_doorDistanceAdd "150"
seta s_globalFraction "0.8"
seta s_subFraction "0.75"
seta s_playDefaultSound "1"
seta s_volume_dB "-5"
seta s_meterTopTime "2000"
seta s_reverse "0"
seta s_spatializationDecay "2"
seta s_maxSoundsPerShader "0"
seta sys_lang "english"
seta sys_videoRam "0"
seta in_dgamouse "1"
seta in_mouse "1"
seta s_dsp "/dev/dsp"
seta s_driver "alsa"
seta s_alsa_lib "libasound.so.2"
seta s_alsa_pcm "default"
seta net_clientLagOMeter "1"
seta g_spectatorChat "0"
seta net_serverDlTable ""
seta net_serverDlBaseURL ""
seta net_serverDownload "0"
seta mod_validSkins "skins/characters/player/marine_mp;skins/characters/player/marine_mp_green;skins/characters/player/marine_mp_blue;skins/characters/player/marine_mp_red;skins/characters/player/marine_mp_yellow"
seta g_mapCycle "mapcycle"
seta g_voteFlags "0"
seta g_gameReviewPause "10"
seta g_countDown "10"
seta g_password ""
seta g_showBrass "1"
seta g_showProjectilePct "0"
seta g_showHud "1"
seta g_showPlayerShadow "1"
seta g_showcamerainfo "0"
seta g_healthTakeLimit "25"
seta g_healthTakeAmt "5"
seta g_healthTakeTime "5"
seta g_useDynamicProtection "1"
seta g_armorProtectionMP "0.6"
seta g_armorProtection "0.2"
seta g_damageScale "1"
seta g_nightmare "1"
seta g_decals "1"
seta g_doubleVision "1"
seta g_bloodEffects "1"
seta g_projectileLights "1"
seta g_muzzleFlash "1"
seta r_aspectRatio "1"
seta ui_showGun "1"
seta ui_autoReload "1"
seta ui_autoSwitch "1"
seta ui_team "Red"
seta ui_skin "skins/characters/player/marine_mp"
seta ui_name "brebs"
seta si_serverURL ""
seta si_spectators "1"
seta si_usePass "0"
seta si_warmup "0"
seta si_teamDamage "0"
seta si_timeLimit "10"
seta si_fragLimit "10"
seta si_maxPlayers "4"
seta si_map "game/mp/d3dm1"
seta si_gameType "singleplayer"
seta si_name "DOOM Server"

```

You'll need to modify these 2 lines:

seta r_customHeight "1080"
seta r_customWidth "1920"

---

### Post by Paul Lynch on 2010-02-21
Thanks for your help Brebs... in the end I borrowed a friends monitor and ran the game, changed the res and put my TV back in place, the game is nor running fine for me in 1024 x 768. There are many ways to skin a cat!!.

Thanks again

---


---
title: "Quake 4 Fails to initialize OpenGL"
date: 2010-06-12
forum: Gaming &amp; Leisure
---

### Post by realdude19 on 2010-06-12
[SIZE="4"]Hi All, I have a Issue with my Quake 4 install.[/SIZE]

[CENTER]***[COLOR="Red"]***Please Be Warned! I have Read All applicable Posts and have done a long and time consuming search to solve this issue! So please don't just post a link to another thread unless you are certain it is the solution. and please explain why you think the link is going to help! it will save a lot of time and confusion. ***[/COLOR]***[/CENTER]

I am Getting a Error Everytime I try to start Quake 4. 

Here is everything from the Terminal:

```
luke@BlueShift:~$ quake4
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface wlan0 - 192.168.0.104/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/luke/games/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /home/luke/games/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /home/luke/games/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
Loaded pk4 /home/luke/games/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /home/luke/games/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /home/luke/games/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /home/luke/games/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /home/luke/games/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /home/luke/games/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /home/luke/games/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /home/luke/games/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /home/luke/games/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /home/luke/games/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /home/luke/games/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /home/luke/games/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /home/luke/games/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /home/luke/games/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /home/luke/games/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /home/luke/games/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /home/luke/games/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /home/luke/games/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /home/luke/games/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /home/luke/games/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /home/luke/games/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /home/luke/games/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /home/luke/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Loaded pk4 /home/luke/games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /home/luke/games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /home/luke/games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Addon pk4 /home/luke/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/luke/.quake4/q4base
/home/luke/games/quake4/q4base
/home/luke/games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/home/luke/games/quake4/q4base/zpak_italian.pk4 (3500 files)
/home/luke/games/quake4/q4base/zpak_french.pk4 (3462 files)
/home/luke/games/quake4/q4base/zpak_english_04.pk4 (3 files)
/home/luke/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/home/luke/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/home/luke/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/home/luke/games/quake4/q4base/zpak_english.pk4 (3457 files)
/home/luke/games/quake4/q4base/pak022.pk4 (14 files)
/home/luke/games/quake4/q4base/pak021.pk4 (89 files)
/home/luke/games/quake4/q4base/pak020.pk4 (11 files)
/home/luke/games/quake4/q4base/pak019.pk4 (1206 files)
/home/luke/games/quake4/q4base/pak018.pk4 (3 files)
/home/luke/games/quake4/q4base/pak017.pk4 (3 files)
/home/luke/games/quake4/q4base/pak016.pk4 (193 files)
/home/luke/games/quake4/q4base/pak015.pk4 (34 files)
/home/luke/games/quake4/q4base/pak014.pk4 (552 files)
/home/luke/games/quake4/q4base/pak013.pk4 (239 files)
/home/luke/games/quake4/q4base/pak012.pk4 (1081 files)
/home/luke/games/quake4/q4base/pak011.pk4 (5620 files)
/home/luke/games/quake4/q4base/pak010.pk4 (5539 files)
/home/luke/games/quake4/q4base/pak009.pk4 (1284 files)
/home/luke/games/quake4/q4base/pak008.pk4 (1289 files)
/home/luke/games/quake4/q4base/pak007.pk4 (1330 files)
/home/luke/games/quake4/q4base/pak006.pk4 (1343 files)
/home/luke/games/quake4/q4base/pak005.pk4 (1395 files)
/home/luke/games/quake4/q4base/pak004.pk4 (2249 files)
/home/luke/games/quake4/q4base/pak003.pk4 (1281 files)
/home/luke/games/quake4/q4base/pak002.pk4 (313 files)
/home/luke/games/quake4/q4base/pak001.pk4 (5837 files)
/home/luke/games/quake4/q4base/game200.pk4 (9 files)
/home/luke/games/quake4/q4base/game100.pk4 (2 files)
/home/luke/games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
/home/luke/games/quake4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 64 loaded
166ms to load 1125k of material
59ms to load 43k of skin
99ms to load 723k of sound
4ms to load 1k of materialType
247ms to load 2889k of lipSync
47ms to load 105k of playback
768ms to load 1690k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
696 strings read from strings/english_code.lang
1794 strings read from strings/english_guis.lang
5756 strings read from strings/english_lips.lang
5759 strings read from strings/english_mappack.lang
6235 strings read from strings/english_maps.lang
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
execing Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1280x1024 1280x960 1152x864 1024x768 960x600 960x540 840x525 832x624 800x600 720x450 720x400 
700x525 680x384 640x480 640x400 640x350 512x384 400x300 320x240 320x175 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1280x1024 1280x960 1152x864 1024x768 960x600 960x540 840x525 832x624 800x600 720x450 720x400 
700x525 680x384 640x480 640x400 640x350 512x384 400x300 320x240 320x175 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Fatal Error: Unable to initialize OpenGL
--------------- BSE Shutdown ----------------
---------------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL
luke@BlueShift:~$ sudo quake4
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface wlan0 - 192.168.0.104/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/luke/games/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /home/luke/games/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /home/luke/games/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
Loaded pk4 /home/luke/games/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /home/luke/games/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /home/luke/games/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /home/luke/games/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /home/luke/games/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /home/luke/games/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /home/luke/games/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /home/luke/games/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /home/luke/games/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /home/luke/games/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /home/luke/games/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /home/luke/games/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /home/luke/games/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /home/luke/games/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /home/luke/games/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /home/luke/games/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /home/luke/games/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /home/luke/games/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /home/luke/games/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /home/luke/games/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /home/luke/games/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /home/luke/games/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /home/luke/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Loaded pk4 /home/luke/games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /home/luke/games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /home/luke/games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Addon pk4 /home/luke/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/luke/.quake4/q4base
/home/luke/games/quake4/q4base
/home/luke/games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/home/luke/games/quake4/q4base/zpak_italian.pk4 (3500 files)
/home/luke/games/quake4/q4base/zpak_french.pk4 (3462 files)
/home/luke/games/quake4/q4base/zpak_english_04.pk4 (3 files)
/home/luke/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/home/luke/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/home/luke/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/home/luke/games/quake4/q4base/zpak_english.pk4 (3457 files)
/home/luke/games/quake4/q4base/pak022.pk4 (14 files)
/home/luke/games/quake4/q4base/pak021.pk4 (89 files)
/home/luke/games/quake4/q4base/pak020.pk4 (11 files)
/home/luke/games/quake4/q4base/pak019.pk4 (1206 files)
/home/luke/games/quake4/q4base/pak018.pk4 (3 files)
/home/luke/games/quake4/q4base/pak017.pk4 (3 files)
/home/luke/games/quake4/q4base/pak016.pk4 (193 files)
/home/luke/games/quake4/q4base/pak015.pk4 (34 files)
/home/luke/games/quake4/q4base/pak014.pk4 (552 files)
/home/luke/games/quake4/q4base/pak013.pk4 (239 files)
/home/luke/games/quake4/q4base/pak012.pk4 (1081 files)
/home/luke/games/quake4/q4base/pak011.pk4 (5620 files)
/home/luke/games/quake4/q4base/pak010.pk4 (5539 files)
/home/luke/games/quake4/q4base/pak009.pk4 (1284 files)
/home/luke/games/quake4/q4base/pak008.pk4 (1289 files)
/home/luke/games/quake4/q4base/pak007.pk4 (1330 files)
/home/luke/games/quake4/q4base/pak006.pk4 (1343 files)
/home/luke/games/quake4/q4base/pak005.pk4 (1395 files)
/home/luke/games/quake4/q4base/pak004.pk4 (2249 files)
/home/luke/games/quake4/q4base/pak003.pk4 (1281 files)
/home/luke/games/quake4/q4base/pak002.pk4 (313 files)
/home/luke/games/quake4/q4base/pak001.pk4 (5837 files)
/home/luke/games/quake4/q4base/game200.pk4 (9 files)
/home/luke/games/quake4/q4base/game100.pk4 (2 files)
/home/luke/games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
/home/luke/games/quake4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 64 loaded
167ms to load 1125k of material
68ms to load 43k of skin
100ms to load 723k of sound
4ms to load 1k of materialType
247ms to load 2889k of lipSync
48ms to load 105k of playback
773ms to load 1690k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
696 strings read from strings/english_code.lang
1794 strings read from strings/english_guis.lang
5756 strings read from strings/english_lips.lang
5759 strings read from strings/english_mappack.lang
6235 strings read from strings/english_maps.lang
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
execing Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1280x1024 1280x960 1152x864 1024x768 960x600 960x540 840x525 832x624 800x600 720x450 720x400 
700x525 680x384 640x480 640x400 640x350 512x384 400x300 320x240 320x175 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1280x1024 1280x960 1152x864 1024x768 960x600 960x540 840x525 832x624 800x600 720x450 720x400 
700x525 680x384 640x480 640x400 640x350 512x384 400x300 320x240 320x175 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Fatal Error: Unable to initialize OpenGL
--------------- BSE Shutdown ----------------
---------------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL

```

I also have the libsdl1.2-pulseaudio installed (I have even tried reinstalling them).

Well here is my xorg.config file:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:45:35 PDT 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:44:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Compaq  P110"
    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 160.0
    Option         "DPMS"
	# HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
EndSection

Section "Screen"

	# Removed Option "metamodes" "nvidia-auto-select +0+0"
	# Removed Option "metamodes" "1280x1024 +0+0"
# Removed Option "metamodes" "1024x768 +0+0"
# Removed Option "metamodes" "1280x1024 +0+0"
# Removed Option "metamodes" "1280x1024_85 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "NoLogo" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024 +0+0; 1280x1024_85 +0+0"
    SubSection     "Display"
        Viewport 0 0
	Depth 24
	Modes "1280x1024" "1280x800" "1024x768" "1024x640" "800x600" "640x480"
    EndSubSection
EndSection

```

I Would love to get this game running Because I have Completely cut Microsoft out of my life! I want to see more people using Ubuntu, I have already converted my Brother and my mother and Father over to Ubuntu and they love it, But as for Gaming I need some help here and there.

Any Help in solving this issue would be Greatly Appreciated.

BTW I am currently running Ubuntu 10.04 x86 (32-bit).
Thanks in advance for any and all help!

---

### Post by Brebs on 2010-06-12
DefaultDepth should be 24, not 16.

Comment out your "Modes" line - let the nvidia driver do its own job.

Also try commenting out your metamodes line, just in case.

---

### Post by tommcd on 2010-06-12
> **Brebs said:**
> DefaultDepth should be 24, not 16.

+1
Setting the default depth to 24 solved the problem in this thread:
[http://www.mepis.org/node/11541](http://www.mepis.org/node/11541)
Hope this helps.

---

### Post by realdude19 on 2010-06-13
Ok Thanks Guys I had set the Color Depth to 24 But I must have forgotten to save the x config.

I am going to restart my system and see if it fixed the problem.

My new xconf is as follows:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:45:35 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Compaq  P110"
    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024 +0+0; 1280x1024_85 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I really hope this solves the OpenGL issue... Here goes...

---

### Post by realdude19 on 2010-06-13
Ok so I fixed my xconfig and when i try to start the Game (Quake4) I get this:

```
luke@BlueShift:~$ quake4
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface wlan0 - 192.168.0.104/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/luke/games/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /home/luke/games/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /home/luke/games/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
Loaded pk4 /home/luke/games/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /home/luke/games/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /home/luke/games/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /home/luke/games/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /home/luke/games/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /home/luke/games/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /home/luke/games/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /home/luke/games/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /home/luke/games/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /home/luke/games/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /home/luke/games/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /home/luke/games/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /home/luke/games/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /home/luke/games/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /home/luke/games/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /home/luke/games/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /home/luke/games/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /home/luke/games/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /home/luke/games/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /home/luke/games/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /home/luke/games/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /home/luke/games/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /home/luke/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /home/luke/games/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Loaded pk4 /home/luke/games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /home/luke/games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /home/luke/games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Addon pk4 /home/luke/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/luke/.quake4/q4base
/home/luke/games/quake4/q4base
/home/luke/games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/home/luke/games/quake4/q4base/zpak_italian.pk4 (3500 files)
/home/luke/games/quake4/q4base/zpak_french.pk4 (3462 files)
/home/luke/games/quake4/q4base/zpak_english_04.pk4 (3 files)
/home/luke/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/home/luke/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/home/luke/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/home/luke/games/quake4/q4base/zpak_english.pk4 (3457 files)
/home/luke/games/quake4/q4base/pak022.pk4 (14 files)
/home/luke/games/quake4/q4base/pak021.pk4 (89 files)
/home/luke/games/quake4/q4base/pak020.pk4 (11 files)
/home/luke/games/quake4/q4base/pak019.pk4 (1206 files)
/home/luke/games/quake4/q4base/pak018.pk4 (3 files)
/home/luke/games/quake4/q4base/pak017.pk4 (3 files)
/home/luke/games/quake4/q4base/pak016.pk4 (193 files)
/home/luke/games/quake4/q4base/pak015.pk4 (34 files)
/home/luke/games/quake4/q4base/pak014.pk4 (552 files)
/home/luke/games/quake4/q4base/pak013.pk4 (239 files)
/home/luke/games/quake4/q4base/pak012.pk4 (1081 files)
/home/luke/games/quake4/q4base/pak011.pk4 (5620 files)
/home/luke/games/quake4/q4base/pak010.pk4 (5539 files)
/home/luke/games/quake4/q4base/pak009.pk4 (1284 files)
/home/luke/games/quake4/q4base/pak008.pk4 (1289 files)
/home/luke/games/quake4/q4base/pak007.pk4 (1330 files)
/home/luke/games/quake4/q4base/pak006.pk4 (1343 files)
/home/luke/games/quake4/q4base/pak005.pk4 (1395 files)
/home/luke/games/quake4/q4base/pak004.pk4 (2249 files)
/home/luke/games/quake4/q4base/pak003.pk4 (1281 files)
/home/luke/games/quake4/q4base/pak002.pk4 (313 files)
/home/luke/games/quake4/q4base/pak001.pk4 (5837 files)
/home/luke/games/quake4/q4base/game200.pk4 (9 files)
/home/luke/games/quake4/q4base/game100.pk4 (2 files)
/home/luke/games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
/home/luke/games/quake4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 64 loaded
166ms to load 1125k of material
60ms to load 43k of skin
99ms to load 723k of sound
4ms to load 1k of materialType
247ms to load 2889k of lipSync
48ms to load 105k of playback
773ms to load 1690k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
696 strings read from strings/english_code.lang
1794 strings read from strings/english_guis.lang
5756 strings read from strings/english_lips.lang
5759 strings read from strings/english_mappack.lang
6235 strings read from strings/english_maps.lang
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
execing Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1280x1024 1280x960 1152x864 1024x768 960x600 960x540 840x525 832x624 800x600 720x450 720x400 
700x525 680x384 640x480 640x400 640x350 512x384 400x300 320x240 320x175 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1280x1024 1280x960 1152x864 1024x768 960x600 960x540 840x525 832x624 800x600 720x450 720x400 
700x525 680x384 640x480 640x400 640x350 512x384 400x300 320x240 320x175 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Fatal Error: Unable to initialize OpenGL
--------------- BSE Shutdown ----------------
---------------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL

```

So as far as I can tell its still doing the same thing... any ideas?

---

### Post by tommcd on 2010-06-13
> **realdude19 said:**
> Ok so I fixed my xconfig and when i try to start the Game (Quake4) I get this:

```

Loading GL driver 'libGL.so.1' through SDL

Do you have the **libsdl-image1.2** package installed? I know that in your first post you mentioned libsdl1.2-pulseaudio, but what about libsdl-image1.2 itself? 
Also, try commenting out the:
[CODE]Option         "metamodes" "1280x1024 +0+0; 1280x1024_85 +0+0"

```
line in your xorg.conf as Brebs suggested in his last post, then reboot and restart X.
I assume that your nvidia driver is working ok otherwise. Is that correct? What is the output of:
```
glxinfo | grep -i direct
```
It should report:
```
 tom@ubuntu:/data$ glxinfo | grep -i direct
**direct rendering: Yes**
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
```
or something like that. The important part is highlighted in bold (emphasis mine, for clarity).

I am not sure what else you could try at this point.

---

### Post by realdude19 on 2010-06-13
> **tommcd said:**
> Do you have the **libsdl-image1.2** package installed? I know that in your first post you mentioned libsdl1.2-pulseaudio, but what about libsdl-image1.2 itself?
Yes installed and running.

>  
Also, try commenting out the:
```
Option         "metamodes" "1280x1024 +0+0; 1280x1024_85 +0+0"

```
line in your xorg.conf as Brebs suggested in his last post, then reboot and restart X.

I didnt think that would be nessisary, but I will try it.

> 
I assume that your nvidia driver is working ok otherwise. Is that correct? What is the output of:
```
glxinfo | grep -i direct
```
It should report:
```
 tom@ubuntu:/data$ glxinfo | grep -i direct
**direct rendering: Yes**
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
```
or something like that. The important part is highlighted in bold (emphasis mine, for clarity).


BINGO! That is one thing I dont have right... I think I might have installed my nVidia Driver incorrectly or there was a missing step in the installation. But I did just notice today that all of my games are not starting and giving me video errors. ok so the code I get reads:

```
luke@BlueShift:~$ glxinfo | grep -i direct
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils

```

So I am assuming all I need to do is run the code that was suggested and all will be fine? cause rairly is that the case lol.

Well I am going to give this a try.



> 
I am not sure what else you could try at this point.

Thanks For the help! you did more than I could have asked for, now give me a few minutes to test this out...
Thanks again tommcd!

---

### Post by realdude19 on 2010-06-13
ok just to keep this simple. How can I uninstall my videodrivers and revert back to ones that will work? 

Or is there a simpler way to fix this problem?

Cause I tried the Mesa install and Nothing. I am starting to think that installing Nvidia Drivers are a Pain in the Rear...

oh and here is what I get now:
```

luke@BlueShift:~$ sudo glxinfo | grep -i direct
Error: glXCreateContext failed

```

God I wish there was a linux guru around my area...

---

### Post by realdude19 on 2010-06-13
Ok Everyone...

Well I Got Fed up with the Graphics drivers and dependencies being incorrect or whatever.. So I simply did this (Yes I Reinstalled my Drivers!):

First things First Download the newest Drivers from Nvidia [***HERE***]("http://www.nvidia.com/Download/index5.aspx?lang=en-us")

And please keep in mind where you downloaded it too. because you are going to have to navigate to that folder to run the installer on the second to last step.

```

sudo service gdm stop

sudo apt-get --purge remove nvidia-*

sudo reboot

```

Then after the system rebooted I went back into a console:

Ctrl + Alt +F1

2nd. Login. 
***If you have a numeric password refrain from using the Keypad! use the numbers above the QWERTY! or it wont let you log in at all. num Lock doesnt work in console.***

3RD. CD to the Folder you saved the installer in.
(Now this is where I said you would need to navigate to that folder you downloaded your driver to...)

```


sudo sh NVIDIA-  ***I HIT TAB A FEW TIMES HERE TO AUTO COMPLETE THE LINE***


```

After you followed all the installer steps please reboot your X by typing:

This will restart you GUI.
```
 
sudo service gdm start

```

Enjoy! :D

Thanks everyone for your input and help in trying to resolve my problems with Quake 4! It now loads perfectly and runs just as well. :D You all Rock!

---

### Post by tommcd on 2010-06-15
Sorry to get back to you so late.
Since you have an nvidia 9600GT, you could have just run:
```

sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot

```
Or go to: system > administration > hardware_drivers and enable the nvidia driver.
It is usually better to use the nvidia driver from the Ubuntu repos, so the package manager (APT) can take care of nvidia driver updates.

Just keep in mind that if (and when) there is a kernel update for Ubuntu you may need to reinstall the nvidia driver.

---

### Post by realdude19 on 2010-06-16
Oh yeah I have been reading up on that. its no big deal, I am trying to "Dive" into the CLI anyways. I really enjoy learning the system and all it ins and outs. 

I really appreciate the help though. I decided on installing the newest stable release from nVidia just to see if they might have ironed out any bugs. also I might be upgrading to a Gforce 480 later this month so I need the Drivers current to the hardware.

And I also was having Sound Issues with Quake 4 so I ended up installing all the libs I could find for Alsa and OpenAL and Wouldnt you know it... 

IT FIXED IT! Lol. Oh well I will iron out all the details later as I continue to live in the world or Ubuntu. :D

So far I am in love with it. but I just wish that Everything in my user (home/luke/) would all be writable... It seams I have to type "sudo" for everything...

also do you happen to know of a good thread to teach me how to make what Microsoft calls "Shortcuts"? because I would like to place some links on my desktop for games and include the "sudo" command so they will run correctly.

Thanks again. :)

---

### Post by tommcd on 2010-06-16
> **realdude19 said:**
> ... but I just wish that Everything in my user (home/luke/) would all be writable... It seams I have to type "sudo" for everything...
*Everything* in your home directory should be writable by you. This is the default in any linux distro.
**Two very important questions!! Both of which are verboten in Ubuntu!!!**

1. Have you enabled the root account???
2. Are you running the system as root ???

If you can answer both of these questions with a very firm and resounding NO!!!, then I do not know why anything in your home directory would not be writable by you.
In any case, if you run:
```
sudo chown -R luke:users /home/luke
```
This will set everything in /home/luke to be owned by you, but readable and possible executable by other users on the system. If you are the only user, then this is academic. If you want to set everything to only be readable by you, then run:
```
sudo chown -R luke:luke /home/luke
```
and you will be the only one who can access /home/luke
> **realdude19 said:**
> 
also do you happen to know of a good thread to teach me how to make what Microsoft calls "Shortcuts"? because I would like to place some links on my desktop for games and include the "sudo" command so they will run correctly.

What games are these? and how did you install them?
Any games in that you install from the Ubuntu repos should be available in the Applications menu for you without using sudo. 
If you installed anything else in any other way, then state what you installed, and exactly how you installed it.

---

### Post by realdude19 on 2010-06-17
> **tommcd said:**
> *Everything* in your home directory should be writable by you. This is the default in any linux distro.
**Two very important questions!! Both of which are verboten in Ubuntu!!!**

1. Have you enabled the root account???
2. Are you running the system as root ???

If you can answer both of these questions with a very firm and resounding NO!!!, then I do not know why anything in your home directory would not be writable by you.
In any case, if you run:
```
sudo chown -R luke:users /home/luke
```


I can answer both Questions with a Firm "NO" I would never do such a thing! 
I understand that Ubuntu is setup in such a manor as to protect us "n00bz" from making fatal mistakes and making our operating Systems in operable. Btw I keep a "Live" Disc close to me at all times cause I am exploring and learning from experience and helpful people as yourself. and I also understand that I could accidentally type something incorrectly into the CLI, so I am prepared and willing to reinstall.

Now that does bring up a very interesting Question:

Is there a Tool available to make a Image of my Ubuntu install as it stands so if a system fatal error is invoked I could more or less "Restore" the system from said image?

> **tommcd said:**
> 
What games are these? and how did you install them?
Any games in that you install from the Ubuntu repos should be available in the Applications menu for you without using sudo. 
If you installed anything else in any other way, then state what you installed, and exactly how you installed it.

Well mainly Quake 4... But that was only because I for some odd reason couldn't Edit the Config file in its respective directory. I guess I feared that if I couldn't edit that file then maybe the game would be having the same issue.. But I realize I am way off base I just don't understand the dynamics behind it.

I guess I just don't understand why some programs require to say install and then others don't, say when they are installed... Its almost as if the system gives the program root privileges. 

Does any of that make sense?

Well anyways thanks again for your time and patience. You are truly and asset to me in this endeavor to learn Ubuntu.
I guess I just want to learn all I can because I am the "Geek" when it comes to computers in my family and I would like to save my family money and in return give them an outstanding solution such as Ubuntu is. 

I simply feel Microsoft is taking advantage of people with their OS and Office productivity suite. and I know a Community is stronger when there are more people involved and contributing to the cause. 

:D

---

### Post by tommcd on 2010-06-17
> **realdude19 said:**
> 
Is there a Tool available to make a Image of my Ubuntu install as it stands so if a system fatal error is invoked I could more or less "Restore" the system from said image?
When the new Btrfs file system is eventually included in a future release of Ubuntu, there will be this kind of restore from a snapshot backup capability:
[https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)
Btrfs is available for Ubuntu now, but it is not yet ready for prime time from what I have read:
[http://ubuntuforums.org/showthread.php?t=1389279&highlight=btrfs+file+system](http://ubuntuforums.org/showthread.php?t=1389279&highlight=btrfs+file+system)
In the meantime there is **remastersys** that can be used to backup your Ubuntu and make a live CD / DVD of that backup:
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
> **realdude19 said:**
> 
Well mainly Quake 4... But that was only because I for some odd reason couldn't Edit the Config file in its respective directory. I guess I feared that if I couldn't edit that file then maybe the game would be having the same issue.. But I realize I am way off base I just don't understand the dynamics behind it.
If you installed Quake4 to /usr/local/games (which is the default if I remember correctly) using sudo, then you clicked "yes" to "launch the game now" (or whatever it exactly says) then this screws up the game's permissions so that it must be run using sudo. Choosing "no" and exiting from the installer would enable the game to run without sudo. I found this out the hard way the first time I installed Quake4. I did manage to fix it, but I had to change the permissions on a lot of the Quake4 files. Since I don't have Quake4 installed right now, I am not sure exactly what I did to fix it.
If you installed Quake4 to your home directory (which also works fine) without using sudo to install it, then it should run without sudo just by running **quake4** in the terminal.
You should be able to right-click on the Applications menu and select "edit menus". Then you can navigate to "games" and add an entry to launch Quake4.

---

### Post by realdude19 on 2010-06-17
Thanks Tommcd. 

I Added you to my Yahoo IM. But That was on a whim. I am sure I have gotten a grip on the situation thanks to you.

I am going to Mess around with KDE a bit. I just installed all Desktop and I am a bit curious.

ttyl and ty again.

P.s. "sayhitoluke"

---


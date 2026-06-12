---
title: "Quake 4 Not runnig"
date: 2008-06-11
forum: Gaming &amp; Leisure
---

### Post by kayfes on 2008-06-11
It starts the boot sequence but stops:

steven@steven-desktop:~$ sudo quake4
[sudo] password for steven: 
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface eth0 - 192.168.1.4/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /usr/local/games/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
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
Loaded pk4 /usr/local/games/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /usr/local/games/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Addon pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/steven/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_english_04.pk4 (3 files)
/usr/local/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/usr/local/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/usr/local/games/quake4/q4base/zpak_english.pk4 (3457 files)
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
/usr/local/games/quake4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 64 loaded
282ms to load 1125k of material
66ms to load 43k of skin
187ms to load 723k of sound
3ms to load 1k of materialType
376ms to load 2889k of lipSync
76ms to load 105k of playback
941ms to load 1690k of effect
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
1680x1050 1600x1024 1440x900 1400x1050 1280x1024 1280x960 1280x800 1280x768 1152x864 1024x768 960x600 
896x672 840x525 832x624 800x600 800x512 720x450 700x525 640x512 640x480 640x400 
640x384 576x432 512x384 416x312 400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1680x1050 1600x1024 1440x900 1400x1050 1280x1024 1280x960 1280x800 1280x768 1152x864 1024x768 960x600 
896x672 840x525 832x624 800x600 800x512 720x450 700x525 640x512 640x480 640x400 
640x384 576x432 512x384 416x312 400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Fatal Error: Unable to initialize OpenGL
--------------- BSE Shutdown ----------------
---------------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL


It was working yesterday with no sound but I would rather have no sound then no Quake.

---

### Post by Sleaka J on 2008-06-11
First, you shouldn't be running it with 'sudo'. Why are you doing it that way? I have Quake 4 working perfectly (almost finished actually) and 'sudo' is most certainly not required.

Secondly, do you have the correct video drivers installed? What video card do you have? Can you run glxgears?

---

### Post by breadbin on 2008-06-12
Hiya I had problems getting QUake 4 running too with Nvidia. I can't tell you a specific way to solve it because I don't know how  I did it but I installed the nvidia package drivers from ubuntu and then uninstalled them then installed the nvidia ones from installer and then it somehow worked. I also used synaptic to install anything related to nvidia. I hope you find the solution and sorry I couldn't be more help. I'm a noob

---

### Post by Sleaka J on 2008-06-12
I install all my video drivers using EnvyNG, which is in the repositories. The latest version that's installed by that is 169.12, not the newer 173 drivers (which people have reported a slight decrease in performance with them).

---

### Post by Sockerdrickan on 2008-06-12
> **Sleaka J said:**
> I install all my video drivers using EnvyNG, which is in the repositories. The latest version that's installed by that is 169.12, not the newer 173 drivers (which people have reported a slight decrease in performance with them).
I bet that depends on what gpu you are using though

---

### Post by Sleaka J on 2008-06-12
> **Tux0r said:**
> I bet that depends on what gpu you are using though

Actually, the guy who wrote EnvyNG has specifically said that the newer driver version needs to be written into the program. The latest nVidia driver it will install is 169.12 and the latest ATI driver it will install is 8.4 and there are newer drivers for both (You can force it to install whatever version you want listed in the program).

So it's just a matter of waiting until he's written support for the newer driver versions, AND waiting for it to appear in the Ubuntu repositories.

I haven't tried to install the newer 173 drivers manually because I've heard reports of a performance decrease in that version and since I own a 7600GS, I need all the performance I can get.

---

### Post by BBQ'er on 2008-06-13
```
Fatal Error: Unable to initialize OpenGL
--------------- BSE Shutdown ----------------
---------------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL
```It failed to start the openGL.

That im pretty sure is directed towards your drivers for your video card.
 Check to see if you have anything listed in system/administration/hardware drivers/. 
Select your video card drivers from that list if it's avalible.

---

### Post by kayfes on 2008-06-18
Ok this is kind of weird.  I reinstalled Ubuntu Hardy onto my large drive to run as the main drive.  Thus I had a completely fresh install.  My drivers are up to date.  I have an nvidia 9600gt and I learned how to install the drivers on the first drive I had Ubuntu installed on.  Now I had the game running fine I even got sound working this time.  I changed some settings and quit Quake 4 to post a reply on a different forum topic about how I had gotten the sound working.  I changed Anti aliasing to run at 16X and something else don't remember it was 2 hours ago and Im still stuck with the same error I was running into before but just beause I will post it over again in case some is different.




steven@steven-desktop:~$ quake4
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface eth0 - 192.168.1.4/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /usr/local/games/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
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
Loaded pk4 /usr/local/games/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /usr/local/games/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Addon pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/steven/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_english_04.pk4 (3 files)
/usr/local/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/usr/local/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/usr/local/games/quake4/q4base/zpak_english.pk4 (3457 files)
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
/usr/local/games/quake4/q4base/pak012.pk4 (1081 files)
/usr/local/games/quake4/q4base/pak011.pk4 (5620 files)
/usr/local/games/quake4/q4base/pak010.pk4 (5539 files)
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
134ms to load 243k of material
70ms to load 43k of skin
197ms to load 723k of sound
2ms to load 0k of materialType
387ms to load 2889k of lipSync
1ms to load 0k of playback
62ms to load 25k of effect
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
1680x1050 1600x1024 1440x900 1400x1050 1280x1024 1280x960 1280x800 1280x768 1152x864 1024x768 960x600 
896x672 840x525 832x624 800x600 800x512 720x450 700x525 640x512 640x480 640x400 
640x384 576x432 512x384 416x312 400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1680x1050 1600x1024 1440x900 1400x1050 1280x1024 1280x960 1280x800 1280x768 1152x864 1024x768 960x600 
896x672 840x525 832x624 800x600 800x512 720x450 700x525 640x512 640x480 640x400 
640x384 576x432 512x384 416x312 400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Fatal Error: Unable to initialize OpenGL
--------------- BSE Shutdown ----------------
---------------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL


Oh and yeah I got it to run without sudo and I tried to use sudo anyways just to see if that was the problem but that didn't work.



Does anyone know if there is a way have Q4 run in the original display settings for example is there something I can type into the terminal to reset them to default.

I also tried deleting all the files Q4 installs and then reinstalling and still I get the same result.  

Also I have tried the method of making changes to the xorg.conf and they didn't work so I went to my backup and here I with the same results.

I am pretty sure that it has something to with the settings I changed and I don't think I completely uninstalled/deleted Q4 before reinstalling it because I had this game working with sound and everything before I made those changes.

Any help would be great.

---

### Post by rajeev1204 on 2008-06-18
> **kayfes said:**
> Ok this is kind of weird.  I reinstalled Ubuntu Hardy onto my large drive to run as the main drive.  Thus I had a completely fresh install.  My drivers are up to date.  I have an nvidia 9600gt and I learned how to install the drivers on the first drive I had Ubuntu installed on.  Now I had the game running fine I even got sound working this time.  I changed some settings and quit Quake 4 to post a reply on a different forum topic about how I had gotten the sound working.  I changed Anti aliasing to run at 16X and something else don't remember it was 2 hours ago and Im still stuck with the same error I was running into before but just beause I will post it over again in case some is different.




steven@steven-desktop:~$ quake4
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface eth0 - 192.168.1.4/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /usr/local/games/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
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
Loaded pk4 /usr/local/games/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /usr/local/games/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Addon pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/steven/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_english_04.pk4 (3 files)
/usr/local/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/usr/local/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/usr/local/games/quake4/q4base/zpak_english.pk4 (3457 files)
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
/usr/local/games/quake4/q4base/pak012.pk4 (1081 files)
/usr/local/games/quake4/q4base/pak011.pk4 (5620 files)
/usr/local/games/quake4/q4base/pak010.pk4 (5539 files)
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
134ms to load 243k of material
70ms to load 43k of skin
197ms to load 723k of sound
2ms to load 0k of materialType
387ms to load 2889k of lipSync
1ms to load 0k of playback
62ms to load 25k of effect
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
1680x1050 1600x1024 1440x900 1400x1050 1280x1024 1280x960 1280x800 1280x768 1152x864 1024x768 960x600 
896x672 840x525 832x624 800x600 800x512 720x450 700x525 640x512 640x480 640x400 
640x384 576x432 512x384 416x312 400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1680x1050 1600x1024 1440x900 1400x1050 1280x1024 1280x960 1280x800 1280x768 1152x864 1024x768 960x600 
896x672 840x525 832x624 800x600 800x512 720x450 700x525 640x512 640x480 640x400 
640x384 576x432 512x384 416x312 400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Fatal Error: Unable to initialize OpenGL
--------------- BSE Shutdown ----------------
---------------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL


Oh and yeah I got it to run without sudo and I tried to use sudo anyways just to see if that was the problem but that didn't work.



Does anyone know if there is a way have Q4 run in the original display settings for example is there something I can type into the terminal to reset them to default.

I also tried deleting all the files Q4 installs and then reinstalling and still I get the same result.  

Also I have tried the method of making changes to the xorg.conf and they didn't work so I went to my backup and here I with the same results.

I am pretty sure that it has something to with the settings I changed and I don't think I completely uninstalled/deleted Q4 before reinstalling it because I had this game working with sound and everything before I made those changes.

Any help would be great.


Yes, quake 4 wont run with 16 X. antialiasing.


go the the .quake4 folder in ur home .(its hidden file) and search for r_multisampling and set it to 8x or lower.





regards

rajeev

---

### Post by kayfes on 2008-06-18
Thanks jeev thats what I figured it was.  Im installing my printer at the moment and will try that out afterwards.

---

### Post by kayfes on 2008-06-18
Still not able to get the OpenGL to initialize.

steven@steven-desktop:~$ quake4 +set s_driver oss
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface eth0 - 192.168.1.4/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /usr/local/games/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
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
Loaded pk4 /usr/local/games/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /usr/local/games/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Addon pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/steven/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_english_04.pk4 (3 files)
/usr/local/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/usr/local/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/usr/local/games/quake4/q4base/zpak_english.pk4 (3457 files)
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
/usr/local/games/quake4/q4base/pak012.pk4 (1081 files)
/usr/local/games/quake4/q4base/pak011.pk4 (5620 files)
/usr/local/games/quake4/q4base/pak010.pk4 (5539 files)
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
76ms to load 243k of material
49ms to load 43k of skin
213ms to load 723k of sound
2ms to load 0k of materialType
389ms to load 2889k of lipSync
1ms to load 0k of playback
21ms to load 25k of effect
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
1680x1050 1600x1024 1440x900 1400x1050 1280x1024 1280x960 1280x800 1280x768 1152x864 1024x768 960x600 
896x672 840x525 832x624 800x600 800x512 720x450 700x525 640x512 640x480 640x400 
640x384 576x432 512x384 416x312 400x300 320x240 
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1680x1050 1600x1024 1440x900 1400x1050 1280x1024 1280x960 1280x800 1280x768 1152x864 1024x768 960x600 
896x672 840x525 832x624 800x600 800x512 720x450 700x525 640x512 640x480 640x400 
640x384 576x432 512x384 416x312 400x300 320x240 
Fatal Error: Unable to initialize OpenGL
--------------- BSE Shutdown ----------------
---------------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL


Also got rid of the error message asking to set r_useSDLModes "1".

Have no idea whats going on here any help would be welcomed.

---

### Post by kayfes on 2008-06-18
Ok how about this can anyone tell me the best way to uninstall Q4 completely so that I can try with a fresh install of it?  Thank you in advance.

---

### Post by rajeev1204 on 2008-06-19
hi

I think u need to reinstall it again as it seems a lot of pak files are missing. Like i said in a previous thread of yours,all 4 cds have the pak files and u have to copy them .


Just follow my instructions from that thread and make sure u have all pak files from 1 to 14 or so.




regards

rajeev

---

### Post by breadbin on 2008-06-22
yeah I have 29 .pk4 files in my quake4 directory. theres also pk4.off files there. 62 files in total. hope that helps. can't help you with uninstalling. never did it but try google.

---


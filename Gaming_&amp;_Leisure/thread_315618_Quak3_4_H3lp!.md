---
title: "Quak3 4 H3lp!"
date: 2006-12-09
forum: Gaming &amp; Leisure
---

### Post by ZERO_SHIFT on 2006-12-09
I tried running Quake 4 on my laptop with the following specs:

Intel Core2 2.0Ghz
2 GB RAM
128 MB nVIDIA 7200 GeFORCE
Ubuntu 6.10

As I tried running the quake4 command I got the following:

```
zaid@zaid-laptop:~$ quake4
Quake4 Final V1.0.0.0 Build 2147.12 linux-x86 Oct 20 2005
found interface lo - loopback
found interface eth0 - 192.168.2.3/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x6f346a2
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
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /usr/local/games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /usr/local/games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /usr/local/games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Current search path:
/home/zaid/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/usr/local/games/quake4/q4base/zpak_italian.pk4 (3500 files)
/usr/local/games/quake4/q4base/zpak_french.pk4 (3462 files)
/usr/local/games/quake4/q4base/zpak_english.pk4 (3457 files)
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
/usr/local/games/quake4/q4base/game100.pk4 (2 files)
/usr/local/games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 59 loaded
277ms to load 1071k of material
64ms to load 43k of skin
130ms to load 716k of sound
4ms to load 1k of materialType
253ms to load 2078k of lipSync
65ms to load 105k of playback
882ms to load 1665k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
632 strings read from strings/english_code.lang
1654 strings read from strings/english_guis.lang
5616 strings read from strings/english_lips.lang
6085 strings read from strings/english_maps.lang
632 strings read from strings/french_code.lang
1654 strings read from strings/french_guis.lang
5616 strings read from strings/french_lips.lang
6085 strings read from strings/french_maps.lang
632 strings read from strings/italian_code.lang
1654 strings read from strings/italian_guis.lang
5616 strings read from strings/italian_lips.lang
6085 strings read from strings/italian_maps.lang
632 strings read from strings/spanish_code.lang
1654 strings read from strings/spanish_guis.lang
5616 strings read from strings/spanish_lips.lang
6085 strings read from strings/spanish_maps.lang
Couldn't open journal files
execing default.cfg
"ALT" isn't a valid key
"CTRL" isn't a valid key
couldn't exec editor.cfg
couldn't exec Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
TODO: Sys_SetClipboardData
********************
ERROR: SDL_SetVideoMode failed: Couldn't find matching GLX visual
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: SDL_SetVideoMode failed: Couldn't find matching GLX visual

```

I installed quake4 installer and I moved the files they required.
 
I did install the nVIDIA driver through Automatix2.

Any ideas?

Thanks in advance.

---

### Post by billyfoxtrot on 2006-12-09
What does your /etc/X11/xorg.conf file look like?  Try changing the DefaultDepth under "Screen" to 24 if it's still at 16 then restart your computer.  I think that's how I fixed this problem.

---

### Post by ZERO_SHIFT on 2006-12-09
That did solve the problem!

But the bad news is as soon as I started the game I tried to adjust my screen to 1280x1024 and then restarted quake and I got this.

```
zaid@zaid-laptop:~$ quake4
Quake4 Final V1.0.0.0 Build 2147.12 linux-x86 Oct 20 2005
found interface lo - loopback
found interface eth0 - 192.168.1.9/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x6f346a2
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
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /usr/local/games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /usr/local/games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /usr/local/games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Current search path:
/home/zaid/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/usr/local/games/quake4/q4base/zpak_italian.pk4 (3500 files)
/usr/local/games/quake4/q4base/zpak_french.pk4 (3462 files)
/usr/local/games/quake4/q4base/zpak_english.pk4 (3457 files)
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
/usr/local/games/quake4/q4base/game100.pk4 (2 files)
/usr/local/games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 59 loaded
258ms to load 1071k of material
47ms to load 43k of skin
129ms to load 716k of sound
4ms to load 1k of materialType
254ms to load 2078k of lipSync
46ms to load 105k of playback
969ms to load 1665k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
632 strings read from strings/english_code.lang
1654 strings read from strings/english_guis.lang
5616 strings read from strings/english_lips.lang
6085 strings read from strings/english_maps.lang
632 strings read from strings/french_code.lang
1654 strings read from strings/french_guis.lang
5616 strings read from strings/french_lips.lang
6085 strings read from strings/french_maps.lang
632 strings read from strings/italian_code.lang
1654 strings read from strings/italian_guis.lang
5616 strings read from strings/italian_lips.lang
6085 strings read from strings/italian_maps.lang
632 strings read from strings/spanish_code.lang
1654 strings read from strings/spanish_guis.lang
5616 strings read from strings/spanish_lips.lang
6085 strings read from strings/spanish_maps.lang
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
TODO: Sys_SetClipboardData
********************
ERROR: SDL_SetVideoMode failed: No video mode large enough for 1280x1024
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: SDL_SetVideoMode failed: No video mode large enough for 1280x1024

```

I tried reinstalling quake but that did not work, by deleting the file but that did not work.

Is there any other way in which I can restore the default settings? any .config file I can play with?

Thanks.

---

### Post by ZERO_SHIFT on 2006-12-09
OK I fixed that.

However now when I restart quake 4 the previous settings are not implemented?

They just go back o the default.

Any ideas?

---

### Post by Perfect Storm on 2006-12-10
Any output?

---

### Post by testbenchdude on 2006-12-10
How do you launch it? I use sudo quake4 because otherwise it won't run... maybe your permissions are screwy, not letting quake write new settings for itself? I dunno, just throwing out ideas...

---

### Post by Perfect Storm on 2006-12-10
It's properly because you ran Quake afterwards from the installer window. This will give you permission problems and can be one of the reasons that it goes back to default/can't save.

---

### Post by ZERO_SHIFT on 2006-12-10
Okay, I fixed the problem by running the command

```
sudo quake4 +set s_driver oss
```

Thanks **_testbenchdude_**:-D 

And telling it to run the command from terminal. However it's a bit frustrating to have to enter the root password whenever I want to play.](*,) 

Is there a way of not using the sudo command, and still be able to save and change settings in the game.

Thanks in advance.

---

### Post by Perfect Storm on 2006-12-10
```
sudo chown -R [User]:[user] /home/[user]/[Quake3-folder]
```

The quake3 folder is hidden in your home folder **.quake3** perhaps?

---

### Post by ZERO_SHIFT on 2006-12-11
its quake 4 = QUAK3 4

---

### Post by Perfect Storm on 2006-12-11
then change it to **.quake4** :p

---

### Post by ZERO_SHIFT on 2006-12-14
This is an update:

Patch v1.3 for Quake 4 on Linux fixes most of these problems:rolleyes:

---


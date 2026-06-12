---
title: "Problem running quake4"
date: 2006-06-21
forum: Gaming &amp; Leisure
---

### Post by bocmaxima on 2006-06-21
I installed it, I think, and when I go to run it, i get

Quake4 Final V1.2.1.2386 Build 2386.0 linux-x86 Apr 28 2006
found interface lo - loopback
found interface eth0 - 69.221.105.193/255.255.255.252
CPU: AMD CPU with MMX & 3DNow! & SSE
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0x84912b4d
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x8318e568
Loaded pk4 /usr/local/games/quake4/q4base/game200.pk4 with checksum 0xce75dc68
Loaded pk4 /usr/local/games/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /usr/local/games/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /usr/local/games/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /usr/local/games/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /usr/local/games/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /usr/local/games/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /usr/local/games/quake4/q4base/zpak_french_01.pk4 with checksum 0xe909853f
Loaded pk4 /usr/local/games/quake4/q4base/zpak_french_02.pk4 with checksum 0x3e376694
Loaded pk4 /usr/local/games/quake4/q4base/zpak_italian_01.pk4 with checksum 0xef0e1696
Loaded pk4 /usr/local/games/quake4/q4base/zpak_italian_02.pk4 with checksum 0xca9e1dbd
Loaded pk4 /usr/local/games/quake4/q4base/zpak_spanish_01.pk4 with checksum 0xe829a04a
Loaded pk4 /usr/local/games/quake4/q4base/zpak_spanish_02.pk4 with checksum 0xc28f719d
Current search path:
/home/bocmaxima/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_spanish_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_spanish_01.pk4 (2 files)
/usr/local/games/quake4/q4base/zpak_italian_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_italian_01.pk4 (2 files)
/usr/local/games/quake4/q4base/zpak_french_02.pk4 (22 files)
/usr/local/games/quake4/q4base/zpak_french_01.pk4 (2 files)
/usr/local/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_english_01.pk4 (1 files)
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
TODO: Sys_SetClipboardData
********************
ERROR: Couldn't load default.cfg  -  Check your working folder.
********************
Unknown command 'vid_restart'
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg  -  Check your working folder.

---

### Post by MetalMusicAddict on 2006-06-21
Did you copy the q4base dir. from the cds/dvd *before* you ran the installer?

---

### Post by bocmaxima on 2006-06-21
[QUOTE=MetalMusicAddict]Did you copy the q4base dir. from the cds/dvd *before* you ran the installer?[/QUOTE]


No, no I did not :(

I am not sure how to do that anyway. At least not graphically.

---

### Post by MetalMusicAddict on 2006-06-21
Then you dont actually have it installed. You need to copy the "q4base" directory (which has all the models,textures and such) from your media *then* run the installer.

For me I installed Quake to **/home/atm/.quake4**. Within that .quake4 dir. is the q4base dir. The CD/DVD files would go there *then* run the installer. You can install as sudo or a user. 

Do you have the CD or DVD?

---

### Post by bocmaxima on 2006-06-21
[QUOTE=MetalMusicAddict]Then you dont actually have it installed. You need to copy the "q4base" directory (which has all the models,textures and such) from your media *then* run the installer.

For me I installed Quake to **/home/atm/.quake4**. Within that .quake4 dir. is the q4base dir. The CD/DVD files would go there *then* run the installer. You can install as sudo or a user. 

Do you have the CD or DVD?[/QUOTE]


what are the commands to copy them? I tried doing drag and drop but it said I didnt have permissions.

Yeah, I have the CDs :)

---

### Post by MetalMusicAddict on 2006-06-21
From a terminal: **gksudo nautilus**. Then you can drag and drop. Give [THIS FAQ]("http://zerowing.idsoftware.com/linux/quake4/") a look also.

---

### Post by bocmaxima on 2006-06-21
[QUOTE=MetalMusicAddict]From a terminal: **gksudo nautilus**. Then you can drag and drop. Give [THIS FAQ]("http://zerowing.idsoftware.com/linux/quake4/") a look also.[/QUOTE]


Cool, got it running but the sound is all screwed up. Sounds like everything is run through an electronic filter or something.

---

### Post by deathbyswiftwind on 2006-06-21
Open a terminal and enter this command that will solve your sound issue.

```
quake4 +set s_driver oss
```

Also since quake 4 comes with a shitty icon Ive included one I found maybe youll like it

---

### Post by MetalMusicAddict on 2006-06-22
deathbyswiftwinds got it. I like these icons I found on DeviantArt.

[[IMG]http://tn3-1.deviantart.com/300W/fs7.deviantart.com/i/2005/235/9/f/Q_s_Quake_4_Dock_Icons_by_webtrance.jpg[/IMG]]("http://www.deviantart.com/deviation/22101333/")

---

### Post by deathbyswiftwind on 2006-06-22
Cool icons you found man I got mine from deviantart as well. Also for anyones reference if they get Doom 3 the same command is needed to get sound in D3 running right

---

### Post by MetalMusicAddict on 2006-06-23
This might be stupid but wouldnt it be just like: **doom3 +set s_driver oss**?

---

### Post by bocmaxima on 2006-06-23
[QUOTE=deathbyswiftwind]Open a terminal and enter this command that will solve your sound issue.

```
quake4 +set s_driver oss
```

Also since quake 4 comes with a shitty icon Ive included one I found maybe youll like it[/QUOTE]

Perfect!

---

### Post by deathbyswiftwind on 2006-06-23
[QUOTE=MetalMusicAddict]This might be stupid but wouldnt it be just like: **doom3 +set s_driver oss**?[/QUOTE]

yeah thats what i meant sorry i was tired :mrgreen:

---

### Post by MetalMusicAddict on 2006-06-23
[QUOTE=deathbyswiftwind]yeah thats what i meant sorry i was tired :mrgreen:[/QUOTE]
Crap man. I just re-read your post I thought you were asking. :)

---


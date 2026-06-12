---
title: "quake 4 issues &amp; program questions"
date: 2006-06-12
forum: Gaming &amp; Leisure
---

### Post by tokez on 2006-06-12
hey guys. I just bought a copy of quake 4 and it is supposed to have decent/good linux support. most of the gamers are saying better than windows even.

my problem is when i run the game after copying the files off the cd and running the installer, my game is extremely choppy and slow to respond. the audio is garbled and the video is amazingly terrible for my computer.

not amazing but 128mb 9700pro, 2.2ghz 64bit proc, and 1.5gbs of ram should be able to handle quake 4 fairly easy.

if anyone else had this problem and knows a solution please help.

i followed this guide [Linux FAQ]("http://zerowing.idsoftware.com/linux/quake4/")

---

### Post by benplaut on 2006-06-12
have you installed the FGLRX drivers for your card? ATI support is really horrid, regardless.

---

### Post by tokez on 2006-06-12
i had quake4 installed on my dapper system before the release. for some reason it wont even start up now.

i am considering doing it thru cedega or even installing a windows partition for it alone. this would be a solution but not what i want.

heres my error output from terminal.
```
quake4
```

error:
```
...
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
 
```

---


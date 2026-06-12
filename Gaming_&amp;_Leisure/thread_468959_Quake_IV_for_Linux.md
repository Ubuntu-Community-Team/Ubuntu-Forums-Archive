---
title: "Quake IV for Linux"
date: 2007-06-09
forum: Gaming &amp; Leisure
---

### Post by facthemighty on 2007-06-09
[ Quake IV Linux](http://zerowing.idsoftware.com/linux/quake4/)


Errror report.

```

rof@rof2:~$ /home/rof/quake4/quake4
Quake4 Final V1.0.0.0 Build 2147.12 linux-x86 Oct 20 2005
found interface lo - loopback
found interface eth0 - 192.168.1.14/255.255.255.0
CPU: Intel CPU with MMX & SSE
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/rof/quake4/q4base/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /home/rof/quake4/q4base/q4base/game100.pk4 with checksum 0x6f346a2
Current search path:
/home/rof/.quake4/q4base
/home/rof/quake4/q4base/q4base
/home/rof/quake4/q4base/q4base/game100.pk4 (2 files)
/home/rof/quake4/q4base/q4base/game000.pk4 (2 files)
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

Another error trying to install via WINE.

DLL error about CD KEY?

---

### Post by Ferrat on 2007-06-09
no your missing a config file and looks like you are missing the game pk4 files from the cd?

---

### Post by Sockerdrickan on 2007-06-09
And lol why use 1.0 when 1.4.1 is here

---

### Post by Enverex on 2007-06-09
The Quake 4 installer is a bit **** to be honest. It doesn't actually install anything! (well, a few files). You have to manually copy across the files from the CD. This is all documented in the archive that you downloaded and ran the installer from.

---

### Post by facthemighty on 2007-06-09
I noticed the installer made a new "quake4" folder rather than copying the files into my "Quake4" folder. So... Linux recognizes upper and lowercase. I found that out a few days ago. 

[I found another thread on a seperate forum that glossed over my problem. ](http://www.linuxquestions.org/questions/showthread.php?t=378312&page=2)

---


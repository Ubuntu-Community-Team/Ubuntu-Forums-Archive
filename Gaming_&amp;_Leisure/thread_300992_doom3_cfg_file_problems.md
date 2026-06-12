---
title: "doom3 cfg file problems"
date: 2006-11-16
forum: Gaming &amp; Leisure
---

### Post by doh224 on 2006-11-16
------ Initializing renderSystem --------
idRenderSystem::Shutdown()
Sys_Error: _default material not found
doh224@dit-7wht5kdiqox:/usr/local/games/doom3/base/base$ doom3
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.1.76/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/doh224/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
idRenderSystem::Shutdown()
Sys_Error: _default material not found


when I start doom3, it says like this. I have moved the default.cfg file to the base folder. Does anybody have a solution? 
many thanks if help comes.
-doh ;)

---

### Post by dagrump on 2006-11-18
I think pak004.pk4 is missing?

---

### Post by dagrump on 2006-11-18
Looking at it again there might be more *.pk4 files missing, I'm guessing from what files are in my /usr/local/games/doom3/base directory.

---


---
title: "Uninstallation of Games"
date: 2006-02-13
forum: Gaming &amp; Leisure
---

### Post by Jaygo333 on 2006-02-13
How do I uninstall games. 
So far, I've tried to play doom but ATI has been giving me toom any probles so I thought I would just uninstall it.The problem is, I don't know how to. 
I've tried apt-get, synaptic or even deleting the directory itself but cannot manage to do it.How do I just delete the problem.

Another thing, when I run doom3 I get the following errors.

jaygo333@Ubuntu:~$ doom3
DOOM 1.1.1286 linux-x86 Nov 24 2004 17:56:04
Hostname: localhost.localdomain
Alias: localhost
Alias: Ubuntu
local IP: 127.0.0.1
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0x7dafc4d4
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x16cf3b8a
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Current search path:
/home/jaygo333/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg
jaygo333@Ubuntu:~$

ATI isn't it. Graphics problems.

Just how do I remove it. Another thing, 
When I remove some apps from ubuntu, they still leave links in the "start" menu.I don't know how to remove those. HELP

:h34r: Jaygo333 :h34r:

---

### Post by Elvish Legion on 2006-02-13
Open Synaptic Package Manger

Search for what you are trying to remove (in my example lets use Cedega)

Type Cedega in search

It should bring up the program 

Click and select mark for removal

---

### Post by Jaygo333 on 2006-02-13
The method seemed to work for apps like cedega, but wot about games.
I tried it on Doom 3 but it didn't work. 
How do I remove doom 3.?

:h34r: Jaygo333 :h34r:

---

### Post by LordBug on 2006-02-14
Manually installed items will have to be manually un-installed. Nuke the Doom 3 directory (rm -rf) and away it goes.

---


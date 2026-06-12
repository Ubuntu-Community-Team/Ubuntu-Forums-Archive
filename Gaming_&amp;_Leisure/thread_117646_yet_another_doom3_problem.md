---
title: "yet another doom3 problem"
date: 2006-01-15
forum: Gaming &amp; Leisure
---

### Post by jonny_boy27 on 2006-01-15
i've read most of the other doom3 problem threads on here but cant find on that matches the trouble i'm having. i installed doom3 as per the ubuntu wiki and copied the pak's from my doom3 cds but when i run doom3 i get this error:
```

DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth1 - 192.168.0.90/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/jonathan/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg

```

my graphics card is a radeon 9800pro and i've installed the fglrx drivers that are supplied with breezy

---

### Post by Mr_Grieves on 2006-01-15
vid_restart is a command in Doom 3 that starts the rendersystem according to this: [http://www.fakepope.com/doom3/command.php?id=122](http://www.fakepope.com/doom3/command.php?id=122)

My guess is that there were some problems when you installed Doom 3 or there is support issues with you're graphics card or drivers. Try reinstalling the game.

Here's another guide on Doom 3 and Linux:
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=54](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=54)

Else, try upgrade you're drivers, try searching the web on you're graphics card and parts of that error message. That's the best advice I can give you.

---


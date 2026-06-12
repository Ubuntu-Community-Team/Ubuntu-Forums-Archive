---
title: "Doom # Will Not Run"
date: 2007-03-26
forum: Gaming &amp; Leisure
---

### Post by LordZallen on 2007-03-26
Ok guys, my Doom 3 is not running... when i get a console i get this output

DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth1 - 192.168.2.2/255.255.255.0
found interface eth0:avahi - 169.254.9.120/255.255.0.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/clarkd/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
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

I tried the doomconfig at this URL [http://ubuntuforums.org/showthread.php?t=287612](http://ubuntuforums.org/showthread.php?t=287612)

tried renaming it default.cfg and the output was thiis

DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth1 - 192.168.2.2/255.255.255.0
found interface eth0:avahi - 169.254.9.120/255.255.0.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/clarkd/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
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
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
idRenderSystem::Shutdown()
Sys_Error: _default material not found

I'm on feisty, using the r300 dri drivers (accelerated) , output for glxinfo is below, so that's not the problem i think...

glxinfo | grep rendering
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

My hardware specs are an Athlon XP 3200+, 1 GB DDR400, Asus A7N8X-E Deluxe, Radeon 9800 XT

If you guys have anything that could help me, I'd REALLY appreciate it. Thanks! :)

---

### Post by Monk-e on 2007-03-26
You forgot to copy pak000.pk4 and game00.pk4 from your doom3 cds/dvd. :)

---

### Post by LordZallen on 2007-03-26
omg, :lolflag: i made such a n00bish mistake... thanks for the help!

---

### Post by MiD-AwE on 2007-04-18
If you don't mind my asking, Has anyone else experiencing performance loss in DOOM3 since Feisty, or could it be that I'm using a dual core AMD64 4600+? Frame rates are low with a nvidia 7600+ GS. I was prieviously running AMD64 2800+ Sempron with nvidia 6600GT, and getting better frame rates. The only other difference is I was running ubuntu 6.10 in 32bit. Before I tried Feisty on the new gear, I was running the very same Edgy32 and it survived the new hardware like a champ.  . . .brought a tear to me wittle eye?

I'm not yet sure about gaming on Feisty. It's pritier, but i'm thinking about, switchin' back to Ubuntu 6.10 EDGY 32bit.

---


---
title: "doom 3"
date: 2006-04-21
forum: Gaming &amp; Leisure
---

### Post by ice.man on 2006-04-21
i keep getting this error

------ Initializing File System ------
Loaded pk4 /home/iceman/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /home/iceman/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /home/iceman/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /home/iceman/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /home/iceman/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /home/iceman/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/iceman/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/iceman/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/iceman/.doom3/base
/home/iceman/doom3/base
/home/iceman/doom3/base/pak007.pk4 (38 files)
/home/iceman/doom3/base/pak006.pk4 (48 files)
/home/iceman/doom3/base/pak005.pk4 (63 files)
/home/iceman/doom3/base/pak002.pk4 (6120 files)
/home/iceman/doom3/base/game03.pk4 (2 files)
/home/iceman/doom3/base/game02.pk4 (2 files)
/home/iceman/doom3/base/game01.pk4 (2 files)
/home/iceman/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg


and i have tryed sudo chown iceman:iceman /home/iceman/doom3 -R

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.5755 (8.24.8)

---

### Post by DoktorSeven on 2006-04-22
Looks like you're missing a few pk4 files.  You need game00-game03 and pak000-pak007 in that directory -- if they're in there then do **chmod -R 750 /home/iceman/doom3** as well.

---

### Post by ice.man on 2006-04-22
thanx mate i put the rest of the pak files in there and now it all works

---


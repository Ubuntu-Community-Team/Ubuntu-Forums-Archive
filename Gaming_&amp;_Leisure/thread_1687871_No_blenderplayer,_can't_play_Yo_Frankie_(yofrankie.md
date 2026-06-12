---
title: "No blenderplayer, can't play Yo Frankie (yofrankie-bge) in Ubuntu 10.10"
date: 2011-02-14
forum: Gaming &amp; Leisure
---

### Post by clockworkpc on 2011-02-14
OS: Ubuntu 10.10
Blender: 2.56 (20110214+bzr23869+ext798+pkg6~maverick1) installed from ppa:cheleb/blender-svn
Yo Frankie: 1.1b~svn91-0ubuntu

I downloaded Yo Frankie and also have Blender 2.56  but when I try to launch Yo Frankie this is what I get:

```
clockworkpc@clockworkpc-Inspiron-1564:~$ exec blenderplayer /usr/share/yofrankie-bge/levels/start_menu.blend
bash: exec: blenderplayer: not found

```

According to synaptic there is no executable file called blenderplayer installed.

I then downgraded to Blender 2.49 and it has both /usr/bin/blenderplayer and /usr/bin/blender-bin.  So it seems that for the meantime the PPA Blender 2.56 does not have blenderplayer or blender-bin.

---


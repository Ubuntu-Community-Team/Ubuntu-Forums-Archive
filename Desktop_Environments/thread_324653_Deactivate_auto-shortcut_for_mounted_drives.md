---
title: "Deactivate auto-shortcut for mounted drives"
date: 2006-12-24
forum: Desktop Environments
---

### Post by B-Con on 2006-12-24
Ubuntu creates a shortcut on my desktop for every mounted drive/partition I have, and also creates a shortuct to the drive under my "Places" menu (Gnome). Is it possible to turn this feature off? I don't necessarly want an icon on my desktop for every mounted drive I have, and neither do I want one for every mounted drive in my "Places" menu. Among other things,  tt gets annoying, every time I mount a drive, to have an icon pop up on my dekstop, and my "Places" menu gets cluttered with all my drives. I'd rather just personally create the shortcuts as I deem convenient.

How can I deactivate that feature?

---

### Post by B-Con on 2006-12-28
(Bump.)

Any advice on how to turn off that "feature" would be appreciated.

---

### Post by mcduck on 2006-12-28
The way to get them removed from both desktop and places menu is to mount them anywhere else than /media. Try /mnt instead.

To just remove the drive icons from desktop start Configuration Editor (Alt-F2 and run gconf-editor), browse to apps/nautilus/desktop and disable 'volumes_visible'.

---


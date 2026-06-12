---
title: "Deleting Special Icons from The Desktop"
date: 2009-11-20
forum: Desktop Environments
---

### Post by DeadlyOats on 2009-11-20
I have two icons on my desktop.  They are: "6.3 GB Filesystem" and "129 GB Filesystem".  These icons represent my Windows partitions.

I want to remove the icons permanently from the desktop, so that my desktop is not cluttered, but I do not want to unmount the filesystems, nor delete the filesystems when the icons are deleted.

How can I do this?

I'm using Ubuntu 9.10.

---

### Post by sowjendra on 2009-11-20
[FONT=Arial][SIZE=2]
There is no direct option to disable the mounted drives. we need to do the following

1. Press Alt+F2 and type gconf-editor
2. Goto apps\nautilus\desktop
3. untick volumes_visibile..

you can also enable or disable the other settings from there .. 

Regards
Surendra
[/SIZE][/FONT]

---

### Post by DeadlyOats on 2009-11-20
Thank you very much, Surendra.  That is precisely what I needed.  Plus, you taught me something new; "Alt-F2" and "gconf-editor."

Now my desktop is uncluttered, and I am happy.

---

### Post by biohazardhm on 2009-11-20
could you mark this topic as [SOLVED] ;)

---


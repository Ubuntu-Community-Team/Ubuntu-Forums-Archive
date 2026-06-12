---
title: "mount points not in &quot;my computer&quot; anymore"
date: 2008-04-27
forum: Desktop Environments
---

### Post by ignasigarcia on 2008-04-27
Hi there!

I just upgraded from gutsy to hardy and there is one behavior I noticed has changed and I wonder if I can revert it the way it was before. Let me explain:

I have some mount points in fstab such as this:

/```
/192.168.10.1/cavanilles       /mnt/cavanilles cifs    iocharset=utf8,noauto,user,credentials=/etc/samba/credentials   1 1

```
in gutsy, "my computer" would show that mount point as a smb folder when unmounted (that is the default). when I doubled click to mount it it would then show as a mounted drive (and also appeared the icon in my desktop). now with hardy no smb folder appears in "my computer" and even if I mount it using the mount command in the shell no drive appears in "my computer" nor in the desktop.

Does anybody know how to make it behave in hardy the way it did in gutsy?

TIA

Ignacio

---

### Post by ignasigarcia on 2008-04-28
ok, if I move the mount point from /mnt to /media I can see the drive mounted in the gnome desktop. However, I still have to mount it through bash (the smb folder for the unmounted resource still does not appear in "my computer" folder in gnome as it did in gutsy)

please, anybody can reproduce this behavior?

TIA

Ignacio

---

### Post by pholden on 2008-04-28
Also experiencing the same behaviour here... most frustrating :|

See the following threads:
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=766496](http://ubuntuforums.org/showthread.php?t=766496)
[*][http://ubuntuforums.org/showthread.php?t=767844](http://ubuntuforums.org/showthread.php?t=767844)
[/LIST]
Edit - found the solution to the icon problem in the following thread (/mnt doesn't get icons):
[LIST][*][http://ubuntuforums.org/showthread.php?t=771057](http://ubuntuforums.org/showthread.php?t=771057)[/LIST]
Just need to prevent nautilus putting icons on the desktop for all SFTP bookmarks now...

---

### Post by ignasigarcia on 2008-05-01
ok, I've found something interesting.... if I add to any panel the disk mounter miniapplication (might have another name, my gnome is not in english), it works the way we want (unmounted resources DO appear), si it should not be too hard to revert it to the way it was.

---


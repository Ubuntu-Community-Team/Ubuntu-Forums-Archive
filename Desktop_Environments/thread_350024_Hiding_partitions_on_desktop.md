---
title: "Hiding partitions on desktop?"
date: 2007-01-31
forum: Desktop Environments
---

### Post by DMAthlon on 2007-01-31
I use Ubuntu v6.10 Edgy Eft

How do i hide the icons on my desktop for the partitions on my computer? it shows 3 NTFS partitions and i dont want them seen!


thanks a lot! you guys are the greatest!

---

### Post by taurus on 2007-01-31
Don't mount them to /media in /etc/fstab.  Instead, mount them to /mnt.  So, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace the /media with /mnt.  And of course, you need to create the new mount points for those three ntfs partitions in /mnt.

If you don't know how to do it, post your /etc/fstab here then.

```
cat /etc/fstab
```

---

### Post by nkkromhof on 2007-01-31
Alternatively, start gconf-editor and navigate to /apps/nautilus/desktop, scroll down till you see 'volumes_visible' in the right pane and uncheck it.

---

### Post by DMAthlon on 2007-01-31
thans you nkkromhof. excellent information.

---


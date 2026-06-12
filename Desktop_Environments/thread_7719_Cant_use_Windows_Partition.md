---
title: "Cant use Windows Partition"
date: 2004-12-10
forum: Desktop Environments
---

### Post by Rebelthought on 2004-12-10
I can look at the root of the Windows partition, but.... when i try to go into a fo9lder it does nothign and when i right click on it...it disappears..... everythign is alrgith though but i would like to read/write to my fat32 partitons. So far this is a hot distro and Gnome is pretty good. PLease someone help me out 


RebelThought

---

### Post by willis on 2004-12-10
Do they actually apear as folders?  Make sure that you're mounting it as a user instead of root.

sudo umount /mnt/windows
mount /mnt/windows

and then try looking again (obvisouly replace /mnt/windows with it's mount point)

---

### Post by mattyh on 2004-12-10
in a post elsewhere on the forums, they discussed an issue like this.  It happened to me too.  On the fstab line you need to set it like the following I believe off the top of my head:

/dev/sda1    vfat     umask=000       0  0

---


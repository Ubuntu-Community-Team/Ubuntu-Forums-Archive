---
title: "fstab and ntfs"
date: 2005-10-27
forum: Desktop Environments
---

### Post by tosyu on 2005-10-27
Well, I have and ntfs partition and I can browse it only when I run nautilus as root.

My fstab looks like this

/dev/hda3   /windows     ntfs     ro,noexec,users    0    0

Is something wrong?

BTW: I can mount/umount the partition but I can't browse it. And even with the rw option as root I cant change the mounted dir (/windows) access rights

---

### Post by hajk on 2005-10-27
Add "umask=0222" to the options.

---

### Post by Pablo_Escobar on 2005-10-27
/dev/hda3       /windows  ntfs    nls=utf8,umask=0222 0       0

And You should be set

EDIT: Man, my quickness seems to be lacking :D

---

### Post by tosyu on 2005-10-27
thanks... I'll try it when I'll get back home

---

### Post by flower on 2005-10-27
yes ... add umask=0222 
but ... this doesn't always guarantee success,
some files just keep showing strange permissions tough (in ntfs partitions).
nothing to be done about it :)

---

### Post by tosyu on 2005-11-02
Well it works.

But there is a thing :]. Partition is only ro, yes I know that rw is not fully supported, but on Knoppix there was some app that downloaded ntfs drivers from microsoft and use a wine-kind-wrapper to mount/umount/write/read the ntfs partition.

Does anybody know what it was? I can't recall the name of the app.

:/

---

### Post by GeneralZod on 2005-11-02
[QUOTE=tosyu]Well it works.

But there is a thing :]. Partition is only ro, yes I know that rw is not fully supported, but on Knoppix there was some app that downloaded ntfs drivers from microsoft and use a wine-kind-wrapper to mount/umount/write/read the ntfs partition.

Does anybody know what it was? I can't recall the name of the app.

:/[/QUOTE]

"captive-ntfs".  Use at your own risk!

---

### Post by ashrack on 2006-01-09
could some1 explain the UMASK command to me. I know it's used for setting permission. But is there an explanation how do U get UMASK='0222' or 'UMASK=0000' and what's their difference?

---


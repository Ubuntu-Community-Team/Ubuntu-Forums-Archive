---
title: "fstab permissions"
date: 2005-09-18
forum: Desktop Environments
---

### Post by flny007 on 2005-09-18
Hi,
Can someone please help me replicate this:

mount -t ntfs /dev/hdb1 /mnt/windows -o ro,umask=0222

with an fstab entry? I currently have:

/dev/hdb1	/windows	ntfs	ro,umask=222	0	0

but it won't let me into the folder w/o being root. What's the correct way to do this?

---

### Post by flny007 on 2005-09-18
Just to clarify, I've got Ubuntu and XP on one disk in two partitions, and another disk (the one I'm trying to mount w/ fstab) for mp3s and other media. I just want MusicPlayer to be able to access it (which it can when I manually mount).

---

### Post by Xian on 2005-09-18
Try this entry:

```
/dev/hdb1   /windows    ntfs  ro,users,gid=users,umask=0002,nls=utf8 0 0
```

---

### Post by flny007 on 2005-09-19
Bingo! Thank you so much. I've tried about a million different fstab entries. I can't believe that one isn't listed more often, because it seems like a lot of people have the same problem.

---


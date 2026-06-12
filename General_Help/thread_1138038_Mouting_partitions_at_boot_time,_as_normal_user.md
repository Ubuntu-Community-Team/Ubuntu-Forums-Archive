---
title: "Mouting partitions at boot time, as normal user"
date: 2009-04-26
forum: General Help
---

### Post by jeenuv on 2009-04-26
Hi,

This is the problem I face: I've a FAT32 partition. And I wanted that to be mounted:

1) With permission 755 or 775, and user and group set to me (jeenu).
2) Automatically at boot time.

Before mouting, my mount target has:

[FONT="Courier New"]drwxrwxr-x 2 jeenu jeenu 4096 2009-04-25 22:57 /vfat[/FONT]

To achieve (1), I shall have in /etc/fstab:

[FONT="Courier New"]/dev/sda3 /vfat vfat defaults,user,rw,noauto 0 0[/FONT]

and later do [FONT="Courier New"]mount /vfat[/FONT]. Later, [FONT="Courier New"]ls -ld /vfat[/FONT] gives

[FONT="Courier New"]drwxr-xr-x 3 jeenu jeenu 16384 1970-01-01 05:30 /vfat[/FONT]

All fine. But for (2), I believe, I've to remove [FONT="Courier New"]noauto[/FONT] from the fstab line. And now after I do a [FONT="Courier New"]sudo mount -a[/FONT] and [FONT="Courier New"]ls -ld /vfat[/FONT], I get:

[FONT="Courier New"]drwxr-xr-x 3 root root 16384 1970-01-01 05:30 /vfat[/FONT]

I.e. it's not writeable for me! The reason I want that to be mounted at boot time is that many directories in [FONT="Courier New"]/vfat[/FONT] is used as the default directories by many applications. And I may not remember to do this manual mount everytime I log in.

Could somebody suggest a solution?

TIA
:J

---

### Post by hw-tph on 2009-04-26
You can specify who should be the owner by using the uid and gid options:

```
/dev/sda3 /vfat vfat defaults,user,rw,uid=1000,gid=1000 0 0
```

Find out you uid and gid by typing **id**.

---

### Post by jeenuv on 2009-04-26
Oh yes; that worked. Thank you!

But according to the mount(8) manual, this is an option for (including) fat file systems. Is the same applicable to extX filesystems?

(Sorry, I don't have a spare file system to experiment)

Thanks
:J

---


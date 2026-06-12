---
title: "External  drive permissions"
date: 2006-09-07
forum: Desktop Environments
---

### Post by ashari on 2006-09-07
Hi,

I plugged in my external (SATA) drive via USB and it gets
mounted as read only.  The output from mount command is:

```

/dev/sda1 on /media/SATA200GB type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)
```

Output from "ls -l /media"

```
dr-x------ 1 ashari ashari 4096 2006-09-03 21:45 SATA200GB
```


I tried to chmod 755 of /media/SATA200GB but the file 
permissions are not changed and I get:

```
chmod: changing permissions of `/media/SATA200GB/': Read-only file system
```

How do I make it read/writable?

Help appreciated.

ashari

---

### Post by bmadaras on 2006-09-08
The NTFS file system is not writable by default in linux, there are ways to make it writeable, check out ntfs-3g.

---

### Post by bmadaras on 2006-09-08
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

---


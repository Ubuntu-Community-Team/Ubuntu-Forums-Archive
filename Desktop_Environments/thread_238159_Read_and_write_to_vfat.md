---
title: "Read and write to vfat"
date: 2006-08-17
forum: Desktop Environments
---

### Post by jan-banan on 2006-08-17
Hi, i just bought a new harddrive and have managed to format/mount it and all that, but i cant write to it unless i'm root, this is my fstab:
```
/dev/sda1	/media/1	vfat	iocharset=utf8,mode=000,umask=0222  0    0
```

Whats wrong?

---

### Post by givré on 2006-08-17
You have set the owner of the file to you.
Add the option : uid=1000,gid=1000
It should work.

---

### Post by jan-banan on 2006-08-17
Fixed it, i used: 
```
/dev/sda1	/media/1	vfat	iocharset=utf8,uid=1000,gid=1000,umask=000  0    0
```

---


---
title: "Add mounted partitions to desktop"
date: 2005-12-22
forum: General Help
---

### Post by filipenetto on 2005-12-22
Hi guys ... :) 

Well, this days I was having problems to mount partition with write acess, and I got the resolution. But, now I want to know what command to adds in the fstab file to mount the partition to desktop, like when you insert the CD on the drive.

The line that I want to do this is this:

```
/dev/hdb5      	/documentos	vfat	iocharset=utf8,umask=000	0       0
```

I hope someone know this. Thanks ... ;)

---

### Post by filipenetto on 2005-12-22
Hehehe ..... ok, I got it !

I have only added the 'user' command on the line.

Tks !

---


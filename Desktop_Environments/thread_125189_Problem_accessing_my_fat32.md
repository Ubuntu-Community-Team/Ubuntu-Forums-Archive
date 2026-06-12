---
title: "Problem accessing my fat32"
date: 2006-02-03
forum: Desktop Environments
---

### Post by kpurcell on 2006-02-03
I have setup an automatic mount of a fat32 partition.  Here is how I entered the line in fstab.

```
/dev/sda4	/media/fat32	vfat	auto,user,exec,rw	0	0
```

So now I can access the drive and read it, but I thought the rw option was supposed to allow me to read and write.

I want to be able to both read and write this partition so I can keep my files on it and access them via both Windows and Ubuntu.

---

### Post by RAOF on 2006-02-03
You probably want to check out link 3 (accessing windows drives) in my sig.

---

### Post by lol on 2006-02-03
the quick answer is just replace "rw" with "umask=000".

---


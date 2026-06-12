---
title: "Trying to mount NTFS slave drive..."
date: 2006-05-05
forum: Desktop Environments
---

### Post by warriorness on 2006-05-05
warriorness@ubuntu:~$ sudo mount -t ntfs /dev/hdb1 /media/Windows

The problem is that it doesn't give me permissions to read/write the disk. I can only even browse it via Admin > Disks.

---

### Post by JoshHendo on 2006-05-05
Look on UbuntuGuide.org. It has instructions on how to mount it. The only thing is that you won't be able to write to the partition.

---

### Post by Sutekh on 2006-05-05
Use ```
sudo mount /dev/hdb1 /media/Windows -t ntfs -o nls=utf8,umask=0222
```
You will not be able to write to the partition.  If you really want to do that, there are projects like **captiveNTFS** that allow it, although they are experimental and I don't really know how well they perform.

---

### Post by warriorness on 2006-05-05
Ah, that worked; thanks.

Eh, not like I to write to the drive everyday anyways. I could always boot up Windows if I really needed to.

---


---
title: "FAT Panic: Curious filenames?!"
date: 2006-09-17
forum: Desktop Environments
---

### Post by SirKillalot on 2006-09-17
Hello
I have some files on my ipod which where created by a broken program I think. Now my problem is that I cannot delete these files anymore. I tried a fsck for vfat partitions but that didn't help.

The files look like: 
[IMG]http://img125.imageshack.us/img125/8640/errorye6.png[/IMG]

dmesg sais:
```
...
[17195010.304000] FAT: Filesystem panic (dev sda2)
[17195010.304000]     invalid access to FAT (entry 0xf0936fbf)
[17195010.304000] FAT: Filesystem panic (dev sda2)
[17195010.304000]     invalid access to FAT (entry 0xf0936fbf)
[17195010.304000] FAT: Filesystem panic (dev sda2)
[17195010.304000]     invalid access to FAT (entry 0x33b27327)
[17195010.304000] FAT: Filesystem panic (dev sda2)
[17195010.304000]     invalid access to FAT (entry 0x33b27327)
[17195010.304000] FAT: Filesystem panic (dev sda2)
[17195010.304000]     invalid access to FAT (entry 0x1ffe9e66)
...
```

When I try to delete the files the drive gets mounted read-only and I have to remount it to have write access.
I know that I could format the drive but isn't there any other way?

Thanks

---


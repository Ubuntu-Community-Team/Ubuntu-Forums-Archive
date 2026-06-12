---
title: "partition restored but wrong size!"
date: 2006-10-01
forum: Desktop Environments
---

### Post by sblanzio on 2006-10-01
Hello!

I've backed up my old linux partition and I restored that to a bigger hd using partimage.

Everything works, but now, even if my new partition shoud be about 27 Gb, KdiskFree tells me that the entire size of the partition is just the same as it was in the older hd! (about 11 Gb)...

The same happens in Nautilus, and the only way to get a different result is to check the partition table with Qtparted or "fsdisk -l".
Here they say correctly that I have a lot of free space in the partition, but it doesn't seems it's possible to make it available.

This is what fdisk -l says
(hda1 is mounted as "/")

```

Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3650    29318593+  83  Linux
/dev/hda2            3651        7299    29310592+   f  W95 Ext'd (LBA)
/dev/hda5            3651        7299    29310561    b  W95 FAT32
[...]

```

So here it says I have about 27Gb both on hda1 and hda5...
But this is what I get when I try to manage the disk free space:

```

xx@xx-desktop:~$ df
Filesystem         blocchi di   1K   Usati Disponib. Uso% Montato su
/dev/hda1             12120444   9710416   1794340  85% /
/dev/hda5             29296224  28836480    459744  99% /media/hda5
[...]

```

here it says i've just about 11 Gb on hda1 while hda5 is correct!

What can I do!?

If it is useful, my hda1 is ext3.

thank you very much!

sblanzio

---

### Post by Rui Pais on 2006-10-01
hi, i don't know partimage or how it work but thats must be the old problem of file system size versus partition size. 
They are not the same thing!

Partimage probably made you a filesystem with 11G from your backup inside a partition with 27G.

Try to boot from a live cd and do:
```
sudo resize2fs /dev/hda1
```

hth

---

### Post by sblanzio on 2006-10-01
this worked perfectly!! :)

thank you very much!!!

sblanzio

---

### Post by Rui Pais on 2006-10-01
you're welcome :)
Glad it worked.

Have fun.

---


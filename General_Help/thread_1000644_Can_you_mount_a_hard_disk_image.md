---
title: "Can you mount a hard disk image?"
date: 2008-12-03
forum: General Help
---

### Post by Cadmus on 2008-12-03
I was looking at a very pleasant guide to SSH piping [here]("http://linux.icydog.net/ssh/piping.php#jump-5") and part 3 got me thinking.

If you had a dump of a hard disk partition (e.g. dd if=/dev/sda1 of=/some/remote/folder/sda1.img) I'm under the impression you can mount it, though mount may complain somewhat.

Now, if you'd taken a dump of a full hard disk (e.g. sda) could you mount one of the partitions within it? Would you need to know the starting/ending sectorsof each partition?

---

### Post by geirha on 2008-12-03
Yes, you need to supply the offset. You can use parted to find the correct offset. I've created a 10MiB image (drive.img) with two 3MiB partitions to use as an example; let's mount the second partition.
```
$ parted drive.img unit B print
WARNING: You are not superuser.  Watch out for permissions.

Disk /tmp/drive.img: 10485759B
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start     End       Size      Type     File system  Flags
 1      16384B    3014655B  2998272B  primary  ext2              
 2      [COLOR="Blue"]3014656B[/COLOR]  6029311B  3014656B  primary  ext2              

$ sudo mount -o loop,offset=[COLOR="Blue"]3014656B[/COLOR] drive.img /tmp/mnt
$ ls /tmp/mnt
lost+found

```

---

### Post by Cadmus on 2008-12-03
That's such a elegant solution it's almost beautiful. Thanks for the concise example and explanation.

P.S. It's also nice to know I won't have to write down the offsets before imaging and risk geting them wrong.

---


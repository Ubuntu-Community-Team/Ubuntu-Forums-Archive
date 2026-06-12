---
title: "partitioning effects"
date: 2007-03-27
forum: Desktop Environments
---

### Post by isaacjoe on 2007-03-27
Awhile ago I juggled my partitions around to make my FAT32 Ubuntu-Windows intermediary that holds all my music, writing, etc bigger. I had to delete the swap and re-create it, and now Ubuntu can't see either of them. I look at system monitor and it isn't using any of the swap, and I can't see my new FAT32 partition.

How do I make these two work?


Also, completely unrelated, gAIM 2.0 beta 3.1 suddenly won't connect to AIM or MSN. I recently configured my router to forward port 7176 to ip 192.168.0.6, the computer downstairs, is there anything I could have screwed up? Aim will connect under windows, and AIM express. It's weird.

---

### Post by taurus on 2007-03-27
Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by isaacjoe on 2007-03-27
```
isaac@isaac-laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375        7649    10241437+  83  Linux
/dev/sda3            7650        9690    16394332+   f  W95 Ext'd (LBA)
/dev/sda4            9691        9729      313267+  88  Linux plaintext
/dev/sda5            7650        7776     1020096   82  Linux swap / Solaris
/dev/sda6            7777        9690    15374173+   b  W95 FAT32
```

SDA4 is the express media player partition that came with my computer, not quite ready to delete that. Sda6 is the one I want to access

And the other one:
```

isaac@isaac-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=8d690dc2-88cf-4715-8170-57a01f687a8e / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=CE94CBBB94CBA475 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=8D4B-880C /media/sda6 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=aebe5cbd-7395-4780-a711-7b714f13772a none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
isaac@isaac-laptop:~$ 

```

I shifted around my partitions AFTER I upgraded to edgy

---

### Post by taurus on 2007-03-27
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```

and change these two lines

```

UUID=8D4B-880C /media/sda6 vfat defaults,utf8,umask=007,gid=46 0 1
UUID=aebe5cbd-7395-4780-a711-7b714f13772a none swap sw 0 0

```
to look like these.

```

/dev/sda6  /media/sda6 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/sda5  none swap sw 0 0

```
Save it and reboot.

---

### Post by isaacjoe on 2007-03-27
It worked, thanks alot. 

Although when I look at my used swap it says it's using 0 bytes out of the 900 odd megs of available swap. I guess it just uses it when it needs to?

---

### Post by taurus on 2007-03-27
Yes, the system will use your swap space if it needs it so don't sweat over it.  ;) 

As long as it's mounted at boot, you are all good.

```
free
```

---


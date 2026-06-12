---
title: "strange partitioning/ grub/menu.lst problem"
date: 2006-06-16
forum: Desktop Environments
---

### Post by gforces on 2006-06-16
Hi - 

I'm running Dapper on an Dell Inspiron 6400.

The output of fdisk is the following: 

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        2650    21205800    7  HPFS/NTFS
/dev/sda3            9154        9545     3148740   db  CP/M / CTOS / ...
/dev/sda4            2651        9153    52235347+   f  W95 Ext'd (LBA)
/dev/sda5            2651        3925    10241406    b  W95 FAT32
/dev/sda6            3926        4020      763056   82  Linux swap / Solaris
/dev/sda7   *        4021        7595    28716156   83  Linux
/dev/sda8            7596        7751     1253038+  82  Linux swap / Solaris
/dev/sda9            7752        9091    10763518+  83  Linux
/dev/sda10           9092        9153      497983+  82  Linux swap / Solaris

When I do df -h i get:  

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda10             11G  8.2G  1.5G  85% /
varrun                501M   88K  501M   1% /var/run
varlock               501M  4.0K  501M   1% /var/lock
udev                  501M  172K  501M   1% /dev
devshm                501M     0  501M   0% /dev/shm
lrm                   501M   18M  483M   4% /lib/modules/2.6.15-25-686/volatile
/dev/sdb1             980M   54M  927M   6% /media/TRAVELDRIVE

So far so good. The problem is,  my system won't boot unless i change the /boot/grub/menu.lst to the root partition on /dev/sda9 instead of /dev/sda10.

I should also mention that I have another ubuntu installation on /dev/sda7.

If anybody has any ideas they would be appreciated.

Thanks.

---

### Post by scxtt on 2006-06-16
/dev/sda10 9092 9153 497983+ 82 Linux swap / Solaris {designated swap here}
/dev/sda10 11G 8.2G 1.5G 85% / {a mounted fs here?}

that's odd ...

what OS are you booted into when you run "df -h"?

and you shouldn't need a bunch of swap partitions - just one, any *nix can share it ...

---

### Post by gforces on 2006-06-16
[QUOTE=scxtt]/dev/sda10 9092 9153 497983+ 82 Linux swap / Solaris {designated swap here}
/dev/sda10 11G 8.2G 1.5G 85% / {a mounted fs here?}

that's odd ...

what OS are you booted into when you run "df -h"?

and you shouldn't need a bunch of swap partitions - just one, any *nix can share it ...[/QUOTE]


Hi - 

Yeah, I'm booted into the Ubuntu on /dev/sda9 (or/dev/sda10) when I run df -h.

And I only ever create one swap partition so I've no idea where they came from or even if they exist!

It seems like it's a partition table problem.

Any suggestions?

---

### Post by scxtt on 2006-06-16
> /dev/sda9 (or/dev/sda10)
that doesn't make sense - it can't be one or the other - the filesystem for Ubuntu is stored on either sda9 (which appears to be the case) or it resides on sda10 (but that's designated "Linux swap / Solaris" above ...

the only thing i can think of is each OS you have installed is referring to the /devs by slightly different names ...

---


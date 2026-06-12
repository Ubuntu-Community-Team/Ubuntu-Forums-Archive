---
title: "prtitioning issue"
date: 2009-03-29
forum: General Help
---

### Post by shahin on 2009-03-29
Greetings-
   Recently I keep getting an error message about my tmp directory being full.  I tried deleting some files, which messed up firefox a little, but it is ok now.  I then used an old desktop cd and using GParted, I see that /dev/sda2 is full.  But I can not resize the partitions.  I have three partitions on my system:
/dev/sda1 which has 40G and I have my xp stuff on it.  Next is /dev/sda2 which is full and only has 7.45 G of space.  then /dev/sda3 with 64.33G.  Out of which 62.16 GiB is dedicated to /dev/sda6 and rest is used by swap.  
Now I can shrink the /dev/sda6 from one side ie. from the right hand side. But I can not add the unallocated space to /dev/sda2 as I want to.  What should I do?

---

### Post by hyper_ch on 2009-03-29
paste the output of

```

sudo fdisk -l

```
and
```

df -h

```

---

### Post by shahin on 2009-03-29
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5223    41953716    7  HPFS/NTFS
/dev/sda2            5224        6195     7807590   83  Linux
/dev/sda3            6196       14593    67456935    5  Extended
/dev/sda5           14312       14593     2265133+  82  Linux swap / Solaris
/dev/sda6            6197       11373    41584221   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
unionfs               1.4G  662M  731M  48% /
varrun                759M   80K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
procbususb             10M  112K  9.9M   2% /proc/bus/usb
udev                   10M  112K  9.9M   2% /dev
devshm                759M     0  759M   0% /dev/shm
lrm                   759M  7.6M  752M   1% /lib/modules/2.6.17-10-generic/volatile
tmpfs                 759M   16K  759M   1% /tmp
ubuntu@ubuntu:~$

---

### Post by hyper_ch on 2009-03-29
please run it again and enclose each output in [noparse]```

```[/noparse] brackets. That makes it simpler to read.

---

### Post by shahin on 2009-03-29
Thanks for the quick reply.  Here is the output
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5223    41953716    7  HPFS/NTFS
/dev/sda2            5224        6195     7807590   83  Linux
/dev/sda3            6196       14593    67456935    5  Extended
/dev/sda5           14312       14593     2265133+  82  Linux swap / Solaris
/dev/sda6            6197       11373    41584221   83  Linux

Partition table entries are not in disk order

```

```

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
unionfs               1.4G  662M  731M  48% /
varrun                759M   80K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
procbususb             10M  112K  9.9M   2% /proc/bus/usb
udev                   10M  112K  9.9M   2% /dev
devshm                759M     0  759M   0% /dev/shm
lrm                   759M  7.6M  752M   1% /lib/modules/2.6.17-10-generic/volatile
tmpfs                 759M   16K  759M   1% /tmp
ubuntu@ubuntu:~$ 

```

---

### Post by hyper_ch on 2009-03-29
this is weird. What's unionfs? and if I read that correctly then you mount /tmp into your ram. So if you run out of ram you run out of /tmp also.

I don't see any partition mounted.

---

### Post by shahin on 2009-03-29
I ran those commands from the disk. Here is what they look like from my own harddrive:  ( Sorry I did not realize I have to run it from HD )
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d798d79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5223    41953716    7  HPFS/NTFS
/dev/sda2            5224        6195     7807590   83  Linux
/dev/sda3            6196       14593    67456935    5  Extended
/dev/sda5           14312       14593     2265133+  82  Linux swap / Solaris
/dev/sda6            6197       14311    65183706   83  Linux

Partition table entries are not in disk order

```

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             7.4G  7.1G     0 100% /
tmpfs                 758M     0  758M   0% /lib/init/rw
varrun                758M  108K  758M   1% /var/run
varlock               758M     0  758M   0% /var/lock
udev                  758M  2.8M  755M   1% /dev
tmpfs                 758M  104K  758M   1% /dev/shm
lrm                   758M  2.0M  756M   1% /lib/modules/2.6.27-14-generic/volatile
overflow              1.0M  352K  672K  35% /tmp

```

---

### Post by hyper_ch on 2009-03-29
I see your root partition is only 7gb and you have created another linux partition yet that one is not mounted. I assume that should be your /home partition?

---

### Post by shahin on 2009-03-29
Yes.  How did this happen?  How can I fix it please?  I think I chose the default settings during the installation.  How can I add to the partition that is full please?

---

### Post by shahin on 2009-03-29
Is there a way I can use fdisk to change allocated space to /dev/sda2?

---

### Post by hyper_ch on 2009-03-30
you can either just mount /dev/sda6 to where it's intended (probably /home) or try to grow sda2 by shrinking sda6 (and 5 and 3). I don't know what you intended to do.

---


---
title: "A tale of woe and despair"
date: 2009-05-08
forum: General Help
---

### Post by usernam on 2009-05-08
I just installed Ubuntu on my Acer today, and am now dualbooting Ubuntu/Vista.
The Ubuntu is installed on a 139 gig Partition. Whenever i try to install a program using add/remove, or symantec. It always says "no space available on device"



Also, I am typing this on my Vista partition because I cannot login to any websites with Firefox. I cannot download Opera because of the other problem!
Please help!

---

### Post by Alterax on 2009-05-09
open a terminal and type the following:

sudo apt-get clean
sudo apt-get autoclean

Those are just to clear out any locally-cached installer files.

Next, run this command:

sudo df -a

Copy what it tells you and post it here.  This gives us an idea of how much space you're working with here and how it's divided up.

---

### Post by usernam on 2009-05-09
Last night I reinstalled Ubuntu, Firefox works now, but it is still having problems with no space left on device.

I ran sudo apt-get clean, and it just went to a new command line.

When I run sudo apt-get autoclean it says 
```

matt@matt:~$ sudo apt-get autoclean
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
matt@matt:~$ 

```Here is sudo df -a
```

matt@matt:~$ sudo df -a
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb5              2403420   2233952     47376  98% /
tmpfs                  1863168         0   1863168   0% /lib/init/rw
proc                         0         0         0   -  /proc
sysfs                        0         0         0   -  /sys
varrun                 1863168       108   1863060   1% /var/run
varlock                1863168         0   1863168   0% /var/lock
udev                   1863168       176   1862992   1% /dev
tmpfs                  1863168        76   1863092   1% /dev/shm
devpts                       0         0         0   -  /dev/pts
fusectl                      0         0         0   -  /sys/fs/fuse/connections
lrm                    1863168      2760   1860408   1% /lib/modules/2.6.28-11-generic/volatile
securityfs                   0         0         0   -  /sys/kernel/security
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon             0         0         0   -  /home/matt/.gvfs
/dev/sdb1            973903552 285193888 688709664  30% /media/disk
matt@matt:~$ 


```

---

### Post by paradigm2 on 2009-05-09
It does appear that your ubuntu disk is full, yes.  How much space did you give the Ubuntu partition.  It needs at least 4 GB but more is highly recommended.

On ubuntu, what is the output of:

```

sudo fdisk -l

```

This should list the partitions and their sizes.  Note that the final option is the letter "L" in lowercase, not the number one.

---

### Post by usernam on 2009-05-09
Thanks!
```

matt@matt:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5f4cb01

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2416    19398656   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2416       20338   143965201    7  HPFS/NTFS
/dev/sda3           20339       20664     2618595    5  Extended
/dev/sda5           20339       20642     2441848+  83  Linux
/dev/sda6           20643       20664      176683+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121275   974141406    c  W95 FAT32 (LBA)
/dev/sdb2          121276      121601     2618595    5  Extended
/dev/sdb5          121276      121579     2441848+  83  Linux
/dev/sdb6          121580      121601      176683+  82  Linux swap / Solaris


```

---

### Post by usernam on 2009-05-09
Vista is installed on that 320 gig hd as well... but it is only taking up like 100 gig

---

### Post by paradigm2 on 2009-05-09
> **usernam said:**
> Thanks!
```


/dev/sdb5          121276      121579     2441848+  83  Linux


```

I don't think you really gave it 139 gigs...at least from the output above.  It appears that all your space is going to:

/dev/sdb1               1      121275   974141406    c  W95 FAT32 (LBA)

Are you sure you didn't give it 139 MB (or more likely 1.39 GB) by mistake or give it to the wrong partition?

It appears that your root linux filesystem is set on:

/dev/sdb5              2403420   2233952     47376  98% /

That would also explain why your install is kind of messed up too along with synaptic.  It looks like it ran out of space during the install.

---

### Post by usernam on 2009-05-09
Soooo.... what should I do?

---

### Post by usernam on 2009-05-09
is there a way to add to that partition?

---

### Post by usernam on 2009-05-09
/dev/sdb1 1 121275 974141406 c W95 FAT32 (LBA)  Is Vista I didnt create the partitions myself, when I installed Ubuntu i chose boot side-by-side, choosing between them each startup... I sthere a way to take some space from the sdb1 and put it in the Ubuntu partition?

---

### Post by paradigm2 on 2009-05-09
> **usernam said:**
> is there a way to add to that partition?

It looks like you need to resize your vista partition to be smaller and then repartition for the ubuntu install (give it *at least* 6 GB in my opinion).

It looks to me as if you probably did not get a complete install.  The partition indicates it has 2% free, but often that amount is reserved for the root user so that they can get in for an emergency after the disk is filled.

Since your install is probably botched, you probably might as well just reinstall.

I have no experience with resizing partitions (especially windows vista partitions) though I know such things exist.  Hopefully someone else will help.  Good luck.

---

### Post by paradigm2 on 2009-05-09
> **usernam said:**
> /dev/sdb1 1 121275 974141406 c W95 FAT32 (LBA)  Is Vista I didnt create the partitions myself, when I installed Ubuntu i chose boot side-by-side, choosing between them each startup... I sthere a way to take some space from the sdb1 and put it in the Ubuntu partition?

It looks like there just wasn't enough space to install then...it probably should have told you that.

There are soem utilities that will resize partitions, but unfortunately I have no experience with that and am hesitant to recommend one because of this.

---

### Post by usernam on 2009-05-09
OK... Now when I restart, It wont get past my computer manufacturer's logo!
Can anyone help???

---

### Post by usernam on 2009-05-09
It finally loaded past that and it says 
```

Grub loading, please wait...
Error 21

```

---

### Post by Alterax on 2009-05-09
I'm assuming you originally installed with wubi, then tried to resize, add, or delete partitions.

You'll have to fix your Windows install first.  Boot off of the cd-rom that came with your computer.  Note that this will kill grub, but for the moment that's okay.

Going through the installation procedures, it should detect your old installation.  Take the option to repair it.

Next, once you are back in Windows, remove your old wubi installation.  Reinstall, but this time give it 15-20 megs.  You can do it in four to five gigs, but it is an operating system and will need space to grow if you actually intend on using it, tinkering with it, and learning about it.

That should take care of it.

---


---
title: "need help with windows from linux"
date: 2009-05-16
forum: General Help
---

### Post by vistadude on 2009-05-16
well, can't really explain how i got to this point, but it seems that my NTFS partitions for vista and windows 7 can't be read, they can't even be booted, i am able to get into ubuntu, when i am though i go into the partition editor (GParted) and it has that explanation mark (!) next to the ntfs partitions, dose anyone know how to repair these partitions? i have a feeling that chkdsk would because i think its that the file system is damaged, but i can not boot into windows to do that, and i can't seem to do so from the windows install cd because it dose not detect these partitions. can any one please help? im desperate, all my files and photos and more are in the windows partitions, the partitions can't be mounted form linux either. If i can not fix these partitions, is there atleast a way i can recover the data i can from with in linux

---

### Post by albert ozzy on 2009-05-16
is there any option in your boot menu (/boot/grub/menu.lst) for vista/windows7 . If so what happens when you choose it? If not please make sure you add necessary info for grub to boot vista. It should be sth. like this: 
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
 

---

### Post by albinootje on 2009-05-16
> **vistadude said:**
> when i am though i go into the partition editor (GParted) and it has that explanation mark (!) next to the ntfs partitions

Afair you can double-click (or somehow) get more information from that exclamation mark (or key icon) in Gparted.

Can you post the output of the following :
```

sudo fdisk -l

```

---

### Post by vistadude on 2009-05-16
> **albert ozzy said:**
> is there any option in your boot menu (/boot/grub/menu.lst) for vista/windows7 . If so what happens when you choose it? If not please make sure you add necessary info for grub to boot vista. It should be sth. like this:

well i don have that entry in grub,when i click on it it says error 13, i tried opened the menu/.lst but and it was the way it should be, but it did not say makeactive, i added it and it did not change anything, so i removed it after when i logged back on. and i used to do it so that i used the windows boot loader on the mbr and had an entry on that to boot linux, but when i used it with grub and i went to boot windows it would show me the windows boot loader and it had both windows 7 and vista there, but they dont show up anymore because of the errors

---

### Post by vistadude on 2009-05-16
> **albinootje said:**
> Afair you can double-click (or somehow) get more information from that exclamation mark (or key icon) in Gparted.

Can you post the output of the following :
```

sudo fdisk -l

```

me results are 

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       39268   315363982+   7  HPFS/NTFS
/dev/sda3           39269       60801   172963822+   f  W95 Ext'd (LBA)
/dev/sda5           39269       50295    88574346    7  HPFS/NTFS
/dev/sda6           50296       60368    80911341   83  Linux
/dev/sda7           60369       60801     3478041   82  Linux swap / Solaris

```

---

### Post by albinootje on 2009-05-16
> **vistadude said:**
> 
```

/dev/sda2   *           8       39268   315363982+   7  HPFS/NTFS

```
Thanks, what is the output of the following :
```

sudo apt-get install ntfsprogs
sudo ntfsinfo /dev/sda2
sudo ntfs-3g /dev/sda2 /mnt

```

If the last commands complains that the NTFS partition is unclean (dirty), then try :
```

sudo ntfsfix /dev/sda2
sudo ntfs-3g /dev/sda2 /mnt

```

---

### Post by vistadude on 2009-05-16
well when i try sudo apt-get install ntfs-progs it tells me that the package ntfs-progs can not be found, if i try sudo ntfsinfo /dev/sda2
it says that the command ntfsinfo can not be found, and for sudo ntfs-3g /dev/sda2 /mnt it says: 

"NTFS signature is missing
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?"

---

### Post by albinootje on 2009-05-16
> **vistadude said:**
> well when i try sudo apt-get install ntfs-progs it tells me that the package ntfs-progs can not be found, 

Sorry, should be "ntfsprogs" instead of "ntfs-progs". 
(I'll correct it in the previous post).
Can you try again ?
> 
if i try sudo ntfsinfo /dev/sda2
it says that the command ntfsinfo can not be found, and for sudo ntfs-3g /dev/sda2 /mnt it says: 

"Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?"
Looks like you might have a serious problem with that partition.
Can you still mount /dev/sda1 which seems to have this special Windows Recovery partition ?
```

sudo ntfs-3g /dev/sda1 /mnt

```

---

### Post by vistadude on 2009-05-16
also if its any help i downloaded a live cd of partition recovery from [http://www.partition-recovery.com/](http://www.partition-recovery.com/) and it was able to read the ntfs partitions, so i believe my problem can be fixed, just how? i am near certain that it's because the file system is damaged, but how am i able to fix that, i have Googled it as much as i can, but i can't seems to get any solid results, other than chkdsk, which wont work for me because i can't boot windows

---

### Post by vistadude on 2009-05-16
well, sda1 is not a recovery partition, intact im not sure what it is, all it is is a small 54.88MB fat16 partition, and only 7.29 MB is used

and i forgot to say it uptop but the results for  sudo ntfs-3g /dev/sda2 /mnt also says NTFS signature is missing, ill make the edit

---

### Post by albinootje on 2009-05-17
> **vistadude said:**
>  and i forgot to say it uptop but the results for  sudo ntfs-3g /dev/sda2 /mnt also says NTFS signature is missing, ill make the edit

Try fixing with ntfsfix as described earlier here :
[http://ubuntuforums.org/showpost.php?p=7293132&postcount=6](http://ubuntuforums.org/showpost.php?p=7293132&postcount=6)

If that doesn't help you can use this : [http://ubcd4win.com/](http://ubcd4win.com/)
You need to "build" that yourself, and then you should end up with a bootable MS-Windows cdrom which could be able to fix your problems.

---

### Post by vistadude on 2009-05-17
> **albinootje said:**
> Try fixing with ntfsfix as described earlier here :
[http://ubuntuforums.org/showpost.php?p=7293132&postcount=6](http://ubuntuforums.org/showpost.php?p=7293132&postcount=6)

If that doesn't help you can use this : [http://ubcd4win.com/](http://ubcd4win.com/)
You need to "build" that yourself, and then you should end up with a bootable MS-Windows cdrom which could be able to fix your problems.


it dosn't work, when i try it it says 

"Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk."

---

### Post by albinootje on 2009-05-17
> **vistadude said:**
>  Volume is corrupt. You should run chkdsk."

Okay, then build this ubcd live cdrom on another machine.
[http://ubcd4win.com/](http://ubcd4win.com/) and use that to boot from, and then try to fix it.

---

### Post by vistadude on 2009-05-18
well, thx for ur help anyways, but managed to fix my computer an other way, with out the need to run chkdsk

---

### Post by albert ozzy on 2009-05-18
> **vistadude said:**
> well, thx for ur help anyways, but managed to fix my computer an other way, with out the need to run chkdsk

could you please write down your solution to the problem (or point it, if it's one of the things **albinootje **wrote). It may be helpful for others encountering the same problem.

---


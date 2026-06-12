---
title: "Where is my other partition?"
date: 2005-11-20
forum: Desktop Environments
---

### Post by jasonwvu on 2005-11-20
I'm still new at this so bear with me. I installed Win Xp (with ntfs), ubuntu, and an empty fat 32 partiton on my hard drive. I was told Linux has problems writing to NTFS drives, so i used a Fat 32 partition to acces files in either OS. How do I find this partition in Ubuntu? I rebooted into Windows and saw the partion was configured and recognized, so i know it's there. Can anyone help?

---

### Post by aysiu on 2005-11-20
Type this in a terminal ```
sudo fdisk -l
```

---

### Post by llamakc on 2005-11-20
[quote=jasonwvu]I'm still new at this so bear with me. I installed Win Xp (with ntfs), ubuntu, and an empty fat 32 partiton on my hard drive. I was told Linux has problems writing to NTFS drives, so i used a Fat 32 partition to acces files in either OS. How do I find this partition in Ubuntu? I rebooted into Windows and saw the partion was configured and recognized, so i know it's there. Can anyone help?[/quote]

If you have one hard drive you can check which partition it is with fdisk:

```
fdisk -l /dev/hda
```

or 

```
fdisk -l /dev/sda
```

You'll get something like:

```
root@kenobi:/home/ken# fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        6226    49946085    7  HPFS/NTFS
/dev/sda3            9124        9729     4867695   db  CP/M / CTOS / ...
/dev/sda4            6227        9123    23270152+   5  Extended
/dev/sda5   *        6227        9001    22290156   83  Linux
/dev/sda6            9002        9123      979933+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

So for me, /dev/sda2 is my Windows partition. If I had one for a fat32 (vfat) partition I would see it up there and then modify my /etc/fstab to include it.

---

### Post by jasonwvu on 2005-11-20
I edited the etc/fstab file to include my fat 32 partition, but it dosent show up in dev/. What is the next step to be able to use this drive in Ubuntu?

---

### Post by taurus on 2005-11-20
After you edited your /etc/fstab, did you remove to run

sudo mount -a

---

### Post by jasonwvu on 2005-11-20
I'm dont know what remove to run means.

---

### Post by llamakc on 2005-11-20
[quote=taurus]After you edited your /etc/fstab, did you remove to run

sudo mount -a[/quote]

He probably means 'remember' to run.

Let us see your /etc/fstab. you could do the following to test (and be certain your kernel will mount it):

sudo mkdir /windows

sudo mount -t vfat /dev/hda3 /windows

(or whatever your windows partition is)

and then you can cd into the windows partition. If it fails, post the error. Remember to use the partition info you got from using fdisk -l

---

### Post by taurus on 2005-11-20
[QUOTE=jasonwvu]I'm dont know what remove to run means.[/QUOTE]
That should be "remember..."

---

### Post by Bobbywhiskey on 2005-11-20
I did the same thing but it worked for me but i can only access my other partitions with terminal, is there a command so i can put access to every users?

---

### Post by aysiu on 2005-11-20
[QUOTE=Bobbywhiskey]I did the same thing but it worked for me but i can only access my other partitions with terminal, is there a command so i can put access to every users?[/QUOTE] [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by dev3n on 2005-11-20
so you can only read NTFS disks? :confused:

---

### Post by 23meg on 2005-11-20
The short answer is yes. NTFS write support does exist, but it's still not stable, which means it's dangerous to use it.

---


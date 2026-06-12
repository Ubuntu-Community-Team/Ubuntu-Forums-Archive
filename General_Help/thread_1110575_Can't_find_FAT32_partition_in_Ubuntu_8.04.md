---
title: "Can't find FAT32 partition in Ubuntu 8.04"
date: 2009-03-29
forum: General Help
---

### Post by ttray33y on 2009-03-29
help cant find my FAT32 partition,, after upgrading my Ubuntu 7.10 to  Ubuntu 8.04, 

here is my:

Disk /dev/sda: 40.8 GB, 40822161408 bytes
255 heads, 63 sectors/track, 4963 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4775    38355156   83  Linux
/dev/sda2            4776        4963     1510110    5  Extended
/dev/sda5            4776        4963     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac3aac3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        4997    19655527+   f  W95 Ext'd (LBA)
[COLOR="Red"]*/dev/sdb5            2551        4997    19655496    b  W95 FAT32*[/COLOR]
 the one that has italic and color red.

please help need it badly.

tnx in advance.

---

### Post by HermanAB on 2009-03-30
You can manually mount a block device.  This is typically what I would do to check out such a problem and fix it:
$ sudo ls /dev/sd*
$ sudo mkdir /mnt/fatdisk
$ sudo mount /dev/sdb5 /mnt/fatdisk
$ ls /mnt/fatdisk

---

### Post by ttray33y on 2009-03-30
> **HermanAB said:**
> You can manually mount a block device.  This is typically what I would do to check out such a problem and fix it:
$ sudo ls /dev/sd*
$ sudo mkdir /mnt/fatdisk
$ sudo mount /dev/sdb5 /mnt/fatdisk
$ ls /mnt/fatdisk

it says "special device /dev/sdb5 does not exist" :(

---

### Post by Cap'n Caveman on 2009-05-28
I too have this problem. I have tried the above terminal commands to mount the drive, but it still wont appear in my file system.

Any help would be greatly appreciated, im trying to move things from my Windows partition to my Ubuntu partition by using the FAT32, and as it wont appear, i cant!

---

### Post by ghen on 2009-05-28
please run the commands again and just copy the output into [ code ] tags so we can see what went wrong.

---

### Post by Cap'n Caveman on 2009-05-28
Ok, so re-ran them, and got this:

```
pete@pete-desktop:~$ sudo ls/dev/sd*
[sudo] password for pete: 
/dev/sda   /dev/sda2  /dev/sda4  /dev/sdb1  /dev/sdb5  /dev/sdc  /dev/sde
/dev/sda1  /dev/sda3  /dev/sdb     /dev/sdb2  /dev/sdb6  /dev/sdd  /dev/sdf
pete@pete-desktop:~$ sudo mkdir /mnt/fatdisk
pete@pete-desktop:~$ sudo mount /dev/sdb5 /mnt/fatdisk
pete@pete-desktop:~$ ls /mnt/fatdisk
bin    dev   initrd.img  media  proc  selinux  tmp  vmlinuz
boot   etc   lib         mnt    root  srv      usr
cdrom  home  lost+found  opt    sbin  sys      var
pete@pete-desktop:~$ 
```

/edit
In fact, looking at the /mnt/fatdisk directory, i can see it has been mounted. My actual problem then is that the files that are in there are not in there when i go into windows. Hence me thinking that that correct disk wasnt mounted or that the FAT32 wasnt mounted at all.

---


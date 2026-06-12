---
title: "can not mount volume of flash drive"
date: 2009-04-04
forum: General Help
---

### Post by saskatchewan on 2009-04-04
I installed Ubuntu for eee on my ASUS eee1000 and everything works great. Except for one major thing...

It says "Can Not Mount Volume" when i put in my flash drive.
I thought it might  be the flash drive that is the problem but I  tried it on two other computers and it works on them.
Similarly, I I put in my  can not get into User or other drives.

The only thing that I can access is the Home drive and my MP3 player (if I insert it).

---

### Post by accooper on 2009-04-04
I have had the same problem and here is what I did.

connect your flash drive to an available usb port.  Down load from add/remove programs a program name Disk Manager.

Restart your computer.

After it is completely finished booting, look to see if your flash drive is mounted.  If it is not, start drive manager from the system/administration menu.

It should be listed there.  make sure the box next to the designation for your flash drive is checked then click mount.

That should do it and it should auto mount from that point on.

Worked for me.

:guitar:

Andrew

---

### Post by saskatchewan on 2009-04-04
I can't find Disk Manager in the Synaptec.

Is it under another name?

---

### Post by ShaunG on 2009-04-04
What type filesystem is the flash drive? If it is ntfs you may need to install ntfs-3g

```
sudo apt-get install ntfs-3g
```

Then restart and see if it will mount.

Otherwise you could try the following.

Plus in the usb then type in a terminal

```
sudo fdisk -l
```

There should be a line in there similar to:


>  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36302   291595783+   c  W95 FAT32 (LBA)

just at the end.

The /dev/sdb1 bit at the beginning and sys type at the end are what we're looking for.

Next in a terminal type:

```
sudo mkdir /media/USB
sudo mount -t vfat /dev/sdb1 /media/USB
```

vfat means that it is a fat fs, /dev/sdb1 is what you want to mount, and /media/USB is where it will be mounted.

EDIT: If this fails, you can force it to mount:

```
sudo mount -t vfat /dev/sdb1 /media/USB -o force
```

( you can use vfat for fat16/32, ntfs-3g for ntfs and the /dev/sdb1 bit according to the output of fdisk -l )

---

### Post by saskatchewan on 2009-04-04
from my first attempt this is what I got

shawn@shawn-laptop:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shawn@shawn-laptop:~$ 

Then

shawn@shawn-laptop:~$ sudo fdisk -l

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x294a294a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         400     3212968+  83  Linux
/dev/sda2             401         979     4650817+  83  Linux
/dev/sda3             980         980        8032+   c  W95 FAT32 (LBA)
/dev/sda4             981         981        8032+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ef196

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3757    30178071   83  Linux
/dev/sdb2            3758        3924     1341427+   5  Extended
/dev/sdb5            3758        3924     1341396   82  Linux swap / Solaris

Disk /dev/sdc: 8127 MB, 8127512576 bytes
5 heads, 32 sectors/track, 99212 cylinders
Units = cylinders of 160 * 512 = 81920 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          51       99213     7932992    b  W95 FAT32
shawn@shawn-laptop:~$ 

shawn@shawn-laptop:~$ sudo mkdir /media/USB
shawn@shawn-laptop:~$ sudo mount -t vfat /dev/sdb1 /media/USB
mount: /dev/sdb1 already mounted or /media/USB busy
mount: according to mtab, /dev/sdb1 is mounted on /
shawn@shawn-laptop:~$ sudo mount -t vfat /dev/sdb1 /media/USB -o force
mount: /dev/sdb1 already mounted or /media/USB busy
mount: according to mtab, /dev/sdb1 is mounted on /
shawn@shawn-laptop:~$

---

### Post by ShaunG on 2009-04-04
Try

```
sudo mount -t vfat /dev/sdc1 /media/USB

```

---

### Post by saskatchewan on 2009-04-04
That worked!!!!!!!

Muchos thanks!!!!

---

### Post by ShaunG on 2009-04-04
No problem.

To umount it you will need to run

```
sudo umount <mount point>
```

E.G.
```
sudo umount /media/USB
```

---

### Post by saskatchewan on 2009-04-04
I spoke to soon.

I did a restart and now I have to access the flash via the terminal again.

Is there a way to get around this?

---

### Post by ShaunG on 2009-04-04
It should just mount. Try unmounting the flash drive, and removing it.

Then delete the mount point.

I.e /media/USB or whatever it's called. You will need to be root.

Also delete .hal-mtab. This file contains information about mounted drives. 

```
sudo rm /media/.hal-mtab
```

Then restart and plug in your flash drive and see what happens.

---

### Post by accooper on 2009-04-04
OK, I think the name is diskmanager.  It is located in the install/remove menu.  Do a Search.

:guitar:

Andrew

---

### Post by saskatchewan on 2009-04-05
I did a search for diskmanager in the add/remove progams thing and there was nothing by that name.

Perhaps it is the version of Ubuntu that I am using.

Do you know if it differes on such things?

---

### Post by saskatchewan on 2009-04-06
I have done lots of updates and searched for diskmanager but still not found it.

I am running Ubuntu 8.04.

Any suggestions?

---


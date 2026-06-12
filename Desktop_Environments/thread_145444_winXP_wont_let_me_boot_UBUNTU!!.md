---
title: "winXP wont let me boot UBUNTU!!"
date: 2006-03-16
forum: Desktop Environments
---

### Post by yetanotherpunter on 2006-03-16
Hi guys, 

Grudgingly recently i have ahd to install WinXP for some specialised software. During the instalation it did not recognise that i had Ubuntu installed and now when I boot it boots strait to windows. How can I get it to offer me either?

BEn

---

### Post by codejunkie on 2006-03-16
[QUOTE=yetanotherpunter]Hi guys, 

Grudgingly recently i have ahd to install WinXP for some specialised software. During the instalation it did not recognise that i had Ubuntu installed and now when I boot it boots strait to windows. How can I get it to offer me either?

BEn[/QUOTE]
insert your ubuntu install cd, at the cd menu enter ```
rescue
``` this will startup a text based rescue mode, it's pretty straight forward, so just follow the instructions until you get to the terminal. when you get to the terminal enter 
```
grub-install /dev/hda
```this will reinstall the grub menu, if you have any problems or questions with this let me know here, and i'll try my best help you out.

---

### Post by ssalman on 2006-03-16
try [this ]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")wiki page... good luck.

Edit: Sorry [[COLOR=#FB8B00]**codejunkie**[/COLOR]]("http://www.ubuntuforums.org/member.php?u=13310"), I took too long to post and I didn't see you post!

---

### Post by Buffalo Soldier on 2006-03-16
To learn more about rescue mode -> [http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-rescuemode](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-rescuemode)

---

### Post by yetanotherpunter on 2006-03-16
hey guys, having issues! 

using the recovery i get a message somthing like cannot find file.

Using ubuntu live and a grub command when given "find boot/grub/stage1" it returns a cannot find file.

Oh and the site with Super Grub disk seems to be non-existant. Are there no mirrors?

Sorry guys but can anyone shed any more light on the situ?

---

### Post by codejunkie on 2006-03-17
[QUOTE=yetanotherpunter]hey guys, having issues! 

using the recovery i get a message somthing like cannot find file.

Using ubuntu live and a grub command when given "find boot/grub/stage1" it returns a cannot find file.

Oh and the site with Super Grub disk seems to be non-existant. Are there no mirrors?

Sorry guys but can anyone shed any more light on the situ?[/QUOTE]
if your using the ubuntu live cd you need to mount your ubuntu partition first then chroot into it before using the```
sudo grub-install /dev/hda
```command try this boot into the ubuntu livcd open a terminal and run 
```
sudo mkdir /mnt/ubuntu
```
then run this command ```
sudo fdisk -l
``` it will output something like this
```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         182     1461883+  82  Linux swap / Solaris
/dev/hdb2   *         183        2589    19334227+  83  Linux

```find your ubuntu partition on mine my partition is /dev/hdb2 now mount your drive with 
```
sudo mount /dev/hdb2 /mnt/ubuntu
```replace /dev/hdb2 with your actual partition.
now chroot into it with this command.
```
sudo chroot /mnt/ubuntu
```
and run 
```
sudo grub-install /dev/hda
```
and this should restore the boot loader.

---

### Post by yetanotherpunter on 2006-03-17
Heya thanks for your help thus far. 

when i try the chroot /mnt/ubuntu It gives me:-

chroot: cannot run command `/bin/bash': No such file or directory

Any ideas. 

Also ifi try to mount any other partitions on that drive it tells me i must specify the file system

Dows this shed sany light on the system.

BElow is a copy of my Fdisk list:-

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        9726    77875087+   5  Extended
/dev/sda5              32        9726    77875056   8e  Linux LVM

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hdc2            1276        7296    48363682+   f  W95 Ext'd (LBA)
/dev/hdc5            1276        7296    48363651    7  HPFS/NTFS



Also is there anywhere else that one can get hold of this Super Grub disk, the one download site seems to be down?

---

### Post by codejunkie on 2006-03-17
[QUOTE=yetanotherpunter]Heya thanks for your help thus far. 

when i try the chroot /mnt/ubuntu It gives me:-

chroot: cannot run command `/bin/bash': No such file or directory

Any ideas. 

Also ifi try to mount any other partitions on that drive it tells me i must specify the file system

Dows this shed sany light on the system.

BElow is a copy of my Fdisk list:-

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        9726    77875087+   5  Extended
/dev/sda5              32        9726    77875056   8e  Linux LVM

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hdc2            1276        7296    48363682+   f  W95 Ext'd (LBA)
/dev/hdc5            1276        7296    48363651    7  HPFS/NTFS



Also is there anywhere else that one can get hold of this Super Grub disk, the one download site seems to be down?[/QUOTE]
if you ran the chroot command like this
```
chroot /mnt/ubuntu
```
it won't work.

it needs to be run as root, to run it as root use the command like this.
```
sudo chroot /mnt/ubuntu
```if this dosen't work, since your using LVM for your partitions, i'll need to see your fstab file. mount your drive and post the contents of the /mnt/ubuntu/etc/fstab file here.

---

### Post by yetanotherpunter on 2006-03-17
sorry i switched to the root user (sudo su) for the lot instead of typng sudo in every line

Now at the moment i can only mount sda1, everything alse throughs up "mount: you must specify the filesystem type"

---

### Post by codejunkie on 2006-03-17
[QUOTE=yetanotherpunter]sorry i switched to the root user (sudo su) for the lot instead of typng sudo in every line

Now at the moment i can only mount sda1, everything alse throughs up "mount: you must specify the filesystem type"[/QUOTE]

i think i might have found what the problem is, it's because your using LVM instead of standard partitions. this should activate the LVM group so you can mount the partition try this
```
sudo vgscan
```
then
```
sudo vgchange -ay
```
then mount it with
```
sudo mkdir /mnt/ubuntu
```
then
```
sudo mount /dev/volumegroup/logicalvolume /mnt/ubuntu
```
then
```
sudo chroot /mnt/ubuntu
```
and last
```
sudo grub-install /dev/sda
```

---

### Post by yetanotherpunter on 2006-03-17
> 
```
sudo mount /dev/volumegroup/logicalvolume /mnt/ubuntu
```


Hey mate i'm ok up to here, i may be being really thick but how /dev/volumegroup/logicalvolume translates in to what i put, please see below for my attemps

```
  Reading all physical volumes.  This may take a while...
  /dev/sdc: open failed: No medium found
  Found volume group "Ubuntu" using metadata type lvm2
ubuntu@ubuntu:~$ sudo vgchange -ay
  2 logical volume(s) in volume group "Ubuntu" now active
ubuntu@ubuntu:~$ sudo mkdir /mnt/Ubuntu
ubuntu@ubuntu:~$ sudo mount /dev/Ubuntu/* /mnt/Ubuntu
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount /dev/Ubuntu/sda /mnt/Ubuntu
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount /dev/Ubuntu/sda0 /mnt/Ubuntu
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount /dev/Ubuntu/sda1 /mnt/Ubuntu
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount /dev/Ubuntu/sda5 /mnt/Ubuntu
mount: you must specify the filesystem type

```

---

### Post by steve.horsley on 2006-03-17
I think it's worth persuing the approach from the wiki. Two things though,
* you must run grub using root provolege, e.g. **sudo grub**
* you must search for /boot/grub/stage1, not boot/grub/stage1:
> grub> find boot/grub/stage1

Error 15: File not found

grub> find /boot/grub/stage1
 (hd0,0)
 (hd0,5)
 (hd0,6)

Yes, I have 3 linux's installed.

I guess you will find the file on (hd0,0), in which case you would want to do:
root (hd0,0)
setup (hd0)

---

### Post by codejunkie on 2006-03-17
[QUOTE=steve.horsley]I think it's worth persuing the approach from the wiki. Two things though,
* you must run grub using root provolege, e.g. **sudo grub**
* you must search for /boot/grub/stage1, not boot/grub/stage1:

Yes, I have 3 linux's installed.

I guess you will find the file on (hd0,0), in which case you would want to do:
root (hd0,0)
setup (hd0)[/QUOTE]
\\:D/  man you are truely my hero, i've been thinking this whole time, that this could be solved in the same way, as you would use on standard linux partitions by chrooting the drive and running
```
sudo grub-install /dev/hda
``` but that just refuses to work with LVM partitions but **[[COLOR="Blue"]This[/COLOR]]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")** works great.

---

### Post by yetanotherpunter on 2006-03-22
Hey guys many thanks fo all your help, in the end nothing was working, not event he super grub disk so i had to re-install

But thanks anyway

---


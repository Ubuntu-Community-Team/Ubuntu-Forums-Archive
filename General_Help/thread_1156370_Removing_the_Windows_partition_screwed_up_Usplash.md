---
title: "Removing the Windows partition screwed up Usplash"
date: 2009-05-11
forum: General Help
---

### Post by the8thstar on 2009-05-11
Hi all,

I removed my Windows partition and I only have Ubuntu on my computer. Strangely enough this operation has screwed up my usplash screen : the bar bounces right and left for five seconds now before the screen defaults back to text mode.

Is there a way to get my usplash running normally?

Thanks in advance.

BTW, here is my *fstab* :

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9ae55765-f591-4704-9f14-b294b5f7850c /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=a1b073c0-1472-4286-868d-3526a8210d49 /home           ext4    relatime        0       2
# swap was on /dev/sda3 during installation
UUID=07c40c7c-dd4e-4193-9279-6c5b2c604081 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by jimbob on 2009-05-11
I have the same problem on my beta version of 9.04 Jaunty.  It happened after I removed one of my hard drives.

I have notes on how to fix it in Kubuntu and Edubuntu but not for regular Ubuntu.  They involve removing and re-installing usplash.

There is also a note here to make sure initramfs is regenerated.  Maybe you can try that by itself and see if it makes a difference.

 apt-get update-initramfs -c all -u

---

### Post by lovinglinux on 2009-05-11
Does it return any error?

---

### Post by the8thstar on 2009-05-12
Here's the output :

> the8thstar@the8thstar-laptop:~$ sudo apt-get update-initramfs -c all -u
E: Opening configuration file all - ifstream::ifstream (2 No such file or directory)

Hmm... I guess that didn't work.

---

### Post by the8thstar on 2009-05-12
I tried the following :

> sudo update-initramfs -u

but nothing has changed. I take it that *initramfs* is updated but *usplash* hasn't changed its behavior at all.

---

### Post by plucky on 2009-05-12
The command is ```
sudo update-initramfs -u -k all
```

But first of all,when you deleted the windows partition,did you change the size of the Ubuntu partition? If you did,it is likely the UUID changed and that will cause the usplash not to work.

Post output of ```
sudo fdisk -l
sudo blkid
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

and check for differences in UUID.

Good Luck

---

### Post by jimbob on 2009-05-12
These are the commands for Kubuntu that I used  followed by re-generation of initramfs that cured it for me:

  apt-get remove kubuntu-artwork-usplash
  apt-get install --reinstall usplash

Synaptic shows only usplash in Ubuntu so I guess you would have to modify the first one.
  
You got me interested so later this AM I will try it on my beta version that still has the problem and report back.

---

### Post by the8thstar on 2009-05-12
*fdisk*

> the8thstar@the8thstar-laptop:~$ sudo fdisk -l
[sudo] password for the8thstar: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d352

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   83  Linux
/dev/sda3            9469        9729     2096482+  82  Linux swap / Solaris
/dev/sda4            1276        9468    65810272+  83  Linux



*blkid*

> the8thstar@the8thstar-laptop:~$ sudo blkid
/dev/sda1: LABEL="root" UUID="9ae55765-f591-4704-9f14-b294b5f7850c" TYPE="ext4" 
/dev/sda3: TYPE="swap" UUID="ccd0afd7-5131-42f6-93a2-78bf068fd5a2" 
/dev/sda4: LABEL="Home" UUID="a1b073c0-1472-4286-868d-3526a8210d49" TYPE="ext4"

*fstab*

> the8thstar@the8thstar-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9ae55765-f591-4704-9f14-b294b5f7850c /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=a1b073c0-1472-4286-868d-3526a8210d49 /home           ext4    relatime        0       2
# swap was on /dev/sda3 during installation
UUID=07c40c7c-dd4e-4193-9279-6c5b2c604081 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


*initramfs*

> the8thstar@the8thstar-laptop:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=07c40c7c-dd4e-4193-9279-6c5b2c604081

---

### Post by jimbob on 2009-05-12
I have been messing around with this all day and still no joy.

If you do a search on usplash in the forums you will find a lot of solutions but none of them work for me yet.

---

### Post by jimbob on 2009-05-12
Looks like your swap UUID in blkid doesn't match the fstab or initramfs for some reason.

---

### Post by plucky on 2009-05-12
The output for **sudo blkid** gives the correct UUID for the different partitions.

Edit the /etc/fstab and /etc/initramfs-tools/conf.d/resume files and replace the UUID for the swap partition with the one given by **sudo blkid** and then run ```
sudo update-initramfs -u -k all
``` to update the initramfs file and see if the usplash then works.

Good Luck

[color=red]Please make backups of these files if you are unsure about editing the files.[/color]

---

### Post by jimbob on 2009-05-12
Mine didn't match either so I did all those things above and it still doesn't work. Good luck on yours.

---

### Post by the8thstar on 2009-05-13
It worked for me. Thanks a lot for your help!

---

### Post by jimbob on 2009-05-13
I fixed mine by adding the boot parameter ***[COLOR="Blue"]noresume[/COLOR]*** on the kernel line.  Everything is working now.

This probably has something to do with the file /etc/initramfs-tools/conf.d/resume but I checked this half a dozen times for accuracy and regenerated the initramfs each time but no joy.  Why this now works is beyond me.

---


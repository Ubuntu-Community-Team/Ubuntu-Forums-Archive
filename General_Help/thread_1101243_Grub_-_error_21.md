---
title: "Grub - error 21"
date: 2009-03-20
forum: General Help
---

### Post by charlescarroll1 on 2009-03-20
I screwed up grub again.

I decided to install Xubuntu 8.10 on an external hard drive to try it out.  The install did something to the grub on my laptop, and I now have to have the external hard drive with Xubuntu on it in order to load up my default Ubuntu.

When I start my laptop withOUT the external hard drive plugged in, I get the following...

> Grub Loading stage1.5.

Grub loading, please wait...
Error 21

What should I do?

---

### Post by jbrevik on 2009-03-20
> **charlescarroll1 said:**
> I screwed up grub again.

I decided to install Xubuntu 8.10 on an external hard drive to try it out.  The install did something to the grub on my laptop, and I now have to have the external hard drive with Xubuntu on it in order to load up my default Ubuntu.

When I start my laptop with the external hard drive plugged in, I get the following...



What should I do?

Looks like grub cant find the HDD. Since you are using a USB drive you may want to enable the BIOS to boot from USB

---

### Post by jbrevik on 2009-03-20
Im not sure how you installed Ubuntu on the external drive but you may want to look at this thread:
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

---

### Post by charlescarroll1 on 2009-03-20
I'm sorry, I made a typo in the last sentence of my first post.  I cannot load Ubuntu on my laptop, unless the external hard drive is plugged in.

I'm attempting to boot the Ubuntu install off my laptop.  I hooked up an external hard drive to install Xubuntu on to try it out.  Now, I cannot boot Ubuntu off my laptop due to the issue with grub I spoke of in my first post.

As I said, I am able to load the Ubuntu install on my laptop ONLY if my external (with Xubuntu) is plugged in, as it gives the option to do so.

I tried reinstalling grub through synaptic, but I still have the same error.

---

### Post by jbrevik on 2009-03-20
> **charlescarroll1 said:**
> I'm sorry, I made a typo in the last sentence of my first post.  I cannot load Ubuntu on my laptop, unless the external hard drive is plugged in.

I'm attempting to boot the Ubuntu install off my laptop.  I hooked up an external hard drive to install Xubuntu on to try it out.  Now, I cannot boot Ubuntu off my laptop due to the issue with grub I spoke of in my first post.

As I said, I am able to load the Ubuntu install on my laptop ONLY if my external (with Xubuntu) is plugged in, as it gives the option to do so.

I tried reinstalling grub through synaptic, but I still have the same error.


Looks like the GRUB loader got move to the external drive
Try this:
1. Boot into your Ubuntu installation (with external drive plugged in)
2. Open terminal and type
```
sudo su
```
3.```
fdisk -l
``` locate your Ubuntu Boot partition. Probably going to be hdx or sdx
4. ```
grub-install /dev/sdx
``` x being your partitoin of your Ubuntu installation
5. Reboot

---

### Post by sahabcse on 2009-03-20
Hi

Try to reinstall the grub, For fixing the grub follow below url


[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by charlescarroll1 on 2009-03-21
> **jbrevik said:**
> Looks like the GRUB loader got move to the external drive
Try this:
1. Boot into your Ubuntu installation (with external drive plugged in)
2. Open terminal and type
```
sudo su
```
3.```
fdisk -l
``` locate your Ubuntu Boot partition. Probably going to be hdx or sdx
4. ```
grub-install /dev/sdx
``` x being your partitoin of your Ubuntu installation
5. Reboot

Hey, this didn't work, but I might not have done it correctly.  When I entered fdisk -l, I got the following.

> root@sysop-laptop:/home/sysop# fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        2566      128520    5  Extended
/dev/sda3            2567        7296    37993725   83  Linux
/dev/sda5            2551        2566      128488+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe25de25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9400    75505468+  83  Linux
/dev/sdb2            9401        9729     2642692+   5  Extended
/dev/sdb5            9401        9729     2642661   82  Linux swap / Solaris


I assume its sda3?  I entered the command you said

> root@sysop-laptop:/home/sysop# grub-install /dev/sda3
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb
root@sysop-laptop:/home/sysop# 


I still have the same error message when I start my laptop without the external plugged in.

Am I doing something wrong, or is there something else I should try?

---

### Post by meierfra. on 2009-03-21
Grub needs to be installed to the MBR, not the boot sector of the Ubuntu partition. Try

```
sudo grub-install /dev/sda
```

---

### Post by charlescarroll1 on 2009-03-23
> **meierfra. said:**
> Grub needs to be installed to the MBR, not the boot sector of the Ubuntu partition. Try

```
sudo grub-install /dev/sda
```

Sweet, this worked!  Thanks yo!

---

### Post by meierfra. on 2009-03-23
> Sweet, this worked! Thanks yo!

Great. Have fun with {X,}Ubuntu

---


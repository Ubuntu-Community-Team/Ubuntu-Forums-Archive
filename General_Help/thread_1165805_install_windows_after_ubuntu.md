---
title: "install windows after ubuntu"
date: 2009-05-21
forum: General Help
---

### Post by bertolo on 2009-05-21
Hi!
i used ubuntu sucessfully for 3 months. i am happy with it, but i have some programs that need to have windows instaled since they require a good performance from my graphic card. those programs are called games :P
i still want to have ubuntu, but i prefer dual boot rather than virtual box, or wine.

i followed this tutorial:
[http://bit.ly/et1ET](http://bit.ly/et1ET) 

when i try t install windows it says that i can't install in that ntfs partition. :(

hug

plz answer

---

### Post by bertolo on 2009-05-21
someone plz ?

---

### Post by StuartN on 2009-05-21
> **bertolo said:**
> when i try t install windows it says that i can't install in that ntfs partition.

Some older versions of Windows require installation in the first physical partition. No version of Windows can be installed in a logical partition.

Check that your NTFS partition is big enough, and that it is the first, non-logical partition on the disk.

You will need to rewrite the grub master boot record after you have installed Windows.

---

### Post by bertolo on 2009-05-21
ok so i have to rezise (move all partitions to the left), so i can create a space good enough to install windows ?
i know how to recover boot points, i have done it sometimes, but isn't this riscky ?

can't u recomend me a version of windows that not require to be instaled in the first partition ?

---

### Post by reevine on 2009-05-21
ufortunately he is kinda right. Windows bootloader will look at the first partition only. Im not entirely sure if that applies to Vista and Windows 7 or not. if i remember correctley their bootloaders are more intelligent. but vista sucks so i dont really recomend it.

Make sure that space is around 50GB or more if your going to be playing games. and no if you simply delete the NFTS partition you have created and simply move the  partitions over. it will take a while to move them depending on how much data you have.

and for your question on weither its dangerous or not? well anything is dangerous when dealing with anytype of dual-boot. simply because you have for the most part two different types of operating systems that aren't even similar.

---

### Post by bertolo on 2009-05-21
can't move swap :(
[http://img297.imageshack.us/my.php?image=screenshotfkz.png](http://img297.imageshack.us/my.php?image=screenshotfkz.png)
my partitions table

bertolo@bertolo-desktop:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9b9e9b9

Device Boot Start End Blocks Id System
/dev/sda1 * 1 31 248976 82 Linux swap / Solaris
/dev/sda2 32 10011 80164350 5 Extended
/dev/sda5 32 1505 11839873+ 83 Linux
/dev/sda6 1506 7459 47825473+ 83 Linux
/dev/sda7 7460 10011 20498908+ c W95 FAT32 (LBA)

Disk /dev/sdb: 1031 MB, 1031798784 bytes
33 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x000e38a4

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 970 1007600 6 FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
phys=(231, 32, 63) logical=(969, 10, 51)
bertolo@bertolo-desktop:~$

---

### Post by chriskin on 2009-05-21
windows 7 can get installed on later partitions other than the first one (i have it at the second partition) and it is installed on a logical one . 
so you might like trying the free release candidate from the site

---

### Post by bertolo on 2009-05-21
ok i will try

---

### Post by reevine on 2009-05-21
> **chriskin said:**
> windows 7 can get installed on later partitions other than the first one (i have it at the second partition) and it is installed on a logical one . 
so you might like trying the free release candidate from the site
ok thats what i though but i wasnt sure. i just installed Vista on my third partition on a logical also and it works. so Vista and Windows 7 both have new bootloaders.

---

### Post by bertolo on 2009-05-21
no it is not possible. i formated my pc.

---

### Post by reevine on 2009-05-21
> **bertolo said:**
> no it is not possible. i formated my pc.
ok what do you mean formatted your pc? the whole hard drive?

---

### Post by Yellow Pasque on 2009-05-21
You should do this from a LiveCD environment. You could use the Ubuntu CD or something like this: [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by tad1073 on 2009-05-21
I suggest you create a back up partition for Linux and Windows then back up your important data.

remove existing Linux and Windows installation then reinstall.

It has been my experience that it takes longer to move your partition around than it will to back up your data to separate partitions and reinstall both Linux and Windows

---

### Post by reevine on 2009-05-22
> **tad1073 said:**
> I suggest you create a back up partition for Linux and Windows then back up your important data.

remove existing Linux and Windows installation then reinstall.

It has been my experience that it takes longer to move your partition around than it will to back up your data to separate partitions and reinstall both Linux and Windows
true in some cases it has been faster. depending on how much data you have.

---


---
title: "Don't understand partitioning"
date: 2006-06-20
forum: Desktop Environments
---

### Post by 1002285 on 2006-06-20
I don't understand partitioning anymore.
I got a new computer (60 Gb HD) and I asked them at the shop to make a Windows partition (10 Gb) and a Documents partition (35 Gb) and leave the rest unused for myself to install Ubuntu and possibly other OS-s.
Now I don't understand what I see in GParted.
There are 5 lines:
/dev/sda1 ntfs 9,77 Gb (flags) boot
/dev/sda2 extended 46,12 Gb (flags) lba
/dev/sda5 ntfs 34,18 Gb
unallocated 11,93 Gb
unallocated 7,84 Gb

What is this "extended" thing? I don't understand which place to use for installation. And I don't know why there are two separate "unallocated" areas.
 
sudo fdisk -l:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        7295    48355650    f  W95 Ext'd (LBA)
/dev/sda5            1276        5737    35840983+   7  HPFS/NTFS

Can anyone help or point me to a guide where this would be explained for a dummie? I did understand partitioning in Breezy install, but I have never seen GParted and don't understand the lines there.

---

### Post by narnian99 on 2006-06-20
The partitioning mechanism that you see has been there for a long time. Put simply, since the first days of DOS, a hard disk support 4 primary partitions. In order to allow for more than 4, the concept of an extended partition was created. So one of your primary partitions, /dev/sda2 in your case, is now an extended partition. This then contains all your extra partition. So the size of /dev/sda2 includes /dev/sda5 plus some unallocated area. You should be able to use gparted (or fdisk if you are brave) to allocate this unallocated space within the extended partition.

---

### Post by Ramses de Norre on 2006-06-20
An extended partition is used to create more than 4 primary partitions, it counts as a primary one but you can make uo to 21 logical partitions in it. So you've got on primary (ntfs) and one extended partition, in the extended one you've got a logical partition (ntfs) and some unallocated space, outside this two you've got another bit of unallocated space.
Best to do I think is shrink the extended to the size of the one ntfs inside and create a second primary partition for ubuntu or others.

---

### Post by 1002285 on 2006-06-20
[QUOTE=narnian99]You should be able to use gparted (or fdisk if you are brave) to allocate this unallocated space within the extended partition.[/QUOTE]

OK - sda2 includes sda5 plus 11,... Gb unallocated space. And the other unallocated space is outside sda2?
What would be a smart thing to do, if I want to install Dapper and leave some space for another OS?
Or, what could I do to install Dapper on one of the unallocated spaces? Right-click and "new"?
Breezy install had an option to partition free space automatically, so that it created swap itself - do I have to do this myself here?

Anyway, you have already helped, so thank you even if you don't have energy to bother to answer more of my questions :).

---

### Post by Ramses de Norre on 2006-06-20
I'd boot a live disc and try to shrink the extended to fit the ntfs partition so that all unallocated space is outside the extended one and can be used to create a primary ext3.
I think this is easy to do but I'm not sure (never tried it before).

I think it's also possible to install inside the extended and boot from there, but I'm not sure about this neither.

Or install outside the extended and use the space inside the extended for /home or something..

Many possibilities, pick the one that fits your needs ;)

---

### Post by 1002285 on 2006-06-20
Ok, I did it so that I made ext3 and swap inside the extended partition and installed Dapper on the ext, and I think it's ok.
I did not find a way in Gparted to shrink extended partition, because I just didn't dare to do it - was afraid that I might loose some of the documents.
Anyway, I think I'm fine for now.
Thank you.

---


---
title: "/home partition"
date: 2006-06-09
forum: Desktop Environments
---

### Post by TimmyJ on 2006-06-09
Hi, I currently have one partition on my computer that contains everything (with the exception of the swap partition of course). I would like to change this so that I can have a seperate ext3 /home partition. If I'm not mistaken this will allow me to put my files and pictures and movies there and be able to change operating systems freely and then just point the new OS to this seperate partition.

So basically I need to create this new partition, put my files that I want to keep there (from my current "everything" partition), and then install dapper to access this new partition. Can anyone tell me the best way to do this?

Thanks in advance,
Tim

---

### Post by aysiu on 2006-06-09
I wouldn't use the same /home partition for separate operating systems.

The advantage of a separate /home partition is allowing you to reinstall the same operating system or newer versions of the same operating system while keeping your files and settings intact.

So if you plan to do a clean reinstall of Ubuntu when Edgy Eft comes out, then a separate /home is good: [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html) has instructions.

If you plan to use the /home for SuSE, Mandriva, PCLinuxOS, Xandros, etc., then don't do it.

---

### Post by Rui Pais on 2006-06-09
Hi,
do you have only one disk with 2 partitions?

Anyway , you can boot from a livecd. Launch gparted. 
Shrink your now big all-in-on partition (to get free space)
Make another partition on free space, ext3 or whatever. 
Close gparted.
Mount that partition with any name you want.
Mount your all-in-one partition.
Move your home to the new one.
soethign like
```
mv /mnt/old_and_fat/home /mnt/young_and_innocent/
```
(If I was in your boots, i would play safe and prefer to do cp -a instead of mv and then rm -rf .../home/* to be shore of permitions... but mv should keep them too)
Edit /mnt/old_and_fat/etc/fstab
add a line like:
> /dev/hdaX       /home           ext3    noatime                 0       1
wheree you put hdaX according to your partition scheme.
Now umount -a. Reboot. Live Happy.
Don't need to reinstall Dapper. ;) Linux is cool isn't it?

Ok aysiu was faster. And right, mixing homes get you in trouble sooner or later (sooner in fact) Better  is do a all Linux partitions only for documents, pictures and movies. I have one called pub.

---


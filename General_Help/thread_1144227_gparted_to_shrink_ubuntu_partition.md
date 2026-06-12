---
title: "gparted to shrink ubuntu partition?"
date: 2009-04-30
forum: General Help
---

### Post by pmiln099 on 2009-04-30
I have a dual-boot Vista/Ubuntu. The Vista partition is only 20GB and out of space. I need to shrink the Ubuntu partition and give some room to Vista. I have gparted and have looked at it. I realize I need to unmount the Ubuntu partition before I can shrink it. Questions:
1 - If I am using Ubuntu and I unmount the partition, can I continue working with gparted to shrink it?
2 - If I unmount it, do I lose data from that system?
3 - Is it easy to remount or do I need to reinstall?
4 - Anyone care to provide some step-by-steps for me since I really am not that comfortable and tend to break more things than I fix! The gparted user manual leaves me really unsure of how to actually go about things.

Thx

---

### Post by kanikilu on 2009-04-30
You cannot unmount a partition that's in use, and you cannot resize a mounted partition.

Simply boot up with an Ubuntu Live CD, or download the GParted Live CD from their website. When you boot up, you'll be running off the CD, and your hard drive won't be mounted, so you can proceed to resize the partition.

While gparted can resize partitions non-destructively (and I've done it successfully), it's always a good idea to back up important files before doing **anything** with the partitions...

---

### Post by taurus on 2009-04-30
You need to run gparted from either Ubuntu LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

You can't really unmount it while you are still using it.

---

### Post by djbushido on 2009-04-30
As stated above DO NOT UNMOUNT THE DRIVE WHILE IT IS IN USE!!! Pain will ensue.
I personally recommend using the ubuntu live cd over the Gparted one, but both should work.
Resizing will not destroy data, but better safe than sorry.
Also, be careful you don't mess up the UUID of the ubuntu drive - look in /etc/fstab to see the UUID of the drive, and make sure it is the same afterwards.

---

### Post by Polygon on 2009-04-30
if you resize the partition, the UUID will change. so be sure to make the appropriate changes in your /etc/fstab file or else things won't mount

ALSO

when you want to resize the vista partition, let vista itself do it, if you don't, then vista won't even boot, and you will have to boot up the vista install cd and repair the partition, which is a pita. Just let vista expand it and all should go well.

---

### Post by taurus on 2009-04-30
> **Polygon said:**
> if you resize the partition, the UUID will change. so be sure to make the appropriate changes in your **/etc/fstab** file or else things won't mount

ALSO

when you want to resize the vista partition, let vista itself do it, if you don't, then vista won't even boot, and you will have to boot up the vista install cd and repair the partition, which is a pita. Just let vista expand it and all should go well.

And probably /boot/grub/menu.lst too.

---

### Post by pmiln099 on 2009-04-30
> **Polygon said:**
> if you resize the partition, the UUID will change. so be sure to make the appropriate changes in your /etc/fstab file or else things won't mount

So....boot from gparted CD, shrink ubuntu partition, and when do I make these UUID changes? Before rebooting back into Ubuntu? After? Do I change the UUID back to what it was before?

ALSO

> **Polygon said:**
> when you want to resize the vista partition, let vista itself do it, if you don't, then vista won't even boot, and you will have to boot up the vista install cd and repair the partition, which is a pita. Just let vista expand it and all should go well.

How do I let Vista do it? Do I just boot up Vista and it will see new space and voila? Or do I use the Vista disk management tool and expand Vista there?

---

### Post by Polygon on 2009-04-30
> **pmiln099 said:**
> So....boot from gparted CD, shrink ubuntu partition, and when do I make these UUID changes? Before rebooting back into Ubuntu? After? Do I change the UUID back to what it was before?



How do I let Vista do it? Do I just boot up Vista and it will see new space and voila? Or do I use the Vista disk management tool and expand Vista there?

you boot from the live cd or gparted cd (either one will work), shrink ubuntu, then..you need to mount the new drive (the one you just shrank), and you need to edit both the /etc/fstab file and the /boot/grub/menu.lst file and change the UUID to be the one of your new drive.

i think this command will list all drives and their uuid's, although i am reading it might only work with mounted drives and you have to restart in order for it to reflect any recent changes? anyway, try it:

ls -l /dev/disk/by-uuid/

and yeah, you need to go to vista disk management and have it expand to the partition, i HOPE that the vista disk management tool is good enough to do that, if it isn't however, you are going to have to boot back into the live cd again, expand it using gparted, then boot from the vista install cd, and once it gets to the first menu, there is an button that you click that you can use it to 'repair' the vista install and it will fix it.

---


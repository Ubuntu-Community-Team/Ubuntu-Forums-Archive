---
title: "Removing Windows and making ubuntu default"
date: 2008-12-07
forum: General Help
---

### Post by texas.chef94 on 2008-12-07
I would like to remove windows hda1 partition put ubuntu there as default and would like either a resouce site or someone kind enough to explain. An additional concern I have in looking at the partitions in gparted is on the NTFS under flags is the word boot. I understand / but do not understand /boot. Is that default and is that what is needed with ubuntu in hda1

Thank you

---

### Post by Simplicius on 2008-12-07
How's your Ubuntu organized? Do you have everything in one partition or have /home in a separate partition?

---

### Post by texas.chef94 on 2008-12-07
> **Simplicius said:**
> How's your Ubuntu organized? Do you have everything in one partition or have /home in a separate partition?

1 NTFS
2. Swap
3 ubuntu ext3

Thanks

---

### Post by Nathan Sweeney on 2008-12-07
> **texas.chef94 said:**
> I would like to remove windows hda1 partition put ubuntu there as default and would like either a resouce site or someone kind enough to explain. An additional concern I have in looking at the partitions in gparted is on the NTFS under flags is the word boot. I understand / but do not understand /boot. Is that default and is that what is needed with ubuntu in hda1

Thank you

The boot flag beside the NTFS partition is not related to /boot, a directory in the Linux tree.  As you will be using grub, I am pretty sure that the boot flag is ignored anyway, and grub just handles loading.  If you are getting rid of windows, there should be no problem with having to change another partition to have the boot flag (I am pretty sure of this anyway)

---

### Post by caljohnsmith on 2008-12-07
As Nathan mentioned, Grub does not care about which partition has the boot flag in order to boot it, but it is important to have at least one of your primary partitions marked as bootable; some BIOSes will refuse to boot a HDD that doesn't have one of its partitions marked as bootable, because the BIOS assumes the drive is then a data drive. Therefore, it is important to set the boot flag on one of your primary partitions if you want to make sure your BIOS doesn't give you a "no bootable drive found" type error. 

Also, it probably goes without saying, but I would definitely recommend backing up anything important in Ubuntu before doing your partition changes. As far as your partition changes go, one option you might want to consider is to delete your Windows partition and then simply resize the Ubuntu partition so that it takes up the space that Windows occupied. If you do that, the UUID of the Ubuntu partition will change, but you can manually fix it with a single command to restore its original UUID. Another alternative is to keep your Ubuntu partition as is and instead turn the Windows partition into a data partition for your personal files. Let me know if you would like more specifics or have more questions, or otherwise let us know how it goes. :)

---

### Post by sellwowgold2 on 2008-12-07
[size=2][color=#282827][color=#000000][sell wow gold](http://www.virdeal.com),[sell ffxi gil](http://www.virdeal.com),[sell maple story mesos](http://www.virdeal.com),[sell gaia gold](http://www.virdeal.com) [http://www.virdeal.com](http://www.virdeal.com) [/color][/color][/size]

---

### Post by texas.chef94 on 2008-12-07
> **caljohnsmith said:**
> As Nathan mentioned, Grub does not care about which partition has the boot flag in order to boot it, but it is important to have at least one of your primary partitions marked as bootable; some BIOSes will refuse to boot a HDD that doesn't have one of its partitions marked as bootable, because the BIOS assumes the drive is then a data drive. Therefore, it is important to set the boot flag on one of your primary partitions if you want to make sure your BIOS doesn't give you a "no bootable drive found" type error. 

Also, it probably goes without saying, but I would definitely recommend backing up anything important in Ubuntu before doing your partition changes. As far as your partition changes go, one option you might want to consider is to delete your Windows partition and then simply resize the Ubuntu partition so that it takes up the space that Windows occupied. If you do that, the UUID of the Ubuntu partition will change, but you can manually fix it with a single command to restore its original UUID. Another alternative is to keep your Ubuntu partition as is and instead turn the Windows partition into a data partition for your personal files. Let me know if you would like more specifics or have more questions, or otherwise let us know how it goes. :)

Thread resolved and thanks to all. As a matter of information I deleted windows, have ubuntu which I will add KDE desktop to as my primary in hda1. I am comfortable with moving around in ubuntu. I mention that merely because at 77 Linux is an adventure, but I need stability and I have it in 8.10.
The remainder of the partition will be my playground and I installed debian there and my first impression is it is not user friendly as ubuntu. This damn continuous accepting and rejecting cookies in debian is an absolute turnoff. But anyway again thanks I can always rely on the forum for clarity and patience with my comprehension challenges

---


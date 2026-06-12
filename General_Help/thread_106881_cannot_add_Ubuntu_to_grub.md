---
title: "cannot add Ubuntu to grub"
date: 2005-12-21
forum: General Help
---

### Post by bigblop on 2005-12-21
I have just inserted a new harddisk with ubuntu in my computer (I already have a primary harddisk with winXP installed). I have then use an Ubuntu Live CD to get access to the ubuntu disk and did the following:

used sudo fdisk -l to see that the ubuntu disk is called hdd1 and then:

sudo mkdir /mnt/hdd1
sudo mount /dev/hdd1 /mnt/hdd1
sudo chroot /mnt/hdd1
update-grub

But when I restart the computer there is no grub menu and I goes directly to winXP any hints??

---

### Post by aysiu on 2005-12-21
Windows is in charge of your MBR, not Ubuntu's Grub.
You need to [reinstall Grub](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by bigblop on 2005-12-21
I don't get what "6" is...

root (hd0,6)
setup (hd0)

---

### Post by aysiu on 2005-12-21
Try the instructions in the first post, not the second.

---

### Post by bigblop on 2005-12-21
After I have booted Ubuntu Live CD I cannot type "grub" I just get the message command not found.

---

### Post by bigblop on 2005-12-21
Maybe its not the hdd1 disk that I should mount but instaed the disk where winxp is installed...

---

### Post by Sutekh on 2005-12-21
First post, not second would be easier to follow.  Use the install disc, not the LiveCD.

But yes you probably want GRUB on the WinXP disc, if that's the disc you boot from.

---

### Post by bigblop on 2005-12-22
Just found out that I only have the Live CD. I have now tried the following:

sudo fdisk -l

tells me that winXP is on my primary drive called hda (not sure if its hda1)

and that my linux disk/partition is hdd1

I have then tried:

sudo mkdir /mnt/hdd1
sudo mount /dev/hdd1 /mnt/hdd1
sudo chroot /mnt/hdd1
grub-install /dev/hda

But it gives the error:

"The file /boot/grub/stage1 not recited correctly"

What is wrong?

---


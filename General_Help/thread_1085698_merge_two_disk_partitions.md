---
title: "merge two disk partitions"
date: 2009-03-03
forum: General Help
---

### Post by Ixai on 2009-03-03
When I installed Ubuntu I made 4 partitions, swap (3G), /(14G), /home(132G) and /boot(40M), all primary partitions. Now I want to install OpenSolaris, so I thought I'd reduce my /home to 102G the problem is that a Hard Drive can't contain more than 4 primary partitions so I'm looking for a way to merge two partitions, i.e. merge /boot back into /, I don't care if I loose the GRUB (I know how to reinstall it).

Thanks

---

### Post by Benic on 2009-03-03
You can try Gparted, an user-friendly partition manager. You need to unmount partitions before merging them or changing their size. You can do it with your Ubuntu live CD or the [_Gparted live cd_]("http://gparted.sourceforge.net/livecd.php").

---

### Post by Ixai on 2009-03-03
Thanks Benic, I'm familiar with gparted (although I use the one in Ubuntu's live CD). What I'm more concerned about is the files that are in the /boot partition, I believe I can edit */etc/fstab* so it won't mount that partition anymore and copy the files to an actual /boot folder inside the / partition, but I don't know if there's anything else that needs to be done (besides reinstalling GRUB on MBR). The contents in that computer are important and I don't want to reinstall the system.

---

### Post by geirha on 2009-03-03
/boot/grub/menu.lst and /etc/fstab should be the only files you'll need to change. [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by heindsight on 2009-03-03
What you could do, is unmount your /boot partition, remount it on /mnt, and copy the contents of /mnt into the /boot directory:

```
sudo umount /boot
sudo mount /dev/sda2 /mnt
sudo cp -aT /mnt /boot

```
Now the old contents of your /dev/sda2 partition (which is normally mounted at /boot, are in the /boot directory on your /dev/sda1 partition.

Next edit /etc/fstab and delete the line for /boot.

Finally boot off a live CD, use gparted to delete /dev/sda2.

---

### Post by hexanol on 2009-03-03
I'll add 2 things to the last post: don't forget to reinstall grub. Also, no need two actually delete /dev/sda2 when you are done if you want to install another OS in it (because if you delete it, you'll need to recreate it after, so it's not useful).

---


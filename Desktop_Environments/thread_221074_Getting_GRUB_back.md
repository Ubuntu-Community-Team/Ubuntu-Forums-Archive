---
title: "Getting GRUB back"
date: 2006-07-22
forum: Desktop Environments
---

### Post by woul on 2006-07-22
Hello everyone. This is my first post. My english is not good, but i nedd some help :)
I was using Kubuntu Dapper when i had to install windows or my brother`s games. Now when i try to re-install grub from the live cd i get error messages. This is what happens: 
#hda6 is where i have linux installed

ubuntu@ubuntu:~$ sudo mkdir /mnt/hda6
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda6 /mnt/hda6
ubuntu@ubuntu:~$ chroot /mnt/hda6
root@ubuntu:/# grub-install /dev/hda
/dev/hda: Not found or not a block device.

#then i do a fdisk -l and get this:
root@ubuntu:/# fdisk -l
cannot open /proc/partitions

Can anyone help to solve this? i miss linux very much! thank you
#windows at hda1 working fine

---

### Post by 5-HT on 2006-07-22
Doing it that way, you may need to bind /dev and /proc to your chroot environment.
The following wiki page walks you through many different ways of recovering GRUB:[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
If it still isn't working after following the steps to reinstall GRUB using grub-install in a chroot environment, you may want to try the  manual method described in the guide.

If you want a really easy way to reinstall GRUB I would highly suggest using the automated GRUB recovery option available in the alternate install CD. If you have that CD, select the repair installation option and you can then opt to have the CD automagically resintall GRUB for you (either to the MBR or a partition).

Hope that helps.

---


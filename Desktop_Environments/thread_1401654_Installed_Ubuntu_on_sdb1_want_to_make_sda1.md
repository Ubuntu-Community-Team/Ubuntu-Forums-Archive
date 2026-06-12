---
title: "Installed Ubuntu on sdb1 want to make sda1"
date: 2010-02-08
forum: Desktop Environments
---

### Post by kylea on 2010-02-08
I built a new version of 9.10 on a Esata disk (sdb1) and it boots fine as long as its in its sata cradle and the existing original disk sda1 is in the laptop primary disk slot.

Its a Dell E6500 Laptop - single 250GB Sata drive.

If I move the new sdb1 into sda1's position in my laptop I cannot boot.

I know the issue is with the sda versus sdb etc but I am not sure how to make the new disk the primary and bootable. (I used Disk Partition tool in Gnome to mark the sdb1 as bootable)

I read through the Grub2 notes (on Ubuntu help site) and can see a bunch of possible fixes but I don't want to muck up 5 hours work.

Any ideas how I can edit the grub.cfg to make the sdb1 boot as the primary drive.

Thanks

---

### Post by kylea on 2010-02-08
Self - Help - followed these steps from:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

and all is good


1. Boot to the LiveCD Desktop (Ubuntu 9.10 or later).

2. Open a terminal by selecting Applications, Accessories, Terminal from the menu bar.

3. Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L".

   a.  sudo fdisk -l

      If the user isn't sure of the partition, look for one of the appropriate size or formatting.

      Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The device/drive is designated by sdX, with X being the device designation. sda is the first device, sdb is the second, etc. For most users the MBR will be installed to sda, the first drive on their system. The partition is designated by the Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently. 

4. Mount the partition containing the Ubuntu installation.

      sudo mount /dev/sdXY /mnt

      Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot

5. Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.

      sudo grub-install --root-directory=/mnt /dev/sdX

      Example: sudo grub-install --root-directory=/mnt /dev/sda

6. Reboot
7. Refresh the GRUB 2 menu with sudo update-grub

---


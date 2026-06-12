---
title: "GRUB menu with zero timeout"
date: 2009-01-28
forum: General Help
---

### Post by abeautifulbeat on 2009-01-28
Pressing ESC or the arrow buttons don't work.

I've already tried what they suggest here to fix it: [http://ubuntuforums.org/showthread.php?t=835188](http://ubuntuforums.org/showthread.php?t=835188) , which is to boot with the Live CD and access menu.lst from there, but it opened an empty document! 

I selected "Try without installing", was that right?

I have Vista, can I change it from there???

---

### Post by taurus on 2009-01-28
If you want to access /boot/grub/menu.lst on the harddrive from the LiveCD, you first _must_ mount the partition where / (root filesystem) is located or /boot partition if you have a separate /boot partition.  Assuming it is /dev/sda2, you can mount it from a terminal with

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda2 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```
Now, you are editing the menu.lst on your harddrive.

---


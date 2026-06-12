---
title: "Grrrub problems after XP reinstall"
date: 2006-08-14
forum: Desktop Environments
---

### Post by RedFive on 2006-08-14
I've searched through the forums to solve this, but when I do the standard grub thing I get this:

> grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
grub> root (hd0,5)
root (hd0,5)
 Filesystem type is ext2fs, partition type 0x83
grub> setup (hd0,5)
setup (hd0,5)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,5) /boot/grub/stage2 p /boot/grub/menu.lst "... failed

Error 12: Invalid device requested
grub>



Help!

---

### Post by RedFive on 2006-08-14
I guess I should add that this is while I'm using the live cd. I read a post that suggested mounting my linux install to my live cd os (i.e. /mnt/xubuntu), but i couldn't get that to work. Ahhh, why does this have to be so difficult?

---

### Post by patrickfromspain on 2006-08-14
I've had problems with reinstalling GRUB after an XP install ;)

Have you mounted the partition??

---

### Post by seshomaru samma on 2006-08-14
can you post your fdisk -lu?

---


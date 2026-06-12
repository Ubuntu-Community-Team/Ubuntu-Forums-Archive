---
title: "GRUB Configuration"
date: 2006-08-05
forum: Desktop Environments
---

### Post by GoLoGo on 2006-08-05
Alright, I have 2 Hardrives, 1 20GB (Ubuntu Dapper Drake) and 1 200gb (4 partitions - 1st NFTS Windows XP, 2nd FAT32, 3rd ext3, 4 Fat32) I want to edit my grub so I can choose the OS, I had earlier added a few other lines of code to the grub conf file, but I want to know the exact code I should put for dual boot. Thanks.

---

### Post by h00s on 2006-08-05
Edit /boot/grub/menu.lst according to this:

#-------
#no need to edit this, leave it as is
title    Ubuntu, kernel 2.6.15-26-386
root	   (hd0,0)
kernel   /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd   /boot/initrd.img-2.6.15-26-386
savedefault
boot

#add this
title	    Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	(hd1,0)+1
makeactive
#---------

---


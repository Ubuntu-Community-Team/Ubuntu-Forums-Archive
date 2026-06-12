---
title: "Converting partition"
date: 2006-07-15
forum: Desktop Environments
---

### Post by freddym on 2006-07-15
I'm new to linux, and this seems to be a simple task, but i cant figure out how to fix it. 

I've just installed Ubuntu 6.06 on my laptop as a dualboot with WinXP. My plan was to have my 30gb disk partitioned in four partitions - swap, ubuntu, ntfs with winxp, and a fat32-partition for the rest. 

The problem is that the 15gb partition that i wanted to be fat32 is now ext3, and cant be read by winxp. How can i convert this to fat32, and make it work in ubuntu?

---

### Post by elettronicha on 2006-07-15
I've just been searching the web for a while and I'm afraid you can't convert ext3->fat32 without data loss. So I think you should backup your data before and then convert the partition.

---

### Post by freddym on 2006-07-15
Okay, but how can i reformat the partition and get it to work in ubuntu again? The partition is empty, so theres no data loss.

---

### Post by elettronicha on 2006-07-16
You can use graphical partition tools such as gparted or qtparted or the command line with parted. ;)

---

### Post by freddym on 2006-07-16
It seems like theres no graphical partition manager in the installed ubuntu. I've tried to boot it up from cd (like i did before i installed it), and convert the partition there, but then ubuntu wont recognize the partition once i boot it from the harddrive again. Any tips on how to make ubuntu accept this new fat32-partition?

---

### Post by dolby on 2006-07-16
have u [mounted](http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite) it?

---


---
title: "windows partitions"
date: 2006-04-04
forum: Desktop Environments
---

### Post by mitooz on 2006-04-04
hello,
its my first time to use linux.
i just followed these steps 
[PHP]Q: How to mount/unmount Windows partitions (FAT) manually, and allow all users to read/write?

   1. Read General Notes
   2. Read How to list partition tables?
   3.

e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT)
     Local mount folder: /media/windows

   4. To mount Windows partition

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

   5. To unmount Windows partition

sudo umount /media/windows/

[/PHP]
and now i can only the windows installed drive which C but i cant see the other 2 
they'r fat32 too

thanks

---

### Post by ELD on 2006-04-04
Can you past in your fstab file with your mount configurations in?

I mounted my vfat d drive perfectly fine ealier so i should be able to help a bit.

---

### Post by mitooz on 2006-04-04
how to paste it i dunno , from where to open it

---

### Post by taekappa on 2006-04-06
sudo mount /dev/hda5 /media/windows/ -t vfat -o iocharset=utf8,umask=000 

i have c and d c is hda1 and d is hda5

---

### Post by frodon on 2006-04-06
mittoz look at the unofficial starter guide in general it will really help you if you're new to linux : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by localzuk on 2006-04-06
You need to repeat the steps with each of the other partitions. To do this, you need to know the device name (/dev/hdaX) and create a new directory for each one.

---


---
title: "USB Stick: Read only device !warning!"
date: 2005-08-23
forum: Desktop Environments
---

### Post by dqsis on 2005-08-23
Hello Ubuntu friends!

I have a problem related to my MP3 - USB stick player.

When I plug it in, Ubuntu mounts it perfectly automatically. I can see the files and even play the songs. 

Nevertheless, when I try to copy or delete, I get the message: Read only device (and of course nothing happens)!

When I try chmod the files I get the warning: You are not the owner of the device.

Does anyone have a clue on how to fix this?  :-? 

Thank you all in advance!

DQ

---

### Post by nad on 2005-08-23
You need to tell the file system table how you wish to mount the device. Edit the file /etc/fstab (as root) to include a line (or edit your line) similar to this: /dev/sda1       /mnt/sda1       vfat    rw,user,noauto,noatime .

This will tell your operating system to mount the first sda type device at the directory /mnt/sda1 with read and write permissions for the user who mounted it, don't check for it when the mount -all command is given and don't update the access time of any files on it (flash memory has a limited number of write cycles). Make certain that you specify an existing directory for the mount point, or create one.

---


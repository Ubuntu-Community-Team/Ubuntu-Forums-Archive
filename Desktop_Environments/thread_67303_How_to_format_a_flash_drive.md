---
title: "How to format a flash drive?"
date: 2005-09-19
forum: Desktop Environments
---

### Post by erik-the-red on 2005-09-19
How do you format a flash drive under Ubuntu?

Do I need to download any accessory utility?

---

### Post by frodon on 2005-09-20
What do you mean by format ? fill all the flash memory with "1" or just erase all the files present on your flash memory (often called quick format).
If you just want to erase the flash, open the file browser and delete all the files in the flash, and then do a Ctrl + H in order to see hidden files and delete the trash present in your flash memory.

---

### Post by sbassett on 2005-09-20
Are you asking who to recreate or change the filesystem on the drive? This would be fairly easy to do, once you know where the flash drive is mounted. Barring any scsi devices on the system you would execute
```
sudo mkfs.ext3 /dev/sda1
``` 
or
```
sudo mkfs.vfat /dev/sda1
``` 

Keep in mind that this will wipe anything that is contained on /dev/sda1. 
PLEASE VERIFY THAT THIS IS WHERE YOUR FLASH DRIVE IS MOUNTED FIRST!

The first example makes an ext3 filesystem on the flash drive, while the second makes a vfat, for use with linux and windows, on the drive.

---

### Post by erik-the-red on 2005-09-20
[QUOTE=frodon]What do you mean by format ? fill all the flash memory with "1" or just erase all the files present on your flash memory (often called quick format).
If you just want to erase the flash, open the file browser and delete all the files in the flash, and then do a Ctrl + H in order to see hidden files and delete the trash present in your flash memory.[/QUOTE]
 I guess the CTRL+H was what I was looking for.

---


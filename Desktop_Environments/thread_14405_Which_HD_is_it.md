---
title: "Which HD is it?"
date: 2005-02-07
forum: Desktop Environments
---

### Post by defazn on 2005-02-07
I know how to mount my windows NTFS drive. My question is, I have two hard drives, I know my first ntfs is hda1, but what is my other hard drive (i have all my mp3s in there). I tried hdb, hdc etc ...is there a way i can check? Thanks a lot!

---

### Post by ilari on 2005-02-07
You can check that, if nothing else, with fdisk, using command 'sudo fdisk /dev/hd[a|b|c|d]'. But be careful that you DO NOT change anything unintentionally. The namig scheme of the partitions goes as stated [here](http://ubuntuforums.org/showthread.php?t=14077).

---

### Post by kamome on 2005-02-07
Or, even better, use the "-l" Option: "sudo fdisk -l /dev/hda" (or hdb...), which will simply list you harddisk configuration without the option to modify anything.

cu
kamome

---

### Post by JackDog on 2005-02-07
[QUOTE=defazn]I know how to mount my windows NTFS drive. My question is, I have two hard drives, I know my first ntfs is hda1, but what is my other hard drive (i have all my mp3s in there). I tried hdb, hdc etc ...is there a way i can check? Thanks a lot![/QUOTE]

dmesg | grep hd
-or-
cd /proc/ide && ls

If your other drive is SATA or SCSI 

dmesg | grep sd
-or-
cd /proc/scsi && ls

---

### Post by defazn on 2005-02-07
thanks guys it worked, now im using ubuntu with my mp3s! =)

---


---
title: "Windows partition"
date: 2005-08-25
forum: Desktop Environments
---

### Post by Infatuated_iPod on 2005-08-25
I am trying to mount my windows partition but i ran into a road block. 

this is what i did.. 

sudo mkdir /mtn/windows 

then  $ sudo mount /dev/hda1 /mnt/windows -t ntfs -o umask=0222

It says that special device /dev/hda1 does not exist.. 

how do i find out where windows is located? i am pretty sure its hda1. Someone help pleasE!

---

### Post by Tinuz on 2005-08-25
The source of all Ubuntu wisdom: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) ;)

It is in there, but to help a little: *sudo fdisk -l*

---

### Post by Infatuated_iPod on 2005-08-25
when i did what the site told me to do, i got this message... 

wrong fs type, bad option, bad superblock on /dev/hda1, 
missing codepage or other error. 
in some cases useful information is found  in syslog - try 
dmesg | tail or so 

????

---

### Post by EnderTheThird on 2005-08-26
If your HDD is SATA, it won't be /dev/hda1, it will (probably) be /dev/sda1 instead.  Do ```
sudo fdisk -l
``` to make sure though.  If it shows your Windows disk as /dev/sda1, then make sure you change your fdisk entry.  Also, you had a typo in your first post ("mtn" instead of "mnt"), so make sure that you have the directories correct on your computer or there will be nowhere to mount the drive anyway.

---


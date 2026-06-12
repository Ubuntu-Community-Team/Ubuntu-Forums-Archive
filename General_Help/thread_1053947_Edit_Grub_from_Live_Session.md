---
title: "Edit Grub from Live Session"
date: 2009-01-29
forum: General Help
---

### Post by spandon on 2009-01-29
Have messed up my grub, and wish to edit it via a live session.
Could someone please give me the commands to type into terminal to edit the grub?
Ubuntu 8.10 is installed to hda6.
Thanks
sp[andon

---

### Post by Elfy on 2009-01-29
```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/hda6 /mnt/tmp
sudo nano /mnt/tmp/boot/grub/menu.lst
```

---

### Post by spandon on 2009-01-29
Thanks for you prompt reply forestpixie.
Unfortunately,when I enter the second line 
'sudo mount -t ext3 /dev/hda6 /mnt/tmp'
returns
mount: special device /dev/hda6/does not exist
can't understand why, as Ubuntu is loaded on ide hard drive 1 (hda) and is on partition 6 thus (hda6)
any ideas as to why it is rejecting your command?
spandon

---

### Post by Elfy on 2009-01-29
try sda6

Just assumed that fdisk had given you that information

---

### Post by spandon on 2009-01-29
Hi forestpixie,
Thanks again, but no go with sda6 replacing hda6
Thinking it may be quicker to re install?
Have checked again that the system exists on hda6, have tested by 
sudo grub
root (hd0, (tab)
which then shows ext2fs as being on partition 6
the line in grub that is wrong is:
/boot/initrd.img-2.6.27-9-generic
it should read  /boot/initrd.img-2.6.27-11-generic
spandon

---

### Post by Elfy on 2009-01-29
```
sudo fdisk -l
``` will tell you partitions

If grub is saying hd(0,6) then that is sda7 or hda7.
Grub numbering starts from 0

---

### Post by spandon on 2009-01-29
Thanks again forrestpixie,
got it this time, it was sda7.
the problem is that I can get into the grub file, but have not got the permission to change it, how can i change the permission to r/w?
spandon

---

### Post by Elfy on 2009-01-29
sorry my fault 

sudo nano /mnt/tmp/boot/grub/menu.lst

---

### Post by spandon on 2009-01-29
Hi forrestpixie,
Job done, **many thanks for your assistance**.
spandon

---


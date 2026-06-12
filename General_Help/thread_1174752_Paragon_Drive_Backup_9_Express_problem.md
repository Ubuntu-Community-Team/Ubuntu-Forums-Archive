---
title: "Paragon Drive Backup 9 Express problem"
date: 2009-05-31
forum: General Help
---

### Post by qunungnauraq on 2009-05-31
I have a dual boot ubuntu 8.10/windows xp pro configuration that I want to back up with paragon drive backup 9 express. The backups actualy work but after I restore either partition i get " GRUB Loading stage1.5. GRUB loading, please wait... Error 17 ". I then have to use gparted on my ubuntu live cd to change my boot flag back to ext3/. I am suspecting that i need to move the bootloader to another location but when i do i have other problems such as only being able to boot into ubuntu or in other cases xp. I know I'm doing something wrong. Solutions anyone?,Thanks.

---

### Post by blueridgedog on 2009-05-31
One option that comes to mind is to also make a backup of the master boot record of each hard drive as part of your backup process (before you run the image, so the mbr file is on the restored drive).

Take a look at a recent Linux Journal article that goes over the process:

[http://www.linuxjournal.com/article/10385](http://www.linuxjournal.com/article/10385)

---


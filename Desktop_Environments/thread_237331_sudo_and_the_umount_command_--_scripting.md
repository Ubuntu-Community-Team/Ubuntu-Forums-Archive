---
title: "sudo and the umount command -- scripting"
date: 2006-08-16
forum: Desktop Environments
---

### Post by vangheem on 2006-08-16
Hi, I wrote a simple shell script for my father that automatically transfers new photos from his camera to the computer when he connects his camera.

   I have everything working, but I want to be able to unmount the usb disk after the transfer is complete.

   My problem is, I can't get the umount command to work without using the sudo command.  Which means that when the script is run there is no terminal where a password can be entered in for the sudo command..  Which means I can't unmount the disk.

   Is there a way around this?  Or is there a way to have the nice GUI password request screen come up so I can get a temporary security lock?


Thanks for any help.

---

### Post by vangheem on 2006-08-16
sorry about double post....  

Web site hung the first time so I didn't think it went through

---

### Post by cheburashka.dave on 2008-04-26
try using gksu or su instea of sudo.. i am not sure, but it may provide a password field.

---


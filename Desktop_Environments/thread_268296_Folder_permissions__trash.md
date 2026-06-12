---
title: "Folder permissions  trash"
date: 2006-09-29
forum: Desktop Environments
---

### Post by Gimlet on 2006-09-29
Hi Linux Newbie here. I transfered a pile of mp3's from a portable HD to my Ubuntu 6.06 install and then discovered i had transfered my wifes backed up iTunes music folder. So I deleted it to my trash. Now I cannot get rid of about half of the files. They show a little lock icon on the folders and when I try to delete them they say "/home/terr... Make.mp3" cannot be deleted because you do not have permissions to modify its parent folder." I tried to use sudo but it says no such folder existes. Can someone help. These files are taking up several hundred megs

---

### Post by odinfromvalhalla on 2006-09-29
try this in a terminal:

cd; cd .Trash; sudo rm -rf * <Enter>

this will remove everything in the trash folder.

---

### Post by aysiu on 2006-09-29
Please do not ever type ```
sudo rm -rf *
``` A lot of bad things can happen if you accidentally type the wrong thing.

Instead, press Alt-F2 and type ```
gksudo nautilus
``` Then go to /home/username/.Trash and delete the offending files.

---

### Post by Atomic Dog on 2006-09-30
> **aysiu said:**
> Please do not ever type ```
sudo rm -rf *
``` A lot of bad things can happen if you accidentally type the wrong thing.

Instead, press Alt-F2 and type ```
gksudo nautilus
``` Then go to /home/username/.Trash and delete the offending files.

Yea using rm can be dangerous.

gksudo is for running GUI apps as root (just using sudo can possibly make things run flakey).  aysiu is right.  Running nautilus as root (gksudo nautilus) will allow you to delete the files in the trash can if you drill to the trash folder.

---


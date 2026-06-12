---
title: "Read NTFS files"
date: 2005-12-16
forum: General Help
---

### Post by Donnut on 2005-12-16
Hi.  I have used ubuntu for a bit, and I managed to convince a friend to change over.  One problem though, we made two new partitions on a 300gb serial ata hard drive, keeping a 250gb formated NTFS with all his files on it.  Now it is a "read only drive" that I can just read through sudo nautilus, but can't change the permissions so that users can read it...  Any Ideas?

---

### Post by thezerogroup on 2005-12-16
Check out captive NTFS. . . I have not yet used it w/ Ubuntu, but i have with other distros and it works great 

[http://www.jankratochvil.net/project/captive/]("http://www.jankratochvil.net/project/captive/")

---

### Post by soulestream on 2005-12-16
you dont need captive to read to a ntfs drive

edit /etc/fstab

find the line about ntfs and either use umask to set permissions or change "defaults" to ro,user

that will let a user mount and read the drive. if you have a problem search the forum for NTFS, you will get about 2 billion hits.

as a note if he plans on keeping a dual boot with linux and windows it would be better to format the drive fat32. that way you dont have to use a ntfs driver for  linux, like captive.

soule

---

### Post by Donnut on 2005-12-16
He wants to reformat it to linux but when we try with a live CD, it says that one or more of the partitions are mounted, it is recomended you restart your computer.  We have tried using th umount command, none of the parts are mounted.  The last suggestion didn't work, we can see the mounted drive as user, but can not read it.

---

### Post by soulestream on 2005-12-16
here is mine

/dev/sda1       /media/windows  ntfs    ro,noauto,umask=222  0   0


that give all users rx access to the drive with no write.

the noauto means you have no manually mount it.

of course your /dev/*** will be different and your /media/*** probably will also

also if he is new to linux, you might not want to got to the trouble of backing up and reformatting the drive, just to go through the process again, if he decides linux sucks. "those" people do exist.

soule

---


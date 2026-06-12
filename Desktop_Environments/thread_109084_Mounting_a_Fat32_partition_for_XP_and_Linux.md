---
title: "Mounting a Fat32 partition for XP and Linux"
date: 2005-12-27
forum: Desktop Environments
---

### Post by icarius on 2005-12-27
I have recently created a new partition to act as a shared hd for XP and Ubuntu. However, I cannot get Ubuntu to give the user access to write to the drive, I have tried the Disk option and it only gives the root user access and I can't get it to work in /etc/fstab either, HELP!!!!!

---

### Post by briancurtin on 2005-12-27
first off, you arent trying to write from ubuntu to an NTFS partition are you?

---

### Post by icarius on 2005-12-27
Nope, I am writing from both OS's to a Fat32 partition.

---

### Post by Hangetsu on 2005-12-27
I set noauto,rw,uid=<<your user id >> when setting up my two fat32 drives in fstab.  I remember when I was playing with this that umask wouldn't always work for me.

Give that a shot.

---

### Post by fordfan753 on 2005-12-27
Mine will always work with ```
rw,user,umask=000
``` as the options.

---

### Post by jjross on 2005-12-27
check out this thread  [http://www.ubuntuforums.org/showthread.php?t=102220&highlight=change+permissions](http://www.ubuntuforums.org/showthread.php?t=102220&highlight=change+permissions)

---


---
title: "Adding A New Hard Drive"
date: 2005-12-21
forum: Desktop Environments
---

### Post by TuxDaddy on 2005-12-21
I am adding a new hard drive today or tomorrow and I have some questions.

Once I add the new hard drive I want to devote it all for /home.  Then I want to delete the old home paritition and add it to /root (I am running out of space on /root).

How do I this?  Does anyone know of a doc the explains the Lunix file system?  Like what is stored in /var and such?  

Thanks for the help!

R

---

### Post by schilcha on 2005-12-21
[QUOTE=TuxDaddy]Once I add the new hard drive I want to devote it all for /home.  Then I want to delete the old home paritition and add it to /root (I am running out of space on /root).[/QUOTE]

I assume your situation is: 1 drive, 1 partition (disregarding swap). If thats true, just 
*)add the drive, partition it to your needs (e.g. one partition for the new home of home). 
*)Mount it temporarily (e.g. to /mnt). 
*)Copy the contents of /home to the new drive (/mnt). 
*)To make sure you don't loos any data, rename /home to /home.backup. 
*)Create new, empty /home
*)Umount /mnt
*)Edit /etc/fstab to mount the partition on your new drive as /home
*)Mount new /home
*)Once you're sure everything's allright, delete /home.backup

This is the console-approach. I don't know, if there are any GUIs to do this in ubuntu (except for gparted).

ALSO: renaming /home if you're logged in using /home is probably causing troubles. I suggest doing this in runlevel 1 (single user mode) or in the recovery-mode (I've never used it, but I guess you do not login as the normal user there).

Good Luck

---


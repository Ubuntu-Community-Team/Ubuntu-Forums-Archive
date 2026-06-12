---
title: "password for my regular user not working"
date: 2005-04-11
forum: Desktop Environments
---

### Post by neighborlee on 2005-04-11
hi..

   my user password is no longer working and I did NOT change it.  Is there a fix for this or am I looking at a complete reinstall...

cheers
nl
----

---

### Post by bored2k on 2005-04-11
Here's is a method that worked on me a while back [just like ubuntuguide.org]:
1. Boot with your installation disc.
2. Follow instructions until the [Partion disks].
3. Without going any further, press Ctrl+Alt+F2.
4. Press enter to activate the root console.
5. > ~ # mkdir /ubuntu
~ # fdisk -l /dev/discs/disc0/disc
~ # mount <wherever your Ubuntu root device is> /ubuntu/
~ # chroot /ubuntu/ 
6. To change root passwd press 
# passwd

After this, you can boot through your HDD just like usual, and when the GDM appeats, hit Ctrl+Alt+F2 to get a shell, and there login as root. After logged in, 
# passwd username
To reset your user passwd, then Ctrl+Alt+F7 to go to the GDM again.

---


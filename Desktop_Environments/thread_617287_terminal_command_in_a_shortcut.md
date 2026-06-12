---
title: "terminal command in a shortcut"
date: 2007-11-19
forum: Desktop Environments
---

### Post by quickshot89 on 2007-11-19
basically i have gnump3d, but to update the libary, i have to enter in a terminal

sudo /etc/init.d/gnump3d stop

and then 

sudo gnump3d --background

is there a way to create a desktop shortcut that excutes these commands with me needing to enter them into terminal everytime i get a new album? it would be handy as i plan to rip all the CD's downstairs onto my server for ease to listening

cheers

---

### Post by bingoUV on 2007-11-19
You can use gksudo instead of sudo, and then you can easily create a desktop shortcut that does what you want. But it will ask for a password. If you do not want it to ask for a password, follow steps similar to [http://ubuntuforums.org/showthread.php?p=3768173#post3768173](http://ubuntuforums.org/showthread.php?p=3768173#post3768173).

---


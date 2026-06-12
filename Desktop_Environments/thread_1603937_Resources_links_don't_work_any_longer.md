---
title: "Resources links don't work any longer"
date: 2010-10-23
forum: Desktop Environments
---

### Post by dongiulio on 2010-10-23
Hi all, 

Since I've moved the /home directory to a new mountpoint 

(UUID=160b687f-3e30-472e-97c2-7fd6149ec2a0 /home		  ext4    nodev,nosuid    0       2 in the fstab menu) 

I have troubles with the links on the places menu. all the links there that point to /home or to one of its subdirectories don't work any longer. 

The links to usb drivers and other places work just fine. 

I've tried reinstalling xdg and gnome-menu, but no success. Any clue on how I could fix this? 

if I do cat .xsession-errors right after trying to click on one of the links in the menu this is what I see: 
 
giulio@giulio:~$ cat .xsession-errors
...
/home/giulio: /home/giulio: is a directory


Thanks a lot, 
Giulio

---

### Post by dongiulio on 2010-11-09
Found a solution on this @ [http://wwww.ubuntuforums.org/showthread.php?t=1610745](http://wwww.ubuntuforums.org/showthread.php?t=1610745)


thanks,

---


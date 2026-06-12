---
title: "Mouse Video problem"
date: 2006-08-17
forum: Desktop Environments
---

### Post by marvlus on 2006-08-17
I could not see where this problem has been posted.  I recently upgraded to Dapper Drake from 5.10.  When I move my mouse, the cursor "paints" over the area where I'm moving.  I am using a KVM with a wireless Logitech keyboard and mouse.  I never had this problem with Ubuntu 5.10.   In addition, if I boot with the Live CD of Dapper Drake, this problem does not occur.  I'm thinking of reinstalling Dapper Drake.   Any thoughts from anyone would be appreciated.

---

### Post by murataht on 2006-08-17
maybe it is a problem left from old configuration files. try to delete .gnome .gnome2 and other gnome related configuration files. (back up them first!!!!). and login to see if it has fixed. if it has not yet, maybe the mouse configuration in xorg.conf has something do to with it. try to compare the live CD xorg.conf file and your system xorg.conf file. 
above are just suggestions. and before editing/deleting the configuration files, please do make a backup. 
good luck

Murat

---

### Post by marvlus on 2006-08-21
Thanks for your suggestions!

---

### Post by marvlus on 2006-08-29
I finally resolved the issue, but I'm not sure why this works.  I changed the monitor resolution from 1024 X 768 to 1280 x1024.  The problem went away!

---


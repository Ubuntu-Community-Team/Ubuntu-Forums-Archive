---
title: "[SOLVED] Sudo cp (from thumb drive)"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by Corbin on 2007-08-11
Hey, I was messing with the xorg.conf file and screwed something up. I backed up file to my thumb drive tho. But i am unsure as  how to replace the xorg.conf_backup on the thumb drive with the xorg.conf  on 
the hard drive

I know i would do something along the lines of:

sudo cp (???????????)xorg.conf_backup /etc/X11/xorg.conf

But What do i put in the (????????????) part... 

-Thanks


I am running the newest version of Ubuntu on a 32bit P4.

---

### Post by Corbin on 2007-08-12
AHH! NVM 

I got it


I got it with 

sudo cp /mnt/thumb/xconf.conf /etc/X11/xconf.conf



 (IIRC) 

-Thanks

---


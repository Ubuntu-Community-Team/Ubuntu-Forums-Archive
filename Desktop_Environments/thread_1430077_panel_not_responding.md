---
title: "panel not responding"
date: 2010-03-14
forum: Desktop Environments
---

### Post by zander1013 on 2010-03-14
hi,

i am using ubuntu 9.10 and have been successfully on this machine for awhile.

tonight when i reboot the machine and tried to login to my usual user account it seems to be hanging when the panel (the app panel across the top of the screen)tries to start. this is the case with repeated attempts to login to my normal user account.

so i have logged in as root and it seems to be working okay in the root account.

perhaps i should reinstall this panel?

please advise.

---

### Post by phillipjennings5 on 2010-03-16
HAHA i got my panel to work!   put this in the terminal

gksudo pkill gnome-panel

hope this helps

---

### Post by dp69_2001 on 2010-04-03
revive this one. I did a clean install of 9.1 and got the psb driver working, and did all the updates. Now the ubuntu menu button doesn't respond. Right clicking on the desktop brings up no menu. but right clicking on most of top bar does bring up a menu. Alt+f1 does bring up the ubuntu menu.

---

### Post by dp69_2001 on 2010-04-03
> **dp69_2001 said:**
> revive this one. I did a clean install of 9.1 and got the psb driver working, and did all the updates. Now the ubuntu menu button doesn't respond. Right clicking on the desktop brings up no menu. but right clicking on most of top bar does bring up a menu. Alt+f1 does bring up the ubuntu menu.
 
 
removed it from panel and re-added it, that fixed it.

---


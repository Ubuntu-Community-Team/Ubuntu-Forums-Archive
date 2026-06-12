---
title: "Display Settings"
date: 2007-09-29
forum: Dell  Ubuntu Support
---

### Post by seegreen on 2007-09-29
I have a dell Iinspiron E1505 with a nivida graphics card and I just upgraded to Ubuntu 7.10 beta. I saw that there ware options for dual monitors so I went and found another monitor. I changed the setting multiple times but when being prompt to log off users, I log off or I may have accidentally rebooted instead but I can not remember but then before logging back in a screen and graphics settings window comes up and ask me to set up the screen but when I click OK it just opens up again and the same thing happens if I click cancel. I can hit ctr+alt+F1 to switch out of gnome and use terminal but I do not know how to get rid of the graphics and screen settings window coming up.

---

### Post by ridgeland on 2007-09-30
from the terminal have you tried to edit
/etc/X11/xorg.conf
This has the monitor settings. 
Try
$ ls -l /etc/X11/xorg*
and see if there is a backup that works.
first copy xorg.conf to a safe name then overwrite it with a backup

---

### Post by seegreen on 2007-10-04
Thanks, that worked very well

---


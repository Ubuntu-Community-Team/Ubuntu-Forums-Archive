---
title: "Unusual boot issue, always boots recovery console"
date: 2009-06-17
forum: General Help
---

### Post by sparklyprgs on 2009-06-17
+ Fresh install of 9.04 alternate CD, select defaults, but use LVM + disk encryption for entire partition
+ Install finished with no problems, rebooted and by default, recovery console appears! :(
+ BUT ... can't select items on the menu properly. Arrow keys generate "^[[[B" type codes (ansi or esc codes?) on top of menu (plz see picture)

[http://bayimg.com/IabLaaAcC](http://bayimg.com/IabLaaAcC)

If I press escape once then press enter (not just press enter), the machine boots fine! :confused:

If I **force** GRUB to boot the recovery mode option, the recovery menu works fine (arrows move menu normally and selecting resume normal boot works fine).
Live CD works normally but haven't tried to reload using Live CD (it wont do LVM + disk encr enyhow)

Any clues where to look to find the problem?  Thanks!

---

### Post by sparklyprgs on 2009-06-17
I forgot to mention that I can reproduce the problem. When I reinstalled using the exact same way (alt cd, LVM etc) a second time, the problem was identical.

---

### Post by Augsburg on 2009-06-17
Try this:


sudo nano /boot/grub/menu.lst

Change the line that says:

default x

(x being some number - this is the 14th line of the file on my install)

to 

default 0

---

### Post by sparklyprgs on 2009-06-18
Thanks Augsburg but the menu file already had "default 0".

If I press ESC at the GRUB prompt and manually select to boot the first normal kernel from the menu (not the recovery one), I get the same problem.

---


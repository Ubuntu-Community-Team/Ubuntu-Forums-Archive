---
title: "startx no longer kicks off automatically?"
date: 2008-12-21
forum: General Help
---

### Post by tescott on 2008-12-21
I'm running Ubuntu 8.10 off a USB pendrive with my MSI Wind netbook.  Things had been going fine until I installed aircrack-ng.  I was messing around with that and got my machine to lock up hard.  Mouse didn't respond, alt-tab, special-tab, nothing got a response from it.  After waiting a bit and seeing no change, I did the worst and held down the power key until the thing finally powered down.

Now, when it comes up, it dumps me to the command prompt instead of kicking off the desktop gui.  I can "startx" and get things running again, but want to understand what might have happened and what it will take to get the desktop gui going automatically.

I was thinking the runlevel may have changed.  Doing "sudo runlevel" shows me "N 2".  I think this is normal.

Assuming that aircrack-ng was at fault, I uninstalled that, but I'm left with the same issue.

Thanks in advance for any help.

---

### Post by tescott on 2008-12-22
I ended up just reinstalling everything to get back to square one.  :P

---

### Post by xRes on 2008-12-22
reinstall always works :)
Perhaps in the future running ```
sudo dpkg-reconfigure xserver-xorg
``` may have also worked for you.

---


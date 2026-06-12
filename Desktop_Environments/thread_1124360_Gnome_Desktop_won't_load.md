---
title: "Gnome Desktop won't load?"
date: 2009-04-13
forum: Desktop Environments
---

### Post by javyn999 on 2009-04-13
Hey all, new Ubuntu user here.  Installed it on my computer Thursday night and love it. 

But I ran into a problem when I booted this morning... 

Now when I boot into Ubuntu, my GNOME desktop doesn't load.  The background wallpaper loads, but none of the toolbars or anything.  

The only change I made was uninstalling Evolution, I guess that screws things up?  I uninstalled Evolution, installed Thunderbird, then had a change of heart and Uninstalled TBird and reinstalled Evolution.  

I guess removing the apps that came with Ubuntu breaks the installation?

Or perhaps it's a hardware issue, because my Windows OS on this computer won't load either.

I'd appreciate any ideas!

---

### Post by PacSci on 2009-04-13
My guess is that when you uninstalled Evolution, you uninstalled ubuntu-desktop, the package that contains all of the GNOME stuff. Even if you reinstall Evolution, ubuntu-desktop isn't automatically reinstalled, and if a crucial GNOME component had some kind of update or something, it might not have been picked up. Try running "sudo apt-get install ubuntu-desktop" to reinstall the desktop package (if your computer can get as far as the wallpaper, you can press Ctrl+Alt+(F2-F6) to switch to a console).

---

### Post by javyn999 on 2009-04-13
Thanks!  I appreciate the response!  I'm getting the sinking suspicion it may be hardware related, since I get random reboots all the time, and Windows doesn't load either.

I will definitely give what you said a try though!

---

### Post by javyn999 on 2009-04-14
Reinstalled the ubuntu desktop from the command line, worked fine.  Then I just decided to format the drive, removing my Windows partition and went straight Ubuntu.  If I need Windows I'll just run a virtual machine, solved all my problems thanks!  How would I mark this thread as solved?

---


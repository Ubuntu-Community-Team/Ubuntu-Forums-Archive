---
title: "HELP with monitor"
date: 2007-11-05
forum: Desktop Environments
---

### Post by Roller005005 on 2007-11-05
i changed the monitor settins and now my screen is all messed up so is there any way to restore the defult settings in 7.10 without booting it? also when i boot it up it says out of range so plz help

---

### Post by l33t_3lv3n_g33k on 2007-11-05
When your computer first boots up, there should be a GRUB screen that asks you to select your OS.  (Sometimes there is simply a message at boot that says to press ESC to see the GRUB menu.  Press ESC!)
 
The second entry down should be a "recovery console"  Select this one and you should boot up to a command console (no GUI to be messed up).  Enter this command:
 
```
sudo dpkg-reconfigure xorg-xserver
```
 
This will run you through a wizard to reconfigure your display settings.  Should be fairly straight-forward.
 
As far as the "Out of range" message when booting...  I'm still working on that issue myself.  It's just cosmetically irritating rather than an actual problem.  The installer misconfigured the display settings for the boot splash screen (called usplash).

---

### Post by Roller005005 on 2007-11-05
the code didnt work it said that xorg-xserver is not installed

---


---
title: "Nautilus (and desktop) won't start in jaunty"
date: 2009-05-05
forum: Desktop Environments
---

### Post by Freckletoe on 2009-05-05
So I've had some trouble with my desktop as of late and the short of it is that I uninstalled all of the file managers on my system (Nautilus, Konqueror, Dolphin) and only reinstalled nautilus. (I have no desktop at this point) So I go into gconf-editor to change my preferences and find that the 'show_desktop' box *is* checked, but still no desktop. 

So I try to open a folder and it won't open, which shouldn't happen. So I went into the terminal and typed in 'nautilus' and it came up and said that Nautilus wasn't installed. So I tried apt-get and it said that it didn't install, delete, upgrade any files so that said to me that Nautilus was, indeed, installed.

So as of now I have:
-no desktop
-a limited knowledge of the terminal
-no file manager
-a headache

What should I do to get Nautilus up and running again?

---

### Post by gettinoriginal on 2009-05-10
I hope you have already fixed this, but in case you have not.
Try this: System Restore
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---


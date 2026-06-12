---
title: "GNOME will not start after update"
date: 2008-07-04
forum: Desktop Environments
---

### Post by robf1225 on 2008-07-04
I did a new install of 8.04 (Hardy Heron).  After I did an update of all the packages and rebooted, GNOME doesn't start.  I get wallpaper and nothing else, no menubar, and I can't run any programs.  I deleted my .gnome* directories.

---

### Post by sayakb on 2008-07-04
Try logging in to Failsafe session. Press F10 at the login prompt (GDM) and click **Select Session** and click on Failsafe Gnome from there.

---

### Post by maengyi on 2008-07-04
I also have this problem.

I just installed the Ubuntu 8.04, And installed ATI graphic card driver & configured compiz.
Then upgread.

After reboot, the gnome wont start up, after the login window.

I can enter the Failsafe Gnome mode.  BUT I dont know what to do after that. -_-; 

Plz help.  Thanks a lot!

---

### Post by robf1225 on 2008-07-04
When I login in via GNOME Failsafe I get the same thing.  I can access the file browser via ctrl-f and can run stuff that way.  I don't know how your are supposed to fix this via GNOME Fail safe of a failsafe command prompt.

---

### Post by biopsiste on 2008-07-05
i have the same problem. is there a way to open the terminal?

---

### Post by sayakb on 2008-07-05
Press Ctrl+Alt+F1 (to F6) to open a tty terminal.
Add a user there using useradd
[http://www.ss64.com/bash/useradd.html](http://www.ss64.com/bash/useradd.html)
Try logging into the new user.

---

### Post by robf1225 on 2008-07-05
Nope, same problem with a new user.

---

### Post by maengyi on 2008-07-05
I thought it is the problem of the gnome.  So i tried the KDE.  
But nothing changed. 

And this problem only happed When i installed the compiz and updated.

BTW, my computer has a ATI graphic card. 

& the computer with Nvidia graphic card does not have this problem.

---

### Post by robf1225 on 2008-07-06
I have a ATI card as well, a Radeon, and I don't have compiz installed.  KDE works just fine, this is just a problem with GNOME.

---

### Post by robf1225 on 2008-07-07
For whatever reason gnome-panel was not installed.  Everything is fixed after re-installing gnome-panel.  Question is why was gnome installed without gnome-panel, sounds like a dependency issue.

---


---
title: "apparently lost all GUI"
date: 2010-10-17
forum: Desktop Environments
---

### Post by PerryTrenton on 2010-10-17
Suddenly and without reason or recent changes or upgrades to my system I cannot log in to my desktop.  I am presented with the standard log-in screen where I click on my user name and type in my password.  Then the screen goes dark momentarily before returning to this same log-in screen.  I can log into a terminal with recovery mode, and from the terminal I can start Xfce4, but of course the recovery mode and the Xfce environment are in root.  I tried reinstalling xserver-xorg-core and xubuntu-desktop, but the problem remains.  Suggestions?

update: After much searching and research I find that there is tendency since at least 2006 for the .ICEauthority and .Xauthority files to become owned by root with restricted permissions.  If you are having the same problem as I describe above you will see an error message in the terminal when trying to startx "unable to access /home/<username>/.ICEauthority."   These two files are in the home user directory.  The solution is to remove or rename them.  Worked for me!

---


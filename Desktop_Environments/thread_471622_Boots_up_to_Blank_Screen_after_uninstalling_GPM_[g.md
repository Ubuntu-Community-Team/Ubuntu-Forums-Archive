---
title: "Boots up to Blank Screen after uninstalling GPM [gnome power manager"
date: 2007-06-12
forum: Desktop Environments
---

### Post by medium-newbi on 2007-06-12
I thought i could solve a bug problem in GPM gnome power manager by uninstalling it.  But what i got after rebooting is blank screen after booting process finished.  How do i undo what i did.  The only way i got my browser to use was by clicking on the keyboard for 'print screen ' and then went through 'help' to get help online.  Can someone guide me into how i can reinstall gnome power manager thru Terminal?  But the only way i know how to get to the Terminal prompt is by stopping the rebooting process at 'recovery' i think.  Well any way i need help 

Ubuntu 6.06 Dapper Drake i386 Pent 4 RAM 1165Mb gnome power manager ver 2.14.0
DBUS 0.60-6ubuntu8.1 HAL 0.5.7-1ubuntu18.2
Kernel 2.6.15-28-386

---

### Post by medium-newbi on 2007-06-12
Answer supplied by: Hanusz Lescek: Hello,

You should be careful when removing packages.
When you removed gnome-power-manager, it also removed gnome-session and ubuntu-desktop
(because gnome-power-manager is a dependency of gnome-session and gnome-session is a dependency of ubuntu-desktop)

to solve this, go to a terminal with <CTRL><ALT>F2
Enter your login and password
then type this:
sudo apt-get install ubuntu-desktop

---


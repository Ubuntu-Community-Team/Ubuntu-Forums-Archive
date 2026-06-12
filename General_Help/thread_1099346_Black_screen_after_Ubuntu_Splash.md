---
title: "Black screen after Ubuntu Splash"
date: 2009-03-18
forum: General Help
---

### Post by nefrin on 2009-03-18
Have asked for help on IRC and searched the forums, but not found an answer yet, so here is the problem.

Uninstalled the file for OpenOffice.org 2.4 and associated file, so I could install OpenOffice 3.0. After doing that, my computer will boot up through the Ubuntu Splash screen, and then goes directly to a black screen with a mouse pointer (that I can move around). cntl alt f1 takes me to the text login.

This problem has only occure since the uninstall of OpenOffice 2.4 (so either the system is dependent on that, or I accidently uninstalled something important).

Things I have tried:
reconfigure xserver-xorg (no avail)
replace xorg.conf with my xorg.conf_backup file (no avail)
Booting into recovery mode, using the options to fix packages or the xserver (no avail)
Booting into a previous kernal (no avail)

system specs:
HP machine, 500gb hard drive
Windows XP/Ubuntu 8.04 dual boot
Ubuntu partitions: /boot, /home, / , /tmp, swap
5.5 GB of RAM
Nvidia 8600 graphics card with dual monitor setup
AMD 64 dual core processor (running 8.04 64)

If anyone can help, please. I am down to doing a full reinstall, and would prefer not to have to do that.

---

### Post by ruel- on 2009-03-18
have you tried:

```
sudo apt-get install --reinstall ubuntu-desktop
```

maybe you accidentally uninstalled gnome.. or w,e

---

### Post by nefrin on 2009-03-18
It worked!

Exact steps taken:

Booted up the system until I got the black screen with the mouse pointer

cntl alt F1 to the text login

logged in with username/password

did "sudo apt-get install --reinstall ubuntu-desktop"

allowed the system to install, then did a sudo reboot

System started up, all my files and desktop presets were still present.

Thank you so much!

---

### Post by ruel- on 2009-03-18
no problem.. :)

---


---
title: "Ubuntu 10.10 theme changed after driver install"
date: 2011-01-23
forum: Desktop Environments
---

### Post by DRJTower on 2011-01-23
After installing the nvidia drivers and rebooting my theme changed to an ugly gray theme. Changing the theme in the System>Preferences>Appearance only changes the window title bars but everything else stays in this ugly gray theme.

Attached is screenshot.

The drivers are installed and working (visual effects work).

How can I get rid of the this gray theme?

Also I am new to ubuntu, mainly use GUIs to set things up.  I'm not afraid of the terminal, but I just don't know my way around the Linux file system yet.

Thanks for your help!


EDIT: Just remembered I also updated everything from the Update Manager before rebooting.
Also this is a brand new install.  Only changes are from the Update Manager and the Driver utility.
Every thing looked fine before I rebooted (default ubuntu 10.10 theme)

EDIT2: Just noticed that if you log out and log back in themes work fine, but every time you reboot and login for the first time you get the gray theme again.

---

### Post by Krytarik on 2011-01-23
There is a megathread running regarding similar behaviours, seems to be a common issue currently:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

You may also check ~/.xsession-errors and /var/log/Xorg.0.log for error messages.

---


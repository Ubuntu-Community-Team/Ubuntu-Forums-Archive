---
title: "New Install Locks Up"
date: 2005-10-13
forum: Desktop Environments
---

### Post by jhuff on 2005-10-13
[FONT='Times New Roman']Downloaded the new version of ubuntu 5.10.  Tried installing it on the Pentium II computer.  It locks up prior to loading GNOME.  One time it got as far as allowing me to log on then locked up prior to displaying the desktop.  I restarted the computer and then it locked up just prior to loading the login screen.  Any suggestions[/FONT]

---

### Post by adwait on 2005-10-13
Seems like a problem with video drivers. What kind of card do you have? Have you installed the drivers for it? Have u tried running this:
```
sudo dpkg-reconfigure xserver-xorg
```

To run this, at the GRUB menu press e to edit the boot options and at the end of the line add "1". Then press b to continue booting. That should get you in a command prompt.

---

### Post by jhuff on 2005-10-14
Were do I add the "1"?  After "boot"?

---

### Post by adwait on 2005-10-14
RIght at the end of the line

---


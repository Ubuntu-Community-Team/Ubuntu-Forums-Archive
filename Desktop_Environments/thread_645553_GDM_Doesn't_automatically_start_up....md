---
title: "GDM Doesn't automatically start up..."
date: 2007-12-20
forum: Desktop Environments
---

### Post by iposner on 2007-12-20
Trying to fix a sound card issue, I followed the instructions of a post on this site, one of the steps of which was to remove the ubuntu-desktop. Big mistake. Having reinstalled it from the console with apt, the system no longer automatically loads the Session login screen. Instead, I have to login using the console and start gnome with "sudo gdm".

Obviously something has been deleted from the boot sequence, but what and where?

---

### Post by oldos2er on 2007-12-20
Once you're logged in and running Gnome, go to System, Administration, Services, and check off Graphical login manager.

---

### Post by iposner on 2007-12-21
The Graphical Login Manager (gdm) is already checked when Gnome is running.Unchecking or checking made no difference, even if rebooting inbetween. Does anybody KNOW what file contains the initialization sequence?

---

### Post by iposner on 2007-12-21
Solved it myself: /etc/X11/default-display-manager had the path mistakenly set to /usr/bin/gdm :

Correcting this to /usr/sbin/gdm solved the problem.

---

### Post by porolycapa on 2008-02-07
I had the same problem after install / uninstall KDE 4 (not stable enough for everyday use). The mentioned method above works just fine! Smooth...:)

---


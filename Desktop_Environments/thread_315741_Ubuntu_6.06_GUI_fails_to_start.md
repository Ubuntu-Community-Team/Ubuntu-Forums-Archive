---
title: "Ubuntu 6.06 GUI fails to start"
date: 2006-12-09
forum: Desktop Environments
---

### Post by paul.c on 2006-12-09
Hi
I tried to upgrade my KDE version via Automatix2 but since doing so when I power up my PC it goes into a tty login prompt. I am unable to start KUbuntu but I can start Ubuntu with startx. Can anyone let me know how to get my system to go straight into the GUI on startup.

Thanks for any help.

---

### Post by Tyche on 2006-12-10
> **paul.c said:**
> Hi
I tried to upgrade my KDE version via Automatix2 but since doing so when I power up my PC it goes into a tty login prompt. I am unable to start KUbuntu but I can start Ubuntu with startx. Can anyone let me know how to get my system to go straight into the GUI on startup.

Thanks for any help.

Take a look at /etc/X11/default-display-manager (I had a similar problem).  If you "sudo vim /etc/X11/default-display-manager", even in console mode, (and remember to type your password at the prompt) you should see a single line of text with the complete path to your display manager.  It should read either "/usr/sbin/gdm" or "/usr/bin/kdm".  Please note that the gnome display manager is in sbin and the kde display manager is in bin (there IS a difference, as I discovered after a frustrating half-hour :)  ).

---


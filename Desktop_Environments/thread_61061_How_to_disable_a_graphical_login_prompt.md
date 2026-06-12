---
title: "How to disable a graphical login prompt?"
date: 2005-08-30
forum: Desktop Environments
---

### Post by z-vet on 2005-08-30
Hi all.
I would like to disable a graphical login prompt and start X manually (login in console and then 'startx &'). Tried to change the default runlevel in /etc/inittab to init:3 but it didn't helped. How can i do it in Kubuntu?

---

### Post by ispmarin on 2005-08-30
Comment the line  /usr/bin/gdm inside the file default-display-manager on /etc/X11. This should help. If you dont want to reboot, go to a terminal (with Crtl+Alt+F1), log in and issue as root 'killall gdm'. This should kill the running gdm. 

Hope it helps.

Ivan

---

### Post by incinerator on 2005-08-30
sudo update-rc.d -f kdm remove

---

### Post by z-vet on 2005-08-30
Thanks, ppl, it works. :)

---

### Post by gstover on 2007-07-23
The update-rc.d from the first reply worked for me if I changed "kdm" to "gdm".  So: 

sudo update-rc.d -f gdm remove

---


---
title: "How do I change the Default Display Manager?"
date: 2006-05-24
forum: Desktop Environments
---

### Post by Sukarn on 2006-05-24
Hey guys,
I installed kubuntu-desktop on top of ubuntu-desktop and selected kdm as default display manager, but now I want gdm back as the display manager. Is there a way to do this without removing kubuntu-desktop?

---

### Post by Qrk on 2006-05-25
Here are a couple of ways.

[http://ubuntuforums.org/showthread.php?t=136758&highlight=switch+kdm+gdm](http://ubuntuforums.org/showthread.php?t=136758&highlight=switch+kdm+gdm)

---

### Post by jones_jj on 2006-05-25
Sukarn, the easiest way to switch between the 2 managers is on the welcome/login screen.  You will see near the bottom of the screen it says **Session**  click this, and you will be able to choose which desktop manager you want to run.  Good luck.

---

### Post by Sukarn on 2006-05-25
Thanks. I tried the first method (sudo dpkg-reconfigure gdm) listed in the thread that Qrk pointed me to. It worked with a system restart.

**jones_ji**, selecting the session type (KDE, Gnome, failsafe(terminal only), etc) only selects the session type. I was asking about the display manager (the login screen).

---


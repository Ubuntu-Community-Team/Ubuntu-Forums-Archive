---
title: "CTRL-ALT-F[1-6] doesn't show login prompt"
date: 2005-08-04
forum: Desktop Environments
---

### Post by mstralka on 2005-08-04
I've been running Hoary on my Compaq SR1210NX with Gnome and Kubuntu for several months now and this has been a problem for a while, although I don't know exactly when it started.  If I'm running Gnome or KDE and I press CTRL-ALT-F2 (or any other F key up to 6), it takes me to the black screen but does not present a login prompt.  There is text at the top of the screen, but it's the boot-up text.  I have to press CTRL-ALT-F7 and return to Gnome/KDE in order to do anything.   Does anyone know why C-A-[Fx] doesn't work?

Thanks
Mark

---

### Post by mstralka on 2005-08-05
Nobody has ever experienced this problem where CTRL-ALT-F2 doesn't bring up a login prompt?  Please :)

---

### Post by helsby on 2005-08-05
think yourself lucky you get a gnome/kde login screen. I just get a black screen on all choices  :neutral:

---

### Post by az on 2005-08-05
What video card do you have?  It sounds like a framebuffer problem.  What happens when you go into the blank screen and type in blindly your username and then your password, followed by 
sudo halt
(and then your password, enter)

---

### Post by helsby on 2005-08-05
mines actually a livecd so i don't have a username and password.
What I don't understand is why the laptop beeps and then about 3-5 minutes later shuts down. I guess somehow it is receiving the shutdown sequence.

---

### Post by mstralka on 2005-08-05
[QUOTE=helsby]mines actually a livecd so i don't have a username and password.
What I don't understand is why the laptop beeps and then about 3-5 minutes later shuts down. I guess somehow it is receiving the shutdown sequence.[/QUOTE]

Umm... I think you have a different issue which should probably be in a different thread.  I started this thread because I can login to Gnome or KDE and my NVIDIA card works just fine, but, once in Gnome/KDE, if I press C-A-F2, I get a black screen, instead of the login prompt

---


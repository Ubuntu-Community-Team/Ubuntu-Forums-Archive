---
title: "Time consuming steps"
date: 2009-02-13
forum: General Help
---

### Post by Hartfield on 2009-02-13
I have a couple of issues with linux at the moment.

I have Ubuntu installed on a laptop (Vostro 1700) It has becomed such a hassle logging back on after putting the laptop in sleep mode (or closing lid).  I have to log on and then log on again to connect to the internet (wireless). 

Is there any way I can avoid the log in window at the start?

---

### Post by mb_webguy on 2009-02-13
Well, you could enable automatic login in Login Window.  I think that will cause you to automatically login upon returning from suspend.

---

### Post by Hartfield on 2009-02-13
I saw the option on System>Administration>login window

I put my username but it did not work

---

### Post by geirha on 2009-02-13
I assume it didn't work when coming out of suspend, but it logs you in if you reboot the computer?

To have it stop locking X when suspending, you'll need to do it from gconf. Hit Alt+F2 to get the run dialog, run «gconf-editor», browse to /apps/gnome-power-management/lock/ and untick «suspend».

---


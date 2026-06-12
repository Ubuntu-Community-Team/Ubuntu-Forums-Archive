---
title: "915 resolution problems HELP!!!"
date: 2009-03-11
forum: General Help
---

### Post by Atrio05 on 2009-03-11
I was recently trying to hook up my laptop to my HDTV and messed with some resolution settings and now every time i restart my computer it goes to 1024x786 resolution instead of 1280x800. I tried re-installing 915 resolution. I can reset it to 1280x800 in system>administration>screens and graphics, but when i restart the computer it resets it back to 1024x768. and its quite annoying having to reset it every time i log onto the computer. 

Can anyone help?

---

### Post by LegendofTom on 2009-03-11
Try runnning dpkg-reconfigure xserver-xorg as root. This may be able to reset your resolution.

---

### Post by anlag on 2009-03-11
Try 

> sudo dpkg-reconfigure xserver-xorg

and follow on-screen instructions to redo the configuration of your X server. Often helps when something that used to work suddenly doesn't due to some setting one poked around with.

---

### Post by Atrio05 on 2009-03-12
bump!!!

---


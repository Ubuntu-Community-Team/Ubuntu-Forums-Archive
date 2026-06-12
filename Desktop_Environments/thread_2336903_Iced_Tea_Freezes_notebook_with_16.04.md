---
title: "Iced Tea Freezes notebook with 16.04"
date: 2016-09-12
forum: Desktop Environments
---

### Post by luke24592 on 2016-09-12
upgraded from 14.04 to 16.04 on HP-15 notebook.  I use this primarily to monitor dlink security cameras on my LAN.  One camera requires Java to show video and I always used Iced Tea on 14.04.  Since upgrading to 16.04 the entire PC will freeze up within a few minutes of activating Java on this camera.  All other cameras work fine until I activate Java on this one.  Freeze up locks mouse and keyboard.  Only option is to power off and back on.  Thanks for looking.
Luke

---

### Post by &amp;KyT$0P# on 2016-09-12
Few things to check:

1) Are you using the same Java version as you were on 14.04?
2) Is the system really locked up or just the graphics?  Can you Ctrl-Alt-F1 (or through Ctrl-Alt-F6) to get to a console login?
3) Have you tried running nothing else and no other cameras, just this one specific camera?

(It'd be smart to **backup your system before testing**.)

---

### Post by luke24592 on 2016-09-12
Thanks halogen2
I'm sorry but I don't know exactly what version I was using before the upgrade.  If it helps, I always did all the software upgrades when prompted by the system. I did the upgrade on 9/10/2016.  The version of Iced Tea I have now is 1.6.2-3ubuntu1.  The system locks up when there is only one Firefox window open with this camera in it or several windows open with other cameras.  As soon as I click the java button in the window for this camera, the system freezes in a few moments.  The sound stops and the picture freezes.  I tried Ctrl-Alt-F1 and Ctrl-Alt-F6 while it was locked up and nothing happened with either.

---

### Post by &amp;KyT$0P# on 2016-09-12
> **luke24592 said:**
> The version of Iced Tea I have now is 1.6.2-3ubuntu1. 
That would be Java 8, which unfortunately looks like the only version for 16.04 from the repositories.  Previous versions of Ubuntu offered the choices of Java 6 and Java 7 in the repositories.

Can you go back to 14.04, or (if your netbook has sufficient hardware) run this camera in a virtual machine running 14.04? :-k

I don't think I have any further ideas on this, sorry.  Someone else here might though?

---


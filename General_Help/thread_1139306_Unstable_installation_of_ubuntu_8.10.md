---
title: "Unstable installation of ubuntu 8.10"
date: 2009-04-26
forum: General Help
---

### Post by doggbat on 2009-04-26
I'm not sure what the issue is with my laptop, but the entire system goes all colourful and glitchy sometimes.  It freezes right up, but for a little quiver, and I have to do a hard reboot.  I'm fairly new to linux, so I don't even know how to get a crash report of some kind.  Any help is appreciated.  Please let me know how to find out any information about this problem.

My computer:

HP Pavillion dv9535nr
2 110GB Hard Drives
nVidia graphics card (i'm not sure which)
1.6GHz Intel dual core processor.
2GB of Ram


I set up a two GB swap memory partition in hopes of solving the problem, but it did not help.
I cannot link  the crashes to any programs.  (well, it happened twice when I ran OOo word processor for a long time, then ran XMoto without closing OOo.  On the third time, it did not happen). 

Thanks, doggbAT.

---

### Post by Sam Lars on 2009-04-28
You could look in /var/log/syslog, which you can also see in the System Log Viewer in the menus.  Look at right before the time of the crash and see if there are any problems.

---


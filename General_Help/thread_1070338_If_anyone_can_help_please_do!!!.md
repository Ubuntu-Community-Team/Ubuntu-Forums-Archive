---
title: "If anyone can help please do!!!"
date: 2009-02-15
forum: General Help
---

### Post by megaJuice on 2009-02-15
I installed Ubuntu 8.10 about 3 months ago, and haven't had any problems with it. I recently (about 2 weeks ago) bought an ATI 9550 and tried to install and use it, and thought everything went fine. I booted up as usual, and got to the login screen with no problems (YAY!) but unfortunately that's where the good news ends (BOO!). As soon as I logged in the entire desktop was a mess of diagonal screen segments. I can see my mouse and everything on the screen, but it was all spread out and broken on the diagonal lines. Now I don't know anything about Ubuntu, and have no idea what codes to try and what codes to post. If anyone could help me I'll gladly post anything needed.

---

### Post by Alterax on 2009-02-15
sure.  Boot into the CD-rom.  Use it to repair your system.  There should be (under the Rescue a Broken System part) a section on repairing the Xorg Server (also known as the X server).  Try that, and let us know.  I'm running with an ATI card on my desktop as well; since they use the same driver I think we can make this work.

---

### Post by megaJuice on 2009-02-15
I think it has something to do with the resolution. After running fglrxconfig I got to the end where it says "Press Ctrl+Alt+Num- or Num+ to change resolution" and if I did that (pressing Num-) it changes the resolution and does the same diagonal line thing. Also at the end it says "Run startx" which I have no idea how to do, so if anyone has any idea how to do that, please let me know. I can only do stuff on my computer right now if I log in to "Failsafe Terminal". (I'm on my friends computer)

---

### Post by Elfy on 2009-02-15
Try to boot with the recovery mode - there is a small root menu - pick xfix

Once it has finished then use resume, that should set the system up with the default vesa driver

You will need to install the driver for the card from Hardware Drivers again.

---


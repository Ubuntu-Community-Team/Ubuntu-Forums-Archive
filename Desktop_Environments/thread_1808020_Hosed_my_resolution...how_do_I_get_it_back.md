---
title: "Hosed my resolution...how do I get it back"
date: 2011-07-19
forum: Desktop Environments
---

### Post by BarnOwl on 2011-07-19
I'm running Unbuntu 11.04 on a Dell laptop with a 19 wide monitor attached.  I tried setting it to 1440X900 with the GUI system tool and it seemed to work till I rebooted.  I didn't get the launcher (That's a problem for another thread.) but, I did still have the panel at the top.  So, I tried to set it back to 1024X768.  Then when it booted and I still didn't have the launcher but, this time I didn't have the panel either.  I was able to right click on the screen and create an xterm launcher.  I got here by typing firefox at the command line.  I used xrandr to see what my resolution was.  It's 2048X768 which explains some things.  There's also a .xsession-error file in my home directory.  I tried to attach it but, that didn't work and I don't know how to cut and paste in xterm.

 So, how can I straighten this out?

---

### Post by BarnOwl on 2011-07-19
I did a little digging around in apropos and found the command gnome-control-center.  It took a little playing around in there but, I got things working again.

---


---
title: "system hangs when I use firefox or galeon"
date: 2005-04-04
forum: Desktop Environments
---

### Post by plebeien on 2005-04-04
I make an upgrade of my ubuntu system twice a day and from two days ago, when I use firefox, loading my bookmarks it hangs and so do the system, I can't do anything, even getting out the X system... I have to reboot the computer.
today I installed Galeon and get exactly the same problem, there was an upgrade for firefox during my apt-get but didn't change anything, still the same problem.

I'm using epiphany without my bookmarks for the moment.

Does anyone have this problem ? Is there something to do ?

---

### Post by Leif on 2005-04-04
If you've got an nvidia card, renderaccel seems to be causing problems right now. Edit your xorg.conf to comment out the line with it.

---

### Post by BloGTK on 2005-04-06
Yes, it's a problem with the current NVIDIA drivers and render acceleration. I'm having the same problem with every application and having the system locking up. Commenting out the render acceleration line in your x.org conf appears to clear things up. 

Also, if you can SSH/Telnet into your machine, you can always do an '/etc/init.d/gdm restart' which will restart X without having to fully reboot the system.

---


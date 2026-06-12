---
title: "Can't open terminal and any GNOME applications"
date: 2009-04-15
forum: General Help
---

### Post by chang5562 on 2009-04-15
I used the remastersys to create a bootable LiveUSB.  However I found out that I could not open terminal and any other GNOME application, such as Firefox and Bresero DVD burner program, either default text editor IF I connected to the network (eht0).  when I unplug the cable, then I could use those programs again.  I made a change to the alsa-utils by adding a line -  ifconfig eth0 down, inside the stop) section.  The change is based on the bug report about ACIPD: exiting problem during the shutdown.  
I have 2.6.27.11 kernel.

---


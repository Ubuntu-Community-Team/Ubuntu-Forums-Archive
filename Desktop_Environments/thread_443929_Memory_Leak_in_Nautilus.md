---
title: "Memory Leak in Nautilus?"
date: 2007-05-14
forum: Desktop Environments
---

### Post by talcite on 2007-05-14
Hey guys,

I left my system on for a weekend and went home. When I came back, Nautilus was using 600M of ram!! Is it a memory leak, or something else?

This has happened one other time when I left my system on for an extended period of time. I'm running feisty. 

Thanks in advance.

---

### Post by benmoreassynt on 2007-05-22
Could it be something to do with Beagle? I found Beagle mashes the memory and hard drive, and since it is integrated with nautilus ...? I uninstalled Beagle and memory problems went away.

---

### Post by taylorkh on 2008-02-22
I just experienced something similar in Ubuntu 7.10.  I copied about 7,200  (530 MB) files from a CD to the desktop with a simple copy & paste.  After the copy completed I observed the memory in use rapidly move to 100%.  Nautilus was showing that it had 1.9 of 2.0 GB.  The sway then went to about 2/3 used.  After 10 minutes I killed the nautilus process and the system returned to normal.  

I copied the same files using gnome-commander with no problem.  I have removed beagle and am trying again.

Same problem. Nautilus eats the machine :mad:

Ken

---


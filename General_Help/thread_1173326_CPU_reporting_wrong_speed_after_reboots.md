---
title: "CPU reporting wrong speed after reboots"
date: 2009-05-29
forum: General Help
---

### Post by HarryTruman on 2009-05-29
I've had this problem with previous versions of Ubuntu but I'm currently on 9.04.  Whenever I reboot, BIOS recognizes my CPU as functioning at about half its speed.  Any time I shutdown or anytime I'm in a different OS both BIOS and the OS recognize the processor correctly.  It's just after rebooting in Ubuntu that this problem occurs.

Has anyone come across a fix for this?

---

### Post by bowens44 on 2009-05-29
By default, frequency scaling is enabled in Jaunty. /proc/cpuinfo shows my processor at 1gig most of the time , I have 2.8 gig processor. However if I run a CPU intensive application like glxgears cpuinfo shows the processor at 2.8 gig.

Of course this would no explain why you would see half speed in BIOS, this would have nothing to do with your OS.

---

### Post by HarryTruman on 2009-05-29
Yeah I understand CPU scaling IN Ubuntu, but like you said it shouldn't be affecting anything once the OS unloads and the comp reboots.

---


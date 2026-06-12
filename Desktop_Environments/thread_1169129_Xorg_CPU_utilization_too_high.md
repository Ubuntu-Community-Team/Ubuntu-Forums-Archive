---
title: "Xorg CPU utilization too high"
date: 2009-05-24
forum: Desktop Environments
---

### Post by deamon_knight on 2009-05-24
I've been having the problem on and off for a while. I'm running Xubuntu 9.04 on an old system (P2 400mhz). Sometimes it runs fine but more often than not, Xorg is using 30% CPU idle. I see alot of posts with similar problems but I can't find a solution. 

Another, possibly related? problem is that I can change my screen resolution to any of several options, but on a reboot it has always reverted back to 1024x768.

Any suggestions?

---

### Post by Arup on 2009-05-25
> **deamon_knight said:**
> I've been having the problem on and off for a while. I'm running Xubuntu 9.04 on an old system (P2 400mhz). Sometimes it runs fine but more often than not, Xorg is using 30% CPU idle. I see alot of posts with similar problems but I can't find a solution. 

Another, possibly related? problem is that I can change my screen resolution to any of several options, but on a reboot it has always reverted back to 1024x768.

Any suggestions?

What video card are you using currently?

---

### Post by deamon_knight on 2009-05-25
Thanks for the Reply Arup

From lspci:

00:0e.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

---

### Post by JabaDisa on 2009-12-02
Same problem with X server CPU load (15-25% when idle, reported by htop).
Video card is ATI Radeon 9200. CPU is Athlon 900MHz. OS is Xubuntu 9.04. There are also graphical bugs with the "System Load Monitor" panel applet. I'm thinking this might be ATI related. I'm going to look for proprietary drivers and possibly try that option out.

---


---
title: "ATI x1400+Compiz/Fusion - Gutsy - CPU 2 maxes out"
date: 2007-10-13
forum: Desktop Effects &amp; Customization
---

### Post by raydeen on 2007-10-13
I installed the Gutsy RC last night (distro-upgrade from Feisty) and while everything seemed to work well at first, I'm now noticing that after an indeterminate amount of time, everything slows to a crawl. I opened up the System Monitor and noticed that XGL was taking up almost all of CPU 2's cycles. It registers as using 49% total CPU power (makes sence). The only way I've gotten out of it is to kill XGL and re-log in. Is this the ATI driver or something else? Anyone else seeing this? I'm running a Dell Inspiron e1505, ATI x1400, 1 Gig ram. Seems like it goes crazy after I've been using the cube and Expo stuff for a while.

---

### Post by O_Isoz on 2007-10-14
I have the same problem and almost the same graphics card (X1300) 
(but for me it sucks up both my CPU's...)
rather annoying....

---

### Post by raydeen on 2007-10-15
Well, at least we're narrowing it down. Gonna have to start looking for problems relating to C/F and multi-core systems. Thanks for the reply. :)

Edit: Had it happen again just a few minutes ago, but this time it was CPU 1. I've also noticed that when I have to kill XGL, it's usually taking up 80-150 megs of memory. Memory leak here?

---

### Post by raydeen on 2007-10-15
Well, the problem *seems* to be solved. I'm holding my breath, but haven't had the slowdown yet after several hours of use. Here's what I did:

I followed the info at:
[http://ubuntuforums.org/showthread.php?t=574302](http://ubuntuforums.org/showthread.php?t=574302)

I didn't like the results (really slow redraw, no title bars on windows, etc.) so I turned off the 3d acceleration in the Restricted Drivers Manager, took fglrx out of the blacklist, restarted, turned 3d acceleration back on, rebooted and I'm pretty much back to where I was but without the slowdown. I can only conclude that I had a corrupted driver or config or something that was wiped out and refreshed. I'm still seeing one of the CPUs maxing now and again and XGL is currently up to 148 megs of memory, but things are a lot more stable right now.

Hopefully this helps others.

---


---
title: "System administrative application... won't start"
date: 2008-06-08
forum: Desktop Environments
---

### Post by aczar on 2008-06-08
Hi
Strange problem, I updated to heron when it was released and everything was working fine but then something weird started happening. When I run update manager it would check for updates and when I hit install a tab would show on the taskbar saying "starting system administrative application" or something like that and then dissapear after 10-20 seconds, but nothing would happen. At first this would only happen some times, now it doesn't work at all. I can still run the update manager with sudo through the terminal and it works, but this problem seems to effect anything that requires password input... installing downloaded packages, synaptic, etc. 
so far i have ignored the problem because as i said i can get whatever i need done through the terminal, but i'm pretty new to all this so i cant always find a terminal solution to things i want to get done..... any ideas what the problem is?
before im accused of being lazy, i've been searching forums all day and have found similar problems but still not any applicable solutions
thanks people

---

### Post by Happy_Man on 2008-06-08
Have you tried running ```
gksudo synaptic
``` from the terminal and seeing if it gives you any error messages?

---

### Post by aczar on 2008-06-08
thanks for the quick reply.. found the problem though, something to do with my network hosts.. it works now though. 
:D

---


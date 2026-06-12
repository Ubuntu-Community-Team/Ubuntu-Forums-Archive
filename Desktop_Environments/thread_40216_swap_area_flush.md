---
title: "swap area flush?"
date: 2005-06-08
forum: Desktop Environments
---

### Post by IndieRockSteve on 2005-06-08
I only have 256megs of ram on my laptop (I know, I need more, but I need PC100 SODIMM's for which 512megs is like $200...). About every 3-4 days my laptop slows to a crawl within about 10minutes while it thrashes away at the harddrive. all as I can tell its doing this because of swapping to memory. but it takes a while to get to this point, and the only way I've been able to solve it is to reboot (usually forcing a power off cause I can't do anything let alone reboot...).  I was wondering if there was a way to flush the swap memory or some other method of solving this issue short of buying more ram? I have a 500meg swap partition too btw, is this too large?


THANKS!!!!

---

### Post by Joeb on 2005-06-08
Your swap partition isn't too large.  I'm curious as to what is causing the memory leak.  Are you maybe running gdesklets?  They seem to cause memory problems.  If so, stopping daemon and restarting it should fix it, without rebooting.  If you can, before your next reboot, drop to a command line and run "top" to see what is eating up all of your memory.

---

### Post by IndieRockSteve on 2005-06-09
no gdesklets. I have usually around 3-5 ssh sessions to my server open. but even closing that out doesn't fix it. I've tried going through Top and killing/restarting apps. I've tried shutting X down and restarting services. nothing seems to help. theres no single app taking up all that much space, and the numbers don't seem to change much from a fresh boot to when I run into this... In fact Firefox is the only thing that takes up more ram than it should, and if I quit out of it that doesn't seem to help. But I do notice that KMail and Firefox always are running when I have the issue. But I've tried shutting them down and killing them and that too doesn't do anything. If I start either back up I get this whole issue over again...

---


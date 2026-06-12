---
title: "Is there a hibernation FAQ or something? I need help with it..."
date: 2006-09-05
forum: Desktop Environments
---

### Post by juraj on 2006-09-05
Ok, I'm really getting pissed of. I installed Ubuntu Dapper on 3 PCs and hibernate doesn't work on neither of them. I've googled the hell out of these forums and other Ubuntu sites but I haven't found a solution or at least some kind of a FAQ.

Anyway, I'm runnning the latest official k7 kernel (tried with the 386 kernel too), and ATI fglrx drivers, those from the repository (could this be the problem, I read about it somewhere?). Motherboard is Abit NF7-S. It has 1024 megs of RAM and 1.5 gigs of swap(maybe not enough swap?). However, if I open System monitor at any time and check swap usage, it says 0 bytes out of 1.5 gigs (but that still means Swap partition is used and recognized, right? Should I torture my system with something like mPrime to see if it will use swap?).

After attempting hibernation from GNOME, the computer fades out, displays the screensaver and turns off the monitor. A few moments later I get the prompt to unlock my session, and a "time has expired" or something like that message. After I enter the password I return to my desktop, and on the lower right corner of the screen appears the infamous "HAL failed to hibernate, click here to view a useless Gnome power manager FAQ" popup.

Can I at least run hibernate from a terminal or something, to see what's really wrong and how to fix it? I really wanna be able to hibernate my machine.

Thanks in advance. ;)

Cheerios

---

### Post by juraj on 2006-09-06
Bump... :(

---

### Post by pennguin on 2006-09-06
Try [suspend2]("http://suspend2.net"). But you must compile your own kernel to get it working (it isn't very hard, there is a guide to compile new 2.6.17 somewhere here you can use first part of it to callect all needed additional programs and then use the howto from suspend2 how to patch kernel). It made hibernating possible on my PC and notebook without any troubles. Just follow their howto.

> However, if I open System monitor at any time and check swap usage, it says 0 bytes out of 1.5 gigs (but that still means Swap partition is used and recognized, right?
Yes, it will be used when you run out of free mem.

I'll try to write some clear step-by-step howto during this week.

---

### Post by Treviño on 2006-09-06
Nothing to compile... There are precompiled kernels (and other required stuff) here [http://dagobah.ucc.asn.au/dapper-kernels/](http://dagobah.ucc.asn.au/dapper-kernels/) !

Read this for more informations: [http://ubuntuforums.org/showthread.php?t=221088](http://ubuntuforums.org/showthread.php?t=221088)

Bye ;)

---

### Post by pennguin on 2006-09-07
> **Treviño said:**
> Nothing to compile... There are precompiled kernels (and other required stuff) here [http://dagobah.ucc.asn.au/dapper-kernels/](http://dagobah.ucc.asn.au/dapper-kernels/) !

Read this for more informations: [http://ubuntuforums.org/showthread.php?t=221088](http://ubuntuforums.org/showthread.php?t=221088)

Didn't notice it :)

---


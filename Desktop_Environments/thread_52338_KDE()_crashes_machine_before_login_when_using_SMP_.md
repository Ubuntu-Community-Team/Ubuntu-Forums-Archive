---
title: "KDE(?) crashes machine before login when using SMP kernel"
date: 2005-07-27
forum: Desktop Environments
---

### Post by TheSerpent on 2005-07-27
Apologies for seeming to start half-way through a problem, but I have had no luck in the Kubuntu forum. I was wondering if anyone here had any ideas.

The story so far:

---
Post 1
---
I have a home-brew machine with two AMD Athlon MP 2000 CPUs in it. They work happily together in a certain O/S that will not be mentioned here!
 
 I can happily run Hoary on kernel image 2.6.10-5-k7 with KDE 3.4.0
 
 However if I boot using kernel image 2.6.10-5-k7-smp to get my second cpu into action, KDE freezes the machine unrecoverably just before the login prompt. X starts OK and I see my background appear but the machine locks just before the login prompt screen appears.
 If I switch to a different tty before KDE crashes, the machine functions perfectly. I can log on and use the command line forever. As soon as I switch to tty7, on go the brakes.
 
 I have tried looking at KDE logs but nothing appears amiss, it just stops running - it is highly likely that I am looking in the wrong place though!
 
 Rather than post pointless info I'd like to know what logs I should retrieve to help find the bug. Or if anyone has solved this before, well, that would be great too!
 
 Thanks in advance

---
Reply 1
---
Try with "sudo /etc/init.d/kdm stop" from a tty (pther than tty7 off-course) and then type "startx" and go to tty7. Tell us if it works.

---
Post 2
---
Thanks for the suggestion Ptero
 
 I switched to tty1 as soon as I was able and entered your suggested command. KDM stopped OK.
 I then ran startx, which caused the same problem as I described before, only this time without the background image - just a white background with pointer, then total freeze up. I can't return to another tty only cycle the power, just like with KDM.
 
 Further suggestions much appreciated!
---

Nothing further has been forthcoming. Does anyone have any advice or ideas?

---

### Post by TheSerpent on 2005-07-28
Perhaps if someone could tell me which is/are the appropriate logs(s) to examine?

---


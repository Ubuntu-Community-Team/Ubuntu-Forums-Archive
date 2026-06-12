---
title: "No video output, driving me nuts"
date: 2009-02-13
forum: General Help
---

### Post by skatermike21988 on 2009-02-13
Hello all. I am new to linux and I have little experience with it, but this is my first installation. After I installed ubuntu It said installation was successful and to reboot, after reboot I see:
"Starting Up" in the upper left hand corner, then I see the Ubuntu splash screen w/ the progress bar, after that loads 100% my screen just goes black. And that's it. I have tried rebooting over and over again, reinstalling 3 or 4 times, I've tried versions 8.04 lts and 8.10. Any help is appreciated. 

My specs:
ECS GF6100PM-M2 Motherboard
AMD Athlon 64 x2 4400+
1gb Corsair xms2 ram
Onboard Geforce 6100 video
350W Raidmax PSU

---

### Post by LowSky on 2009-02-13
reboot into recovery mode. to do so press Escape whenyou see starting up, this willl get yu into the GRUB menu, pick recovery, and try the Xfix Option

---

### Post by skatermike21988 on 2009-02-14
Well, I tried that, still no luck.

---

### Post by razy60 on 2009-02-14
I've got exactly the same problem, however it may be more than just a xorg problem, i have tried a number of distros and windows os's all with a similar issue, except in some cases it will load eventualy.
On the 8.10 set up disc if i use safe graphical mode it works apart from its screen resolution is barely useable, then if i reboot into normal mode it sets up ok until i try to reboot, then it gets stuck back to either the brown or black screen with the cursor on the screen but its doing nothing.
I keep thinking that it may be a graphical memory problem.

Raz

---

### Post by skatermike21988 on 2009-02-14
Thanks for the suggestions, but I finally got it to work, it appears it was something to do with my onboard video, I popped in a PNY Geforce 7600 gs 256mb pci-e card and away it went. All is good now. :)

---

### Post by razy60 on 2009-02-14
well not sure how long my fix will last but, as my mobo only has pci slots, no pcie, I found an old pci graphics card from a win98 pc put that in and it seems to have fixed the problem, not that i am using it its just plugged onto the mobo and the VGA cable is plugged into the on board graphics slot:confused:
Any bets on how long before it goes pear shaped again.

Raz

---


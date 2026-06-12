---
title: "SUCCESS!! - 7600GS Working!"
date: 2008-01-07
forum: Desktop Effects &amp; Customization
---

### Post by TechRavingMad on 2008-01-07
After tearing my hair out for over a week, I have FINALLY succeeded in getting my 7600GS to use the nVidia drivers and have full blown Compiz Fusion working!  Yeah!

My setup:
AMD Athlon 64 3400+
eVGA 7600GS 256MB 8xAGP
Asus K8V Deluxe Special Edition
1GB Ram
Ubuntu 7.10 fully patched

I had tried everything to get it to work, using the restricted drivers, using the nvidia .run file, the envy script, modifying by hand, everything, and no matter what I tried as soon as I enabled the nvidia driver I would be stuck with the Low Resolution warning after x failed to start.

The odd part was that the Restricted Driver Manager would show that the nvidia driver was in use, but the Screen Resolution tool would report vesa.

I ran the nvidia-bug-report.sh script and began to look through there to identify issues.  After working through various items I noticed a line that said "polling IRQ 16, no answer" (paraphrased).  It also said to try booting with "irqpoll".  Added irqpoll, rebooted, no joy.  I then remembered seeing earlier that my AGP card was assigned IRQ 16 and thought that was odd.  After a little digging I discovered that my onboard Firewire was also assigned IRQ 16.  EUREKA!  as they say.

Disabled the onbord Firewire and boom!  Booted up with the Nvidia driver in use, even saw the splash Nvidia screen.

Hopefully this will help others out there having issues.  Check your IRQ's, it could be you have a conflict.

Ubuntu ROCKS!
TRM

---


---
title: "Gutsy, ATI 8.42, Compiz, severe corruption and artifacts"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by Doctor Zip on 2007-10-25
I am running a fresh install of Gutsy (Kubuntu), using the new ATI 8.42 drivers, AIGLX, and compiz fusion.

I installed all these using Forlong's writeups:
For the new drivers: [http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#comments](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#comments)

And for compiz in KDE (yes, I realize this tutorial is for Feisty) [http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users#](http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users#)

When I run compiz --replace, it actually works.  That is to say, the desktop effects work.  I get wobbly bobbly windows, and slidey desktops.  However, there is severe corruption.  Green and pink snow cover the terminal window that I run the command from.  Window title bars are blank (no text, sometimes artifacts, usually just grey).  The kicker pane becomes mostly white, with only small bits of buttons showing.  The K menu, when clicked, does not display until I mouse over each row.

I don't know where to go from here.  I am at work now, but I can post my xorg.conf later today.

Thanks

---

### Post by sdowney717 on 2007-10-27
this happened to me when I was playing around with the buggy Catalyst Control Center.
To fix, simply open synaptic and delete including config files the amdcc control center.
you dont need it at all.

I later on reinstalled and that problem did not recur.

---

### Post by Random20230808 on 2007-11-11
Have you solved the problem?

---


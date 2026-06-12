---
title: "Getting XfWM4 to autostart in KDE SC 4.4"
date: 2010-02-16
forum: Desktop Environments
---

### Post by Farmer of Bricks on 2010-02-16
I'm using KDE SC 4.4 from kubuntu-backports on 64-bit Kubuntu 9.10. I have an AMD Athlon x64, 1.25Gb of RAM, and an nVidia MX 4000.
<backstory>I upgraded to 4.4 yesterday, and I've found it unusably slow when Plasma is performing sliding-actions: the sliding part moves, and nothing else happens. I decided to try XFCE4, but didn't really like it, for a host of reasons. I uninstalled XFCE, but XFWM stayed (my apt-fu is lacking). I saw it, and figured, "Why not?" I ran **xfwm --replace**, played around with the theming, and liked it. XFWM ran incredibly faster than KWin did.</backstory>
Unfortunately, XFWM does not return automatically when I log back in. 
How do I get it to run automatically when I log in to KDE? It doesn't seem to be in the alternate-window-manager choices section of System Settings, as seen in the attached image. 

Thank you for your help.

---

### Post by Farmer of Bricks on 2010-02-16
Actually, it does start when I log in, but it seems to be going off of the previous session, and I'd like something a little more concrete than the last-session method. 
Also, it flickers as it switches from the kdm used in the login screen to xfwm on the desktop. Is there a way to fix/prevent that?

---

### Post by Farmer of Bricks on 2010-02-22
blk@blackbox:~$ fortune
Shoot me again.
Just proving that the quickest way to solve the problem is to post a whine to the newsgroups: within moments the solution presents itself to me, and meanwhile my *** is hanging out on the Net...
*sigh*...
                -- Dave Phillips,

Problem solved.

---

### Post by carbonfreeze on 2011-02-11
So did you use an autostart entry, or some other method?

---

### Post by CraigPaleo on 2011-02-11
Glad to see you solved it. :D


__________________
**[Pardus at Distrowatch]("http://distrowatch.com/pardus")**

---


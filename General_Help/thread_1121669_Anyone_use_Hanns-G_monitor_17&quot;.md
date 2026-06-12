---
title: "Anyone use Hanns-G monitor 17&quot; ?"
date: 2009-04-10
forum: General Help
---

### Post by raffytaffy on 2009-04-10
I have a Hanns-g monitor ( the 17 inch wide one ). I have been having a weird problem lately. When I powerup my computer and turn on both monitors ( both hanns-g 17w ), one of them takes about 10 minutes to turn on. It has this strange behavior, where the LED turns on green for a few seconds and then turns off. It does this for about 10 minutes, after which the monitor turns on and works for the remainder of the day. Has anyone had this problem before?

---

### Post by Rocket2DMn on 2009-04-10
Moved to General Help.

It sounds like the X server may be having trouble starting up, and if it keeps restarting itself, it could produce behavior like this.  Possibly a video card or monitor detection problem.  Are you stuck in low graphics mode?  Check yout logs, like ~/.xsession-errors (or something like that) and /var/log/Xorg.0.log

---


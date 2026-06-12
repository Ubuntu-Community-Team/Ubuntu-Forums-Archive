---
title: "Monitor Resolution after 9.10 upgrade"
date: 2009-11-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Eyore15 on 2009-11-04
I run my Ubuntu as a WUBI installation.  I've been running along on 9.04 (and 8.10 before that) without any problems.  When I upgraded to WUBI 9.10 a number of problems developed. My system is an Optiflex GX 270 with a Dell LCD monitor.

1.  Monitor display is limited to 800X600.
2.  No sound (although this seems to be almost universal)
3.  When exiting, I get the error message "Buffer I/O error on device loop0 logical block" followed by a 7-digit number.  After six of these error messages, the system locks and shot-down can only be accomplished by turning off the power.

Of the three, I'd most satisfied if I can resolve #1 and get back to a decent resolution.

mcm

---

### Post by cybrsaylr on 2009-11-04
Have you tried experimenting with other screen resolutions by going to:
Preferences > Display?

This should give you several other screen resolution choices.

---

### Post by lowpan on 2009-11-04
I had bad resolution after installing v9.10 too.  My problem and solution is solved by this [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

After I get the proper video driver installed, I got much higher resolutions.

---

### Post by Eyore15 on 2009-11-05
> **cybrsaylr said:**
> Have you tried experimenting with other screen resolutions by going to:
Preferences > Display?

This should give you several other screen resolution choices.

800X600 is the highest resolution available in preferences >> display.

---

### Post by Eyore15 on 2009-11-05
> **lowpan said:**
> I had bad resolution after installing v9.10 too.  My problem and solution is solved by this [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

After I get the proper video driver installed, I got much higher resolutions.

trouble is that stops at Jaunty; I need Kosmic

---


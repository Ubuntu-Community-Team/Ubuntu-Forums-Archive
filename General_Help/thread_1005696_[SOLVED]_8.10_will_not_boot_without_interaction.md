---
title: "[SOLVED] 8.10 will not boot without interaction"
date: 2008-12-08
forum: General Help
---

### Post by lowtolerance on 2008-12-08
I'm having a weird issue with intrepid on an HP laptop dv9600 series. During the boot process, I've got to hit the enter key several times to advance anything. I'm not given any prompts or errors, and yet the system seems to pause until I get to the init.d stuff. Other than this, everything seems to be working fine. The problem happens from the Live CD as well as from the hard disk, and the problem is new to 8.10

It's more of an annoyance than anything, but any help would be much appreciated.

EDIT- Apparently the problem is with the hpet clocksource in kernel 2.6.27. Passing clocksource=jiffies to the kernel solves the problem(and probably introduces others, but hey...)

---


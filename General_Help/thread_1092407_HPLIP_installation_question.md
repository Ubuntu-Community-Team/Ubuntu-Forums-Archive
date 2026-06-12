---
title: "HPLIP installation question"
date: 2009-03-10
forum: General Help
---

### Post by hawkhock on 2009-03-10
Am trying to install an HP DeskJet 697C (not sure how old).  OpenSourePrinting says it is supported and should work well.

I tried installing through System>Administration and that did not work. From research, it appears the best approach is to install using HPLIP through terminal.

?Can I install HPLIP _without_ the printer being hooked up?

?Is the newest version of HPLIP compatible with all HP printers 
OR is a specific version linked to a specific set of printers, i.e. by age or model?

I ran an HP check log and it said that CUPS backend was missing and 18 dependencies were not met.  However, the log also said HPLIP was already installed on my computer and that the parallel port is recognized.

According to the install directions at HPLIP, using HPLIP should take care of everything.  Yes or No?

---

### Post by rbmorse on 2009-03-10
Should work, but HPLIP will install the printer into CUPS, so you have to fix that, first. 

You can install HPLIP itself without the printer. You should install the package hplip-gui from repository if you want the GUI front end.  

HPLIP will want the printer connected and powered up when you run the printer install wizard.

---

### Post by hawkhock on 2009-03-10
> **rbmorse said:**
> Should work, but HPLIP will install the printer into CUPS, so you have to fix that, first. 

You can install HPLIP itself without the printer. You should install the package hplip-gui from repository if you want the GUI front end.  

HPLIP will want the printer connected and powered up when you run the printer install wizard.


Thanks for your reply -- was getting nowhere!

[COLOR="Red"]Should work, but HPLIP will install the printer into CUPS, so you have to fix that, first. [/COLOR]

What exactly do you mean by this: Will CUPS require something after I install HPLIP OR first install HPLIP, then hplip-gui?- us newbies appreciate very specific directions!  Should I add the HP Tool Box as well?

---

### Post by rbmorse on 2009-03-10
My reference to CUPS was regarding this:
> I ran an HP check log and it said that CUPS backend was missing and 18 dependencies were not met. However, the log also said HPLIP was already installed on my computer and that the parallel port is recognized.

HPLIP requires a working CUPS server, but CUPS is beyond my keen.  I suggest you start another thread with CUPS in the title so you get the attention of the right experts.

---

### Post by hawkhock on 2009-03-11
Much thanks for your help.  If all does not go well, I'll address the CUPS issue in another thread.

G in UT

---


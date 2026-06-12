---
title: "Feisty Compiz w/ ATi Radeon (FGLRX)"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by Supercross on 2007-04-26
My question is how do I get the Compiz thats preinstalled into Feisty to work after I've installed the fglrx drivers for my Radeon 9500.  According to the install guide for fglrx it tells you to paste:

```
Section "Extensions"
        Option  "Composite" "Disable" 
EndSection
```

into /etc/X11/xorg.conf.  However, now when I goto Desktop effects from the menu, it just comes up with a dialog saying, "The Composite extension is not available."  Do I have to go back into xorg.conf and enable composite, and if I do, will there be any adverse effects to my system.  Now, with is disabled, everything works fine, but compiz won't run.

---

### Post by Faire on 2007-04-26
I have an Ati mobile radeon (?) X1300, and I had the same problem. You don't have to enable the composite extension... just try to run compiz manually and don't make use of "Desktop Effects" (What it does is running Compiz).

---


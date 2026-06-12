---
title: "Linux Distro- Best Battery"
date: 2009-03-11
forum: General Help
---

### Post by Turnips on 2009-03-11
Hey guys, Im just wondering which linux distro I can use when going to school.  Im looking for something with the best battery life possible without being totally useless, ie) nothing that runs from command prompt only or anything.  So with the basic neccessities which is best?

---

### Post by LegendofTom on 2009-03-11
Distro doesn't really matter.  You want a lighter GUI.  Try XFCE, Fluxbox, IceWM.

---

### Post by mb_webguy on 2009-03-11
There really isn't any significant difference between distros in terms of power consumption.  Using fewer system resources will technically use less power, it probably won't be noticeable.

The best way to prolong your battery life is to turn off your wireless card when you're not using it and dim your monitor when you don't need full brightness.  Wireless and bluetooth use a lot of power even when they aren't being used, and while LCD monitors don't consume a huge amount of power, every little bit helps.

---

### Post by Turnips on 2009-03-12
Ah, so just linux sucks at battery life in general no matter what you do?  I figured loading things into ram and stuff would help it, maybe decreasing things that interupt it.

---

### Post by mb_webguy on 2009-03-12
It's not just Linux.  Windows, Mac OS X, Linux...  it basically doesn't matter.  Your hardware uses a certain amount of power, and there are only so many ways of reducing that usage.  There really shouldn't be any difference in power consumption between OSes assuming similar power management configurations.  Linux generally provides comparable power management as Windows or Mac OS X, though there it may vary depending on hardware and BIOS.  

That said, your computer *could* be using more power using Linux than other OSes, but it's not the fault of Linux.  The power management settings in the BIOS of some computers is entirely too aggressive by default.  Some operating systems like Windows *may* override these settings, which would give a false impression of better power consumption.  But Linux doesn't override BIOS settings, since these settings *should be* OS-independent.  The Linux and Ubuntu developers assume that computer manufacturers should know best about your computer's hardware, and so don't alter the BIOS.  If your power consumption seems unusually high with Linux compared to other OSes, check your BIOS settings.

---


---
title: "conky- cpu speed display"
date: 2009-06-10
forum: Desktop Environments
---

### Post by blur xc on 2009-06-10
So, I've got an Intel Core 2 Duo 3.0ghz processor- says so in my bios and system information screens (and on the box it came in).

Conky says its only a 2.0ghz processor.  What gives?  I paid close attention today when I booted up, and it said 3.0ghz for the first few seconds, and once it was finished starting up, it dropped to 2.0ghz.  I recall seeing something about that when I first set up the system, may have been while installing ubuntu (don't perfectly recall).  Should I not care?  Or is there a way to make it run at 3.0ghz?  Or is it a Conky issue?

thanks
BM

---

### Post by Hund on 2009-06-10
It might be the "CPU Frequency Scaling" function?

This command should give you the supported frequensys:

> cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

---

### Post by blur xc on 2009-06-10
That's probably it- found this on a google search- [http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

Thanks,
BM

---


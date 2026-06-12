---
title: "Cpu scaleing"
date: 2007-07-03
forum: Dell  Ubuntu Support
---

### Post by weaver4 on 2007-07-03
I have a Dell Inspiron 6000 notebook.  It is using a Pentium M processor at 1.6Ghz.

When I use the CPU Frequency Monitor in the Panel it shows 50% or 100%.  Shouldn't it have more steps in it rather than just two?  How do I change that?

---

### Post by neptho on 2007-07-04
Some of them don't.  Try this in the terminal:

```
%cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

This will tell you the abilities of your system.  For instance, here's mine (1.6, 1.33, 1.06, and 800Mhz):

```
%cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1600000 1333000 1067000 800000
%
```

---


---
title: "CPUFreq frontend in LXPanel not working"
date: 2010-07-02
forum: Desktop Environments
---

### Post by r3make on 2010-07-02
Hi,

i tried getting the CPUFreq frontend plugin of LXPanel to work (It shows only: "CPUFreq not supported"). The daemon cpufreqd is running and i am able to change the profile by cpufreq-set. Also cpufreq-info reports correct informations.

To get some debug messages i killed lxpanel and started it in a terminal. On clicking the cpufreq plugin icon it prints this:
```
cpufreq: cannot open  /sys/devices/system/cpu/cpufreq/cpufreq/scaling_available_governors
```

And this is correct. In /sys/devices/system/cpu/cpufreq is no folder cpufreq, but it is in /sys/devices/system/cpu/cpu0 and also the requested file is available at:
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors


What's going wrong here and of course how can i fix this?

---

### Post by dvarrazzo on 2010-07-29
I've checked out the code for lxpanel and it seems the issue was fixed on 2010-07-15 and released in 0.5.6.

---


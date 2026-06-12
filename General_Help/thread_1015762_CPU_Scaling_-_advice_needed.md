---
title: "CPU Scaling - advice needed"
date: 2008-12-19
forum: General Help
---

### Post by Riven213 on 2008-12-19
Hello,

I have an Intel Core 2 Duo 2x2,5 Ghz processor. I've set frequency ratio in BIOS to 2,5 Ghz. However, the default value in the CPU Frequency Scaling Monitor is 1,2 Ghz. Why is that? I know I can set it to be 2,50 Ghz and I did so, I'm just curious why it has 1,2 set by default. I hope there's nothing wrong about using the maximum scaling ratio available? :P

Regards

---

### Post by madverb on 2008-12-19
Isn't this something to do with power saving... if you aren't doing much with your PC it reduces the CPU power.

---

### Post by sdennie on 2008-12-19
You might want to try the tool cpufreq-info.  It gives human readable information about what the cpu scaling is currently doing.  My guess is that you are using the ondemand governor and when the cpu is idle, it's scaling down to 1.2Ghz.  This is desirable behavior and should have no performance impact on the system.

---


---
title: "cpufreq applet not correct?"
date: 2006-07-02
forum: Desktop Environments
---

### Post by kinematic on 2006-07-02
you all know that cpu applet you can place in the panel right?
well....most of the time it says my amd sempron 3000+ is running at 1ghz.
but here's the weird part....the output from "cat /proc/cpuinfo" says it running at 1.8ghz and gdesklets also says it's running at 1.8ghz.
so i checked the output of lsmod and the attachment is the stuff relating to my processor.
so i guess i'm wondering if the scaling is working?
anybody got any comments on this?

---

### Post by gborzi on 2006-07-02
I have noticed the same problem in my laptop, which has a Pentium 4M. After some search, I realized that the problem is not that there isn't frequency scaling, but that it's not reported in /proc/cpuinfo. If you look at /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
you'll see the "right" frequency. Also, you can see that the bogomips at the last line of /proc/cpuinfo raises when your system is loaded and goes down when it's idle.

---

### Post by kinematic on 2006-07-02
you're right....that displays the current frequency.
strange.....

---


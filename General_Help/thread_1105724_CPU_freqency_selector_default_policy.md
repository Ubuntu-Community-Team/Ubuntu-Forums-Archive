---
title: "CPU freqency selector default policy"
date: 2009-03-25
forum: General Help
---

### Post by dread22 on 2009-03-25
Currently when I start my machine it the cpufreqz-selector start on the OnDemand governor. How can I change that to start in the Performance governor and if needed I can change it manually later.

Thx

---

### Post by dcstar on 2009-03-25
> **dread22 said:**
> Currently when I start my machine it the cpufreqz-selector start on the OnDemand governor. How can I change that to start in the Performance governor and if needed I can change it manually later.


```
sudo dpkg-reconfigure gnome-applets
```
and tick the box log out and in again.

You should be able to (install and) click the CPU Frequency Scaling Applet and set whatever your system supports.

---

### Post by dread22 on 2009-03-25
Tried that but that only allows a normal user to change the frequency. I don't want to actually have to change it at startup to Performance each time. The only time I want to use the cpu scaling is when I'm running on battery which I can do manually if needed.

---

### Post by robobot on 2009-03-25
Look into using the "cpufreqd" governor for CPU frequency scaling. It lets you create rules regarding which frequency scaling mode (if any) to use in different situations. You can even create application-specific profiles and change display brightness. Just "apt-get cpufreqd". It will replace Ubuntu's default frequency scaling governor.

Here's some links on it:
[http://www.thinkwiki.org/wiki/How_to_configure_cpufreqd]("http://www.thinkwiki.org/wiki/How_to_configure_cpufreqd")
[http://www.go2linux.org/how-to-configure-cpufreqd]("http://www.go2linux.org/how-to-configure-cpufreqd")

Personally, I'd say just to leave the frequency scaling on even when running on AC power. It cuts down on heat and power usage, and there is no noticeable decline in performance, since the CPU frequency scales up when necessary. Running my desktop with CPU frequency scaling enabled shaved off about $10 US from my monthly electric bill. However, I have a 95-Watt AMD Phenom--not exactly a laptop processor.

---


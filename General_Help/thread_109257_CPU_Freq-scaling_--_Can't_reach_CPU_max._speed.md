---
title: "CPU Freq-scaling -- Can't reach CPU max. speed"
date: 2005-12-28
forum: General Help
---

### Post by nicors on 2005-12-28
Hi
I'm setting up Breezy on my Compaq evo n1020v (Mobile Pentium 4-m 1.8Ghz). After correct a problem modifiying cpufreq-detect.sh to load p4-clockmod if I boot the cpu freq. scaling works. The problem is that very often the maxium cpu speed I can reach is 1.2Ghz. When this happens a *cat /proc/cpuinfo* reports correct values but if I navigate to */sys/devices/system/cpu/cpu0/cpufreq* the cpu speeds are not reported correctly (cpu-max, cpu-max-sacaling, scaling-avaiable-freqs...). When I can reach 1.8Ghz speed all this files content the correct values. 

It's an annoying problem because the lowest speed is set on 150Mhz. and after idle periods freezes about a second until the cpu speed reaches 225Mhz, the lowest speed on "correct" speed setting. 

Someone know what is happening?

Thanks a lot.

---

### Post by nicors on 2005-12-28
Ok, problem info update
 
If I restart the computer from a 1.8Ghz "state" then the max speed is 1.2Ghz. but if I restart again the max speed is 1.8Ghz! The max speed change every time I reboot!!
Please help!!

---


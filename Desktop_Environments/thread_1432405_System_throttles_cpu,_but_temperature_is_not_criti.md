---
title: "System throttles cpu, but temperature is not critical..."
date: 2010-03-17
forum: Desktop Environments
---

### Post by osfight.de on 2010-03-17
I have an annoying problem: I use the sensor applet to monitor my cpu's temperature and the CPU Scaling Monitor to set governor / frequency. Everytime I watch flash videos or does other cpu demanding task I can see how the CPU is throttled to 1.6GHz (2.2MHz is Max, 800Mhz min) and this happens when the temperature reaches approx. 85C. I cannot force it to use max frequency again. 

I cannot find any setting how to change this, the AMD site states the cpu runs at  max 95C so if the system throttles it should happen at 90C or later. I know it was not always like that, but not sure since when I have this problem (a kernel update maybe...)

Here is some output:

cat /proc/acpi/thermal_zone/THRM/trip_points 
critical (S5):           95 C
passive:                 100 C: tc1=2 tc2=3 tsp=100 devices=CPU0 CPU1 

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
performance

cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq 
2200000

Thanks for any input...

osfight

---

### Post by osfight.de on 2010-03-18
I did not find any information on that, but cleaning the fans helped to keep the temp. low, so the system does not scale down too quickly anymore...

---


---
title: "Cant change scaling_min_freq file"
date: 2007-03-20
forum: Desktop Environments
---

### Post by muhu on 2007-03-20
Hello

I want to change this file /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq to set down the cpu frequency because my fan is always running I hope it gets out when the cpu is more down -  but I cant. I get an error bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq: Permission denied 
I tried with  sudo echo 600000 >/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
I dont have a root account do I need one or how can I change this file?

thx

---

### Post by pedro-kun on 2007-05-21
Well, you can apt-get install fakeroot, and then:
```
sudo fakeroot
echo 600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
```

OR, you can give the root account a password and use it:
```
sudo passwd su
su
echo 600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
```

Make sure scaling_freq_min doesn't fall below cpuinfo_freq_min ;)

---

### Post by victorgreen on 2008-05-04
I have scaling enabled and everything works, but for some reason the OS refuses to even try to use my cpu speed. Ive got a T7500 in my X61 and frequency scaling at 800, 1200, 1600, and 2200mhz worked in Fiesty 32 and Gutsy 32. Im now on a clean install of Hardy 64.

Is this only a 64bit issue???


```
~# cpufreq-info
```

> 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
driver: acpi-cpufreq
CPUs which need to switch frequency at the same time: 0 1
hardware limits: 800 MHz - 2.20 GHz
available frequency steps: 2.20 GHz, 2.20 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
available cpufreq governors: powersave, userspace, ondemand, conservative, performance
current policy: frequency should be within 800 MHz and 1.20 GHz.
The governor "userspace" may decide which speed to use
within this range.
current CPU frequency is 1.20 GHz (asserted by call to hardware).
analyzing CPU 1:
driver: acpi-cpufreq
CPUs which need to switch frequency at the same time: 0 1
hardware limits: 800 MHz - 2.20 GHz
available frequency steps: 2.20 GHz, 2.20 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
available cpufreq governors: powersave, userspace, ondemand, conservative, performance
current policy: frequency should be within 800 MHz and 1.20 GHz.
The governor "userspace" may decide which speed to use
within this range.
current CPU frequency is 1.20 GHz (asserted by call to hardware). 

---

### Post by w4ngsta07 on 2008-05-11
> **pedro-kun said:**
> Well, you can apt-get install fakeroot, and then:
```
sudo fakeroot
echo 600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
```

OR, you can give the root account a password and use it:
```
sudo passwd su
su
echo 600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
```

Make sure scaling_freq_min doesn't fall below cpuinfo_freq_min ;)

How do you make this permanent? It resets after every reboot, so I have to put this in the terminal every time.

---

### Post by w4ngsta07 on 2008-05-11
Ok a little update here. I found out that I had to install sysfsutils to make changes to this when I boot up. Now comes a totally different and wierd problem.

When I run cpuburn, the 'Userspace' will only let me change frequences of 3 settings instead of 5 settings. My 5 settings of frequencies are "2001MHZ, 2000MHZ, 1600MHZ, 1200MHZ, and 800MHZ". running cpuburn only lets me run the top 3 choices. 

Is this just the intel speedstep kicking in?

---


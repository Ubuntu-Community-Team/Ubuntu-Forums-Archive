---
title: "cpufreq doesn't work"
date: 2011-11-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by enboig on 2011-11-14
My laptop (DELL n7110) works all time at full speed, so battery life is really short.

I had to add "pci=noacpi" to grub in order to make it boot; and cpufreq-info returns

analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.30 GHz
  available frequency steps: 2.30 GHz, 2.30 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.30 GHz and 2.30 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.30 GHz.
  cpufreq stats: 2.30 GHz:99,96%, 2.30 GHz:0,00%, 1.80 GHz:0,00%, 1.60 GHz:0,00%, 1.40 GHz:0,01%, 1.20 GHz:0,01%, 1000 MHz:0,01%, 800 MHz:0,01%  (39)


So my speed is always between 2.30 GHz and 2.30 GHz. Any hint on how to correct cpufreq?

---

### Post by boast on 2011-11-14
[https://wiki.archlinux.org/index.php/CPU_Frequency_Scaling#CPU_frequency_driver](https://wiki.archlinux.org/index.php/CPU_Frequency_Scaling#CPU_frequency_driver)

on the wiki under "Scaling governors" specifies how to set the range. give that a try

---

### Post by matt_symes on 2011-11-14
[LEFT]Hi

Install Jupiter and change the cpu scaling governor.

Or from the command line change the governor. Not sure how acpi=off will affect this.
Also, you need to do this for all your cores.

```
echo powersave | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

These are the available governors.

```

matthew@matthew-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
conservative ondemand userspace powersave performance 
matthew@matthew-laptop:~$
```

Kind regards
[/LEFT]

---

### Post by enboig on 2011-11-15
After playing a little with /etc/cpufreqd.conf now my cpu speed is stuck at 800 Mhz; exactly like before, but now at lowest speed.

I have read arch documentation and I didn't understand how cpufreqd.conf works.

My cpu frequencies are:
2301000 2300000 1800000 1600000 1400000 1200000 1000000 800000

And my governors are:
conservative ondemand userspace powersave performance

thanks.

---


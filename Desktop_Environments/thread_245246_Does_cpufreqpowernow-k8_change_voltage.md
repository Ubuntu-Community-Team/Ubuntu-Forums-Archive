---
title: "Does cpufreq/powernow-k8 change voltage?"
date: 2006-08-27
forum: Desktop Environments
---

### Post by omion on 2006-08-27
Hi all,

I've been tinkering around with Ubuntu on my secondary desktop and want it to be as quiet as possible. I've gotten everything up and running, but I'd like some confirmation that my voltage is getting throttled down with my CPU frequency.

I have an Athlon 64 3500+ on an MSI K8NGM2 motherboard, and dmesg says:
```

powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6 (1400 mV)
powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8 (1350 mV)
powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
```

There are a lot of things which *imply* the voltage is changing, but I see no way of actually confirming that it is. /proc/cpuinfo lists the current CPU frequency and lists "vid" under "power management", but it does not list the current voltage. lm-sensors does not show any voltages either.

---

### Post by lagagnon on 2006-08-27
Then your lm-sensors is not configured correctly becuse it should show you all the voltages. Read the lm-sensors docs to find out how to fix it.

---


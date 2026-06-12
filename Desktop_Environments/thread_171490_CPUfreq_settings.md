---
title: "CPUfreq settings"
date: 2006-05-06
forum: Desktop Environments
---

### Post by adam.tropics on 2006-05-06
So the panel applet now works, great, but how do I set it to only change if I tell it, or if running on battery??

---

### Post by hw-tph on 2006-05-06
powernowd is by default what controls the switching between CPU frequencies. If it doesn't exist, create /etc/default/powernowd and in it define whatever options to powernowd that you want to pass. This file should just contain a line like this:[code]OPTIONS="-foo -bar"[/b]
...where -foo and -bar are the options you want to set. To find out about the options, read powernowd(1). (that is, type **man 1 powernowd**)

For full control you can set the scaling governor in /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor.

Håkan

---


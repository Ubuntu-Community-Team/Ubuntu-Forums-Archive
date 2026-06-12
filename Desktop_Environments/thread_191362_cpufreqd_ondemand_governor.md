---
title: "cpufreqd ondemand governor"
date: 2006-06-07
forum: Desktop Environments
---

### Post by shomati_sen on 2006-06-07
Hi,

I updated my Breezy to Dapper and most things worked fine. The main grouse is that cpufreqd no longer works well. After doing some checking, I found the following issues:
[LIST]
speedstep_centrino module needs to be loaded for CPU freq scaling to work, but it didn't get loaded automatically. I had to manually add it to /etc/modules. Of course, figuring this out took time.
[/LIST]
[LIST]
The governor modules need to be loaded.
[/LIST]
[LIST]
When I use ondemand governor, the freq never drops when I'm on battery. Poking around, it appears to me that /sys/devices/system/cpu/cpu0/cpufreq/ondemand directory doesn't contain a down_threshold file, only an up_threshold file. Could this be the cause ?
[/LIST]

Thanks for such a fabulous distro,

Shomati

---

### Post by the_maassk on 2006-06-07
I think the setting is in the /etc/acpi/power.sh script. There should be an entry which mentions that 'battery event should/should not control the CPU frequency'. By default it is set to false (0). Try setting it to true (1).

---

### Post by shomati_sen on 2006-06-07
Thanks for responding. I checked the different scripts sourced by power.sh and power.sh itself. I didn't find anything that mentions whether the CPU freq is controlled by battery event or not. 

Shomati

---


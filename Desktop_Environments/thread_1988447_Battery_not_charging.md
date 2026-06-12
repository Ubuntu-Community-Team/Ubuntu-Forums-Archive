---
title: "Battery not charging"
date: 2012-05-27
forum: Desktop Environments
---

### Post by vapor0 on 2012-05-27
For whatever reason, Xubuntu doesn't charge my battery.

```
sudo cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          critical
charging state:          charged
present rate:            0 mA
remaining capacity:      10 mAh
present voltage:         15000 mV
```


```
sudo cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         247 mAh
last full capacity:      247 mAh
battery technology:      rechargeable
design voltage:          15000 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
cycle count:		  0
capacity granularity 1:  0 mAh
capacity granularity 2:  247 mAh
model number:            PA3399U-2BAS/BRS
serial number:           08FC
battery type:            Li-ion
OEM info: 
```               

It could theoretically be that my battery is dead, but it worked fine under "normal" Ubuntu.

Any thoughts?

---

### Post by searchfgold6789 on 2012-05-27
Try it again with an Ubuntu live CD/USB, just to make sure.

---

### Post by vapor0 on 2012-05-27
Alright, so I'm typing this from the Ubuntu live cd. When I click on the battery icon, it says "Battery (not present)". 

But when I click on Power Settings, it says the battery is charging, as opposed to Xubuntu which says it's charged.

So... dead?

---

### Post by searchfgold6789 on 2012-05-28
Dead.

---

### Post by jimmyco2008 on 2012-05-28
I'm having the same problem, on 12.04 x64, the battery icon doesn't fill in 48% of the battery like it should, yet it says battery is at 48% and charging.

It's not charging. 

To be clear, you tried shutting down your laptop, removing the battery, rebooting Ubuntu, then putting the battery back in?

I'll try that now. But this hasn't happened before, I've been going back and forth between Windows 7, 8, and Ubuntu 12.04 for the past month or two, I will say that this happened after leaving a Windows 7 installation where a program was keeping the battery from charging after it got to 50%, since I never really leave AC power (helps conserve battery).

Just know you're not alone!

---

### Post by jimmyco2008 on 2012-05-28
Yeah that fixed it lol. Give it a try.

---


---
title: "Clocksource TSC unstable"
date: 2009-04-09
forum: General Help
---

### Post by change_mode on 2009-04-09
My applications crash, because the hardware timer is out of sync. It starts lagging, sound stops, then it freezes. 
Log says 'Clocksource TSC unstable'. My default timer is acpi_pm. Ubuntu 8.04, 2.6.24-23.

What I tried:

- using another timer
-- clocksource=tsc: system runs in slow motion, unusable
-- clocksource=hpet: hpet is not available, it defaults back to acpi_pm
```
cat /sys/devices/system/clocksource/clocksource0/available_clocksource

acpi_pm jiffies tsc
```

- notsc: system doesn't start (segfault)


This needs to be solved. I'm using the LTS for stability and application crashes because of a bugged hardware timer are not acceptable.

Is there any way to install hpet, as it's said to be a better timer, or does my hardware need to support it?

---

### Post by change_mode on 2009-04-11
Daily bump ;)

---

### Post by change_mode on 2009-04-13
:/

---

### Post by change_mode on 2009-04-23
bump

---


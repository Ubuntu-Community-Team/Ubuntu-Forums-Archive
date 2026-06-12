---
title: "Get CPU Temperature from Console"
date: 2006-03-01
forum: Desktop Environments
---

### Post by Lux Perpetua on 2006-03-01
Say I just quickly want to check my CPU's temperature, but I don't want to run gkrellm or an applet all the time. Is there a command line utility available for this task?

---

### Post by art on 2006-03-01
more /proc/acpi/thermal_zone/THZN/temperature

or something in those lines... This works for me, if it doesn't work for you check what you have in /proc/acpi and go from there.

---

### Post by Lux Perpetua on 2006-03-01
Thanks a bunch! It turns out it's /proc/acpi/thermal_zone/THM0/temperature.

---


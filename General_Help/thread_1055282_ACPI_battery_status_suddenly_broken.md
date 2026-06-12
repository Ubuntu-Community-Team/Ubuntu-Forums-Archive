---
title: "ACPI battery status suddenly broken"
date: 2009-01-30
forum: General Help
---

### Post by DoctorRockit on 2009-01-30
Hi all,

I have a strange problem with the battery status as shown by the gnome-power-manager applet as well as the 'acpi' commandline utility.

Both properly detect the power status (charging, AC power, discharging, ...) but always report a current/remaining capacity of 0.0%.

Contrary to that the information obtained from /proc/acpi/battery/BAT0/state is complete and correct.

Example output from 'acpi -V':
```

Battery 0: Full, 0%
AC Adapter 0: on-line
Thermal 0: ok, 41.0 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: Processor 0 of 10

```

Corresponding output from 'cat /proc/acpi/battery/BAT0/state':
```

present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      4885 mAh
present voltage:         12416 mV

```

I first suspected the recent kernel update from intrepid-updates might be responsible, so I booted an older version to no avail.

Does anyone have helpful suggestions on what my problem may be and how I might be able to solve it? Thanks in advance!

---

### Post by LowSky on 2009-01-30
charge the battery, then run the system on battery poweruntil it dies, then recharge, this should fix the error you are seeing.

---

### Post by DoctorRockit on 2009-01-30
Wow, thanks a lot for the prompt answer! I'll try your suggestion and will report success or failure :).

---

### Post by DoctorRockit on 2009-02-03
I just wanted to report that letting the battery die, and reloading it (while the notebook was off) worked out just fine. Thanks again for the help.

---


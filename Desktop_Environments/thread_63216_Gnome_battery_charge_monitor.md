---
title: "Gnome battery charge monitor"
date: 2005-09-07
forum: Desktop Environments
---

### Post by axcairns on 2005-09-07
Hullo all,

I am having trouble with the Gnome battery charge monitor. 

Firstly, it does not update the power connection status after I start up. If it was plugged in when I turned the machine on, the status stays 'on AC power' even if I pull out the cord. If I start on battery power it stays 'on battery power' even if I plug it in.

The second problem is that the 'time remaining' and battery charge % seem flaky when the monitor is in 'on battery power' mode (see above). At first, the battery level seems to drop normally, but then will suddenly drop to redline and give a 'one hour remaining' warning. If I go into the charge monitor preferences and turn stuff on and off, it resets and shows the real value again.

After reading through these forums I ran a few diagnostics, thinking it might be my hardware -

```
allan@vaio:~$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         4071 mWh
last full capacity:      40710 mWh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 400 mWh
design capacity low:     384 mWh
capacity granularity 1:  64 mWh
capacity granularity 2:  64 mWh
model number:            CL-71
serial number:           15088
battery type:            LION
OEM info:                PS

```

Last full capacity 40710 mWh???

```
allan@vaio:~$ cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            0 mW
remaining capacity:      37070 mWh
present voltage:         16120 mV

```

Battery was unplugged in the above example.

```
allan@vaio:~$ cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            0 mW
remaining capacity:      36810 mWh
present voltage:         17020 mV

```

Battery was plugged in in the above example. Looks like Linux has no trouble tracking the power connection status...

I also tried gkrellm and it detects my power connection status just fine. 

Looks like it is just the gnome monitor. Anyone else had trouble with it?

Thanks,

Allan

---


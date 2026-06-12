---
title: "Ubuntu shuts down when AC disconnected"
date: 2011-09-02
forum: Desktop Environments
---

### Post by darincb77 on 2011-09-02
Hi All,

I am using an MSI x320 with Ubuntu 10.04 . 

If I unplug my AC power, I get the usual buggy message saying there is little power remaining. Then the machine shuts down. I've played with the power settings for suspend/hibernate on low battery, and just set those to "nothing" by hand in the gconf-editor. To no avail. I've also tried unticking setting the gnome-power-manager/use_time_for_policy , to no avail. 

I know it is not a real battery problem, because I can run for a long time if I boot from battery only. But once I plug in and plug out the AC it shuts down, or if I boot from AC and unplug it just shuts down. 

Any thoughts?

**SOLVED. It is related to the Ralink wireless card. To fix, just do: **

```


cd /etc/pm/power.d 
sudo touch pcie_aspm
sudo touch wireless


```

---

### Post by darincb77 on 2011-09-02
Another fact: I tried Xubuntu 10.04 earlier, and it didn't seem to have this problem.

---

### Post by darincb77 on 2011-09-02
Another hint may be that if I happened to be as root in a terminal (sudo su ), then I unplug the AC, a message pops up that says:

System Pologicy prevents stopping the system when other users are logged in. An application is attempting to perform an action that requires privileges. Authentication is required to perform this action. 

If i hit cancel to that message, it doesn't shut down on me. If I authenticate it and hit OK, it shuts down same as before.

That's not a great work around, but does it give anyone any ideas?

---

### Post by raja.genupula on 2011-09-03
try this

[http://ubuntuforums.org/showthread.php?t=1660872](http://ubuntuforums.org/showthread.php?t=1660872)

---

### Post by darincb77 on 2011-09-04
Hi Raja,

Thanks. I've already tried that and unfortunately it doesn't work. 

The only new news is that I realized the suspend/hibernate don't really work (gma500 chipset, everything is awful), so something is either forcing or demaning a shtudown/suspend/hibernate, and is prompted by the battery, and thus far none of the power-manager settings are able to change that. If I could figure out what is actually being prompted perhaps a workaround could be devised. 

Thanks again. I'll post more if there is progress. For now I just pop a terminal and do 'sudo su' if i need to disconnect power, that will at least prompt before the shutdown (due to multiple users) and let me cancel the shutdown...

---

### Post by darincb77 on 2011-09-04
Here is the output of upower -d before and after unplugging:

Before:
```


Device: /org/freedesktop/UPower/devices/line_power_ADP1
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C09:00/ACPI0003:00/power_supply/ADP1
  power supply:         yes
  updated:              Sun Sep  4 11:28:45 2011 (117 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             yes

Device: /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C09:00/PNP0C0A:00/power_supply/BAT1
  vendor:               MSI Corp.
  model:                MS-1351
  power supply:         yes
  updated:              Sun Sep  4 11:30:21 2011 (21 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              18.4408 Wh
    energy-empty:        0 Wh
    energy-full:         32.3676 Wh
    energy-full-design:  31.82 Wh
    energy-rate:         14.0304 W
    voltage:             15.325 V
    time to full:        59.5 minutes
    percentage:          56.973%
    capacity:            100%
  History (charge):
    1315150221	56.973	charging
    1315150191	56.607	charging
    1315150161	56.241	charging
  History (rate):
    1315150161	14.030	charging
    1315150131	14.045	charging

Daemon:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes



```

After:
```

Device: /org/freedesktop/UPower/devices/line_power_ADP1
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C09:00/ACPI0003:00/power_supply/ADP1
  power supply:         yes
  updated:              Sun Sep  4 11:34:19 2011 (4 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             no

Device: /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C09:00/PNP0C0A:00/power_supply/BAT1
  vendor:               MSI Corp.
  model:                MS-1351
  power supply:         yes
  updated:              Sun Sep  4 11:34:23 2011 (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    energy:              19.314 Wh
    energy-empty:        0 Wh
    energy-full:         32.3676 Wh
    energy-full-design:  31.82 Wh
    energy-rate:         11.3516 W
    voltage:             15.074 V
    time to empty:       1.7 hours
    percentage:          59.6708%
    capacity:            100%
  History (charge):
    1315150463	59.671	discharging
    1315150459	59.854	discharging
    1315150431	59.488	charging
    1315150401	59.122	charging
    1315150371	58.756	charging
  History (rate):
    1315150463	11.352	discharging
    1315150459	955.888	discharging
    1315150401	14.030	charging
    1315150371	14.045	charging

Daemon:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      yes
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes


```

---

### Post by SecretCode on 2011-09-04
Have you tried creating empty files 'pcie_aspm' and 'wireless' in /etc/pm/power.d? (See [http://ubuntuforums.org/showthread.php?t=1594473](http://ubuntuforums.org/showthread.php?t=1594473))

If that doesn't work, trying changing your GRUB to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off"
```
(See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745))

---

### Post by darincb77 on 2011-09-04
Thanks SecretCode, creating the empty files worked perfectly! I had made the 'wireless' file before but never the 'pcie_aspm'. Guess I saw it in a different forum. 

Thanks again! Will post as solved with solution.

---


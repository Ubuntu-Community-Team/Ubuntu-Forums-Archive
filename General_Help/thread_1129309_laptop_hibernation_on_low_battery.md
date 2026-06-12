---
title: "laptop hibernation on low battery"
date: 2009-04-18
forum: General Help
---

### Post by broshe on 2009-04-18
Hello, I am using xubuntu 8.10 64 bit on a Dell Vostro 1310 laptop.
For some reason the laptop does not hibernate when the battery is low.
I saw a guide on ubuntu forums 
[http://ubuntuforums.org/showthread.php?t=843641](http://ubuntuforums.org/showthread.php?t=843641)
and tried to implement it.

In /etc/default/acpi-support
I set 
ENABLE_LAPTOP_MODE=true

After restarting, working on battery, I checked in terminal:
code: sudo laptop_mode 
output: Laptop mode enabled, active

This seems to be OK

Now, in etc/laptop-mode/laptop-mode.conf I set the following options:


ENABLE_LAPTOP_MODE_ON_BATTERY=1
MINIMUM_BATTERY_CHARGE_PERCENT=1
DISABLE_LAPTOP_MODE_ON_CRITICAL_BATTERY_LEVEL=1
ENABLE_AUTO_HIBERNATION=1
HIBERNATE_COMMAND=/etc/acpi/hibernate.sh
AUTO_HIBERNATION_BATTERY_CHARGE_PERCENT=5
AUTO_HIBERNATION_ON_CRITICAL_BATTERY_LEVEL=1


I checked the hibernation command
sudo /etc/acpi/hibernate.sh 
It does hibernate.
The battery indicator also seems to be correct.

However, when the battery is low (around 1%) the computer simply shuts down without hibernating.

Can someone suggest a fix to this ?

Thanks,

Eli

---

### Post by s3a on 2009-04-18
**System-->Preferences-->Power management** maybe? I am not 100% sure since I can't see the battery tab since I am running on AC power only.

---

### Post by broshe on 2009-04-18
Thank you s3a.
Yes I forgot to mention that the hibernation on low battery option is activated in: settings->power management.

Still, the thing does not hibernate but just dies without saving anything.

Eli


> **s3a said:**
> **System-->Preferences-->Power management** maybe? I am not 100% sure since I can't see the battery tab since I am running on AC power only.

---

### Post by broshe on 2009-04-20
Hello,

The problem is solved for me now.
I disabled the laptop-mode:
In /etc/default/acpi-support
I set
ENABLE_LAPTOP_MODE=false.

Now, following  pruch in [https://bugs.launchpad.net/bugs/186390](https://bugs.launchpad.net/bugs/186390),
I launched gconf-editor and set:
/apps/gnome-power-manager/general/use_time_for_policy (false)
/apps/gnome-power-manager/thresholds/percentage_low (15)
/apps/gnome-power-manager/thresholds/percentage_critical (12)
/apps/gnome-power-manager/thresholds/percentage_action (10)
/apps/gnome-power-manager/actions/critical_battery (hibernate)

Also, in settings->power management, activate hibernation on low battery option.

Everything works now.

Eli

---


---
title: "Battery Status Indicator Applet Still Not Working (Ubuntu 12.04 - Precise)"
date: 2013-05-13
forum: Desktop Environments
---

### Post by bluebrave on 2013-05-13
Over six months ago, [I posted]("http://ubuntuforums.org/showthread.php?t=2052156") that I had upgraded from 10.04 to 12.04  and that battery status indicator applet in the panel stopped working on  my laptop (an MSI machine).  Specifically:


[LIST=1]
[*]The icon does not change when the power  cord is plugged in or  unplugged (the icon remains a battery if that  was the power source on  boot but won't change if I plug in the power  adaptor and visa-verse). 
[*]The battery indicator does not give me a low battery  warning or  alert (ubuntu just shuts down with no onscreen warnings).   The battery status  isn't updated at all (it doesn't decline as the  battery drains). 
[*]Clicking the icon and selecting "Power Setting" has all the  menus but "Show battery status in the menu bar" is blank and stays  blank even after I select an option (eg: "When battery is present") and  close. 
[*]The battery indicator applet *does temporarily*  work after some updates (I think the kernel updates - maybe).  Ubuntu just  updated a few things on May 4th and the status started working (icon  changed etc when I plugged/unplugged the computer), however, it only lasted until the  next time I booted.  I've noticed this at other time (each time, it only works until the next boot) but I'm not sure what the common denominator is. 
[/LIST]

I am currently using gnome-classic but noticed the same icon issue in   Unity (not sure if unity also has the no low battery warning problem,   however).  I ran dmesg when booted plugged in and on battery but don't  know what to look for and the files are too big to attach (19kb limit).   I can email them if desired or copy/paste them here (if requested).  I  basically can not run the laptop with Ubuntu for long on battery as I  never know when it is going to turn off (and lose my work) - I have a  dual Windows boot but there are things I prefer to do with Ubuntu.

These are outputs from acpi_listen command:

Here are the outputs:
 
 plug in power:
 ac_adapter ADP1 00000080 00000001
 battery BAT1 00000080 00000001
 battery BAT1 00000081 00000001
 
 unplug power:
 ac_adapter ADP1 00000080 00000000
 battery BAT1 00000080 00000001
 battery BAT1 00000081 00000001
Here are the outputs:
 

Here are the uevent outputs
uevent (booted with power):
 
 POWER_SUPPLY_NAME=BAT1
 POWER_SUPPLY_STATUS=Full
 POWER_SUPPLY_PRESENT=1
 POWER_SUPPLY_TECHNOLOGY=Unknown
 POWER_SUPPLY_CYCLE_COUNT=0
 POWER_SUPPLY_VOLTAGE_MIN_DESIGN=10800000
 POWER_SUPPLY_VOLTAGE_NOW=12506000
 POWER_SUPPLY_CURRENT_NOW=0
 POWER_SUPPLY_CHARGE_FULL_DESIGN=4800000
 POWER_SUPPLY_CHARGE_FULL=3344000
 POWER_SUPPLY_CHARGE_NOW=3344000
 POWER_SUPPLY_MODEL_NAME=MS-171F
 POWER_SUPPLY_MANUFACTURER=MSI Corp.
 POWER_SUPPLY_SERIAL_NUMBER=
 
 uevent (booted on battery):
 
 POWER_SUPPLY_NAME=BAT1
 POWER_SUPPLY_STATUS=Discharging
 POWER_SUPPLY_PRESENT=1
 POWER_SUPPLY_TECHNOLOGY=Unknown
 POWER_SUPPLY_CYCLE_COUNT=0
 POWER_SUPPLY_VOLTAGE_MIN_DESIGN=10800000
 POWER_SUPPLY_VOLTAGE_NOW=11361000
 POWER_SUPPLY_CURRENT_NOW=2529000
 POWER_SUPPLY_CHARGE_FULL_DESIGN=4800000
 POWER_SUPPLY_CHARGE_FULL=3344000
 POWER_SUPPLY_CHARGE_NOW=2370000
 POWER_SUPPLY_MODEL_NAME=MS-171F
 POWER_SUPPLY_MANUFACTURER=MSI Corp.
 POWER_SUPPLY_SERIAL_NUMBER=

Finally, I also edited /etc/modprobe.d/blacklist.conf and added "blacklist msi-wmi" but that also didn't change anything.

---


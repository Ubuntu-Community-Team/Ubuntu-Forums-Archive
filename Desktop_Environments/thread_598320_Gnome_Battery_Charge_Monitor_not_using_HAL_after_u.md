---
title: "Gnome Battery Charge Monitor not using HAL after upgrade to Gutsy"
date: 2007-10-31
forum: Desktop Environments
---

### Post by Teasel on 2007-10-31
I have a mains powered desktop PC with a rechargeable cordless mouse.  Under Feisty, the Gnome Battery Charge Monitor applet automatically spotted that I had a mouse battery and reported its charge.  However, after upgrading to Gutsy, all I get is "System is running on AC Power.  No battery present".  Arguably true, perhaps, but not as useful as the Feisty bahaviour!

lshal includes the following:

```
udi = '/org/freedesktop/Hal/devices/usb_device_46d_c50e_noserial'
  battery.charge_level.current = 3  (0x3)  (int)
  battery.charge_level.design = 7  (0x7)  (int)
  battery.charge_level.last_full = 7  (0x7)  (int)
  battery.charge_level.percentage = 42  (0x2a)  (int)
  battery.command_interface = 'csr'  (string)
  battery.csr.has_res = false  (bool)
  battery.csr.has_sms = false  (bool)
  battery.csr.is_dual = false  (bool)
  battery.is_rechargeable = true  (bool)
  battery.present = true  (bool)
  battery.type = 'mouse'  (string)
```

ls /proc/acpi/battery  shows no files.

OK, so my battery's currently about 42% full, and I need to use HAL, not ACPI.  The help page says that HAL should be the default and that there should be a star by Ryan Lortie's name when it's in use.  However, there isn't any star showing (though nor is there any no_hal key in gconf2).

So I'm a bit stuck.  Has Battery Charge Monitor been "debugged" to stop it showing mouse batteries when what most people want is their laptop battery?  Or is there something I can configure to point it at the battery I want it to monitor?

TIA for any suggestions!

Ian

---


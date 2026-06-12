---
title: "suspend to ram is not available in ubuntu 8.10"
date: 2009-03-10
forum: General Help
---

### Post by manusha on 2009-03-10
Hi,
im using ubuntu desktop edition 8.1 and KDE 4.2. In the shutdown menu, i get the option "suspend to disk" but not "suspend to ram".

I checked the BIOS to see of my system supports ACPI and it is set to support ACPI S1.

when i issue a "lshal | grep power_management", it shows  follwing.
....
power_management.can_suspend = false
...

when i try the pm-suspend command, it does nothing.

cat /sys/power/state shows following.
standby disk

however when i issue 
echo standby > /sys/power/state, the system seems to suspend, but monitor stays on. and it resumes for keyboard events/mouse events.

is this the correct way to do this? why does the option not available in KDE shutdown menu. (nor GNOME menu's)

Can anybody diagnose the problem?

Thanks
Maan

---


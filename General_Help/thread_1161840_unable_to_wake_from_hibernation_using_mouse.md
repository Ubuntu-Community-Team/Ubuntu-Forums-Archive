---
title: "unable to wake from hibernation using mouse"
date: 2009-05-17
forum: General Help
---

### Post by the_trooper47 on 2009-05-17
I have Jaunty 64-bit installed on a Gigabyte GA-EG41MF-S2H.

I need the system to wake up from hibernation by double clicking a mouse key, connected to a USB port. WOL & the power key wakes it but ultimately I need it to do the same with the mouse...

Up until now I have gone thru a few steps to try & fix it.. the /proc/acpi/wakeup gets edited each time the system reboots with a script i put together (gathered from other posts) that is saved in the /etc/init.d/ dir.

By typing in cat /proc/acpi/wakeup I can see that the USB devices are enabled after the script is run.

BIOS has the USB mouse enabled & wake by 'double clicking' is also.

I use the pmi command to hibernate, does this affect anything else to inhibit the system from awakening?  

Ideas?

Cheers!

---


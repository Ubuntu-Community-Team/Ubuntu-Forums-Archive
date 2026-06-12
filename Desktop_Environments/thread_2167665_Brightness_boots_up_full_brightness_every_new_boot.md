---
title: "Brightness boots up full brightness every new boot up.."
date: 2013-08-14
forum: Desktop Environments
---

### Post by Linda_Valdeen on 2013-08-14
Running Ubuntu-12.4 ("UE 3.4") in a Toshiba Satelite notebook (160 gig hd, 2 gig ram)..
After every boot up I set brightness to lowest setting.. 
Every boot up the brightness is at brightest setting.. 
Is there a tweak to lock the brightness setting at minimum?..

---

### Post by varunendra on 2013-08-15
> **Linda_Valdeen said:**
> Is there a tweak to lock the brightness setting at minimum?..

I have added this line in my "/etc/rc.local" file -
> echo 0 > /sys/class/backlight/acpi_video0/brightness
Your default video device may be different than "acpi_video**[COLOR="#FF0000"]0[/COLOR]**" and its pertaining setting value (0) maybe different too. Please check it yourself with -
```
ls /sys/class/backlight
```
.. and the pertaining value in the "brightness" file in the found video device(s).

Make sure to add the command above the last line (exit 0) in the /etc/rc.local file, as "exit 0" must be its last line.

---


---
title: "Vostro 2510 Power Management won't dim screen on battery"
date: 2012-08-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Spectre630 on 2012-08-19
I have a Dell Vostro 2510 laptop running a fresh install of 12.04 (currently using KDE, but have KDE, Gnome, and Xfce installed and all have the same problem).  If I go to power management and set the brightness to dim my screen when on battery, it doesn't actually dim.  It detects that I'm on battery, but does not change the brightness.  I can manually adjust the brightness with Fn+up/down, but the power manager doesn't appear to do it.  When I unplug there is perhaps a very small, nearly unnoticeable change in brightness, but nothing significant.

---

### Post by jocefus on 2012-08-19
That check box you speak of only dims the screen after it has been idle for a short period of time. It does not record different brightness settings for battery and AC power like older versions of Ubuntu using classic Gnome. Those brightness settings in gnome-power-manager (gnome2) were apparently left out or not yet implemented in gnome-control-center (gnome3).
 
I have googled and tried various solutions, but none gave me the desired effect. I ended up creating a short script for pm-utils that changes the brightness when on either AC or battery power. It works ok, but there is no GUI. You must manually determine the numerical brightness settings you desire and enter them into the script.
 
EDIT: I am referring to Gnome's behavior. I have no experience with how KDE and Xfce handle power management.

---

### Post by Spectre630 on 2012-08-20
So, I still haven't found a solution to this, but wanted to provide a little extra info.  I've tried any number of things without success.  I'm going to list things I've tried to see if it sparks some idea from someone else.

[LIST]
[*]I added the "acpi_backlight=vendor" to grub, but it did nothing.
[*]I tried downloading xbacklight, but it does nothing.  In fact, [FONT=Courier New]xbacklight -get[/FONT] returns absolutely nothing.
[*][FONT=Courier New]cat /sys/class/backlight/dell_backlight/brightness[/FONT] returns the correct brightness level.
[*]Brightness works properly on Vista (I know, I know, double groan) on this machine.
[*]I have another, older Dell laptop (an Inspiron 600m, ~8 years old) running XUbuntu and power management is working fine on it.  However, as best my newbie self can find, there's no difference in settings or scripts (unedited stock).  Only difference as I can tell is the hardware itself.  The old laptop was running 11.xx and was updated to 12.04, whereas the laptop with the problem was a fresh 12.04 install.
[*]I'm running NVidia proprietary drivers.  I was using "current" and switched to "current-update", but that didn't have any affect.
[/LIST]
TIA!

---


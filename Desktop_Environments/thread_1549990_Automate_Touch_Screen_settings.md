---
title: "Automate Touch Screen settings"
date: 2010-08-10
forum: Desktop Environments
---

### Post by Z.K. on 2010-08-10
I have a touch screen on the device I am using with Ubuntu 10.04.  The touch screen works and I am able to calibrate it, but I am unable to keep the settings after logging out or rebooting.  The command I am using is 

xinput set-int-prop "PANJIT TouchSet USB Digitizer" "Evdev Axis Calibration" 32 575 3553 648 3433

I have put it in rc.local and xinitrc, but it does not set up the touch screen settings the way it does if used in a terminal.

Anyone have any ideas where I can put this command so it runs automatically during login or just after the Gnome starts up.  I would prefer it to start before any user logs in, but anything is okay at the moment.

:(

---


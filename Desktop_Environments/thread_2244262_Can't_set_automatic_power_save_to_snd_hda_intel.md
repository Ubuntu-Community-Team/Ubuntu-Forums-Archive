---
title: "Can't set automatic power_save to snd_hda_intel"
date: 2014-09-15
forum: Desktop Environments
---

### Post by Sotai on 2014-09-15
When I set /sys/module/snd_hda_intel/parameters/power_save manually it works, but the settings in options in /etc/modprobe.d/ and /etc/pm/sleep.d are ignored, power_save of snd_hda_intel always resets to 0 at boot and after resuming from suspend.

---

### Post by Toz on 2014-09-15
Most probably the setting is being changed again by some other program/service. For bootup, try adding the command to the end of /etc/rc.local (before the "exit 0" command). For suspend, try renaming the file you created in the /etc/pm/sleep.d directory so that it starts with "000" (so that it is executed last in the resume sequence).

---

### Post by Sotai on 2014-09-17
That works. Thanks.

---


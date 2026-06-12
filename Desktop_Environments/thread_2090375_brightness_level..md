---
title: "brightness level."
date: 2012-12-02
forum: Desktop Environments
---

### Post by Bigneil on 2012-12-02
ok, this is no big deal, but it is slightly annoying.

whenever I boot into ubuntu the brightness level is set really low. I have to go to "brightness and lock" each time and turn it up manually, It also defaults to dim when I plug in, or out, the power cable.

It doesn't seem to have any brightness memory, nor do the brightness Fn short cuts on the F keys work.

using Ubuntu 12.10 64 bit, on ASUS K55A.

---

### Post by Isamu715 on 2012-12-02
This laptop has an integrated Intel GPU, correct? Then you can use:
```
intel_backlight xx
```changing *xx* to your desired brightness level(numbers are from 0 to 100). This may be already installed on your system, if it's not install *intel-gpu-tools*. To make it run on the login screen add it to */etc/rc.local*.  However, this setting is completely separate from GNOME settings and whenever the DE changes backlight it changes according to it's own settings. To set a certain brightness level for the DE create a .*brightness.sh* file in your home directory:
```
gedit ~/.brightness
```with the following contents:
```
#!/bin/sh
#change brightness setting on startup or resume
pkexec /usr/lib/gnome-settings-daemon/gsd-backlight-helper --set-brightness xxx
```Change *xxx* to a setting suitable for you, the maximum number you can set is 976. Then execute the following command:
```
gsettings set org.gnome.settings-daemon.peripherals.input-devices hotplug-command "/home/$( whoami )/.brightness.sh"
```This should take care of initial brightness settings for the screen. You may want to disable "Dim screen to save power" in brightness settings, this may solve the dimming issue on plugging the power cable in or out.
EDIT:
Adding *acpi_osi=Linux*  and/or *acpi_backlight=vendor* to GRUB_CMDLINE_LINUX in */etc/deafult/grub* could solve the issue, too.

---

### Post by cmcanulty on 2012-12-02
I added this tweak to /etc/default/grub back it up first of course
```

GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

---


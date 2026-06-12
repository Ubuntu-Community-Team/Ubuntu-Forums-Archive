---
title: "DPMS appears not to work on Raspberry Pi 4B (Xubuntu, 19.10)"
date: 2019-11-15
forum: Desktop Environments
---

### Post by steveb-uuser on 2019-11-15
It appears DPMS does not work with Xubuntu (19.10) on Raspberry Pi 4B.

The screen blanks but the HDMI monitor back light is still on (e.g. when the screen saver blanks or log out after DPMS configured)
```
xset dpms force off
``` does blank the screen but the backlight is still on.

This was a firmware issue but ```
tvservice -o
``` does switch off the hdmi and the back light goes off.
(Background info: I think this was fixed in Raspbian).

Any clues?

xset -q  shows DPMS Enabled
Kernel: aarch64 Linux 5-3-0-1012-raspi2
Nothing reported in /var/log/Xorg.0.log with xset dpms force off

Possibly related to the kernel or libxcb-dpms0 package?

---


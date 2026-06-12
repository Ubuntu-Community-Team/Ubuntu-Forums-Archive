---
title: "Adjust trackpoint sensitivity"
date: 2012-04-24
forum: Desktop Environments
---

### Post by niglas on 2012-04-24
I'd like to adjust the mouse sense on a thinkpad x40.

[LIST]
[*]The sense option on the mouse settings is already set to fastest, but i want even higher sense.
[*]I installed *gpointing-device-settings*, but no mouse sense option popped up.
[/LIST]
I'd love to avoid creating/editing the xorg.conf manually.

Any ideas?

---

### Post by scurpio on 2012-04-28
I would also like to increase the sensitivity of my trackpoint. I found some instructions online but I don't know it they would work with Ubuntu 12.04.

---

### Post by mdseymour on 2013-05-04
Tested in Ubuntu 12.10 64-bit on a Thinkpad x220.

Run these commands as root (sudo "cmd" or similar):

echo -n 240 > /sys/devices/platform/i8042/serio1/sensitivity
echo -n 140 > /sys/devices/platform/i8042/serio1/speed

Adjust values as you see fit. sensitivity is 0-255, default is 128. The effect is immediate. No reboot necessary.

To keep the adjustments across reboots, place in the file /etc/rc.local before "exit 0" (edit it as root, or using sudo).

---


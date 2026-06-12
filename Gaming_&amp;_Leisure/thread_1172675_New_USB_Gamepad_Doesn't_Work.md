---
title: "New USB Gamepad Doesn't Work"
date: 2009-05-28
forum: Gaming &amp; Leisure
---

### Post by theshibboleth on 2009-05-28
Hi, I just bought a Vinyson USB gamepad to use with emulators and other games, but they aren't working. I tried doing modproble jsdev, and it didn't return any error, and I also tried running jscalibrator, but the dot on the axes calibration just moves around randomly. If my game controller is working, should I see output with xev?

---

### Post by hikaricore on 2009-05-28
After plugging it in check the output of:

> dmesg

To see if linux is recognizing it.
You may also want to try a different usb port.

---


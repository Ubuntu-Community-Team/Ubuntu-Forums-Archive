---
title: "D830 instalation failure"
date: 2007-06-25
forum: Dell  Ubuntu Support
---

### Post by gszpiniak on 2007-06-25
Hi just recieved the new Latitude D830:

D830 Intel Core 2 Duo T7100 (1.8GHz/2MB/800MHz) with integrated Intel GMA
15.4" WUXGA (1920 x 1200) DellSharp Wide Aspect Ratio TFT display
Mobile Intel 965 Express GMA x3100
2.0GB, 667MHz DDR2 SDRAM (2 x 1024MB)
Internal Dell 360 Bluetooth Card
Core 2 Duo - Intel 3945ABG Wireless Card

I want to install Ubuntu 7.04. When I boot from live CD it stops after the usb configuration in line

[INDENT]***drivers/usb/input/hid-core.c: v2.6:USB HID core driver***[/INDENT]

It stops loading and shows the following message:

[INDENT][B][I]BusyBox v.1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs)_[/I][/B][/INDENT]

[IMG]http://tami-guy.szpiniak.com/varios/D830_ubuntu.jpg[/IMG]

I tried with 64bit and 32bit versions and happened the same. I also tried to enable/disable many options from de BIOS or to start with acpi=off noapic nolapic, but nothing works.

I have to return my old Latitude D800 and I have to migrate to the new one. Anybody can help me??

Thank you very much

---

### Post by apel_2804 on 2007-06-25
You need to install with Ubuntu alternate cd! See also D630 (same base) thread: [http://ubuntuforums.org/showthread.php?t=481651](http://ubuntuforums.org/showthread.php?t=481651)

---

### Post by gszpiniak on 2007-06-26
Thx for your help. I installed it and works great.

---


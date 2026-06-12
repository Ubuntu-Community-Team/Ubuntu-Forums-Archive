---
title: "Ubuntu 12.04 won't suspend, reboot, or shutdown"
date: 2015-02-22
forum: Desktop Environments
---

### Post by Offkey on 2015-02-22
I have recently purchased a new laptop, hp pavilion 11n040ca. I installed Ubuntu 12.04 (64 bit) on it, and it runs great; except it won't reboot, suspend, or shutdown. Specifically, it won't wake-up from suspend (just see black screen), and whenever I try to reboot or shutoff, it get stuck on the ubuntu logo (with the 5 dots filling-in and emptying).

[B]What have I tried
[/B]
[LIST]
[*]After browsing the forums I first tried to reboot and shut-off from the comman line, using *init *and*reboot*.
[*]I tried editing grub. To the line "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" I tried adding (alternately) *reboot=acpi*,  *acpi=nomsi*, and a few other options; I *sudo update-grub* and tried to reboot, same problem.
[/LIST]

Any ideas or new directions to explore would be very much appreciated. Thank you in advance!

---

### Post by mörgæs on 2015-02-25
Hi, welcome to the fora.

New hardware and old software is a bad combination. Have you tried 14.04.2 and/or 15.04 (development)?

---

### Post by Offkey on 2015-03-07
Thank you for the suggestion. I have now tried to install both 14.02 and 14.10 and I run into the same problem. In fact the installation finishes successfully and the computer freezes on the reset step. Any ideas? =(

---

### Post by mörgæs on 2015-03-09
And 15.04?

---

### Post by winter6 on 2015-04-25
I had the same problem.  It was caused by a 'Wireless PCI Card' that was in my rig that I don't use and didn't install drivers for.  I removed the PCI card and all worked fine.  So Ubuntu probably new it was there and tried to shut it down, even though it was never properly installed and hung.  So a possible fix may be make sure all your devices and drivers are properly installed and working.

---


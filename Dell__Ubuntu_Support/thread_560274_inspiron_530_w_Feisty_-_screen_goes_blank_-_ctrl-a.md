---
title: "inspiron 530 w Feisty - screen goes blank - ctrl-alt-keys can reboot"
date: 2007-09-26
forum: Dell  Ubuntu Support
---

### Post by LesFromWaldenVT on 2007-09-26
If I leave my system for even a short time, sometimes less than an hour,  the screen goes black and the green indicator on the monitor goes to yellow.

At this point, ctrl+alt+backspace restarts ubuntu (but not computer).

If instead, I try Ctrl+alt+F1, it says 'trying to continue from /dev/sda5, no resume image'.

Any idea what could be happening? I have all of the power and screensaver options turned off now trying to isolate the problem.

It appears to be Xserver crashing. How do I find out why? Is there an Xserver log saved across restarts?

---

### Post by ddrichardson on 2007-09-27
Is there an option in the laptop BIOS for automatically suspending given a certain amount of time? The resume message would suggest that the system has entered a hibernate mode, but that the system may have a bug with respect to its power saving implementation.

My first suggestion would be to boot using pci=noacpi and see if the fault reappears.

---


---
title: "USB not working on startup"
date: 2009-01-19
forum: General Help
---

### Post by 1script on 2009-01-19
Hi all, hope someone can give me an idea on how to troubleshoot this.

Every day the first start of the day would have all my USB devices (including most frustratingly mouse and keyboard) would not be recognized. If I am lucky, after 2-3 restarts they would all of the sudden start working. Some days are worse than others but today I cannot start USB at all - typing on a second PS2 keyboard I now have attached to the PC for such situations. 'sudo lsusb' and 'lsusb' hung indefinitely and cannot even be killed.

How would I go about troubleshooting a problem like that.

Oh, by the way, the USB keyboard is recognized by BIOS just fine - before PC boots up, I can use it in BIOS setup.

Thanks!

---

### Post by NT4usB on 2009-01-19
You have the 'Legacy USB' option selected in the bios?
Have a bunch of USB hubs hanging off everywhere with drives, modems, cellphones, coffee makers, etc. plugged in?
Maybe start with no USB devices, plug in keyboard first, then mouse, etc. until lsusb breaks.
Beyond that, some system and OS particulars would be helpful.

---


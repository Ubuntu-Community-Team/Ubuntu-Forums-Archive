---
title: "Cannot resume from suspend, reboots instead"
date: 2011-05-30
forum: Desktop Environments
---

### Post by prshah on 2011-05-30
Hello,

I'm sure this has an answer somewhere here, but even after 2 days of searching, I cannot find it.

My desktop computer (home built, Intel PIV 1.66GHz dual core / 2GB / 1TB / Nvidia graphics) can hibernate and resume from hibernation fine. However, when I choose suspend, it suspends correctly (as per log)> /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sun May 29 22:33:32 IST 2011: performing suspend
 but cannot resume correctly.

When I type on the keyboard, or shake the mouse, nothing happens. (Both are USB, USB legacy is enabled in BIOS).

When I press the power button, it seems to come to life (power LED comes on) but there is a long pause (about 90 seconds) and then it seems to reboot. File system is clean on reboot (ie, no disk check). There is no "thawing" entry in the suspend log.

I have already tried the "acpi_sleep=nonvs" kernel parameter tweak, with no result (same problem remains).

Please point out if you have come across a solution.

Tech level: Intermediate-high, Please let me know if you need any more information, such as the entire suspend log.

---

### Post by s.fox on 2011-06-01
BUMP at original posters request. :)

---

### Post by prshah on 2011-06-05
OK, "problem" solved.

In the BIOS for the motherboard, "suspend state" setting was S3. Changing the "suspend state" BIOS option to S1 gave the more conventional resume/thaw activity that I expected. 

I hope this will be of help to future visitors.

All OK here, nothing to see now, move along...

---


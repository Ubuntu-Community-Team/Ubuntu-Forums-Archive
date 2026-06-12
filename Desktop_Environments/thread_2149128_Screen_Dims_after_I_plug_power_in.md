---
title: "Screen Dims after I plug power in"
date: 2013-05-27
forum: Desktop Environments
---

### Post by mythx on 2013-05-27
I've seen some talk of this issue, but haven't seen a resolution.  Thought I'd post and see if I get better luck.

I have a Dell Latitude E5400 Laptop.  I originally installed 12.04 on this, and am currently at 13.04.  This problem existed with 12.04 as well.  I keep the screen at 100%, and have configured the power save features to NOT mess with screen brightness.  When I unplug power, the screen doesn't do anything (as it should).  When I plug power back in, it dims as far as it can.  I'd say 0, but there's still some light.  I slide it back up, then everything is fine.  

Any suggestions?

Thanks

---

### Post by sunfromhere on 2013-05-31
Hello,

I have the same problem as you. My screen dims when power cord is plugged in or out, or on reboot.
I have tried:
1. editing /etc/rc.local to set maximum brightness - didn't work
2. editing grub to acpi_backlight=vendor - didn't work

Not sure what to try next.

---

### Post by sunfromhere on 2013-06-01
Correction: now everything is fixed, works as it should.
I cannot say which of these 2 fixed it, so try both. And reboot 2 times, because I rebooted only once and there was no change. Now today everything works.

---


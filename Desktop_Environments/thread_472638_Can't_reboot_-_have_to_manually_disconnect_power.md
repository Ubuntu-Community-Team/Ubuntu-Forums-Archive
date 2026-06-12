---
title: "Can't reboot - have to manually disconnect power"
date: 2007-06-13
forum: Desktop Environments
---

### Post by cleardensity on 2007-06-13
I've installed Feisty, once booted, the system works (although i do have a few little problems, for another post i suppose). My problem is that when i try and reboot, the computer will "shutdown" and will not actually boot again - i have to manually disconnect power and then boot the machine. I'm a noob on linux, just made the switch, so I would appreciate any help on troubleshooting this issue.

Thank you,

---

### Post by dfreer on 2007-06-14
Just guessing, but that sounds like a motherboard/BIOS issue to me. Did windows do this?

---

### Post by cleardensity on 2007-06-15
> **dfreer said:**
> Just guessing, but that sounds like a motherboard/BIOS issue to me. Did windows do this?

don't know - brand new box, and i never want windows to touch it... 

where would i go to look at this? I know on the boot messages, there's something that fails, i haven't caught it fast enough to see what exactly it is, is there a log or anything i can check? where would i check it?

I built this box with all new components, and the ONLY O/S that's been on it is Ubuntu Feisty. (with Studio). :D

Thanks for any help you can provide.

---

### Post by timcredible on 2007-06-15
shutdowns and reboots are controlled by acpi.  see if it's enabled.  system->administration->services->power management.  i see that ubuntu also has apm there.  if they're enabled, try disabling them to see if it helps.  this also controls monitor power off when nothing's going on, suspend mode, etc.

---

### Post by danhm on 2007-06-15
Have you tried rebooting from the command line?

```
sudo reboot
```

---

### Post by john.nicholls on 2007-06-15
Try looking at /var/log/syslog.

---


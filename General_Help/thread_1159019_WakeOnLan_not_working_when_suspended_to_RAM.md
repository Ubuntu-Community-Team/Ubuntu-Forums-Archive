---
title: "WakeOnLan not working when suspended to RAM"
date: 2009-05-14
forum: General Help
---

### Post by LucaTNT on 2009-05-14
Hi everyone,
I have managed to have WOL working when the computer is turned off or hibernated, but I can't make it wake up when suspended to RAM.

I tried to edit /etc/default/acpi-support and put my NIC's kernel module (via-rhine) into MODULES_WHITELIST and put "eth0" in SKIP_INTERFACES, but with no luck.

Any advices?

Thanks,
Luca

---


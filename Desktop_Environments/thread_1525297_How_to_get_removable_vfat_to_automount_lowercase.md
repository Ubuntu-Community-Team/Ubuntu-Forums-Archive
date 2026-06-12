---
title: "How to get removable vfat to automount lowercase ?"
date: 2010-07-06
forum: Desktop Environments
---

### Post by drgerafe on 2010-07-06
System here is Ubuntu 9.10 x86.

As configured, portable removable USB media (e.g., SD, CompactFlash) auto-mounts with fvat option "shortname=mixed".  While I understand the rational for this, I prefer filenames coming from FATx media to be all lowercase.

Coming from the FreeBSD environment, I could manage this relatively easily from the devd subsystem.

On our Ubuntu desktops, however, this is, so far, a mystery to me, and, as far as I can tell, undocumented anywhere.
I believe I can force an entry in /etc/fstab for a specific device using its LABEL or its UUID, but I don't want to do this for *every* SD or CF card we might attach to these systems.

Surely 9.10 x86 has a (simple) means of changing "shortname=mixed" to "shortname=lower" for all removable USB storage devices.

Pointers & suggestions to solving this are appreciated.

---


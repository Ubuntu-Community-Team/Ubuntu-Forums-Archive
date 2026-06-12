---
title: "automatically mount windows partition in Hardy Heron"
date: 2008-04-27
forum: Desktop Environments
---

### Post by adohall on 2008-04-27
Hardy Heron has recognised two of my Windows ntfs partitions and listed them in 'Places'. Unlike Gutsy Gibbon however, it doesn't mount them automatically on logon.
Is there a simple configuration setting that will mount one of these windows partitions on logon?

---

### Post by mriedel on 2008-04-27
apt-get install ntfs-config, then run Applications -> System Tools -> NTFS Configuration Utility

Alternatively you could add a line similar to "/dev/XXX /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0" to /etc/fstab. The aforementioned tool does that (and a few other things) for you.

---

### Post by adohall on 2008-04-28
Thanks. Multe gratias.

I installed ntfs-config which on launch offered to automatically mount all the drives it found.

---

### Post by freak42 on 2009-08-15
just a quick note for 9.04 jaunty users:

this still works (ntfs-config) however it has moved to system->administration->ntfs configuration tool

---


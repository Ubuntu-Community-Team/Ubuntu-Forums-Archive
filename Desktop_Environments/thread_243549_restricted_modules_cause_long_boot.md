---
title: "restricted modules cause long boot"
date: 2006-08-25
forum: Desktop Environments
---

### Post by DSab on 2006-08-25
Hello,

Sometimes (but not always) the "Initializing modules..." step of the boot takes up to 4 minutes, causing a desperately long boot on my laptop.

After investigation I discovered that this message is from
/etc/init.d/linux-restricted-modules-common
which starts /sbin/lrm-manager, which goes to /lib/linux-restricted-modules/2.6.12-10-386 and for each subdirectory $module here, does:

ld_static -r -o /lib/modules/2.6.12-10-386/volatile/$module.ko $module/*

The output directory /lib/modules/2.6.12-10-386/volatile is apparently a memory mapped part of the RAM, and this apprently has to do with respecting some legal reason that forbids keeping the linked version of these modules.

Does anyone have any idea of WHY this linking sometimes takes 4 minutes, and the next time will take 10 seconds?? I cannot find any correlation (power supply connected / disconnected, ethernet plus of wifi zone, first boot or reboot, etc.).

Anybody noticed this before? Any known cure?

Note that when its long, every module in /lib/linux-restricted-modules/2.6.12-10-386 is equally long to link and this leads to 4 minutes.

ds@10:~$ uname -a
Linux 10.52.10.2 2.6.12-10-386 #1 Tue Jul 18 22:08:27 UTC 2006 i686 GNU/Linux
Ubuntu 5.10 breezy badger, updated recently (july).

Thanks for answer.

---

### Post by DSab on 2006-08-31
Again, does somebody have a clue about these restricted modules slow to be linked at boot time ?:confused:

---

### Post by DSab on 2006-09-02
Again, nobody has an idea?

---

### Post by DSab on 2006-09-15
Again, anybody has an idea?

---


---
title: "Frozen at checking battery state"
date: 2012-02-23
forum: Desktop Environments
---

### Post by cjordan1 on 2012-02-23
I was attempting to update my nvidia drivers from 290.10 to 295.20. (I would have waited, but some cuda software I wanted to try wasn't working b/c the driver components has been upgraded to 295.20 while the kernel module was still 290.10, or so the error messages said.) 

Attempting to upgrade the drivers using the script nvidia provided failed, and my nvidia drivers appeared to be deleted. lightdm wasn't working, so I tried re-installing that. But now whenever I try to boot ubuntu it hangs at checking battery state. It also says "stopping automatic crash report generation" failed.

I read several threads on similar problems on ubuntuforums already. None of their solutions apply because ctrl-alt-f1 though f6 don't give access to other terminals. Oddly, I can still boot in recovery mode. 

System details: Ubuntu 11.10, intel i5 cpu, sabertooth motherboard, two gpus--nvidia gtx 560 (for dual monitors) and gt 520 (for cuda coding).

---

### Post by LinuxFan999 on 2012-02-23
You will need to reinstall Ubuntu, since you have a broken installation. Make sure to back up your data first.

---

### Post by ponsfrilus on 2012-03-08
Many other solution on forums.

Mine was to remove xorg.conf (/etc/X11/xorg.conf)

Cheers

---


---
title: "spontaneous reboots following power failure"
date: 2009-05-19
forum: General Help
---

### Post by scram69 on 2009-05-19
I am running 8.04 LTS on an AMD 64 X2 with a 4-disk raid 5 (mdadm).  Had a power failure at home on 5/17.  I restarted the machine once the power came back, but since then, it reboots itself spontaneously every 2-4 hours.  Upon the first restart and after each reboot, mdadm begins a resync, but the resync never finishes (gets to ~60%) before the next spontaneous reboot. All 4 partitions are active in the array (UUUU).  Doing mdadm -E on each drive partition does not turn up anything wrong with the individual disks.

Any idea on how to stop the reboots?

---

### Post by lovinglinux on 2009-05-19
You should check your hardware. It is possible that you also had a power surge and damaged your motherboard or something else.

I was experiencing spontaneous reboots with my old motherboard for a while, until I discovered a melted component.

---


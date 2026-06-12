---
title: "slow boot (I think it is udev)"
date: 2009-03-03
forum: General Help
---

### Post by andyklaj on 2009-03-03
Hi all

My computer is really slow to boot

this is part of the boot log
[   13.602577] kjournald starting.  Commit interval 5 seconds
[   13.602585] EXT3-fs: mounted filesystem with ordered data mode.
[  142.613462] udevd version 124 started
[  143.102617] iTCO_vendor_support: vendor-support=0

It looks like udev is taking its time to load. am i right? If so how can i fix it?
thanks

---

### Post by vincencollins on 2009-06-24
I am having similar problems.

> [ 21.571926] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 21.572018] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 21.605652] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[ 21.653397] **udev: renamed network interface wlan0 to eth1**
[ 559.321397] lp: driver loaded but no devices found
[ 559.419844] apm: BIOS not found.
[ 559.548999] Adding 2048276k swap on /dev/sda2. Priority:-1 extents:1 across:2048276k
[ 560.089007] EXT3 FS on sda3, internal journal 

Does anyone know what I need to change in the rules to resolve this problem?

---

### Post by vincencollins on 2009-06-27
Try this out - [https://answers.launchpad.net/ubuntu/+question/75240](https://answers.launchpad.net/ubuntu/+question/75240)

---


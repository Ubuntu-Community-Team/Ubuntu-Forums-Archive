---
title: "device-mapper errors"
date: 2005-12-21
forum: General Help
---

### Post by skridsko on 2005-12-21
My newly compiled kernel (vanilla 2.6.14) produced many of these errors on boot-up:

device-mapper: dm-linear: Device lookup failed
device-mapper: error adding target to table

I'm using LVM2 but not EVMS. Weird thing is all my partitions (normal and LVM) mounted correctly. Any idea how I might get rid of these errors? Thanks.

---

### Post by n0fx on 2006-04-12
[QUOTE=skridsko]My newly compiled kernel (vanilla 2.6.14) produced many of these errors on boot-up:

device-mapper: dm-linear: Device lookup failed
device-mapper: error adding target to table

I'm using LVM2 but not EVMS. Weird thing is all my partitions (normal and LVM) mounted correctly. Any idea how I might get rid of these errors? Thanks.[/QUOTE]

I also get these errors using the modified cK patches for the vanilla kernel.  Someone said it might be related to a raid setup but mine seems to work fine (using mdadm with a raid 5 on Serial ATA).

I couldn't figure out how to get rid of them either.  Does anyone know if this error is going to cause any serious problems in the future?  My raid seems to work fine and I also scanned it with fsck2ext.

---


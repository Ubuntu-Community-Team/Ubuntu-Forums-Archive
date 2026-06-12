---
title: "Why sda instead of hda?"
date: 2009-04-01
forum: General Help
---

### Post by Volt9000 on 2009-04-01
Why is it that my hard drives are sda and sdb instead of hda and hdb?
My primary hard drive (sdb) is a SATA, and my secondary hard drive (sda) is an IDE device. Is there a reason Linux decided to assign sda and sdb instead of hda and hdb?

---

### Post by FrankT-Qc on 2009-04-01
Well, in theory, your SATAs would be sd? and your IDE should have been hd? ... How come your IDE is going the sd? way, I don't know !

---

### Post by Iowan on 2009-04-01
I saw an explanation in a similar thread (sure wish I could find it)... it seems like SD is the (new) abbreviation for Storage Device - or something similar.

---

### Post by sisco311 on 2009-04-01
the IDE subsystem in the linux kernel has been functionally replaced by the PATA subsystem which uses the sdX naming convention.

---

### Post by Volt9000 on 2009-04-01
> **sisco311 said:**
> the IDE subsystem in the linux kernel has been functionally replaced by the PATA subsystem which uses the sdX naming convention.

Makes sense. :)

Thanks for your replies, everyone!

---


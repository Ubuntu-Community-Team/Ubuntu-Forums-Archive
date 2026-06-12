---
title: "Hangs at boot"
date: 2012-04-20
forum: Desktop Environments
---

### Post by SBFree on 2012-04-20
I am experiencing hangs at boot. It seems like the system hangs before Grub loads, then I warm reset (crtl-alt-delete) then the machine boots. It has two HD's with several partitions on each drive. One pair of partitions is used as a RAID 1 partition.
Any guides or guidance on debugging boot problems would be appreciated.
Thanks,
Scott

---

### Post by kc1di on 2012-04-20
you might want to try boot repair here's the page:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

I had a similar problem and reinstalling grub2 did the trick.

---

### Post by SBFree on 2012-04-20
Thanks, had already tired that approach. Are you aware of a way to log or view boot activity?
Scott

---


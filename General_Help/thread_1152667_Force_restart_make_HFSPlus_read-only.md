---
title: "Force restart make HFSPlus read-only?"
date: 2009-05-08
forum: General Help
---

### Post by thecheeks on 2009-05-08
Everytime I force restart Ubuntu (happens on multiple versions) my HFS+ drive becomes read only. Journaling has been disabled so I know the drive works in this box, but becomes read-only when I force restart. The only way to fix this is to take the drive out, hook it up to my Macbook, and run Verify and Repair on Disk Utility. 

I heard fsck might do the trick even with HFSPlus support, but it just says

> ** /dev/sdb

Help? Thanks.

Edit: Actually this might have been a combination of several problems. Got it fixed.

---


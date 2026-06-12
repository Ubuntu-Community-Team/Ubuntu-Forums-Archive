---
title: "UUID fstab and upgrading to Jaunty"
date: 2009-04-23
forum: General Help
---

### Post by rativid on 2009-04-23
Hi everyone.
I’m runing Intrepid and still using something like /dev/sda# in fstab as device name. Have I chance to get a problem with it when I will try to upgrade system to Jaunty? Should I change device names in fstab to UUID now?
Thanks in advice.

---

### Post by Tim Sharitt on 2009-04-23
I see no problem with leaving the fstab entry as /dev/sda#, unless you are adding or removing partitions (which still may not cause a problem). You should be fine with what you've got. :)

---


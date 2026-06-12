---
title: "Lost menu in recovery mode"
date: 2009-07-05
forum: Desktop Environments
---

### Post by dentaku65 on 2009-07-05
Hi all,
I have an issue about the recovery mode; this is what happens.
I upgraded through update-manager -d a laptop from Hardy -> Intrepid -> Jaunty (all the steps); now if I choose the recovery mode at grub boot the system goes directly to the root prompt without asking for password and, above all, without the recovery menu (xfix, continue etc..) as I expect to get.... any idea in which way I can recover it?

---

### Post by dentaku65 on 2009-07-07
Bump!

---

### Post by dentaku65 on 2009-07-08
Ok. Fixed by myself.
```
sudo apt-get install friendly-recovery
```
do the job.

---


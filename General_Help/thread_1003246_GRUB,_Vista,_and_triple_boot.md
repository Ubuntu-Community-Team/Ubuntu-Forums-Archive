---
title: "GRUB, Vista, and triple boot"
date: 2008-12-05
forum: General Help
---

### Post by sunjayc_99 on 2008-12-05
I'm trying to triple boot Vista, XP, and Ubuntu, spread out across two separate hard drives. I've got Vista and XP installed on the laptop hard drive, and Ubuntu 8.04 on an external drive.

What I'm trying to do is get it so that if I just boot the laptop normally, it goes straight to Vista, and if I select the external hard drive for manually selecting which device to boot from, then I should get a GRUB menu with Ubuntu, Vista, and XP.

The problem is this: after I get everything working (boots to Vista from default, etc.), I use the GRUB menu to boot to XP. The next time I turn my laptop on, it goes straight to XP instead of Vista. I think this is because of the "makeactive" setting in the GRUB boot, but I'm not sure. Is there any way to make this work?

---

### Post by TeXtonyx on 2008-12-05
Remove makeactive and see if it works.

---

### Post by sunjayc_99 on 2008-12-06
I think I've tried that; it didn't boot into XP.
I'll try it again though.

EDIT: Removing the makeactive worked, and it didn't mess up the boot. I must have done something wrong the last time I tried it. Thanks for the tip!

---


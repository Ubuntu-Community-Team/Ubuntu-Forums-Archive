---
title: "GRUB is removed, error 15"
date: 2008-06-18
forum: Desktop Environments
---

### Post by ali98ir on 2008-06-18
Hello all,

I was going to install debian on my laptop which had ubuntu and winxp. the boot order was ubuntu first then winxp. at the beginning of installation of debian i had to set up partitions. by mistake i erased the linux partion. then debian could not find the root partion and didn't continue to install. the bad thing is that when i restarted the laptop, it cannot find the GRUB and does not boot the system. the error message is:

GRUB loading, please wait...
error 15

Can someone help me please to restor the winxp?

Thanks,
Ali

---

### Post by JC Cheloven on 2008-06-18
From the recovery console of the xp instalation cd, type:
fixmbr

This should reinstall the windows bootloader

---

### Post by rune0077 on 2008-06-18
Here: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

Do what it says in the second post, rather than the first (it's faster and safer).

---


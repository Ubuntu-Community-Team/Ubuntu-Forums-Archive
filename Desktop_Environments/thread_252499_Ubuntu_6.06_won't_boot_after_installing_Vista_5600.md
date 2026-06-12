---
title: "Ubuntu 6.06 won't boot after installing Vista 5600"
date: 2006-09-06
forum: Desktop Environments
---

### Post by kinghajj on 2006-09-06
First, some information on my pre-Vista setup:

I had Ubuntu installed on an SATA drive in the slave slot. I also had four IDE drives (two hard drives, two DVD drives.) I used GRUB to triple-boot between Ubuntu on the SATA, Windows on the IDE0 slave, and another OS on the ID0 master.

To install Vista, I took out the IDE hard drives and installed another. I then installed vista on that drive without problem. After tiring of Vista's crap, I uninstalled that hard drive and put back the original two in the same positions as before.

When I try to boot Ubuntu, however, I get an error (after a quick look at the splash screen) that basically says that it can't read from /dev/sda1, which is what my SATA drive is.

This problem may not be related at all to Vista--I had installed some Ubuntu updates just before shutting down to install Vista.

All help is greatly appreciated. Thank you.

---

### Post by EnderTheThird on 2006-09-06
> **kinghajj said:**
> When I try to boot Ubuntu, however, I get an error (after a quick look at the splash screen) that basically says that it can't read from /dev/sda1, which is what my SATA drive is.

You can manually edit your grub entry by pressing "e" (I think) while it's at the grub menu during boot.  Then select the top entry that starts with "kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 [...]" and press "e" again to edit the entry.  Now, in my case, my SATA drive SHOULD be sdb, but for whatever reason, Ubuntu sees it as sdc, so I have to manually edit my grub menu.lst file whenever I install a new kernel.  I wonder if the same thing is happening to you now, even if it was working fine as /dev/sda1 before.  Try change the "a" to a "b" or "c" and see if it will boot up.  Let me know.

---

### Post by Uncle Spellbinder on 2006-09-07
Check this out:

[***_Ubuntu / Vista dual boot and keeping previous Ubuntu_***](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)

---


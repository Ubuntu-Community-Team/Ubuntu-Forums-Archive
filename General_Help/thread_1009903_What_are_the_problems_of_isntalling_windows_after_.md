---
title: "What are the problems of isntalling windows after ubuntu?"
date: 2008-12-13
forum: General Help
---

### Post by mahela007 on 2008-12-13
Are there any problems/ complications when windows is installed AFTER ubuntu? If so what are the solutions?

---

### Post by overdrank on 2008-12-13
> **mahela007 said:**
> Are there any problems/ complications when windows is installed AFTER ubuntu? If so what are the solutions?

Hi, having a partition for windows install and then recovering the grub
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by TeXtonyx on 2008-12-13
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4)

"To insult to injury, XP detects the Linux partition as an active 
system partition and won't install unless it marks this partition as 
inactive." If you want to boot from Linux later, it needs to be active.
 
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

"At this point, Vista can't install to this space, so we need to
make a new partition and mark it active so that Vista can use 
it. Press SHIFT + F10 to launch a command window, then 
type in DISKPART and press Enter."

Seems like a good idea to install Vista Service Pack 1, SP1,
before restoring grub since SP1 will conflict with grub in the 
MBR. That might be true of Windows XP SP3, I'm not sure.

---


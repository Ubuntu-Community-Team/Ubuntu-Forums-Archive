---
title: "help with a partition"
date: 2009-06-13
forum: General Help
---

### Post by Metz90 on 2009-06-13
hi, im a new member of this forum...i have some questions about the partitions of hd,
i have a one hd where there is installed ubuntu...i would do a partition where can i install window xp and when i start my pc i can choose the operating system, thx a lot,

Sorry for my bad eng..im italian

---

### Post by howefield on 2009-06-13
> **Metz90 said:**
> hi, im a new member of this forum...i have some questions about the partitions of hd,
i have a one hd where there is installed ubuntu...i would do a partition where can i install window xp and when i start my pc i can choose the operating system, thx a lot,

Sorry for my bad eng..im italian

It is usually easier to install xp first and then Ubuntu. Doing it the other way round means you will need to reinstall grub as the windows installer will overwrite it with its own bootloader. 

Search google for "install xp after Ubuntu" and you will get numerous tutorials on how to sort this, eg

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by Magnificence on 2009-06-13
While running Ubuntu, you can't edit the partitions of the HD were it is running.
If you need to edit those partitions you can startup a Ubuntu Live CD. It has GParted already on it. It's under the administration menu, called "Partition Editor". From there you can edit all the partitions you want.
Keep in mind that if you going to edit partitions, it's recommended to do some backups first.

---


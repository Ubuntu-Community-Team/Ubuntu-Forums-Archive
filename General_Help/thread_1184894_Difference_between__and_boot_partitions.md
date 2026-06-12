---
title: "Difference between / and /boot partitions"
date: 2009-06-11
forum: General Help
---

### Post by lindsay7 on 2009-06-11
My computers are set up with a / partition and a /home partition. What is a /boot partition used for or why would you use one?

---

### Post by jonobr on 2009-06-11
Thats a hugely important directory.
It contains important stuff like the kernel, so I would not do anything to that directory

---

### Post by bodhi.zazen on 2009-06-11
One uses a separate boot when grub can not directly boot if /boot is on /

Examples include LVM, RAID, encryption and (for older versions of Ubuntu) ext4 filesystems. With those configurations , configuration of / is in initrd and the system needs to be able to read initrd to boot, thus a separate /boot.

---

### Post by mcduck on 2009-06-11
> **lindsay7 said:**
> My computers are set up with a / partition and a /home partition. What is a /boot partition used for or why would you use one?

/boot is where all the files required to boot the system are located.

In the past this was sometimes necessary when the computer's BIOS wasn't able to handle large hard drive partitions. It helped to put all boot stuff in a small partition to get the system up and running and then let Linux handle the larger main partition.

These days you are unlikely to find a system that couldn't handle a decent-sized partition so the only reasons to use a separate boot partition are special purposes like RAID setups and encrypted systems. On normal setups a separate /boot will only make things more complicated so you wouldn't want to use one unless you really need it.

edit. once again too slow for these forums.. :D

---

### Post by lindsay7 on 2009-06-11
Thank you that clears this up for me.

---

### Post by Chemical Imbalance on 2009-06-11
Having a separate /boot partition is recommended, at least by me ;).

It is necessary to boot your machine.  It holds your kernel images and grub directory and so forth.

I recommend you use ext3 filesystem on it even if you use ext4 on your / partition because ext4 is relatively new and less tested than ext3.

250 mb should be plenty space for /boot, though more wouldn't hurt.

---

### Post by ajgreeny on 2009-06-11
I think one other possible advantage of a separate /boot partition could be seen if you removed ubuntu by deleting the main / partition, which usually also removes the grub configuration files including menu.lst.

In a separate /boot partition you would still have grub and the menu.lst file and so should still be able to boot to windows from that grub, though not, of course, to ubuntu, which would be non-existent.  If you then installed another linux or version of ubuntu with a separate /boot partition again, the new one would overwrite the old one and once again you should be able to boot to both windows and the new linux.

This is, I hasten to add, all theoretical, as I honestly think it is simplest to just use the MBR of the windows, (first) disk for grub and not bother with a separate /boot partition.

---


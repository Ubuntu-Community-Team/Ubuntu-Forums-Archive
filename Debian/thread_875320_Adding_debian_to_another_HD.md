---
title: "Adding debian to another HD"
date: 2008-07-30
forum: Debian
---

### Post by SteveNorman on 2008-07-30
I have ubuntu and xp on one hard drive now. I just installed another HD and want to put debian on it. Should I unplug the other HD first, then add it to grub later, or is it okay to install on hd # 2 and let debians grub overwrite ubuntus?

---

### Post by logos34 on 2008-07-31
either way...letting it overwrite ubuntu grub is easier (it will pick up all the other OS entries), but if you ever remove debian make sure to reinstall ubuntu grub pointing to latter's partition

---

### Post by SteveNorman on 2008-07-31
Thanks,,Ill post the results for posterity

---

### Post by rsambuca on 2008-07-31
I would personally have it install grub to it's own hard drive.  Then add the chainloading entry to your original grub so that you never have to manually update your grub entries after kernel updates.

---

### Post by logos34 on 2008-07-31
> **rsambuca said:**
> Then add the chainloading entry to your original grub so that you never have to manually update your grub entries after kernel updates.

+1.  forgot that part:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---


---
title: "Help changing default OS in boot"
date: 2005-03-30
forum: Desktop Environments
---

### Post by Diego F. on 2005-03-30
Hi. I need to change the default OS in the boot. I'm not the only one that use this computer and I need Windows to be the default one. I haven't find a tool to change that as in other distros. How can I do it?

---

### Post by tonym on 2005-03-30
Edit /boot/grub/menu.lst

I suggest that you move the Windows entries prior to the automatically generated Linux entries.  Check that the "default" entry refers to your Windows entry.

---

### Post by Diego F. on 2005-03-30
Thank you! I just changed the Windows entry to the first position and that's enough.

---


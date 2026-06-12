---
title: "ubuntu startup"
date: 2010-05-29
forum: Desktop Environments
---

### Post by sundays211 on 2010-05-29
Is there a way to change Ubuntu startup back to the way it was in 8.04 where it displayed every process in text. I know that there's no particular point, but I just prefer it that way.

---

### Post by Barafu Albino Cheetah on 2010-05-29
Easily. Edit /etc/default/grub and in the string GRUB_CMDLINE_LINUX_DEFAULT= remove parameters splash and quiet. After that run update-grub.

---


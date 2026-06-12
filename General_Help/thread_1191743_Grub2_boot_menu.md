---
title: "Grub2 boot menu"
date: 2009-06-19
forum: General Help
---

### Post by exXP on 2009-06-19
Following yesterdays update, I now have about 12 entries in my boot menu.  In Menu.lst I could limit how many previous entries were retained.  Does anyone know how to do this with Grub2?  Otherwise in a few months my boot menu will be several pages long!
exXP (and not going back)

---

### Post by mcduck on 2009-06-19
You could just uninstall the old kernel packages with Synaptic/apt-get. There's no reason to have more than one older kernel available anyway. ;)

---

### Post by cariboo on 2009-06-19
Removing the extra kernels, does not yet remove them from /boot/grub/grub.cfg. Grub2 is very much in a state of flux, as it will be the default in Karmic. There are several grub2 threads in [Karmic Testing & Discussion]("http://ubuntuforums.org/forumdisplay.php?f=359"), it might be an idea to look at them.

---

### Post by exXP on 2009-06-20
I assume that anyone who is dual or triple booting has this problem. Initially my second OS was No.4 in the boot menu, now it's No.10!  However I can't edit grub.cfg even as root. Hopefully this will be resolved before Karmic is released.
exXP (and not going back)

---


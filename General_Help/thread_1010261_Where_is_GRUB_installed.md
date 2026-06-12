---
title: "Where is GRUB installed?"
date: 2008-12-13
forum: General Help
---

### Post by mojo_man on 2008-12-13
Hi,

I have two physical hard drives. One with ubuntu and one with WINDOWS XP. GRUB is the bootloader. I want to know on which hard drive GRUB was installed. How can I do this?

Thanks,

---

### Post by caljohnsmith on 2008-12-13
Try doing the following command on each drive:
```
sudo xxd -l 2 -p /dev/[COLOR="Blue"]sda[/COLOR]
```
If the command returns "eb48", then that drive has Grub in the MBR (Master Boot Record), and if it returns "33c0", then that drive has a Windows MBR.

---


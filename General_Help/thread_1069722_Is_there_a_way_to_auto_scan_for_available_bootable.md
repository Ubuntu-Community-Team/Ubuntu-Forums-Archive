---
title: "Is there a way to auto scan for available bootable OSs in Grub?"
date: 2009-02-14
forum: General Help
---

### Post by d58e7 on 2009-02-14
Is there a way to auto scan for available bootable OSs in Grub? I know you can manually add in OSes to the menu.lst but is there a way to have grub do it automatically?

---

### Post by caljohnsmith on 2009-02-14
> **d58e7 said:**
> Is there a way to auto scan for available bootable OSs in Grub? I know you can manually add in OSes to the menu.lst but is there a way to have grub do it automatically?
To my knowledge, unfortunately no. If you need help booting any of your OSes though, let me know, and I'll try to help.

---

### Post by fragos on 2009-02-14
The only place I see something like this done is when installing from a Live CD to dual boot. The menu.lst file in the new installed boot partition will contain OS's installed in other partitions. Using Synaptic to remove old Linux images will also update the menu.lst file. Other than that I couldn't find any way to scan for OS's and build a new menu.lst file. That of course doesn't mean the method doesn't exist just that I couldn't find it.

---


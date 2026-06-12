---
title: "Cannot Access My Computer!"
date: 2008-12-31
forum: General Help
---

### Post by bengreer on 2008-12-31
I tried to uninstall ubuntu that was dual booted with windowsXP but now I can't access my computer. I removed all partitions except for my windows partition. Now when I turn my computer on I get this:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 22


What do I do?

---

### Post by Elfy on 2008-12-31
Reinstall the windows mbr with either your windows disc or supergrub

---

### Post by cdtech on 2008-12-31
You have to use your Windows install disk to repair the MBR of your Windows install. You removed Linux but not the bootloader......

---

### Post by bengreer on 2008-12-31
I don't have my windows xp install disk!  Is there anyway I can fix it using the ubuntu live cd!

---

### Post by dexter on 2008-12-31
You could reinstall grub using the live-cd and add an entry for windows.

This might be usefull: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by bumanie on 2008-12-31
Super grub disk can re-write a windows-like mbr - get the .iso [here]("http://forjamari.linex.org/frs/?group_id=61&release_id=664#664"). It is a live cd.

---


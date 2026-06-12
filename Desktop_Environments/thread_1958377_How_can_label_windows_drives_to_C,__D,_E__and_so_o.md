---
title: "How can label windows drives to C:/,  D:/, E:/  and so on ?"
date: 2012-04-14
forum: Desktop Environments
---

### Post by curiousapprentice on 2012-04-14
:???::-k:roll::-\"#-oI don't like the way the drives are identified on Ubuntu 11.10. I dont like the numbering approach. Rather I want to rename all my disk drives to something easier like C:/, D:/, E:/ etc.

How can I do that using Gparted ? How I can make a backup of all my Ubuntu softwares ? I dont own any external hdd. Can I backup my data on DVDs? How that can be done using Deja Dup ?

---

### Post by 3Miro on 2012-04-14
You can use Gparted to give each drive a label. I don't think you can  use characters like : and \, but you can use WinC or UbuntuA or just C and D. Ubuntu uses numbers only when no labels are available.

---

### Post by lolpenguin on 2012-04-14
AFAIK not possible under Unix-like systems.However Gobo Linux has a filesystem layout similar to Windows.

---

### Post by sudodus on 2012-04-14
> **3Miro said:**
> You can use Gparted to give each drive a label. I don't think you can  use characters like : and \, but you can use WinC or UbuntuA or just C and D. Ubuntu uses numbers only when no labels are available.
+1
Use labels! If you dual boot with Windows, or have external drives, that you attach to different computers, it is very good to have explanatory labels (C, D etc is possible, but it is better with WinC, hdd-data, usb-data, backup etc). Windows can also read and write the labels of FAT and NTFS drives.

---

### Post by zombifier25 on 2012-04-15
> **lolpenguin said:**
> AFAIK not possible under Unix-like systems.However Gobo Linux has a filesystem layout similar to Windows.
Actually, the OP is probably asking to rename the incomprehensible numbers assigned to partitions to easier to remember names like C, D...

---


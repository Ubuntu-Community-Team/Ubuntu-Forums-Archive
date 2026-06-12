---
title: "Ubuntu install under Windows XP question"
date: 2009-03-31
forum: General Help
---

### Post by DefConNegative5 on 2009-03-31
I installed Ubuntu alongside Windows XP. It works really well, I can boot to either with no problems. 

I see the Ubuntu directory in Windows XP, but I can't browse the folders there's just one lump 6 GB file. Is there any way to set it up so I can browse my Ubuntu folders from XP?

Under 'host' in ubuntu, I can see my windows xp directories and even browse them. Is there any way to block this?

---

### Post by James_Lochhead on 2009-03-31
Is this a Wubi install or a normal one?

---

### Post by DefConNegative5 on 2009-03-31
Its a Normal install.

---

### Post by James_Lochhead on 2009-03-31
The problem is that Ubuntu has the correct drivers to read a Windows FAT/NTFS parition, however Windows does not have the drivers to read an ext2/ext3/ext4 partition by default.

You need to download and install the correct drivers on Windows.

---

### Post by James_Lochhead on 2009-03-31
[http://www.go2linux.org/node/51](http://www.go2linux.org/node/51)

Take a look. Be careful though, make sure Ubuntu gets unmounted properly.

---


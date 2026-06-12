---
title: "Disable TRASH completely"
date: 2005-07-11
forum: Desktop Environments
---

### Post by ubuntp on 2005-07-11
How do i disable the trashcan? I especially dislike that on external usb devices a .username-trash folder is created. That's the same thing that drove me crazy in XP ;)

---

### Post by tbasten on 2005-07-12
rm -rf /location/of/file             if it says no permissions to do so just type

sudo rm -rf /location/of/file

CATION :: be sure to make sure you have the correct location in because if you make a mistake you could do some damage to your machine and completely remove the file you request.

---

### Post by ubuntp on 2005-07-12
Yeah, but it will still come back next time!

---

### Post by zubziro on 2005-09-22
Anyone else plz... how to disable Trash completely  ???

---

### Post by johnpetrusa on 2008-01-30
Hi, 

You need to run Gnome Conf Edit, just pres alt-f2 and run: gconf-editor

Go to: apps/nautilus/preferences/enable_delete

And check this option, it's all :)

Keep in mind that this will disable the trash in ALL your drivers.

---


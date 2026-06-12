---
title: "Desktop icons are gone and file manager wont open"
date: 2015-02-16
forum: Desktop Environments
---

### Post by petegregar on 2015-02-16
When I open the file manager the desktop icons/files flash for a second then disappear.
File manager closes.

Anyone see this before?
Suggestions for fixing it

---

### Post by mc4man on 2015-02-17
In some releases of Ubuntu a zero byte file with an ext. & python-nautilus installed could cause a crash
Ck in terminal - 
ls -l 
look for files with an extension &  0 size

---

### Post by petegregar on 2015-02-17
Not sure what that means.
Should I reinstall something?

---

### Post by v3.xx on 2015-02-17
Do you have python-nautilus installed?  In terminal:
```
apt-cache policy python-nautilus
```
If nautilus is your file manager, open it in terminal and look for errors.
```
nautilus
```
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---


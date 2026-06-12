---
title: "GraphicsCard Problem"
date: 2007-11-01
forum: Desktop Environments
---

### Post by hey2222 on 2007-11-01
Whenever I'm at the restrictive drive manager and enable my NVIDIA graphics driver I run into problems. It asks for the Ubuntu 7.10 CD but when I pop it in and press okay it just ask for the cd again every time i press it.

---

### Post by taurus on 2007-11-01
You don't have to use the CD if you don't want.  Just edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of the first line (usually the first line) that has _cdrom_ in it to comment it out.  Save it and run

```
sudo apt-get update
```
Now, it will never ask  you to insert the installer CD again.

---


---
title: "Time Zone"
date: 2009-04-16
forum: General Help
---

### Post by krispy63 on 2009-04-16
I am brand new to Ubuntu being an xp user for years I am totally overwhelmed.  I cannot even figure out how to find my correct time zone it all looks so foreign to me can anyone help?  I live in Lansing Michigan

---

### Post by justc001 on 2009-04-16
In Linux timezones are stored in /usr/share/zoneinfo. Use:
```
ls /usr/share/zoneinfo
```
in a terminal to see a list of them. When you find the one you're in create a symbol link to it at /etc/localtime like this:
```
sudo ln -sf /usr/share/zoneinfo/*yourzone* /etc/localtime
```
Where *yourzone* is the timezone you're in.

---

### Post by jmszr on 2009-04-16
krispy63,

To do it graphically: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---


---
title: "OWFS works for non root in 10.04 but not 10.10"
date: 2011-01-18
forum: Desktop Environments
---

### Post by linuxonbute on 2011-01-18
I have owfs installed on my laptop which is running 10.04 and can access my Miaxim 

ibutton without being root but on my desktop PC which is on 10.10 the same setup does not 

work unless I run it as root.

Does anyone know why this is or how it can be fixed?

---

### Post by linuxonbute on 2011-01-31
Well now I cannot access OWFS on my laptop either unless i am root or are in the 'root' group. Does anyone know how to solve this?

---

### Post by linuxonbute on 2011-03-17
Fixed:

cat /etc/udev/rules.d/90-ds2490.rules 

SYSFS{idVendor}=="04fa", SYSFS{idProduct}=="2490", GROUP="ow", MODE="0664"

---


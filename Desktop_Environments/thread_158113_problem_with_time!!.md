---
title: "problem with time!!"
date: 2006-04-10
forum: Desktop Environments
---

### Post by binilbenjamin on 2006-04-10
current time is shown wrong in ubuntu.. i have selected the correct timezone...but my time is different from what is shown in Windows....if i adjust the time in ubuntu , time will be incorrect in windows!!! but both are set to the same time zone....pls help!!!

---

### Post by ronmarley1 on 2006-04-10
Hi binilbenjamin,
Go to a terminal and type ```
sudo gedit /etc/default/rcS
``` Change UTC=yes to UTC=no.  Then save and exit.

---

### Post by binilbenjamin on 2006-04-11
[QUOTE=ronmarley1]Hi binilbenjamin,
Go to a terminal and type ```
sudo gedit /etc/default/rcS
``` Change UTC=yes to UTC=no.  Then save and exit.[/QUOTE]
thanks....th t worked!!! :)

---

### Post by ronmarley1 on 2006-04-11
Glad I could help.  Welcome to Ubuntu!

---


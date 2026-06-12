---
title: "gnome-app-install does not load, how can I fix it ?"
date: 2007-09-08
forum: Desktop Environments
---

### Post by rniella on 2007-09-08
Hello, my gnome-app-install does not load, this happened about a week ago after perfoming some update.. anybody knows how to fix it ??  thanks !

---

### Post by tyggna1 on 2007-09-08
try:

```
dpkg-reconfigure gnome-app-install
```

in the command line/terminal

---

### Post by rniella on 2007-09-08
Thanks ! I tried that as root and got the following response: 

"gnome-app-install está roto o no está totalmente instalado" 

 which in spanish means "gnome-app-install is broken or is not completely installed"..  any other thing I might try ?  I tried reinstalling it from Synaptic but it did not work, it kept telling me that it depended from ubuntu-desktop which in turn could not reinstall because of some problem wth Python.. I lost guys..  thanks !!

---


---
title: "Logging as root user in Kubuntu"
date: 2007-05-27
forum: Desktop Environments
---

### Post by nuktar on 2007-05-27
Logging as root in kubuntu through KDE sets seems impossible to me...  To make this work first  terminal  sudo passwd , then  edit  /etc/kde3/kdm/kdm.options, find  AllowRootLogin (case sensitive..) and set to true. Save it...
>>IMPORTANT<< The terminal must be ran as root @ 
Exit and login again...

---

### Post by loathsome on 2007-05-27
Ooor you could just do
```
sudo su
```

---

### Post by RedSquirrel on 2007-05-27
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2007-05-27
Alt-F2 ```
kdesu konqueror
``` lets you essentially be root.

---


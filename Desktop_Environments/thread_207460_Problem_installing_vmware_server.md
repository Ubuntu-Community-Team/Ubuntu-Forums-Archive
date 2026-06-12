---
title: "Problem installing vmware server"
date: 2006-07-01
forum: Desktop Environments
---

### Post by Dearhell on 2006-07-01
> Unable to find any instance of the super-server "inetd" or "xinetd".  It is
possible that you do not have one of these packages installed on this machine.
Please install "inetd" or "xinetd".


This is the error that it's displayed

---

### Post by reacocard on 2006-07-01
seems to be faily self-explanatory. VMWare needs one of those packages but neither is installed. solution: install one. do a

```
sudo apt-get install xinetd
```

then try the installer again.

---

### Post by chalex on 2006-07-01
Right, install xinetd.  I wrote a post about this, perhaps it might help you: [http://yalb.net/wp/?p=60](http://yalb.net/wp/?p=60)

---

### Post by Dearhell on 2006-07-02
After installing xinetd with:

> sudo apt-get install xinetd

It works right

Thx

---


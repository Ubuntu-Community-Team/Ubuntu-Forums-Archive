---
title: "update manager error"
date: 2009-04-15
forum: General Help
---

### Post by panamabill on 2009-04-15
I was updating packages when this error occurred: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Tried running it in terminal but got this message: 
dpkg: requested operation requires superuser privilege

I'm a newbie so please go slow!!

---

### Post by taurus on 2009-04-15
You need to include sudo in front of the command.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by panamabill on 2009-04-17
thanks taurus it worked like a snap. Plus it gave some experience with terminal.

---


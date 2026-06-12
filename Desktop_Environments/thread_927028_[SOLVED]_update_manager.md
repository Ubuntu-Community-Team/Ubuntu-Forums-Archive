---
title: "[SOLVED] update manager"
date: 2008-09-22
forum: Desktop Environments
---

### Post by ammikulka on 2008-09-22
when trying to update i get this error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


try the dpkg in terminal get an errer saying cannot do because i am not a "superuser" 

also may be related to this:
when trying to open synaptic package manager i can't download or install anything because i dont have "administrator privileges"

---

### Post by dualpretop on 2008-09-22
Terminal:
sudo synaptic

---

### Post by ammikulka on 2008-09-22
> **dualpretop said:**
> Terminal:
sudo synaptic

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

got this error

---

### Post by kostkon on 2008-09-22
> **ammikulka said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

got this error
You have to add *sudo* before it, i.e.:
```
sudo dpkg --configure -a
```
it will ask for a password, give yours.

---

### Post by kostkon on 2008-09-22
For more information about *sudo*, see [here]("https://help.ubuntu.com/community/RootSudo").

---


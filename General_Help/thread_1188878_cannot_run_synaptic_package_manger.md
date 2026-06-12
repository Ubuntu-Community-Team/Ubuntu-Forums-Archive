---
title: "cannot run synaptic package manger"
date: 2009-06-16
forum: General Help
---

### Post by linuxn00b3355 on 2009-06-16
Synaptic package manger wont run i get this message 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 

im fairly new to Linux should i reinstall ubuntu

---

### Post by SuperSonic4 on 2009-06-16
Do what it suggest you do but preface it with sudo to run as root. You will need to enter your user password which **will not** be displayed as it is typed but is being inputted fine.

```
sudo dpkg --configure -a
```

---

### Post by linuxn00b3355 on 2009-06-16
> **SuperSonic4 said:**
> Do what it suggest you do but preface it with sudo to run as root. You will need to enter your user password which **will not** be displayed as it is typed but is being inputted fine.

```
sudo dpkg --configure -a
```

and how do i do that

---

### Post by SuperSonic4 on 2009-06-16
Copy and paste the stuff in the code tags into a terminal. The terminal can be found under System --> Administration --> Terminal

---

### Post by linuxn00b3355 on 2009-06-16
thank yo so much :D

---


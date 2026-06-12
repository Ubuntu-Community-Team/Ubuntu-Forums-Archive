---
title: "Does anyone know how to be root through wubi ?"
date: 2009-04-14
forum: General Help
---

### Post by rwijaya on 2009-04-14
Hey,

I installed ubuntu through wubi ([http://wubi-installer.org/](http://wubi-installer.org/)), I logged in with the account that I made on the installation

and

I would like to run iptables -L then this message pops up:

iptables v1.4.0: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.

I need to be the root.
Does anyone know how to be root through wubi ?

Thanks!

---

### Post by Tim Sharitt on 2009-04-14
The root account is locked by default on Ubuntu. To gain root privileges, use sudo.

```
sudo command
``` 

To enter a rood shell, use
```
sudo -i
```

More info: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bakon Jarser on 2009-04-14
The fact that it is a wubi installation doesn't really mean anything.  It is a regular Ubuntu installation that happens to be located inside of a windows partition.  Everything should still work the same.

Like the previous poster mentioned, use sudo for root privaleges unless you are trying to run a gui program as root.  Then you use gksudo instead of sudo.

---


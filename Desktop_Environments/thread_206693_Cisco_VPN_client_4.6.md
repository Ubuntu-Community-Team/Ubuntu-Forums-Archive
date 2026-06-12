---
title: "Cisco VPN client 4.6"
date: 2006-06-30
forum: Desktop Environments
---

### Post by ripgut on 2006-06-30
I need some help guys, after installing this app, and confirming my settings:

```
Directory containing linux kernel source code []/etc/init.d

* Binaries will be installed in "/lib/modules/2.6.15-25-386/build".
* Modules will be installed in "/lib/modules/2.6.15-25-386/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/etc/init.d" will be used to build the module.

Is the above correct [y] y
```



then it spits this out:

```
Create directory "/lib/modules/2.6.15-25-386/build".

Making module
./driver_build.sh: line 45: make: command not found
Failed to make module "cisco_ipsec.ko".

```

Any ideas?

---

### Post by raptros-v76 on 2006-06-30
sudo aptitude install build-essential, then do your thing

---

### Post by ripgut on 2006-06-30
[QUOTE=raptros-v76]sudo aptitude install build-essential, then do your thing[/QUOTE]


Nope that didn't work

---


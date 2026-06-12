---
title: "VM Ware bridged network?"
date: 2006-09-16
forum: Desktop Environments
---

### Post by ccheaton on 2006-09-16
During the setup of VMWare, it asked which network connection I wanted to make a bridge between: eth0 or eth1.  I chose eth0, which is the LAN connection, but I would like to change it to eth1 so that my virtual machine will connect through bridged wireless.  However, I cannot figure out how to make that change now.  

Where to I change the option so that it bridges the other network?

---

### Post by mouchyn on 2007-04-30
sudo ./vmware-config.pl

---

### Post by airtonix on 2007-05-01
yep you have to reconfigure it....easiest and proly the only way.

---


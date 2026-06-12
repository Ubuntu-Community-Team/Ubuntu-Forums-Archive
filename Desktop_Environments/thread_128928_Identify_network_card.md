---
title: "Identify network card"
date: 2006-02-12
forum: Desktop Environments
---

### Post by Arinux on 2006-02-12
Hey all,
I got a system in which i have two lan cards, one is on board and the other is through pci.i see two cards detetcted one as eth0 and other as eth1.So how do i detect which card is onboard and which card is pci.as i connect to net through one and one for the home netwoking.secondly whats are the basic networking comands like ping , see ip , subnet etc.
Ari

---

### Post by Ramses de Norre on 2006-02-12
```
lshw
```
Then go search for the ethernet controllers, one will be under *pci other one under *network.
The line "logical name:" displays then their name (like eth0, eth1 etc.).

Which commands do you need? ping is the same as in dos, so as netstat and nslookup. (or were they different in dos? that's been a while).

---


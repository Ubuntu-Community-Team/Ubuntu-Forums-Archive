---
title: "Activating Network Card in Dell Dimension 8300"
date: 2011-02-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kalyan-sg on 2011-02-27
I have a Dell Dimension 8300. I switched to Ubuntu 10.10 and it ran perfectly.

Of late I switched to Edubuntu...the OS loaded OK but I can't access the network card...so I have no network and no Internet.

Any idea how to activate my network card! Thanks in advance!

---

### Post by anglican on 2011-03-01
> **Kalyan-sg said:**
> I have a Dell Dimension 8300. I switched to Ubuntu 10.10 and it ran perfectly.

Of late I switched to Edubuntu...the OS loaded OK but I can't access the network card...so I have no network and no Internet.

Any idea how to activate my network card! Thanks in advance!It helps to know which nic we're talking about. Could you post the output from:
```
sudo lspci | grep Ethernet
sudo ethtool eth0
ifconfig eth0

```H

---

### Post by Kalyan-sg on 2011-03-01
> **anglican said:**
> It helps to know which nic we're talking about. Could you post the output from:
```
sudo lspci | grep Ethernet
sudo ethtool eth0
ifconfig eth0

```H
[COLOR=Red]**Solved:**[/COLOR]

**Typed in Terminal:**
gksudo gedit /etc/network/interfaces

to edit the interfaces file

**Inserted the following in the interfaces file:**

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

Originally it had static ip when I installed Edubuntu

Thanks

---


---
title: "Setting Ubuntu System as a router"
date: 2008-04-08
forum: Dell  Ubuntu Support
---

### Post by atulgoyal52 on 2008-04-08
Hi.. I have Inspiron 1420. I need to set up a router on the system running ubuntu 7.04. I go through lot of links but none seem to help me. What i need is eth1 (wireless) as an internal LAN interface and eth0(wired) as the interface to internet. But I myself is in Internal LAN with connecting Router address 10.X.X.X to outer world.
Please Help me..

---

### Post by gwbennett on 2008-04-08
```
sudo apt-get install firestarter
```

People are gonna tell you to use iptables and postrouting in a terminal window. If you're a professional UNIX sysadmin, that's great. But if you were you wouldn't be asking here.

So just install firestarter, hook up the network cards as intended, launch it and go through the basic setup wizard and tell it which interface is which.

---

### Post by atulgoyal52 on 2008-04-09
I need to use iptables also. So firestarter will not do the purpose.

---


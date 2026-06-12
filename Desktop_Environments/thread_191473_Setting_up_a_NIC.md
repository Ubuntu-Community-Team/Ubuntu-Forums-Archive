---
title: "Setting up a NIC"
date: 2006-06-07
forum: Desktop Environments
---

### Post by endfx on 2006-06-07
First off, I don't have any desktop installed, only ubuntu server, so I only have the command line.

I have installed another NIC in my machine. Ubuntu detects it just fine and if I modify /etc/network/interfaces and then restart the computer my network connection is setup just fine.

My question is, how to I negotiate an IP using DHCP without having to restart my computer.
Lets say I modify /etc/network/interfaces and want to restart the networking system so my changes to 'interfaces' take effect.

How would I do this?
I have run '/etc/init.d/networking restart' and it seems to run just fine (gives the OK message) but my changes have not taken effect.

So basically, how do I restart the networking system to negotiate an IP (using dhcp here) using the command line.

Thanks.

---

### Post by Ramses de Norre on 2006-06-07
```
sudo ifdown eth?
sudo ifup eth?
```

---

### Post by endfx on 2006-06-07
Thanks, that did the trick.

---


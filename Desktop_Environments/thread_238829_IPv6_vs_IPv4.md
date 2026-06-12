---
title: "IPv6 vs IPv4"
date: 2006-08-18
forum: Desktop Environments
---

### Post by bgrabbe on 2006-08-18
I'm new to installing Ubuntu, and relatively new to Linux. I have the desktop cd installed and my network card seems to be only set to use IPv6. 
Is there something I need to do during the install or after to enable IPv4 ? IPPv6 isn't supported on my network. 
Thanks

---

### Post by stdragon on 2006-08-20
IPv4 is enabled by default, but maybe it's not activated on your card. Have you gone into the network settings and set up your ip address (or dhcp server)?

---

### Post by bgrabbe on 2006-08-21
I have manually set an ip address in the nbetwork settings, but I still can';t see any network. I've tried the network cable and port on another Windows machine and it's fine. 
The nic was working with Windows installed on this hardware before I wiped it and installed Ubuntu, is there some particular setting up that needs to be done ? 
It is recognized as a 3com 3c905 card. 
Thanks

---

### Post by stdragon on 2006-08-21
On the command line, try typing "ifup eth0" and see what it says. Then type the command "ifconfig" and paste the output here. Finally type "route -n" and paste the output here as well.

---


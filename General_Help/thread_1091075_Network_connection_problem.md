---
title: "Network connection problem"
date: 2009-03-09
forum: General Help
---

### Post by porkey10 on 2009-03-09
I am using Ubuntu 8.04. Firefox and evolution are offline when I start up my Acer aspire5315 laptop.Although they do connect if I do it manually. This happened after I removed the Network Manager from the notification area and if I try to configure eth0 I get "Interface does not exist". I have tried from Ubuntu help,sudo ifdown eth0 and sudo ifup eth0 and I appear to get the correct message in reply but it still does not work and "Interface does not exist"still comes up if I try to configure.Can anyone help me please?

---

### Post by stanz on 2009-03-09
try checking a file, in nautilus: **/etc/network**, filename: ***/interfaces***
it needs to have ***eth0*** in it.
here's mine for reference:
> 
# This file describes the network interfaces available on your system
# and how to activate them.
# For more information, open terminal--type, *man interfaces*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

---


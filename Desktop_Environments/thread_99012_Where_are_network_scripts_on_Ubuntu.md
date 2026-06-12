---
title: "Where are network scripts on Ubuntu?"
date: 2005-12-04
forum: Desktop Environments
---

### Post by ultranet on 2005-12-04
What is Fedora's /etc/sysconfig/network-scripts equivalent on Ubuntu?

Thanks.

---

### Post by stevea1210 on 2005-12-04
I haven't used FC, but what you're looking for is probably in /etc/network.  The interfaces file inside of that folder is where you'll probably be doing most of your work (configuring for static or dhcp, wireless settings, etc).  Hope that helps.

---

### Post by baeckel on 2008-02-20
I am looking for the same information.  I'm looking for the file on Ubuntu that is the equivalent to the FC /etc/sysconfig/network-scripts/ifcfg files which automatically configure NICs on boot.  An example of the files interior follows:

DEVICE=eth0 #what interface you want to configure
ONBOOT=yes #whether or not it should be activated on boot (this is what i am mainly interested in)
BOOTPROTO=static or dhcp
IPADDR=192.168...
NETMASK=255.255...

---

### Post by isahak on 2008-06-30
I think it's in the /etc/network. The file interfaces does the same thing.

---


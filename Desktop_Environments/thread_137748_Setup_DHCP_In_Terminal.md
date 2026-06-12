---
title: "Setup DHCP In Terminal"
date: 2006-02-28
forum: Desktop Environments
---

### Post by josh34 on 2006-02-28
I wasn't connected to the network when I installed a server install of Ubuntu. How do I now use terminal to setup dhcp?

Thanks,
Josh

---

### Post by dcstar on 2006-02-28
[QUOTE=josh34]I wasn't connected to the network when I installed a server install of Ubuntu. How do I now use terminal to setup dhcp?

Thanks,
Josh[/QUOTE]
Probably have to manually edit the dhclient.conf file, have a look in the man page for it.

Either that or install ubuntu-desktop and use the GUI tools.

---

### Post by josh34 on 2006-02-28
Where is the dhclient.conf file located? What should I edit dhclient.conf to? What is the "man page?"

---

### Post by dcstar on 2006-02-28
[QUOTE=josh34]Where is the dhclient.conf file located? What should I edit dhclient.conf to? What is the "man page?"[/QUOTE]
man dhclient.conf
locate dhclient.conf
sudo gedit /etc/dhcp3/dhclient.conf

---

### Post by josh34 on 2006-02-28
I couldn't locate a dhclient.conf file.

---

### Post by HelLios on 2006-02-28
in the /etc/network/interfaces  
set
iface eth0 inet dhcp

---

### Post by josh34 on 2006-02-28
That did the trick.

Thanks,
Josh

---


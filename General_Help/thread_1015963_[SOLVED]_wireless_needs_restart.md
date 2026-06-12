---
title: "[SOLVED] wireless needs restart"
date: 2008-12-19
forum: General Help
---

### Post by 2handband on 2008-12-19
this may sound a bit silly, but on my Intrepid install the wireless connection needs to be manually started every time I restart the computer. Is there anything I can do about this?

---

### Post by Titan8990 on 2008-12-19
Yes, there is. You just need to edit your /etc/network/interfaces

By default it should look like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

You just need to add your wireless interface to the list. Here is what it would look like assuming you are using DHCP and your wireless interface is wlan0 (if its atheros is could be ath0).

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The wireless interface
auto wlan0
iface wlan0 inet dhcp
```

---

### Post by Wartender on 2008-12-19
or in network configuration, edit your wireless connection and check the "connect automatically" box.

---

### Post by 2handband on 2008-12-19
Fixed! Thanks.

---


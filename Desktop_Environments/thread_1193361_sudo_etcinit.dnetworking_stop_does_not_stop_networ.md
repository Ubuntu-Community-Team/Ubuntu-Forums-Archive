---
title: "sudo /etc/init.d/networking stop does not stop networking"
date: 2009-06-21
forum: Desktop Environments
---

### Post by SilvaRizla on 2009-06-21
Bit stumped on this one.  I'm using a USB Belkin N Wireless with the RT2870 chipset and drivers correctly installed.  When I execute /etc/init.d/networking stop I get the Deconfiguring network devices message and it seems to be successful but doesn't actually take the card down (the activity light still flashes) so for instance I can't change the mac address.

sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                                                                                       [ OK ]
Xdesktop:~$ sudo macchanger --mac=00:16:44:84:F3:89 ra0
Current MAC: XX:XX:XX:XX:XX:XX (unknown)
ERROR: Can't change MAC: interface up or not permission: Device or resource busy


Any ideas?

---

### Post by Brandon Williams on 2009-06-21
Is your interface configured in /etc/network/interfaces? Or is it managed by network-manager?

If it's network-manager, then running '/etc/init.d/networking stop' will do nothing, because that script uses ifdown, which is only for network interfaces managed out of /etc/network/interfaces. You will need to disable the device using a network-manager control utility.

If the device _is_ in /etc/network/interfaces, then try using 'ifconfig <interface> down', where <interface> is the interface name, such as eth0 or wlan0.

---


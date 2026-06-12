---
title: "Changing mac address"
date: 2006-03-07
forum: Desktop Environments
---

### Post by sean_naes on 2006-03-07
My friend is living at a university residence which only has wireless access.  They use the computer's mac address to allow only people in the residence to connect to the wireless, but will only allow one mac address per person.  My friend has a desktop as well as a laptop, and would obviously like both to be able to connect to the internet.
I've found out how to use to restart the connection with the new mac address (by stopping the connection and using ifconfig eth0 hw ether XX:XX:XX:XX:XX:XX up), but of course you need to do that every time you start the computer.
How would this change be made permanent?

---

### Post by swamytk on 2006-03-08
He can include the following line in his network configuration file /etc/network/interfaces. run "man interfaces" for more info.

```
hwaddress ether <mac address>

```

---

### Post by sean_naes on 2006-03-08
Cool, thanks - we'll try that.

---

### Post by stuporglue on 2006-03-08
You could also get a router and register the router's MAC address in his name. I do this at my school and have four computers in the appartment.

---


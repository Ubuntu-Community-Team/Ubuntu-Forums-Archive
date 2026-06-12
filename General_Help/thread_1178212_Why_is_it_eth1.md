---
title: "Why is it eth1 ?"
date: 2009-06-04
forum: General Help
---

### Post by colau on 2009-06-04
Hi,
cat /etc/network/interfaces
```

pre-up /sbin/ifconfig eth1 up 
provider dsl-provider

auto eth1
iface eth1 inet manual

```

And ifconfig
The first line:
```

eth1      Link encap:Ethernet

```

Why is it eth1?
Is it possible to have eth0 again?:(

---

### Post by cdenley on 2009-06-04
```

gksu gedit /etc/udev/rules.d/70-persistent-net.rules

```
or if you don't use gnome
```

sudo nano /etc/udev/rules.d/70-persistent-net.rules

```
This file is used to store persistent names for network interfaces. You probably have or had another NIC which is no longer used.

---

### Post by colau on 2009-06-04
> **cdenley said:**
> ```

gksu gedit /etc/udev/rules.d/70-persistent-net.rules

```
or if you don't use gnome
```

sudo nano /etc/udev/rules.d/70-persistent-net.rules

```
This file is used to store persistent names for network interfaces. You probably have or had another NIC which is no longer used.

Yes there are two subsystems with two mac address as I changed my motherboard.
Should I delete the first line with old mac address?

---

### Post by plucky on 2009-06-04
What does ```
cat /etc/udev/rules.d/70-persistent-net.rules
``` show.If eth0 has already been used it will show up in this file.

---

### Post by cdenley on 2009-06-04
> **colau said:**
> Yes there are two subsystems with two mac address as I changed my motherboard.
Should I delete the first line with old mac address?

You can delete the first line (or comment it out), then change eth1 to eth0 in the second line if you want. Then reboot. It couldn't hurt to save a backup copy before you make changes, though.

---

### Post by colau on 2009-06-04
> **cdenley said:**
> You can delete the first line (or comment it out), then change eth1 to eth0 in the second line if you want. Then reboot. It couldn't hurt to save a backup copy before you make changes, though.
Thanks.

---


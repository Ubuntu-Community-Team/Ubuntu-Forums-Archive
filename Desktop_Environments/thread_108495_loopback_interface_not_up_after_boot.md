---
title: "loopback interface not up after boot"
date: 2005-12-26
forum: Desktop Environments
---

### Post by Shanachie on 2005-12-26
I have compiled a kernel, because I am writing a kernel driver, and somehow the loopback interface isn't started during init anymore. With the standard ubuntu-2.6.12-9-386 kernel there's no problem.
I'm not really familiar with ubuntu/debian network-configuration, I've recently switched from gentoo.

Here's my /etc/network/interfaces file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

iface eth0 inet dhcp
iface eth1 inet dhcp

```
I removed eth0 (wired) and eth1 (wireless) from auto so I doesn't hang init when no network is present.

here's my [kernel-configuration]("http://users.telenet.be/shanachie/files/kernel-config20051221")

Does anybody now how this can solved?

Greets Shanachie

---


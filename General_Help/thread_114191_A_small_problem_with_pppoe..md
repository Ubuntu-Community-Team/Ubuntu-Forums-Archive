---
title: "A small problem with pppoe."
date: 2006-01-08
forum: General Help
---

### Post by rox on 2006-01-08
I installed rp-pppoe to use adsl and generate a dsl-provider config file using pppoeconf.
It seems that it start automatically and there is indeed a ppp sym link in /etc/rc5.d.
But the problem is it started two ppp interfaces at the same time, through ifconfig I find ppp0 and ppp1.
So I have to manually shutdown ppp1 to make it work noramlly.
It's a small problem but a little bit annoying, can anybody give me a clue?
Thank you.

---

### Post by moopere on 2006-01-15
[QUOTE=rox]I installed rp-pppoe to use adsl and generate a dsl-provider config file using pppoeconf.
It seems that it start automatically and there is indeed a ppp sym link in /etc/rc5.d.
But the problem is it started two ppp interfaces at the same time, through ifconfig I find ppp0 and ppp1.
So I have to manually shutdown ppp1 to make it work noramlly.
It's a small problem but a little bit annoying, can anybody give me a clue?
Thank you.[/QUOTE]

What does your /etc/network/interfaces file look like?

Craig

---

### Post by rox on 2006-01-16
Is there anything wrong?
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth0
    iface eth0 inet manual

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

---


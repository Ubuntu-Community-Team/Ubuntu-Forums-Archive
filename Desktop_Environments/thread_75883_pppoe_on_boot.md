---
title: "pppoe on boot"
date: 2005-10-14
forum: Desktop Environments
---

### Post by moose6589 on 2005-10-14
Hello, 

This is now my third reinstall of Breezy since the RC came out; this time, I finally did a fresh install of the final release, hoping that it would fix various problems that I was previously having. However, my original problem still has not been fixed, either with a fresh install or after updates, and this is really starting to tick me off. 

PPPOE will not start on bootup! Whenever I restart, the connection is not automatically connected, meaning I have to run 'pon dsl-provider everytime I need to access the Internet. Here are the contents of my /etc/network/interfaces file: 

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
	map eth0

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth0
    iface eth0 inet manual

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```

Hopefully, someone has the answer to this problem!

---

### Post by adwait on 2005-10-14
When you ran pppoeconf, you did select to connect on start up right? If you did and its still not running......you could just add pon dsl-provider to a script and then set it up to run on boot.

---


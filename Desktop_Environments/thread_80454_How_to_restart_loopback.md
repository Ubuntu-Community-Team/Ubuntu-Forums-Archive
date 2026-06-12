---
title: "How to restart loopback?"
date: 2005-10-22
forum: Desktop Environments
---

### Post by barry_s on 2005-10-22
I'm a bit of a linux noob, but managed to get Breezy installed on my laptop with only one issue, which was it not recognising my wireless network. Somehow in the process of sucessfully setting up wlan I seem to have killed loopback. 

I've installed apache and I know it's running okay beacuse I can see the default apache page from another machine on my network, but if I try accessing localhost on my laptop (or pinging it) it just times out.

Any help would be mych appreciated.

Thanks

Barry

---

### Post by barry_s on 2005-10-22
Okay, I've made a little progress here..

I ran: sudo ifconfig lo up, and now loopback is working, but how do i get it to start at bootup?

Thanks

---

### Post by GeneralZod on 2005-10-22
Can you post the contents of  /etc/network/interfaces?

Obviously, blank out anything personal like WEP key, etc :)

Edit:

Mine begins with

```

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

```

so you should probably make sure yours has the same :)

---

### Post by barry_s on 2005-10-22
Thanks for the quick response GeneralZod

Here is my /etc/network/interfaces file

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface eth0 inet dhcp



subsystem.
mapping hotplug
	script grep
	map wlan0

iface wlan0 inet dhcp
wireless-essid linksys

auto wlan0

```

It looks the same as yours. Am I missing something?

---

### Post by penguindude on 2007-07-25
Hello,
I am having this exact same problem. I am on feisty.  any one know?

---


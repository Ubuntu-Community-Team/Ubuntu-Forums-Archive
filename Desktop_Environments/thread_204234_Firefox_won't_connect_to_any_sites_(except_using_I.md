---
title: "Firefox won't connect to any sites (except using IP)"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Princess_Tiswas on 2006-06-26
/etc/modprobe.d/aliases
```
#alias net-pf-10 ipv6
```
/etc/resolv.conf
```
#nameserver 192.168.1.1
nameserver 212.23.6.100
```
/etc/network/interfaces
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

# The primary network interface


iface eth0 inet static
address 192.168.1.30
netmask 255.255.255.0
gateway 192.168.1.1
```

[Edit]Ooops - hit submit too early

I can conect to the internet in other ways - ping / traceroute / wget all work from the command line, using both IP and urls.

IPV6 is disabled.

MOzilla Web Browser does not work either.

---

### Post by DarthMandeep on 2006-06-26
You're using a router, right? You should have a dns line in your /etc/network/interfaces file that points to your router. If your router address is 192.168.1.1, you'd just add "dns 192.168.1.1" to the eth0 section.

Then uncomment the 192.168.1.1 part of your /etc/resolv.conf file, if that is your routers address. Then restart your network connection with "/etc/init.d/networking restart" and see if it works.

---

### Post by leech on 2006-06-26
Technically you're not supposed to touch /etc/resolv.conf, all the other networking config stuff does that for you.  I just find it quicker though than opening up the networking under gnome just to change the dns values.  I have kind of the same problem when I use my wireless, it works, but it's extremely slow (because it has to wait for the first nameserver to time out then go to the second one, which is set right).  I usually just end up modifying /etc/resolv.conf to point to my server, which has a DNS server on it.  

It does look to me like it's a routing issue.

Leech

---

### Post by Princess_Tiswas on 2006-06-27
I do have a router (at 192.168.1.1)

I previously modified /etc/resolv.conf (under HH) and added my ISPs DNS to deal with resolution issues.

One thing that I discovered last night (whilst trying to install firefox 1.5), was that there were no problems when I ran FF as root.

In fact, there were no DNS problems with anything if I ran them as root.

I'm not on my machine at the moment, but my guess is that I have the wrong permissions on /etc/resolv.conf.

---

### Post by Princess_Tiswas on 2006-06-27
It was the permissions all along. chmod'ed to 644 and all is well with t'internet.

---


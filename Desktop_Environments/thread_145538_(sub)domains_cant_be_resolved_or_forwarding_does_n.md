---
title: "(sub)domains cant be resolved or forwarding does not work"
date: 2006-03-16
forum: Desktop Environments
---

### Post by schildi on 2006-03-16
hello,
i installed ubuntu and i have problems with dns-resolution.
these domainnames for example cant be found:
[http://download.skype.com](http://download.skype.com) 
[http://wiki.ubuntu.com](http://wiki.ubuntu.com)

------------------------------------------------------------------------
my etc/network/interfaces file:
------------------------------------------------------------------------
  GNU nano 1.3.8                                  Datei: /etc/network/interfaces

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
        address 192.168.2.10
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 194.25.2.129, 271.9.42.98, 194.25.0.52

------------------------------------------------------------------------
my hosts file:
------------------------------------------------------------------------

  GNU nano 1.3.8                                      Datei: /etc/hosts

127.0.0.1       localhost.localdomain   localhost
192.168.2.10    XXX

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

------------------------------------------------------------------------

any ideas?

thanks for your help.

---

### Post by dcstar on 2006-03-17
[QUOTE=schildi]hello,
i installed ubuntu and i have problems with dns-resolution.
these domainnames for example cant be found:
[http://download.skype.com](http://download.skype.com) 
[http://wiki.ubuntu.com](http://wiki.ubuntu.com)
......
any ideas?

thanks for your help.[/QUOTE]
You use the following commands to diagnose your system:

**route -n** (to see what routing table your system has)

**traceroute <IP address>** (for instance, to test each of the DNS servers you have listed)

**dig <DNS or IP>** (to test how the DNS server you think you are using is responding)

---


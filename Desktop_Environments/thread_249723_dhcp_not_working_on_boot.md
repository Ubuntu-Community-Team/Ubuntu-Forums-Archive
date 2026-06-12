---
title: "dhcp not working on boot"
date: 2006-09-02
forum: Desktop Environments
---

### Post by notepad on 2006-09-02
ever since i upgraded my ubuntu to version 6.06 my dhcp has generally not worked. almost every single time i boot my system now i have to issue the command "sudo /etc/init.d/networking restart" to get eth0 configured properly.

i have tried disabling ipv6 (successfully) but this is not the problem.

my ifconfig looks like this:

eth0      Link encap:Ethernet  HWaddr 00:14:85:CD:3B:FE
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3540 (3.4 KiB)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11796 (11.5 KiB)  TX bytes:11796 (11.5 KiB)


and my /etc/network/interfaces looks like this:

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

# The primary network interface
auto eth0
iface eth0 inet dhcp



does anybody know how the system makes a dhcp request on boot? any ideas on whats wrong with my system?

---


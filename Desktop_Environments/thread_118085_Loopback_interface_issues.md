---
title: "Loopback interface issues"
date: 2006-01-16
forum: Desktop Environments
---

### Post by mrsuicide on 2006-01-16
My computer won't assign 127.0.0.1 to the loopack interface at boot.
```
sysadmin@laptop-jan:/home/mrsuicide$ sudo ifconfig lo
lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:564227 (551.0 KiB)  TX bytes:564227 (551.0 KiB) 
```
It works, if I do this manually: 
```
sysadmin@laptop-jan:/home/mrsuicide$ ifconfig lo down
sysadmin@laptop-jan:/home/mrsuicide$ ifconfig lo up
```

After that 127.0.0.1 is assigned: ```

sysadmin@laptop-jan:/home/mrsuicide$ sudo ifconfig lo
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:564227 (551.0 KiB)  TX bytes:564227 (551.0 KiB) 
```

My /etc/netowrk/interfaces :```
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
        address 192.168.0.4
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255

iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth0

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```
Privoxy wont work for me without this. Any ideas?

---


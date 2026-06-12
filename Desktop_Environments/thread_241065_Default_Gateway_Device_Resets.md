---
title: "Default Gateway Device Resets"
date: 2006-08-21
forum: Desktop Environments
---

### Post by wugoat on 2006-08-21
Hi Ubuntu Folks. Having networking problems whilst trying to set up a filtered web proxy, using Squid and Dansguardian. 

Starting from a fresh Install of Dapper from the CD.
Configured 2 NIC with Static IP addresses.
Installed Squid Proxy.
Installed Dansguardian (+ latest Blacklists).
Installed Webmin, and configed for the above.

..and the setup is working fine. Great was the celebration and cheerfullness.. Filtered Web access works well from windows box on the LAN.
Could even run MSN messenger (though seemed a bit slow going through Dansguardian 8080, worked much happier proxying through just Squid's 3128  :)

Lastly, installing VNC... Synaptic installed x11vnc.

Could not get it to work... But worse still, now my Default Gateway Device (which should be eth1) now resets on reboot to eth0. I suspect that eth0 is also deactivated, though it shows as active in system-> network as the fix seems to be to reset Default Gateway Device in System-> Network, then Deactivate and Reactivate eth0.

I can then get web/IM access accross the LAN.

Uninstalling x11vnc does not help.

---

### Post by wugoat on 2006-08-23
OK, the problem, like my ignorance, appeas to be more fundemental  :) 

Setting up eth1 to the router is fine.
Setting up eth0 to the LAN is th tricksy bit...

Simply put, I've searched but can't find what I should be setting the Default Gateway IP for the LAN facing NIC (eth0).

If I set it to my router (192.168.1.1) then the Default Gsteway Device setting in Ubuntu becomes confused... Defgaults to eth0 at reboot... and so on..

If I leave it blank, or set it to any other trial-and-error settings, I lose all connection to the LAN.

Help?

for reference
```

wu@wu-ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1


wu@wu-ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:21:D3:C6:E7
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:21ff:fed3:c6e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28696 (28.0 KiB)  TX bytes:32318 (31.5 KiB)
          Interrupt:12 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:20:18:2B:E6:8F
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:18ff:fe2b:e68f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18793 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3 txqueuelen:1000
          RX bytes:23821813 (22.7 MiB)  TX bytes:960385 (937.8 KiB)
          Interrupt:9 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:759048 (741.2 KiB)  TX bytes:759048 (741.2 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```


yet if I set eth0 default gateway to 192.168.1.1
```

wu@wu-ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
wu@wu-ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:21:D3:C6:E7
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:21ff:fed3:c6e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28696 (28.0 KiB)  TX bytes:33914 (33.1 KiB)
          Interrupt:12 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:20:18:2B:E6:8F
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:18ff:fe2b:e68f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18973 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3 txqueuelen:1000
          RX bytes:23990285 (22.8 MiB)  TX bytes:1001000 (977.5 KiB)
          Interrupt:9 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:759312 (741.5 KiB)  TX bytes:759312 (741.5 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

thanks for any help folks...

---

### Post by wugoat on 2006-08-25
...seems sensible to me to have the LAN facing NIC have a default gateway of the router facing NIC's IP...

...but though I try it.. still can't ping LAN or get internet connectivity on the LAN.

...is there anyone out there who can advise???

---

### Post by Uluen on 2006-08-25
It seems to me that the networking applet is buggy. When I installed a second NIC it also changed default gateway, selecting the correct NIC doesn't save.

ifup/down manually seemed to fix it temporary.

---

### Post by wugoat on 2006-08-25
](*,)  yeah, it's driving me crazy... I want to love Ubuntu, and so much of it is very sweet... 

But I need to be able to set up a web proxy for the homelan.. The Way things are going, I strongly suspect that this is something more and more people will want to be doing.  I'm dissapointed that this seems to be something Ubuntu can't do for me...

Personally, I'm thinking of trying a different Linux flavour...

---

### Post by Uluen on 2006-08-25
It's not hard to fix really. Poke around in "man interfaces",
A small script should be all that's needed to bring up the NICs with correct parameters.

---

### Post by wugoat on 2006-09-11
Thanks Uluen!

:-k 

Well, after some perserverance I believe I've discovered that the core of the problem was my routing table!  Briefly it was set up to direct interal and external traffic through the same NIC, and it always found the wrong one first!

My antics...

[http://www.ubuntuforums.org/showthread.php?t=250179]("http://www.ubuntuforums.org/showthread.php?t=250179")

---


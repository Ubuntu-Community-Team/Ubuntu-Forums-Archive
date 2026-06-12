---
title: "how do I enable both onboard Ethernet ports?"
date: 2006-10-01
forum: Desktop Environments
---

### Post by pmark on 2006-10-01
ifconfig gives me this:

```

eth0      Link encap:Ethernet  HWaddr 00:11:D8:8E:E5:23
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:11:D8:8E:ED:05
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe8e:ed05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4644878 (4.4 MiB)  TX bytes:1614386 (1.5 MiB)
          Interrupt:74

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.18.1  Bcast:192.168.18.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

Currently, I can only use eth1. Is there a way to enable eth0 too?

*I exclude the possibility of VMWare having anything to do with this, since I was experiencing the same before installing VMWare.*

---

### Post by kidders on 2006-10-01
Your eth0 appears to be working, but nothing is assigning it an IP ... what's *supposed* to be happening?

---

### Post by pmark on 2006-10-01
[quote=kidders]Your eth0 appears to be working, but nothing is assigning it an IP ... what's supposed to be happening?[/quote]

Plug in the LAN cable from the DSL modem/router, ping on 192.168.1.1 and get a response. Next, ping a domain, like google.com and get a response. It happens with eth1. Why is this not happening with eth0?

---

### Post by NetworkGuy on 2006-10-01
Why do you want to plug both eth0 & eth1 into the same network?  Load balancing or failover maybe?

---

### Post by chele on 2006-10-01
You'll be needing the Advanced Routing HowTo, I believe.

---

### Post by NetworkGuy on 2006-10-01
You can't route when both interfaces are on the same subnet.

---

### Post by kidders on 2006-10-01
I imagine all pmark meant was that he expected both interfaces to behave the same way when subjected to identical circumstances. At least I *hope* that's what he meant :-k

If so, then you need to check that DHCP is enabled on both interfaces and not just one of them. You're other option is to assign an address manually, if you don't feel like setting up a DHCP server wherever the second network card is gonna get plugged.

---

### Post by pmark on 2006-10-02
> **NetworkGuy]Why do you want to plug both eth0 & eth1 into the same network? Load balancing or failover maybe?[/quote]

No, no, no... but I tried that one too :) I just want to use eth0 instead of eth1. This is because Windows sees only eth0, so I have to change the plug between eth0 and eth1 whenever I boot into another OS. This wasn't a problem so far, but it's getting too frequent (several times in a day).

The other approach would be to make Windows see both ports, but I am generally reluctant to tweak an OS that I am gradually replacing and hopping one day to use only for games (the ones that WINE doesn't play).

[QUOTE=kidders said:**
> I imagine all pmark meant was that he expected both interfaces to behave the same way when subjected to identical circumstances. At least I *hope* that's what he meant :-k

If so, then you need to check that DHCP is enabled on both interfaces and not just one of them. You're other option is to assign an address manually, if you don't feel like setting up a DHCP server wherever the second network card is gonna get plugged.

Yes. How do I check that DHCP is enabled on both interfaces? Is there a way to initialize both or to just change the one that is getting initialized from eth1 to eth0? Is the "Advanced Routing HowTo" what I need to find?

---

### Post by kidders on 2006-10-03
You could try looking at /etc/network/interfaces. You'd expect to see something like:

```

auto ethX
iface ethX inet dhcp

```

---

### Post by pmark on 2006-10-05
> **kidders said:**
> You could try looking at /etc/network/interfaces. You'd expect to see something like:

```

auto ethX
iface ethX inet dhcp

```

I see this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

What do I need to change?

---

### Post by kidders on 2006-10-05
Oh dear. You don't seem to need to change anything there :-(

If it were me, I'd try some debugging next. I'd try an **/etc/init.d/networking restart** just to see what it said to me, and then I'd try bringing a DHCP-based network interface up manually, step by step. The hope is that somewhere along the line, a specific problem would crop up that I could look for a quick solution to.

---

### Post by clarknova on 2006-10-05
Yeah, your /etc/network/interfaces file looks correct. Is your eth0 physically connected to the network when you boot or are you moving the wire afterward? I suspect the latter, since eth1 is being configured by dhcp.

If so, then you can either connect the network (router, switch, etc) to eth0 before booting, or, after connecting the network to eth0 post-boot do **sudo ifdown eth0** followed by **sudo ifup eth0**. **/etc/init.d/networking restart**, as mentioned above, will accomplish the same thing.

---

### Post by pmark on 2006-11-24
[quote=clarknova]Yeah, your /etc/network/interfaces file looks correct. Is your eth0 physically connected to the network when you boot or are you moving the wire afterward? I suspect the latter, since eth1 is being configured by dhcp.

If so, then you can either connect the network (router, switch, etc) to eth0 before booting, or, after connecting the network to eth0 post-boot do sudo ifdown eth0 followed by sudo ifup eth0. /etc/init.d/networking restart, as mentioned above, will accomplish the same thing.[/quote]

eth0 is always physically connected to the network.

I was able to make it work by adding this line on rc.local:

```
/etc/init.d/networking restart
```

All this time it has been working fine like this with there is only a small penalty in boot time (just a few seconds) but that's not a problem. However, it would be interesting to discover why eth1 doesn't require this.

Any suggestions or ideas?

---


---
title: "[SOLVED] ethernet and wlan"
date: 2007-07-20
forum: Dell  Ubuntu Support
---

### Post by bash4fun on 2007-07-20
i'm pretty new to linux but i have already been able to solve several problems
but now i got a new one
everytime i activate both, ethernet lan and wlan adapter, firefox and other progs seem
only to use one of the two adapters
my wlan adapter eth1 is connecting to the internet over a wireless router whereas the eth0 lan adapter only should be used to access my 2nd pc locally
how can i configure that internet actions are carried out thruogh eth1 and lan actions through eth0

please help me :confused:

---

### Post by anubhavrocks on 2007-07-20
Do you mean to say that when you have both the interfaces up,you can not access the internet?Also post the output of ```
ifconfig -a
```

---

### Post by anubhavrocks on 2007-07-20
also this might help

[http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)

---

### Post by bash4fun on 2007-07-20
yes then i am not able to connect to the internet

heres the output of "ifconfig -a"

eth0      Link encap:Ethernet  HWaddr 00:15:C5:AC:37:04  
          inet addr:192.168.0.34  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feac:3704/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2292619 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4133417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:222930532 (212.6 MiB)  TX bytes:183694762 (175.1 MiB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:22:95:49  
          inet addr:192.168.0.23  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe22:9549/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:464 errors:425 dropped:4140 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3757969 (3.5 MiB)  TX bytes:617326 (602.8 KiB)
          Interrupt:16 Base address:0xe000 Memory:efcff000-efcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46994 (45.8 KiB)  TX bytes:46994 (45.8 KiB)

---

### Post by anubhavrocks on 2007-07-20
and also the output of

```
route -n
```

I think you havent't  put the right gateway address in your routing table,with both the interfaces UP can you ping your wireless router?Also you might enable DHCP on your router which would assign you the right gateway automatically.

---

### Post by bash4fun on 2007-07-20
i have to say that to my experience it
depends on in wich order i activate the
interfaces in network manager
because when i first activate the wlan
interface i am able to ping the router and
successfully connect to the internet
but by doing it the other way round i can
only access the local network because the
ping is always carried out through eth1 which
has been activated first

---

### Post by anubhavrocks on 2007-07-20
Thats is because the default route gets set with your second interface and that default route is not the one you require

---

### Post by bash4fun on 2007-07-20
so is there any possibility to set the
default route and make it unchangable?

---


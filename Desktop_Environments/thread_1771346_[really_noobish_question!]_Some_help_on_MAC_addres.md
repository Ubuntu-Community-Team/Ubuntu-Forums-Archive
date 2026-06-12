---
title: "[really noobish question!] Some help on MAC addresses?"
date: 2011-05-30
forum: Desktop Environments
---

### Post by Andreawws on 2011-05-30
so I have had problems setting up my Internet (this applies in 10.04, 10.10 and 11.04)
basically it will not set up networking properly, now I can do it manually, or so I think at least...
now, I set up everything (even the MAC address) everything looks good, but the internet will not work properly!
so I run the command 'ifconfig'
I get this:
```
**eth0      Link encap:Ethernet  HWaddr **:**:**:**:**:**  **
          inet addr:***.***.**.*  Bcast:**.**.**.***  Mask:***.***.***.*
          inet6 addr: ****::***:***:****:***/** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163491 (163.4 KB)  TX bytes:62756 (62.7 KB)
          Interrupt:17 

**ham0      Link encap:Ethernet  HWaddr **:**:**:**:**:** ** 
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2352 (2.3 KB)  TX bytes:2352 (2.3 KB)

```

Now I put what I want to know in bold, which one of them should I use?
both say HWaddr (as far as I understand MAC address and hardware address is the same)

additional info, it connects no matter which one I choose :/ 
(I am asking these questions out of pure curiosity)
so can anyone explain this to me?


secondly (not so important since I managed to fix it :D)
My ISP is supposed to automatically assign DNS, but I have to do it manually to be able to connect :/ how does this come? I had to use googles (8.8.8.8, 8.8.4.4)


**I changed everything non essential to "*'s" **

---


---
title: "Wired internet connection not working"
date: 2009-06-10
forum: General Help
---

### Post by Shinka.S on 2009-06-10
I have a desktop computer with 2 hard drives, one with WinXp and the other with Ubuntu 9.04 32bits, my wired internet connection works on WinXp but not on Ubuntu. I have a nForce chipset with a D-Link DFE 538TX network card.

I got help from #ubuntu and I was asked to do; 

[COLOR=Blue]sudo su
updatedb [/COLOR]

And then in the folder with 8139cp.ko; 

[COLOR=Blue]modprobe -i 8139cp[/COLOR]

He said that "if it works you'll need to add it to /etc/modules I think so it will be insmoded every time your system starts" ==> how do I do that ?

Anyway it didn't work and the guy had to go to sleep, I have really no idea what to do next...

The result of [COLOR=Blue]ifconfig[/COLOR]

```
eth0      Link encap:Ethernet  HWaddr 00:22:b0:68:58:26  
          inet6 addr: fe80::222:b0ff:fe68:5826/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by colau on 2009-06-10
> **Shinka.S said:**
> I have a desktop computer with 2 hard drives, one with WinXp and the other with Ubuntu 9.04 32bits, my wired internet connection works on WinXp but not on Ubuntu. I have a nForce chipset with a D-Link DFE 538TX network card.

I got help from #ubuntu and I was asked to do; 

[COLOR=Blue]sudo su
updatedb [/COLOR]

And then in the folder with 8139cp.ko; 

[COLOR=Blue]modprobe -i 8139cp[/COLOR]

He said that "if it works you'll need to add it to /etc/modules I think so it will be insmoded every time your system starts" ==> how do I do that ?

Anyway it didn't work and the guy had to go to sleep, I have really no idea what to do next...

The result of [COLOR=Blue]ifconfig[/COLOR]

```
eth0      Link encap:Ethernet  HWaddr 00:22:b0:68:58:26  
          inet6 addr: fe80::222:b0ff:fe68:5826/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Is it dial-up connection?(PPPoE)?

---

### Post by Shinka.S on 2009-06-10
No, I have a cable modem.

---


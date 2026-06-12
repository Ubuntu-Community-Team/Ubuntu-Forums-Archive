---
title: "athcool and loss of network connection"
date: 2006-04-04
forum: Desktop Environments
---

### Post by Josh M on 2006-04-04
I installed athcool yesterday from the repositories. I like it. It drops the temperature of my Athlon XP 1900+ T-bred by 10 degrees celsius. My motherboard chipset is a Via KT266/333 and is supported by athcool. 

Minutes after starting athcool I seem to lose my network connection. (eth0 connected to a Linksys router and then a cable modem.). I can't access the Internet from Firefox, Azureus, or the terminal. I can't get into my routers administration by directing my browser to [http://192.168.1.1](http://192.168.1.1). I have to reboot in order to get back on the Internet. athcool introduces no other system instabilities as far as I can tell. 

I very much want to use athcool. Does anyone have a workaround for this, or have any network diagnostic tips which might help me figure out this problem. (I am relatively new to Linux.) Thank you.

---

### Post by jamesr on 2006-04-04
Just a thought but ```
sudo ifcong -a 
```before and after failure.

---

### Post by Josh M on 2006-04-05
This time it took a number of hours running athcool before I lost the network connection. 

ifconfig -a before:

```

eth0      Link encap:Ethernet  HWaddr 00:50:BA:FB:8D:F5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fefb:8df5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:582259 (568.6 KiB)  TX bytes:162645 (158.8 KiB)
          Interrupt:16 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:368392 (359.7 KiB)  TX bytes:368392 (359.7 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

ifconfig -a after network loss:

```

eth0      Link encap:Ethernet  HWaddr 00:50:BA:FB:8D:F5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fefb:8df5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13890 errors:0 dropped:115 overruns:0 frame:0
          TX packets:21864 errors:9 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3024169 (2.8 MiB)  TX bytes:25197460 (24.0 MiB)
          Interrupt:16 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1774501 (1.6 MiB)  TX bytes:1774501 (1.6 MiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

I ran the diff between these files. If I am reading this right, the only differences between before and after are the numbers of packets, errors, etc transmitted and received and this is to be expected. Hmmm. :-k 

```

5,6c5,6
<           RX packets:714 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:729 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:13890 errors:0 dropped:115 overruns:0 frame:0
>           TX packets:21864 errors:9 dropped:0 overruns:0 carrier:0
8c8
<           RX bytes:582259 (568.6 KiB)  TX bytes:162645 (158.8 KiB)
---
>           RX bytes:3024169 (2.8 MiB)  TX bytes:25197460 (24.0 MiB)
15,16c15,16
<           RX packets:1351 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:1351 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:6573 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:6573 errors:0 dropped:0 overruns:0 carrier:0
18c18
<           RX bytes:368392 (359.7 KiB)  TX bytes:368392 (359.7 KiB)
---
>           RX bytes:1774501 (1.6 MiB)  TX bytes:1774501 (1.6 MiB)

```

---

### Post by jamesr on 2006-04-05
But the NIC do not seem to have been reset ie no inet address. You say that you have to reboot but have you tried ```
sudo ifdown eth0
sudo ifup eth0
```

---

### Post by dcstar on 2006-04-10
[QUOTE=Josh M]I installed athcool yesterday from the repositories. I like it. It drops the temperature of my Athlon XP 1900+ T-bred by 10 degrees celsius. My motherboard chipset is a Via KT266/333 and is supported by athcool. 

Minutes after starting athcool I seem to lose my network connection. (eth0 connected to a Linksys router and then a cable modem.). I can't access the Internet from Firefox, Azureus, or the terminal. I can't get into my routers administration by directing my browser to [http://192.168.1.1](http://192.168.1.1). I have to reboot in order to get back on the Internet. athcool introduces no other system instabilities as far as I can tell. 

I very much want to use athcool. Does anyone have a workaround for this, or have any network diagnostic tips which might help me figure out this problem. (I am relatively new to Linux.) Thank you.[/QUOTE]
You can go into your BIOS and check for any power saving settings associated with the LAN card, and change them to see if it makes a difference.

---


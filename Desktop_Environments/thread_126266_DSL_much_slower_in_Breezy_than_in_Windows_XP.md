---
title: "DSL much slower in Breezy than in Windows XP"
date: 2006-02-06
forum: Desktop Environments
---

### Post by JariHuomo on 2006-02-06
My biggest problem in Ubuntu is that my DSL speeds are half slower in Ubuntu than in Windows.


I have Acer Aspire 3023Wlmi notebook and my ethernet card is "Realtek RTL8169/8110 Family Gigabit Ethernet Nic"

Here is some info:

sudo mii-tool

SIOCGMIIPHY on 'eth0' failed: Operation not supported
no MII interfaces found

sudo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0A:E4:E1:87:A8
          inet addr:81.175.143.25  Bcast:81.175.143.255  Mask:255.255.252.0
          inet6 addr: fe80::20a:e4ff:fee1:87a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:600535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:871246587 (830.8 MiB)  TX bytes:17144202 (16.3 MiB)
          Interrupt:23 Base address:0x8400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:470904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:470904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:61833643 (58.9 MiB)  TX bytes:61833643 (58.9 MiB)

I tried this but it didn´t help:

sudo /usr/sbin/ethtool -s eth0 autoneg off duplex full

Any suggestions what to try to do?

---

### Post by zAo on 2006-02-06
This helped me
```
https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28staticdns%29
```

---

### Post by JariHuomo on 2006-02-06
Did not help me :(

---

### Post by plexi50 on 2006-02-09
This might help. Try to disable ipv6 following these instructions 
 
[https://wiki.ubuntu.com/WebBrowsingS...ght=%28IPv6%29]("https://wiki.ubuntu.com/WebBrowsingS...ght=%28IPv6%29")

---

### Post by JariHuomo on 2006-02-13
Yes, I know that trick :) I have tried that. It is not useful in my situation.

---

### Post by dcstar on 2006-02-14
[QUOTE=JariHuomo]Yes, I now that trick :) I have tried that. It is not useful in my situation.[/QUOTE]
You still have IPv6 on your network card, unless you are using it you should remove it (and I am **not** talking about Firefox).

---

### Post by HiSpeed15 on 2006-02-14
[QUOTE=plexi50]This might help. Try to disable ipv6 following these instructions 
 
[https://wiki.ubuntu.com/WebBrowsingS...ght=%28IPv6%29]("https://wiki.ubuntu.com/WebBrowsingS...ght=%28IPv6%29")[/QUOTE]


:D Holy Smokers LOL I just shut down ipv6 with these inst  and doubled the speed just like that!!  Thank You!!

---

### Post by JariHuomo on 2006-02-14
thanks for the info. I tried to do this -->

Disabling IPv6

   1.

       sudo gedit /etc/modprobe.d/aliases 
   2.

      Find the line:  alias net-pf-10 ipv6 
   3.

      Replace it with:  alias net-pf-10 off 
   4.

      Save the file and restart your computer

Did not help me.. :cry:

---

### Post by JariHuomo on 2006-02-14
sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Link detected: yes

Like it says, duplex is only "HALF". How to force it to use full-duplex?

---


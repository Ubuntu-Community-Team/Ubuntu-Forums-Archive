---
title: "Wireless problem with Breezy"
date: 2005-11-22
forum: Desktop Environments
---

### Post by rado_london on 2005-11-22
Hi
Im one happy ubuntu user..............until today. I have wireless network at home. I use NETGEAR router. When the WPA was disabled I hadn't got problems with connecting from my HP Pavilion(the card is Intel Pro Wirelee 2200 BG).Then I booted into Ubuntu and.....no internet at all.I configured the eth0 with the WEP key, I tried everything but it still doesnt work. IN windows it works.I was thinking of going back to unsecured WLAN but I have a neighbour who has WLAN as well and probably can connect to mine.
If someone had this problem I found the solution please post it here.

Best Regards
Radoslav

---

### Post by dodongo on 2005-11-22
Can you go to the terminal and type 'ifconfig' and paste the results here?  I'm not familiar with your exact type of wireless card, but maybe if something's way off, I can help :)

---

### Post by rado_london on 2005-11-22
This my ifconfig info
```
rado@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:F0:DC:33:66
          inet6 addr: fe80::212:f0ff:fedc:3366/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xc000 Memory:b0106000-b0106fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
Hope this will help:D

---

### Post by buldir on 2005-11-23
Did you enter your WEP key as:

XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX

(for 128-bit), including the dashes into your /etc/network/interfaces file? Did you also include your network essid? I had problems connecting to my wifi router until I entered my key including the dashes.

---

### Post by rado_london on 2005-11-23
No I didnt. My WEP is 11 characters-xxxxxxxxxxx. What is the correct place of the dashes?

---

### Post by mrmcctt on 2005-11-23
Not sure where to go with this but unless all you have on the laptop is the wireless then your wireless isn't even set up.  All your ifconfig is showing is the ethernet.  

Here's my ifconfig.  ath0 is my wireless.  

```
rlodge@ubuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fec1:a559/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18356 errors:647 dropped:0 overruns:0 frame:647
          TX packets:14356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:26352754 (25.1 MiB)  TX bytes:1189086 (1.1 MiB)
          Interrupt:18 Memory:d8b80000-d8b90000

eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet6 addr: fe80::202:3fff:fed5:779c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:73391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7117203 (6.7 MiB)  TX bytes:7117203 (6.7 MiB)

rlodge@ubuntu:~$

```

Check out [THIS LINK]("http://www.ubuntuforums.org/showthread.php?t=26623") for setting up the wireless card.

Hope this helps

---

### Post by dodongo on 2005-11-23
In the System -> Administration -> Networking menu, do you see a wireless card identified there?

I was also suspicious of how only eth0 came up in your ifconfig output.  The link in the post above should help you out.

---

### Post by aaarg on 2005-11-23
[QUOTE=dodongo]In the System -> Administration -> Networking menu, do you see a wireless card identified there?
[/QUOTE]

along the same lines as dodongo mentioned....is it possible you configured it (properly i assume) and just didnt activate the wireless connection?

---

### Post by ColdWind on 2005-11-23
Did you install the drivers for your card? Maybe you should check a how to about ndiswrapper. [Here's one of them]("http://ubuntuforums.org/showthread.php?t=31926").

---


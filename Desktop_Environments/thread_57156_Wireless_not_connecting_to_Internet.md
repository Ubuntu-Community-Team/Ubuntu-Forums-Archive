---
title: "Wireless not connecting to Internet"
date: 2005-08-15
forum: Desktop Environments
---

### Post by snappieT on 2005-08-15
First off, I'm fairly new to Linux, and definately to Ubuntu. I'm on a Dell Inspiron 8600c laptop, with an Intel PRO/Wireless 2200BG integrated wireless network card. My router is a Buffalo WBR-G54 (European Edition), which is handling the PPPoE for my RADSL connection. The wireless network is 128b WEP.

From Windows XP Pro SP2, all works fine.

From Ubuntu, it connects to the router, signal strength > 90%, and I can ping the router and other computers on my network, but I cannot ping through the router, nor call up webpages etc.

I'd greatly appreciate your help on this,

snappieT

---

### Post by PeP on 2005-08-15
post the result of (if ath0 is the name of your card, replace it with eth0/eth1/wlan0 ... depending on your driver)
/sbin/ifconfig ath0
/sbin/iwconfig ath0
/sbin/route

feel free to change ip adresses , wep keys , network id or any other personal stuff in the output

---

### Post by snappieT on 2005-08-15
[QUOTE=PeP]post the result of (if ath0 is the name of your card, replace it with eth0/eth1/wlan0 ... depending on your driver)
/sbin/ifconfig ath0
/sbin/iwconfig ath0
/sbin/route

feel free to change ip adresses , wep keys , network id or any other personal stuff in the output[/QUOTE]
 PeP
Thanks for your quick response. When I exited Windows and booted back into Ubuntu, it actually seems to have resolved itself.

Anyway, for whatever reference purposes:
```
root@APPLE:/home/stephen # /sbin/ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:0E:35:54:D5:48
          inet addr:192.168.11.3  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe54:d548/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:25195 (24.6 KiB)  TX bytes:7072 (6.9 KiB)
          Interrupt:7 Memory:faffc000-faffcfff

root@APPLE:/home/stephen # /sbin/ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:0E:35:54:D5:48
          inet addr:192.168.11.3  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe54:d548/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:25195 (24.6 KiB)  TX bytes:7072 (6.9 KiB)
          Interrupt:7 Memory:faffc000-faffcfff

root@APPLE:/home/stephen # /sbin/iwconfig eth1
eth1      IEEE 802.11g  ESSID:"Fruit Bowl"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:07:40:F2:23:75
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:736E-6170-7363-616E-3132-3132-70   Security mode:open
          Power Management:off
          Link Quality=68/100  Signal level=-52 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:39

root@APPLE:/home/stephen # /sbin/route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth1
default         192.168.11.1    0.0.0.0         UG    0      0        0 eth1

```

---


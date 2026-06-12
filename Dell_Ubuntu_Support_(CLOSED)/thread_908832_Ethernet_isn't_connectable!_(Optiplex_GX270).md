---
title: "Ethernet isn't connectable! (Optiplex GX270)"
date: 2008-09-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by FJGamer on 2008-09-02
I've searched and all I saw was a little help using two connections to browse the web. I frequently FTP to my Xbox game console in Windows. No problem there. However, in Ubuntu, I can't get it to connect. It knows the ethernet port is there. It just can not connect to the Xbox's address, which is 192.168.0.2... if that matters.

Now, to hurry assistance, I'm on the Dell Optiplex GX270, the big tower one. I'm not sure if I need to download some kind of driver for the ethernet port or not. Again, please, help me connect to my Xbox without booting up Windows.

If you need more information, tell me.

---

### Post by mellowd on 2008-09-02
Is the port itself up? Are you able to ping the xbox? Type this and paste the output here

```
ifconfig
```

---

### Post by FJGamer on 2008-09-02
I did the ping method through Terminal and got nothing. It does work in Windows but only when I manually set the IP. I'm not sure why. Anyway, here's what you asked for:

```
eth0      Link encap:Ethernet  HWaddr 00:0d:56:04:4b:28  
          inet6 addr: fe80::20d:56ff:fe04:4b28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:64 (64.0 B)  TX bytes:492 (492.0 B)
          Base address:0xcdc0 Memory:fe8e0000-fe900000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47208 (46.1 KB)  TX bytes:47208 (46.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:0e:4c:24:35  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:eff:fe4c:2435/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10417389 (9.9 MB)  TX bytes:448736 (438.2 KB)
          Interrupt:18 Memory:fe8dfe00-fe8dfe25
```

I can't really decipher that junk (except the port names), so any explanation is welcome.

---


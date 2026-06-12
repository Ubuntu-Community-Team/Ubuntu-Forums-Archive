---
title: "Dell E1505 Boot Hesitation at Ubuntu Splash screen"
date: 2007-09-29
forum: Dell  Ubuntu Support
---

### Post by Mavtech on 2007-09-29
I've been searching for almost a week on this.  Still haven't resolved it.  

During boot where the orange bar is going across, it sits about half way for about 2 minutes before finishing up.  Anyone have any idea how to resolve this?  Thanks.

---

### Post by MobiusNZ on 2007-09-29
Press alt-f1 while booting... this will show you what its doing while booting.. then you have a bit more to go on

---

### Post by Mavtech on 2007-09-29
Thanks.  It did give me more info.  Here is where it's hanging.

[15.600000] Intel_rng:  FWH not detected

---

### Post by MobiusNZ on 2007-09-30
Google thinks its something to do with [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/102982")

---

### Post by Mavtech on 2007-10-01
I take that back.  I checked 2 more times.  It's hanging at "Initializing Network Interfaces".

---

### Post by MobiusNZ on 2007-10-01
Please post your /etc/network/interfaces and the output of ifconfig...

---

### Post by AJL on 2007-10-02
I am having the exact same issue, so here is my interfaces and ifconfig
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

```

--------@badonkadonk:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:75:EA:7E  
          inet addr:192.168.5.58  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe75:ea7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2659439 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2569329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:631873 txqueuelen:1000 
          RX bytes:929350534 (886.2 MiB)  TX bytes:248604145 (237.0 MiB)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:48:F6:9C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1900 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x2000 Memory:ecfff000-ecffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:59601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:127414783 (121.5 MiB)  TX bytes:127414783 (121.5 MiB)


```

---

### Post by MobiusNZ on 2007-10-02
AJL, as far as I can see that looks perfectly normal there. It's probably something to do with DHCP. Either your DHCP server is acting up and taking it's time, or your computer is trying to get an address for an interface that isn't connected.

Open up a terminal and type ```
sudo /etc/init.d/networking restart
```
That should restart the DHCP process, and give you a bit more info about what its doing and where it is hanging.

---

### Post by Sandlst on 2007-10-03
Hey, I have a E1505 that hesitated on boot (but not as long as two minutes) so in case the same thing happened to you, I fixed it by commenting out the network interfaces except the first one, so instead of ```
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
You should have:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```
Maybe worth a try?

---

### Post by AJL on 2007-10-03
What does that do when I want to connect to my wifi network?  Or my LAN at work?

---

### Post by notwen on 2007-10-03
Does it flicker by chance and you see services starting up and right before GDM greets you w/ a login screen you see a service fail?

---

### Post by Sandlst on 2007-10-03
> **AJL said:**
> What does that do when I want to connect to my wifi network?  Or my LAN at work?
I'm not that technical so I don't really know what it does.  My wireless still works after doing it though, and it is easy enough to reverse if it screws something up.

---

### Post by MobiusNZ on 2007-10-03
If you use NetworkManager or KNetworkManager you will be fine with all entries commented out (except loopback)

---

### Post by AJL on 2007-10-04
Ok, the dhcp thing was a red herring for my case i believe.  I alt-f1'd into  verbose boot mode and it hangs on the KINIT process looking for a previous image to resume. 

Any ideas there?

---


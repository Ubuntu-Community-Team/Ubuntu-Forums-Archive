---
title: "(Wireless) Static Vs DHCP - THE BIG SHOWDOWN"
date: 2006-01-15
forum: General Help
---

### Post by wannabelinuxconvert on 2006-01-15
Hi,

In Gnome, when I set up my USB wirelss card to connect to the wireless router via DHCP, everything runs fine ... and if I 'ifconfig' I get the following ...
```

wlan0     Link encap:Ethernet  HWaddr 00:30:BD:63:72:55
              inet addr:10.0.1.5  Bcast:255.255.255.255  Mask:255.255.255.0
              inet6 addr: fe80::230:bdff:fe63:7255/64 Scope:Link
              UP BROADCAST RUNNING  MTU:1500  Metric:1
              RX packets:23092 errors:0 dropped:0 overruns:0 frame:0
              TX packets:16635 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:29384753 (28.0 MiB)  TX bytes:1714567 (1.6 MiB)

```

But if I set up the card to use the static IP address of 10.0.1.5 (or any given in the range set by the router) I get a connection refused error. The values I enter are as follows ...

IP Address           : 10.0.1.5
Subnet Mask       : 255.255.255.0
Gateway Address: null

The setup will accept this, and when I run 'ifconfig' again I get the following ...
```

wlan0     Link encap:Ethernet  HWaddr 00:30:BD:63:72:55
              inet addr:10.0.1.5  Bcast:10.255.255.255  Mask:255.255.255.0
              inet6 addr: fe80::230:bdff:fe63:7255/64 Scope:Link
              UP BROADCAST  MTU:1500  Metric:1
              RX packets:23039 errors:0 dropped:0 overruns:0 frame:0
              TX packets:16605 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:29375065 (28.0 MiB)  TX bytes:1711414 (1.6 MiB)

```

Which on the surface looks the same, except for some reason the Bcast value has changed from 255.255.255.255 to 10.255.255.255 !?

Does anyone know why this is, and how I can manually change it back !?

Cheers

Mic

---

### Post by healychan on 2006-01-15
I believe that you can change the Bcast address by ifconfig.

Read "man ifconfig" and see what flag you should use.

> But if I set up the card to use the static IP address of 10.0.1.5 (or any given in the range set by the router) I get a connection refused error. The values I enter are as follows ...

IP Address : 10.0.1.5
Subnet Mask : 255.255.255.0
Gateway Address: null

The Gateway address should not be null, it should be the address of your router. I guess it is "10.0.1.1"
I believe this cause you the error.

If your router support DHCP, why would you set it up manually.:rolleyes:

---

### Post by wannabelinuxconvert on 2006-01-15
healychan,

Great advice, setting the Gateway address to the router IP sorted it right out :p , thank you so much.

The reason I need a static IP is there are several computers on the network, and I need to redirect all port 80 and port 25 requests on the router to this linux box, so need the static ip for the rules setup.

Thanks once again.

Mic

---

### Post by healychan on 2006-01-16
As far as I know, DHCP server will allocate an IP to a machine during the first connetion. Since than, the DHCP server can remembers the machine and gives the same IP as last session.

Therefore, the IP of your box should be always 10.0.1.5.

I don't know how your router works but my router will do so. The IP of my laptop is always "xxx.xxx.x.5".

---

### Post by wannabelinuxconvert on 2006-01-16
The router allocates IP's on a first come by serve basis, so if I logged on first yesterday I would have 10.0.1.2 but if I log on last I would have been given 10.0.1.19.

Mic

---


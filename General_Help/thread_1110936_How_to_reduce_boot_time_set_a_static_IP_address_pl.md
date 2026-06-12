---
title: "How to reduce boot time set a static IP address please"
date: 2009-03-30
forum: General Help
---

### Post by franco81 on 2009-03-30
Hi,

My boot times have been up in the 100+ seconds range for a while. I installed boot chart and it seems that a lot of time is spent on dhclient3 and ntpd.

I changed the boot for ntpd according to this page: [https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/224665](https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/224665) the comment from Will Uther.

But the load time was still very long. I tried setting a static IP address for eth1 (my wireless card I think) - but then the connection does not work because I don't really know what I'm doing there.

Can someone help me diagnose my long boot times and set up the static IP address, mostly I don't know what settings I should have for:
=> Network ID: 192.168.1.0
=> Broadcast IP: 192.168.1.255

I think I have the IP, netmask and router addresses correct, not sure about the DNS address which seems to be set to point to my router at the moment?

reference:
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by hyper_ch on 2009-03-30
use dhcp, boot your computer, open a terminal and run

```

ifconfig

```
and paste the output here.

---

### Post by franco81 on 2009-03-30
I managed to get the static IP address configured via the GUI dialog in system->admin->network. But still unsure about how to get all these details extracted from the below:

=> Host IP address 192.168.1.5
=> Netmask: 255.255.255.0
=> Network ID: ?
=> Broadcast IP: 192.168.1.255
=> Gateway/Router IP: ?
=> DNS Server: ? 

The gateway and dns server IPs I set both to point to my router at 192.168.1.1

> 
eth0      Link encap:Ethernet  HWaddr 00:1b:38:a8:69:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:217 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:1c:bf:22:7c:5c  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe22:7c5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:171350 (167.3 KB)  TX bytes:44416 (43.3 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:1b:38:a8:69:16  
          inet addr:169.254.4.150  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:217 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5376 (5.2 KB)  TX bytes:5376 (5.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-22-7C-5C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Even with teh static IP I still have a long boot time ~90seconds. Looks like avahi-autoipd.

I have attached my boot charts, number 5 is with static IP number 6 with DHCP and having made this change: [http://blog.dotkam.com/2008/08/06/speed-up-ubuntu-boot-time-by-starting-networking-on-the-background/](http://blog.dotkam.com/2008/08/06/speed-up-ubuntu-boot-time-by-starting-networking-on-the-background/)

I would like to keep dhcp as its my laptop.

Thanks for any help.

---

### Post by hyper_ch on 2009-03-30
set as gateway/router and dns server:  192.168.1.1

---

### Post by franco81 on 2009-03-30
> **hyper_ch said:**
> set as gateway/router and dns server:  192.168.1.1
Hmm, I did try those settings but the boot is still slow... If it isn't dhclient3 then its avahi-autoipd...

I'd love to know how to reduce the time these tasks take...

---

### Post by hyper_ch on 2009-03-30
well, if you don't use dhcp then you don't need avahi

---


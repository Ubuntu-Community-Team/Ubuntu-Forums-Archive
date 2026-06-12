---
title: "(Just Installed 5.10) No network"
date: 2005-10-17
forum: Desktop Environments
---

### Post by dzonekl on 2005-10-17
Hello, 

I installed Ubuntu for the first time (ever). I have another 2 windows PC's which nicely get a DHCP address from my router/dsl combo. So far so good as my ubuntu box also gets an IP address with DHCP. The router is setting up the PPPOE connection. 

eth0 is enabled and configured, but for some reason it seems packets are not routed to the box. (DNS resolves, I can see in Networking Tools using the Lookup function). So firefox hangs on "connecting to www......"

Propably a newbie stupid question, but would appreciate some help on what is going on? Do I need to do anything after installing Unbuntu? 

Thanks / Christophe

---

### Post by Karasu Tengu on 2005-10-17
Hi mate,
what does "ifconfig eth0" gives you?
did it give you an ip address?
If not, try Re-activating your Ethernet conection

---

### Post by dzonekl on 2005-10-17
Yeah, that's the weird thing. I do get an IP from my DHCP range on the router. It just doesn't want to route the packets back or something....

---

### Post by Karasu Tengu on 2005-10-17
have you tryed simple ping command?
can you ping other computer on your network?
have you installed a firewall?
have you tryed "apt-get update" does it connect?

---

### Post by cytoplasm on 2005-10-17
dzonekl,

Can you ping other IP addresses on your network? (like Karasu  said)
Can you ping your router?
Can you ping your gateway?
Can you ping your DNS servers?

What is in your /etc/resolv.conf file?
cat /etc/resolv.conf
  
Try to renew your dhcp lease:
dhcp-client -w

---

### Post by XekaLula on 2005-10-17
I had exactly the same issue. I could resolve the problem by disabling ipv6 in firefox. Type about:config into the firefox Location field. Then set the filter to 'ipv6'. Toggle the value to false.

Lu

---

### Post by dzonekl on 2005-10-17
Here is an update. 

- Can't ping any IP in my private range 192.168.1/24 except the gateway (.1)
This is I think because of firewall on windows box. I can access my apache
server on the windows box. 
- resolv.conf contains my gateway address 192.168.1.1 
- When I type nslookup [www.jpodder.com](www.jpodder.com), I get the IP of this domain. (66.152.98.202) Can't ping, but this is ICMP blocking on the router I suspect.
- I haven't installed a firewall. This is a clean install.
- DNS is forwarded to the gateway/router. This seems to work. (See above). 
- The router/modem is aztech.
- dhcp-client -> Command Unknown
- sudo apt-get update -> Reading package lists...Done (Very quick). 
- disable network.dns.disableIPv6 in firefox SOLVES THE PROBLEM. 
- I can't logon to GAIM -> MSN (could be account issue). 

Is this a serious misconfig of firefox? I would tend to think so. 
Thanks everyone for helping! 

CHeers / Christophe

---

### Post by dzonekl on 2005-10-18
It's getting frustrating....
Firefox now works, but none of the other network apps I am trying are working. 
This is all which fails: 
- Gaim
- Mail (Evolution)
- Apt-Get

Is there a way to get Unbuntu networking working? 
Thanks. 

ps. My objective is to test and release my application jPodder on Ubuntu/Linux.
So anyone helping out would benefit, as this wonderfull podcasting client
would be tuned for this OS.  More on jpodder at [http://www.jpodder.com](http://www.jpodder.com)

---

### Post by jonbuck on 2005-10-18
I know this doesn't help but I am experiencing exactly the same problems, I also have turned off IPv6 support in firefox which means I can browse the web but it does mean that nothing can connect to the net like mail, can't install other applications like bluetooth support as that needs the net.  I think somehow we need to work out how to turn off IPv6 in the OS!

---

### Post by dzonekl on 2005-10-18
It does help!
 
I was thinking in the same direction, I can see in ifConfig that 
a IPv6 is address is assigned to eth0. 

Any good idea how to remove iwth ifConfig del ???

 eth0      Link encap:Ethernet  HWaddr 00:01:6C:B5:73:E4
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:6cff:feb5:73e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2813337 (2.6 MiB)  TX bytes:477058 (465.8 KiB)
          Interrupt:19 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2066589 (1.9 MiB)  TX bytes:2066589 (1.9 MiB)

Cheers / Christophe

---


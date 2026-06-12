---
title: "How do I connect to the internet from my Ubuntu box through Win XP?"
date: 2006-04-30
forum: Desktop Environments
---

### Post by cburner on 2006-04-30
I have a router between the two computers. I am able to see the windows computer from the ubuntu computer. I am still unable to connect to the internet. When I enable ICS on windows computer the network freezes.

Before I installed ubuntu on the desktop, I was able to connect windows to the internet through a proxy server.  Can't get ubuntu connected through the same proxy server. Can anyone help me?

---

### Post by pappo on 2006-04-30
On my home system I have a router also.  I have on XP machine and one Ubuntu box.  My router is connected to my cable modem and its IP address is the default 192.168.0.1  My router has four output ports besides the WAN connection to the cable modem.    All I did was tell my Ubuntu network connection that my gateway was 192.168.0.1 and it connected.
Now that was when I was using a static (fixed) IP address for my Ubuntu box.

Later on I got a router that had DHCP capabilities.  Then all I did was set it up  to distribute DHCP addresses and then on the Ubuntu and my XP boxes I told the network card to use DHCP.  It all just worked.

---

### Post by cskeide on 2006-04-30
Are you sure you have a router between your computers? Do you mean a hub/switch? How do you connect to the internet? If you actually have a router, one would think that the router connects to the internet and assigns ip-addresses to your computers. In that case, you would have to configure ubuntu to use dhcp. However, if you connect to the internet with your windows computer directly, and you have a hub between the computers, you would most likely have to assign static ip-addresses to your computers.

I would need more information about your setup, in order to answer this question in a better way. Could you please post the output of:
```
cat /etc/network/interfaces
ifconfig -a
cat /etc/resolv.conf
```

---

### Post by cburner on 2006-04-30
I connect through a dialup modem.  That is why I used a proxy server.  I entered everything into the ubuntu computer as the proxy server stated but no internet still.

---

### Post by cburner on 2006-04-30
[I]cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface ppp0 inet ppp
provider ppp0

auto eth0


ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:41:EB:2E:C4
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:feeb:2ec4/64 Scope:Link  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4442 errors:0 dropped:0 overruns:0 frame:0     
          TX packets:2400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:473878 (462.7 KiB)  TX bytes:207291 (202.4 KiB)
          Interrupt:11 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64209 errors:0 dropped:0 overruns:0 frame:0         
          TX packets:64209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5596966 (5.3 MiB)  TX bytes:5596966 (5.3 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



cat / etc/resolv.conf
search gateway.2wire.net
nameserver 192.168.1.254[/I]


Hope this helps.

---

### Post by cskeide on 2006-04-30
This looks alright to me. The only thing is the dhcp option in /etc/interfaces... Does the windows machine work as a dhcp server?

I'm also guessing that 192.168.1.254 is your windows computer...

Try these commands:
```
ping 192.168.1.254
nslookup www.ubuntuforums.org
ping 82.211.81.186
```

---

### Post by cburner on 2006-05-01
ping 192.168.1.254 worked fine

nslookup [www.ubuntuforums,org](www.ubuntuforums,org) was refused

ping 82.211.81.186 destination unreachable

---

### Post by cskeide on 2006-05-02
Ok. It seems like your computer running ubuntu is configured correctly, but your windows machine fails to share its internet connection. Since you are able to ping your DNS (which in this case is your windows box), this suggests that whatever DNS service you are trying to run doesn't work. The same goes for the routing of packages.

You can also check to see if your ubuntu is set up to use the correct gateway, by running "route". I'm guessing 192.168.1.254 is your default gateway.

You said in your initial post that when you enable ICS on the windows computer the network freezes. Can you explain what you mean by freezes? And are you infact able to enable the service? You also said that this was working before you installed ubuntu. Are you able to enable ICS, when the network cable between your computers is unplugged?

I'm sorry if we are going in circles here, but I'm running out of suggestions, since I haven't used windows as a gateway for several years now.

---

### Post by cburner on 2006-05-02
The network freezes by me not being able to access the shared folder on the other computer.

I am new to Ubuntu so bear with me.

I will check route in a few minutes.

When I stated this was working before, I had to install a proxy server "CCProxy" and turn off ICS. That was when windows was installed on the ubuntu machine.  I tried using the proxy server with ubuntu and still did not get to the internet.

---


---
title: "Need help with setting up my internet connection"
date: 2006-03-27
forum: Desktop Environments
---

### Post by bpont on 2006-03-27
I have a dual boot Windows 98 / Hoary Hedgehog system.  Recently, I had my cable provider hook me up with a cable modem (I had dial up before and installed Ubuntu without any internet connectivity).  There was no special software installed on my Windows 98 system to get online.  The technician just plugged the modem into my network card and I was good to go.  However, when I boot into Ubuntu, I still don't have any internet access for some reason.  I hit the #Ubuntu channel to get help and tried everything I was advised to do, but still no luck.

_Here is a summary of some of the IRC advice / output:_

[I]amphi: in a term, try 'host google.com' without quotes and see if it resolves the ip address
amphi	if it doesn't, cat /etc/resolv.conf to see if any nameservers are configured

bpont@pooose:~$ host google.com;; connection timed out; no servers could be reached
bpont@pooose:~$ cat /etc/resolv.conf search cable.rcn.com nameserver 207.172.3.8 nameserver 207.172.3.9

nickrud: try ping 207.172.3.8

bpont@pooose:~$ ping 207.172.3.8
connect: Network is unreachable[/I]

I called up my cable provider and explained what I was trying to do, but they didn't seem too technically proficient at what I was asking about, but they did end up giving me the DNS address.

I'm not much of a hacker, so if anyone can help me solve this issue and get me connected with the rest of the world, so I can surf w/ Firefox under Ubuntu and be able to apt-get too, that would be greeeeeat!!!  ](*,)

---

### Post by jamesr on 2006-03-27
post the outputs of```
sudo ifconfig -a
dmesg |grep eth0
```

This will help to see if the NIC is recognised

---

### Post by Buffalo Soldier on 2006-03-28
I'm not sure if this is how it's done in Windows 98, it's been too long ago. But in Windows XP, type the command **ipconfig /all** at the command prompt, it will display your network details such as IP address, gateway and DNS.

---

### Post by bpont on 2006-03-28
[QUOTE=jamesr]post the outputs of```
sudo ifconfig -a
dmesg |grep eth0
```

This will help to see if the NIC is recognised[/QUOTE]

Thanks...here is the output I got after executing the commands:

```
sudo ifconfig -a
```

[COLOR="Red"]
eth0   [INDENT] Link encap:Ethernet  HWaddr 00:50:BF:19:83:9E
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe800[/INDENT]

lo       [INDENT] Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:35568 (34.7 KiB)  TX bytes:35568 (34.7 KiB)[/INDENT]

sit0     [INDENT]Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/INDENT][/COLOR]

```
dmesg |grep eth0
```

[COLOR="Red"]eth0: RealTek RTL8139 at 0xe800, 00:50:bf:19:83:9e, IRQ 11
eth0:  Identified 8139 chip type 'RTL-8139B'[/COLOR]

What now??

---

### Post by bpont on 2006-03-28
[QUOTE=Buffalo Soldier]I'm not sure if this is how it's done in Windows 98, it's been too long ago. But in Windows XP, type the command **ipconfig /all** at the command prompt, it will display your network details such as IP address, gateway and DNS.[/QUOTE]

Thanks Buffalo...I executed the command and got a bunch of useful output.  What am I supposed to do with it?

---

### Post by jamesr on 2006-03-28
Try the following```
sudo dhclient eth0
```and post output please

---

### Post by bpont on 2006-03-28
[QUOTE=jamesr]Try the following```
sudo dhclient eth0
```and post output please[/QUOTE]

Output:

```
sudo dhclient eth0
```

[COLOR="Red"]
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:50:bf:19:83:9e
Sending on LPF/eth0/00:50:bf:19:83:9e
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 216.220.64.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 216.220.64.1
bound to 216.220.64.226 -- renewal in 20458 seconds.[/COLOR]

What now?

---

### Post by jamesr on 2006-03-28
The last reply especially the section,> Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 216.220.64.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 216.220.64.1
bound to 216.220.64.226 -- renewal in 20458 seconds.

 seem to indicate that it now has a TCP/ip address

see if you can ping various addresses```
ping www.google.com
ping xxx.xxx.xxx.xxx
``` where xxxx.xxx.xxx.xxx is the DNS address of your ISP

---

### Post by bpont on 2006-03-29
[QUOTE=jamesr]The last reply especially the section, seem to indicate that it now has a TCP/ip address

see if you can ping various addresses```
ping www.google.com
ping xxx.xxx.xxx.xxx
``` where xxxx.xxx.xxx.xxx is the DNS address of your ISP[/QUOTE]

OK, James...for the first time ever I am surfing the web with Firefox under Ubuntu!  BUT...  Originally, when I followed your instructions I got this:

[COLOR="Red"]bpont@pooose:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
bpont@pooose:~$ ping 216.220.64.1
connect: Network is unreachable[/COLOR]

Then I executed these commands with the following results:

[COLOR="Red"]bpont@pooose:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:50:bf:19:83:9e
Sending on   LPF/eth0/00:50:bf:19:83:9e
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 216.220.64.1
bound to 216.220.64.226 -- renewal in 10038 seconds.
bpont@pooose:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (72.14.203.99) 56(84) bytes of data.
64 bytes from 72.14.203.99: icmp_seq=1 ttl=247 time=12.1 ms
64 bytes from 72.14.203.99: icmp_seq=2 ttl=247 time=10.6 ms
64 bytes from 72.14.203.99: icmp_seq=3 ttl=247 time=9.80 ms[/COLOR]

After this successful ping of Google I fired up Firefox and here I am posting this under Ubuntu, finally.  

Therefore, this whole problem must be a root priviledge / user group issue I imagine.  I'm not too polished on those skills, so how do I 'authorize' my user to surf the internet and execute apt-get commands, etc. without doing this 'sudo' ritual each time?  

Thanks for getting me this far!  :D

---

### Post by sdide on 2006-03-29
Hi bpont, 

Could you post the content of your /etc/network/interfaces.

---

### Post by bpont on 2006-03-29
[QUOTE=sdide]Hi bpont, 

Could you post the content of your /etc/network/interfaces.[/QUOTE]

bpont@pooose:~$ cat /etc/network/interfaces

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

iface ppp0 inet ppp
provider ppp0

---

### Post by jamesr on 2006-03-29
You need to modify the file /etc/network/interfaces
Current file
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

iface ppp0 inet ppp
provider ppp0

Change to > # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

[COLOR="Red"]auto eth0
iface lo inet dhcp[/COLOR]

iface ppp0 inet ppp
provider ppp0

Using ```
sudo nano /etc/network/interfaces
```

---

### Post by bpont on 2006-03-29
James, I did what you said, but it didn't work.  These are the contents of my current /etc/network/interfaces for verification:

```
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

auto eth0
iface lo inet dhcp

iface ppp0 inet ppp
provider ppp0
```

Also, during startup, I see the following messages on my screen:

```
Configuring network interfaces................FAIL

ror : Temporary failure in name resolution.............FAIL
```

It's not until I execute:

```
sudo dhclient eth0
```

and enter my root password that I'm able to connect to the internet.

Any more suggestions?

---

### Post by jamesr on 2006-03-29
Sorry but I made a mistake because the line

iface lo inet dhcp

should have read 

iface eth0 inet dhcp

Sorry about this but I did a copy and paste but did not do all of the edits.

---

### Post by bpont on 2006-03-29
No apologies necessary, Jim...an honest oversight...made your suggested correction and SUCCESS...problem solved...thanks!

Here's the contents of my ***/etc/network/interfaces*** file, for the record, in case some other poor soul can benefit from our efforts:

```
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

auto eth0
iface eth0 inet dhcp

iface ppp0 inet ppp
provider ppp0
```

Thanks again!  =D>

---


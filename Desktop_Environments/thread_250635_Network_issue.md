---
title: "Network issue"
date: 2006-09-04
forum: Desktop Environments
---

### Post by motin on 2006-09-04
**Summary**
A few selected sites that I frequently use(d) are now unreachable by my machine, despite the fact that they are online and reachable by other (XP-powered) machines on the network... As well as on any other computer that I know of. 

**Background info**
It started to spook when we switched ADSL-provider to one that requires a PPPoE connection instead of having the router connecting directly. 

Instead of a router at 192.168.0.1 that handled the connection, I moved the router to 192.168.0.10 and instead set up one of the XP machines for PPPoE together with internet connection sharing at 192.168.0.1, letting the remaining machines keep it's config and continue using the internet. 

But... some sites were mysteriously not reachable from these machines.

Then I left the ICS-machine as it was but set-up direct PPPoE on all XP computers, which solved the issue there. 

It took a while to figure out how to do this on Ubuntu (the answer is using Automatix to install RP-PPPoE, a graphical PPPoE connection manager), but even now after successfully connecting over PPPoE (confirmed to be using the same DNS servers as the XP machines), those sites cannot be reached!

It is a most annoying problem since two of the affected sites are my University's schedule information system and the city's travel planner - that is everyday used sites, and now I have to use a XP computer to check them...

Will submit output of ifconfig, netstat -nr, arp -a and some ping's as soon as I come back to the problematic network. 

All tips appreciated!

---

### Post by wieman01 on 2006-09-04
You probably need to disable IPV6. I had similar problems before I disabled it and blacklisted the module.

---

### Post by wieman01 on 2006-09-04
Check this out:

[http://www.ubuntuforums.org/showthread.php?t=87798]("http://www.ubuntuforums.org/showthread.php?t=87798")

Fairly simple... In summary you have to edit this file:
> sudo gedit /etc/modprobe.d/aliases
And add/modify these lines:
> # Disabling ipv6
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
If you want to speed up Firefox by disabling IPV6, try this:

[http://www.ubuntuforums.org/showthread.php?t=249218&highlight=ipv6+firefox]("http://www.ubuntuforums.org/showthread.php?t=249218&highlight=ipv6+firefox")

---

### Post by motin on 2006-09-04
> **wieman01 said:**
> Check this out:

[http://www.ubuntuforums.org/showthread.php?t=87798]("http://www.ubuntuforums.org/showthread.php?t=87798")

Fairly simple... In summary you have to edit this file:

And add/modify these lines:

If you want to speed up Firefox by disabling IPV6, try this:

[http://www.ubuntuforums.org/showthread.php?t=249218&highlight=ipv6+firefox]("http://www.ubuntuforums.org/showthread.php?t=249218&highlight=ipv6+firefox")

Thanks both of you!

Reading those threads lead me to this: 
$ sudo -s
# echo alias net-pf-10 off > /etc/modprobe.d/bad_list

Rebooting in a sec to see how it turns out. 

(Btw, disabled ipv6 system-wide should automatically disable it in FF)

---

### Post by wieman01 on 2006-09-04
Disabling IPV6 system-wide won't impact Firefox... That's the crux. You'll have to disable it there in a separate step. But that's easily done.

---

### Post by motin on 2006-09-05
> **wieman01 said:**
> You probably need to disable IPV6. I had similar problems before I disabled it and blacklisted the module.

Home again and tested it all - still the same problem...

> **wieman01 said:**
> Disabling IPV6 system-wide won't impact Firefox... That's the crux. You'll have to disable it there in a separate step. But that's easily done.

I got that notion from one of the other threads, now I disabled it in FF as well - sadly to no success...

It is like these dns's have been cached in a problematic manner. Is there any such caches in Ubuntu and if there is, how do one reset them? Shooting in the wild here...

Here is some network info:

ifconfig -a:
```

eth0      Link encap:Ethernet  HWaddr 00:15:00:24:68:4F
          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20623 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:66149887 (63.0 MiB)  TX bytes:11494473 (10.9 MiB)
          Interrupt:201 Base address:0x6000 Memory:b0106000-b0106fff

eth1      Link encap:Ethernet  HWaddr 00:0A:E4:D9:EC:DF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0x8400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:26645 (26.0 KiB)  TX bytes:26645 (26.0 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:84.217.8.206  P-t-P:195.58.100.213  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:2713 errors:3237 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:358634 (350.2 KiB)  TX bytes:61 (61.0 b)

```

netstat -nr:
```
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
195.58.100.213  0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

```

route -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
195.58.100.213  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```

arp -a:
```
halvnya (192.168.0.1) at 00:02:A5:32:6A:94 [ether] on eth0

```

Some pings of problematic sites:
```

motin@laptop:~$ ping schema.sys.kth.se
PING timeedit.ad.kth.se (130.237.32.104) 56(84) bytes of data.

--- timeedit.ad.kth.se ping statistics ---
137 packets transmitted, 0 received, 100% packet loss, time 136377ms

motin@laptop:~$ ping timeedit.ad.kth.se
PING timeedit.ad.kth.se (130.237.32.104) 56(84) bytes of data.

--- timeedit.ad.kth.se ping statistics ---
9 packets transmitted, 0 received, 100% packet loss, time 8015ms

motin@laptop:~$ ping www.sl.se
PING www.sl.se (194.237.104.3) 56(84) bytes of data.

--- www.sl.se ping statistics ---
183 packets transmitted, 0 received, 100% packet loss, time 182423ms

motin@laptop:~$ ping sl.se
PING sl.se (194.237.104.3) 56(84) bytes of data.

--- sl.se ping statistics ---
158 packets transmitted, 0 received, 100% packet loss, time 157474ms

```

traceroutes (these are interesting...):
```

motin@laptop:~$ traceroute www.sl.se
traceroute to www.sl.se (194.237.104.3), 30 hops max, 40 byte packets
 1  halvnya (192.168.0.1)  1.989 ms  1.932 ms  2.000 ms
 2  * * *
 3  ge-1-2-0.0010.se-sthms001-pe-1.tu.telenor.net (195.58.100.221)  9.213 ms  9.034 ms  8.571 ms
 4  ge-0-0-0.se-suncs001-pe-1.tu.telenor.net (212.105.101.214)  14.846 ms  16.458 ms  14.442 ms
 5  netnod-ix-ge-b-svl-4470.skanova.net (194.68.135.111)  15.602 ms  16.885 ms  15.129 ms
 6  oes-b-c1-link.se.telia.net (81.228.73.222)  18.486 ms  17.319 ms  17.562 ms
 7  hy-c1-link.se.telia.net (81.228.73.247)  112.324 ms  190.321 ms  206.420 ms
 8  hy-c2-link.se.telia.net (81.228.72.215)  17.223 ms  18.375 ms  21.438 ms
 9  asp-a13-link.se.telia.net (81.228.72.81)  18.668 ms  17.748 ms  17.518 ms
10  sl-102797-am01.k.se.telia.net (212.181.255.206)  17.827 ms  18.270 ms  18.524 ms
11  www.sl.se (194.237.104.3)  18.349 ms  17.388 ms  17.575 ms
motin@laptop:~$ traceroute www.sl.se
traceroute to www.sl.se (194.237.104.3), 30 hops max, 40 byte packets
 1  halvnya (192.168.0.1)  1.985 ms  2.651 ms  27.139 ms
 2  * * *
 3  ge-1-2-0.0010.se-sthms001-pe-1.tu.telenor.net (195.58.100.221)  8.802 ms  9.508 ms  8.610 ms
 4  ge-0-0-0.se-suncs001-pe-1.tu.telenor.net (212.105.101.214)  14.513 ms  18.141 ms  13.774 ms
 5  netnod-ix-ge-b-svl-4470.skanova.net (194.68.135.111)  15.621 ms  15.451 ms  15.586 ms
 6  oes-b-c1-link.se.telia.net (81.228.73.222)  17.631 ms  17.750 ms  16.517 ms
 7  hy-c1-link.se.telia.net (81.228.73.247)  20.617 ms  16.379 ms  40.022 ms
 8  hy-c2-link.se.telia.net (81.228.72.215)  17.552 ms  17.649 ms  17.556 ms
 9  asp-a13-link.se.telia.net (81.228.72.81)  17.632 ms  23.285 ms  19.193 ms
10  sl-102797-am01.k.se.telia.net (212.181.255.206)  17.755 ms  24.935 ms  17.807 ms
11  www.sl.se (194.237.104.3)  16.602 ms  21.258 ms  17.626 ms

```

```
motin@laptop:~$ traceroute schema.sys.kth.se
traceroute to timeedit.ad.kth.se (130.237.32.104), 30 hops max, 40 byte packets
 1  halvnya (192.168.0.1)  3.389 ms  2.376 ms  6.748 ms
 2  * * *
 3  195.58.100.153 (195.58.100.153)  8.580 ms  9.282 ms  8.617 ms
 4  netnod-ix-ge-a-sth.sunet.se (194.68.123.19)  9.930 ms  9.228 ms  9.606 ms
 5  kth1-SRP1.sunet.se (130.242.85.67)  10.096 ms  8.591 ms  10.672 ms
 6  ea6-kth1-p2p.gw.kth.se (130.237.211.154)  11.724 ms  11.696 ms  9.606 ms
 7  ea4-ea6-p2p.gw.kth.se (130.237.211.117)  9.721 ms  9.414 ms  8.812 ms
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * *
forever...

```

```
motin@laptop:~$ traceroute ubuntuforums.org
traceroute to ubuntuforums.org (82.211.81.186), 30 hops max, 40 byte packets
 1  halvnya (192.168.0.1)  1.982 ms  27.152 ms  2.072 ms
 2  * * *
 3  195.58.100.153 (195.58.100.153)  9.310 ms  9.190 ms  8.622 ms
 4  213.242.110.1 (213.242.110.1)  9.128 ms  8.666 ms  8.799 ms
 5  ge-2-0-0.mp1.Stockholm1.Level3.net (4.68.125.217)  8.760 ms ge-0-0-0.mp1.Stockholm1.Level3.net (4.68.96.221)  9.417 ms ge-2-0-0.mp1.Stockholm1.Level3.net (4.68.125.217)  8.592 ms
 6  as-0-0.bbr2.London2.Level3.net (4.68.128.110)  37.077 ms  36.863 ms  37.752 ms
 7  ae-0-54.gar2.London2.Level3.net (4.68.117.107)  37.465 ms ae-0-56.gar2.London2.Level3.net (4.68.117.171)  36.939 ms  37.028 ms
 8  so-0-0-0.gar1.London2.Level3.net (4.68.124.69)  37.127 ms  38.292 ms  36.694 ms
 9  195.50.91.146 (195.50.91.146)  38.065 ms ge-6-1.core-r-1.lon2.mnet.net.uk (195.50.91.134)  37.403 ms ge-6-2.core-r-1.lon2.mnet.net.uk (195.50.91.138)  37.880 ms
10  vlan102.core-l-1.lon2.mnet.net.uk (62.140.218.201)  37.029 ms  36.918 ms  37.089 ms
11  85.133.32.130 (85.133.32.130)  40.043 ms  37.009 ms  38.055 ms
12  82.211.81.76 (82.211.81.76)  37.147 ms  37.984 ms  37.085 ms
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * *
forever
```

Some clearification: DHCP autmatically connects me to the ICS machine, and afterwards I start the RP-PPPoE connection program and initiates that connection. The DNS servers then change to 213.150.135.210 and 195.58.103.18 instead of 192.168.0.1

It looks like 1. All traffic still goes through the 192.168.0.1 gateway instead of directly through the PPPoE connection and 2. That the gateway sometimes just gives up on this client, leaving traceroutes hanging like that... (Even for ubuntuforums.org as you see, which also had me waiting 2 minutes before I could preview or submit this post...)

Please help once again...

Thanks!

---

### Post by motin on 2006-09-05
SOLVED

Solution:
1. Add a row with "defaultgateway" in /etc/ppp/options
2. Remove the existing default gateway via:
```
sudo route del default gw 192.168.0.1 eth0
``` 
3. Disconnect, reconnect the PPPoE connection

---

### Post by the lush on 2006-09-15
I have been experiencing what seems to be a very similar problem on my home machine. I installed Ubuntu on 4 machines at my workplace (1 server to connect to the internet, 1 Laptop (Acer Ferrari), 2 Desktops), and was able to succesfully download and run Automatix to install all the bits and bobs I wanted. When I tried the same thing on my home machine that connects via PPPOE, I have never been able to succesfully do this. 

I guessed the PPPOE thing was making the difference, so will try the above solution tonight on that machine. I'll report back if it works.

---

### Post by the lush on 2006-09-19
Well, I tried the above but couldn't get it to work. I gave up and took my machine to a place without pppoe in order to install Automatix. I will try to get Firestarter to sort this out, as it can configure things and may do a better job.

If anyone can give some real novice proof instructions to supplement Motin's that would be great. When I tried sudo route del default gw 192.168.0.1 eth0 all I got was an error message about there not being one.

---

### Post by motin on 2006-09-19
> **the lush said:**
> Well, I tried the above but couldn't get it to work. I gave up and took my machine to a place without pppoe in order to install Automatix. I will try to get Firestarter to sort this out, as it can configure things and may do a better job.

If anyone can give some real novice proof instructions to supplement Motin's that would be great. When I tried sudo route del default gw 192.168.0.1 eth0 all I got was an error message about there not being one.

I guess we didnt have the same problem to begin with. I was in a DHCP network that gave me a default gateway that wasnt working properly. But I could install Automatix and after PPPoE connection it was still using the faulty gateway. Then, my commands will solve it.

---

### Post by the lush on 2006-09-29
Ah, that would explain it then. I still have no idea how to fix the issue of pppoe connections not allowing me to use Automatix, so will try to pester the folk at Chunghwa Telecom to give me a new account where I don't need it. I think there was a mix-up when I upgraded to a faster connection a while back.

---


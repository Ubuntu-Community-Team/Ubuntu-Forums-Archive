---
title: "Can't log into router - IP conflict?"
date: 2009-03-04
forum: General Help
---

### Post by afrodeity on 2009-03-04
I had this problem a week ago, and it was fixed by pinging my ISP. Now, I can't even log into my router. This is after a 48hour XP session, and the ISP tells me its something to do with my profile and "why don't i get a bridge" or something and "call your dealer".

I can ping my router, and it pings, but not even able to log into the router, so it appears to have been taken over either by the technicians who shaped down my ports after I reached my cap, or by goodness knows what, a robot or hacker. Perhaps its an IP conflict, since I got this message when I went back to the XP for about 3 minutes and then it resolved on the XP side, but no go with Ubuntu.

What should I do? My XP setup is happily connecting to the internet, but my Ubuntu won't budge.:(

---

### Post by blazemore on 2009-03-04
Is there a "hard reset" button on your router? This will revert it to factory settings (including default password: Google this beforehand)

---

### Post by ryan.nabinger on 2009-03-04
XP works?  On the same network/subnet/default gateway?  Is this the same box.  

on ubuntu:
```

ifconfig
traceroute www.google.com

``` 

on XP:
```

ipconfig
tracert www.google.com

```

and post the output of both please.  Also if you can, try running a traceroute on your router to [www.google.com](www.google.com) (if you know how or can do this).

EDIT: (I added ifconfig and ipconfig)

---

### Post by afrodeity on 2009-03-05
Here is the ifconfig
afrodeity@afrodeity-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:74:13:a9  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe74:13a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21322907 (20.3 MB)  TX bytes:2637817 (2.5 MB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46276 (45.1 KB)  TX bytes:46276 (45.1 KB)


and traceroute for [www.google.com](www.google.com)

afrodeity@afrodeity-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:74:13:a9  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe74:13a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21322907 (20.3 MB)  TX bytes:2637817 (2.5 MB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46276 (45.1 KB)  TX bytes:46276 (45.1 KB)

The network is up but still can't log into my router. I've tried hard resetting to default but no go. It's pretty much stuck on the XP side, but at least I have internet even if my ISP owns me. :)

---

### Post by ryan.nabinger on 2009-03-05
looks like a copy-paste failure...

Getting the results of both a traceroute and a ifconfig from both the XP box and the Ubuntu box would be helpful.  I am assuming these are two different boxes.  Given that the ip you show in Ubuntu is a .2 I assume this ip was setup statically.  

Going on nearly nothing, I would say to check your /etc/resolve.conf file and make sure you have 'nameserver xx.xx.xx.xx' entries and that they are correct.

```

xxx@yyy# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.128 U     0      0        0 eth5
114.0.1.0       *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         172.22.34.1     0.0.0.0         UG    100    0        0 eth5

```

*note that my default gateway line.  yours should read 192.168.1.1 with Iface eth0.

---

### Post by afrodeity on 2009-03-05
Oops, that happens sometimes. Here is the correct tracer.

afrodeity@afrodeity-desktop:~$ traceroute [www.google.com](www.google.com)
traceroute to [www.google.com](www.google.com) (72.14.235.147), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  0.921 ms  1.326 ms  1.753 ms
 2  dsl-146-180-01.telkomadsl.co.za (165.146.180.1)  33.714 ms  42.910 ms *
 3  * * 196.43.35.57 (196.43.35.57)  102.949 ms
 4  * * *
 5  * * *
 6  * 196.43.33.5 (196.43.33.5)  50.077 ms  53.208 ms
 7  * * *
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
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

I think my default gateway is my router for some reason, I'll have a look at the /etc/resolve.conf. BTW the XP is on another partition.

---

### Post by afrodeity on 2009-03-05
nameserver 192.168.1.1
nameserver 192.168.1.1

Yes it is. This is the default IP for my router. 

kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by ryan.nabinger on 2009-03-05
So is the problem that you cannot telnet/ssh/http into your router or that you cannot reach the outside world?

Your traceroute indicates that your resolv.conf and your default gateway are setup correctly.  Also, it indicates that your router has no problem with NAT as you receive ICMP TTL Expired messages from nodes outside your network (the mechanism of traceroute).

I am at a loss for the moment, unfortunately, because it looks like you have no problem inbound and outbound through that router ...

---

### Post by dcstar on 2009-03-05
> **afrodeity said:**
> Oops, that happens sometimes. Here is the correct tracer.

afrodeity@afrodeity-desktop:~$ traceroute [www.google.com](www.google.com)
traceroute to [www.google.com](www.google.com) (72.14.235.147), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  0.921 ms  1.326 ms  1.753 ms
 2  dsl-146-180-01.telkomadsl.co.za (165.146.180.1)  33.714 ms  42.910 ms *
 3  * * 196.43.35.57 (196.43.35.57)  102.949 ms
 4  * * *
 5  * * *
 6  * 196.43.33.5 (196.43.33.5)  50.077 ms  53.208 ms
 7  * * *


I think my default gateway is my router for some reason, I'll have a look at the /etc/resolve.conf. BTW the XP is on another partition.

Post the output of these when in XP:

```
tracert www.google.com
ipconfig/all
```

---

### Post by afrodeity on 2009-03-06
I can't http into the router, but am connected to the outside world as you can see. The problem, as it turns out, started when I tested a new version of Puppy Linux :). The old version sits in a self-contained folder inside my Ubuntu. I updated, ran the network DHCP script and it seems to have solved the problem as far as connectivity is concerned. I know it sounds dangerous, but Puppy is possibly the fastest, smallest, Linux around and is designed to co-exist with other distros. 

But I still can't http into my router. This is troubling me, because I don't think its related to the Puppy Linux problem, but is something to do with my ISP, unless the Puppy has somehow taken over the routing with DHCP, and how is this possible if it doesn't exist in the same instance as Ubuntu?

 Will post you what I see when I'm in XP and will do the same for the Pup. Sorry if this seems totally backward, but we can all learn from this.

---

### Post by ryan.nabinger on 2009-03-06
Ah, so the problem is connecting to the router's UI.  Where I live the home-gateway (router) is controlled and maintained by the customer (you) so I would be surprised if your ISP has touched it.  Typically, the settings on your router wouldn't even allow them to http to the router through it's internet-facing port.

I am curious as to the XP settings of this box :popcorn:.  Are you using IE in XP and firefox in Ubuntu by chance?  What error message do you get when connecting to the router in Ubuntu?

---

### Post by afrodeity on 2009-03-08
Windows IP Configuration                                     
                                                             
                                                             
Ethernet adapter VMware Network Adapter VMnet8:              
                                                             
        Connection-specific DNS Suffix  . :                  
        IP Address. . . . . . . . . . . . : 192.168.171.1    
        Subnet Mask . . . . . . . . . . . : 255.255.255.0    
        Default Gateway . . . . . . . . . :                  
                                                             
Ethernet adapter VMware Network Adapter VMnet1:              
                                                             
        Connection-specific DNS Suffix  . :                  
        IP Address. . . . . . . . . . . . : 192.168.68.1     
        Subnet Mask . . . . . . . . . . . : 255.255.255.0    
        Default Gateway . . . . . . . . . :                  
                                                             
Ethernet adapter Local Area Connection:                      
                                                             
        Connection-specific DNS Suffix  . :                  
        IP Address. . . . . . . . . . . . : 192.168.1.2      
        Subnet Mask . . . . . . . . . . . : 255.255.255.0    
        Default Gateway . . . . . . . . . : 192.168.1.1      
                                                             
Ethernet adapter Hamachi:                                    
                                                             
        Connection-specific DNS Suffix  . :                  
        IP Address. . . . . . . . . . . . : 5.169.17.246     
        Subnet Mask . . . . . . . . . . . : 255.0.0.0        
        Default Gateway . . . . . . . . . :                  
                                                             
PPP adapter Telkomsa.net:                                    
                                                             
        Connection-specific DNS Suffix  . :                  
        IP Address. . . . . . . . . . . . : 165.146.181.23   
        Subnet Mask . . . . . . . . . . . : 255.255.255.255  
        Default Gateway . . . . . . . . . : 165.146.181.23

---

### Post by afrodeity on 2009-03-08
Tracing route to [www.l.google.com](www.l.google.com) [72.14.235.99]   
over a maximum of 30 hops:                         
                                                   
  1    25 ms    23 ms    26 ms  165.146.180.1      
  2    45 ms    46 ms    46 ms  196.43.35.57       
  3    43 ms    45 ms    45 ms  196.43.35.57       
  4    49 ms    46 ms    92 ms  196.43.10.130      
  5    46 ms    42 ms    46 ms  196.43.33.5        
  6     *        *        *     Request timed out.

---

### Post by ryan.nabinger on 2009-03-09
Ah Ha!  We are getting somewhere here.  

```

PPP adapter Telkomsa.net:

Connection-specific DNS Suffix . :
IP Address. . . . . . . . . . . . : 165.146.181.23
Subnet Mask . . . . . . . . . . . : 255.255.255.255
Default Gateway . . . . . . . . . : 165.146.181.23

```

```

Tracing route to www.l.google.com [72.14.235.99]
over a maximum of 30 hops:

1 25 ms 23 ms 26 ms 165.146.180.1
2 45 ms 46 ms 46 ms 196.43.35.57
3 43 ms 45 ms 45 ms 196.43.35.57
4 49 ms 46 ms 92 ms 196.43.10.130
5 46 ms 42 ms 46 ms 196.43.33.5
6 * * * Request timed out. 

```

See what is happening here?  Contrast this to the first few hops in your Ubuntu traceroute.

```

afrodeity@afrodeity-desktop:~$ traceroute www.google.com
traceroute to www.google.com (72.14.235.147), 30 hops max, 40 byte packets
1 192.168.1.1 (192.168.1.1) 0.921 ms 1.326 ms 1.753 ms
2 dsl-146-180-01.telkomadsl.co.za (165.146.180.1) 33.714 ms 42.910 ms *
3 * * 196.43.35.57 (196.43.35.57) 102.949 ms
4 * * *
5 * * *
6 * 196.43.33.5 (196.43.33.5) 50.077 ms 53.208 ms
7 * * *

```


Perhaps you may require a PPPoE session with your ISP for authentication purposes?  Maybe someone else will be able to chime in with more experience on this matter ... I may be able to help you with more info later today.

---

### Post by afrodeity on 2009-03-11
So it appears the router is taking a different root on the XP side? As you can see my vmware is stealing focus somehow and I'm not sure what my ISP thinks. Last night had a friend over, who plugged his Ubuntu Hardy running on a Dell laptop into my router and was getting better speeds than my machine. He was also surfing international sites without using the proxy which I have to use in order to do this, so don't know what to think about the router - a parallel dimension to free internet bandwidth?

---

### Post by ryan.nabinger on 2009-03-11
> **afrodeity said:**
>  so don't know what to think about the router - a parallel dimension to free internet bandwidth?

No, your friend probably uses the same ISP as you and therefore when he plugs into your home network he makes that same PPPoE connection that he would make at his house and all is good.

```
sudo pppoeconf
```

I believe this is where you need to go.  search pppoe and ubuntu online you should be able to figure it out.  However, it is possible I am interpreting all of this incorrectly ...

---

### Post by afrodeity on 2009-03-13
Okay, solved the problem. Here's what happened. I unplugged everything including the cable to the wall. Reset the router a couple of times and managed to boot into it for one session. Then no go, it still misbehaving.

Turns out my wonderful pet:P, puppy linux set a policy on the router. Basically set up the DHCP server which is part of the firmware. This I found out because I could boot into the router with the pup, but nothing else. After searching around the settings, found DHCP server ON. I turned this OFF and lo and behold, the router is back to normal.

Still doesn't explain my ghost friend, the hacker from next door who is probably leeching megabits off my account. I will therefore try to reset the password again and hope for the best.;)

---


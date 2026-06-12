---
title: "SSH server Port forwarding on router."
date: 2009-01-03
forum: General Help
---

### Post by Dave_Connor on 2009-01-03
Our old router a 2WIRE model somehow died from a power outage even under surge protection. We where able to get a new router today, but forwarding port 6000 and 2022 for my torrents and ssh do not work. Nmap does not report anything back of the ports being open. (Dns with lan hosts also are broken ****ing router) I tryed forwarding with basic and advanced setup with the router settings. I also updated the firmware with the router but this router will not open up the connections I need. Any help here ? I have an ActionTec GT704WG router. Please I need help, I've tried disabling my firewall and that doesn't work.

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
Are you sure the iptables are letting the data through? iptables --list will tell you what's being let through.

---

### Post by Dave_Connor on 2009-01-03
Iptables --list shows 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
moblock_in  all  --  anywhere             anywhere            state NEW MARK match !0x14 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
moblock_fw  all  --  anywhere             anywhere            state NEW MARK match !0x14 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
moblock_out  all  --  anywhere             anywhere            state NEW MARK match !0x14 

Chain moblock_fw (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            MARK match 0xa 

So everything is allowed but just filtered through moblock. I disabled moblock and tryed sshing to my server but I still get port 2022: connection refused.

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
You have a static IP? Dynamic ones change and mess things up for all that. Perhapse do a ifconfig and check with the router settings to see if they match up regardless?

---

### Post by Dave_Connor on 2009-01-03
ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:7d:a1:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:18:f8:d0:4d:bb  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f8ff:fed0:4dbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1377570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1538261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:888955764 (888.9 MB)  TX bytes:852928319 (852.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1976877 (1.9 MB)  TX bytes:1976877 (1.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-F8-D0-4D-BB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I had a dynamic ip on our old router and it didn't want to fight me with wanting to just open a freaking port >_< even with the rules in place nmap still shows those ports closed.

---

### Post by jre on 2009-01-03
> **Dave_Connor said:**
> Iptables --list shows 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
moblock_in  all  --  anywhere             anywhere            state NEW MARK match !0x14 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
moblock_fw  all  --  anywhere             anywhere            state NEW MARK match !0x14 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
moblock_out  all  --  anywhere             anywhere            state NEW MARK match !0x14 

Chain moblock_fw (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            MARK match 0xa 

So everything is allowed but just filtered through moblock. I disabled moblock and tryed sshing to my server but I still get port 2022: connection refused.
Was Moblock disabled completely? The iptables rules that you posted show a broken setup, which will definitely cause problems.
If MoBlock is disabled then neither moblock_... rules nore chains must be present. Just killing the moblock daemon process is a very bad idea. Instead use "sudo moblock-control stop" and afterwards check the iptables rules again.

---

### Post by Dave_Connor on 2009-01-03
Sorry it didn't show the rules then. I did disable moblock by stopping and I also had my ports whitelisted in the /etc/moblock/moblock.conf file so I don't know why our router is still wanting to fight me. Any other suggestions ? 
```
Updated iptables:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
moblock_in  all  --  anywhere             anywhere            state NEW MARK match !0x14 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
moblock_fw  all  --  anywhere             anywhere            state NEW MARK match !0x14 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
moblock_out  all  --  anywhere             anywhere            state NEW MARK match !0x14 

Chain moblock_fw (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            MARK match 0xa 
RETURN     all  --  192.168.0.0/24       192.168.0.0/24      
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 92

Chain moblock_in (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            MARK match 0xa 
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  192.168.0.0/24       anywhere            
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 92

Chain moblock_out (1 references)
target     prot opt source               destination         
REJECT     all  --  anywhere             anywhere            MARK match 0xa reject-with icmp-port-unreachable 
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  anywhere             192.168.0.0/24      
RETURN     tcp  --  anywhere             anywhere            tcp dpt:whois 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:ircd 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:24800 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:x11 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:2022 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:https 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:www 
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 92
```

---

### Post by Dave_Connor on 2009-01-03
Sorry to bump but I please need some help with being able to have my ssh server backup again.

---

### Post by jre on 2009-01-04
So the new iptables rules look non-broken at least. Still, to rule out MoBlock problems, I recommend to shut down Moblock completely **(verify that absolutely no iptables rule is present)** and then do your tests. You can also check with "tail -f /var/log/moblock.log" if your packets were blocked by MoBlock.

Am I right that your blocked connections were all outgoing (that means you tried on your computer behind the router to access/... a machine in the internet). If yes, this sounds like configuration problems on your computer, not on your router.

---

### Post by Dave_Connor on 2009-01-04
I shut down moblock with "sudo moblock-control stop" and checked that there was no iptables set up and allowed everything and still a connection refused with my domain. I checked the router and portscanned my public ip and all my ports are still closed.

---


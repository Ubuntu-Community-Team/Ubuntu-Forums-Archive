---
title: "ping &amp; ftp problems"
date: 2009-03-11
forum: General Help
---

### Post by dave31175 on 2009-03-11
Relatively new to Ubuntu. I've done a bit of Googling for this problem, but didn't turn up anything of value.

I'm unable to ping any hostname ("destination port unreachable") or establish ftp connections in filezilla or terminal to known working FTP sites ("connection refused").

From a Windows machine on the same network, I can ping and ftp the same hosts with no problem, so it seems the problem is something specific to Ubuntu, not to my network or internet connection.

Any suggestions or solutions would be greatly appreciated. Thanks!

---

### Post by kanikilu on 2009-03-11
Are you trying to reach hosts on the same network or outside? I know on my network, to be able to reach some internal hosts I have to use the fully qualified domain name, especially windows hosts.

Do you have a firewall, proxy or something that would be blocking outbound connections?

Can you ping by IP address? Perhaps it's a DNS problem?

---

### Post by dave31175 on 2009-03-11
I'm trying to reach outside hosts.

The Ubuntu machine and Windows machine (from which pinging and ftp work fine) are both connected to the same Netgear router, which in turn connects to my cable modem. I don't believe there is any config in the router that should be causing this problem, or else I would expect to have the same problem with any other machine connecting through this router. 

I have not changed any networking/firewall/proxy settings within Ubuntu itself. I'm not familiar enough with its workings to know if there is something installed or configured by default in Ubuntu that would be causing this?

I cannot ping by IP address either. When I ping by hostname, it is resolving to the correct IP address, so it doesn't appear to be a DNS problem.

---

### Post by dave31175 on 2009-03-12
Does anyone have any other ideas? What should I be looking for in my Ubuntu network config? 

If I do a tracepath, I get this:

:~$ tracepath 63.253.181.45
 1:  192.168.0.10 (192.168.0.10)                            0.699ms reached
     Resume: pmtu 65535 hops 1 back 64 

It would seem I'm not even getting past my local machine, but I don't understand why. I have no problem with browsing or application downloads/updates.

---

### Post by Peter09 on 2009-03-12
What is the output of the terminal command
```
route
```
for a working and non working machine

---

### Post by dave31175 on 2009-03-12
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0


> **Peter09 said:**
> for a working and non working machine
Not sure what you mean by this -- I only have one ubuntu machine? Sorry if I'm being dense, I'll go look for more caffeine!

---

### Post by Peter09 on 2009-03-12
Can you do 
```
ifconfig
```
in a terminal and post the output.

Note - please check your DHCP function - are you getting a proper IP address?

---

### Post by dave31175 on 2009-03-12
eth0      Link encap:Ethernet  HWaddr 00:0d:61:12:35:ce  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:61ff:fe12:35ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8909887 (8.9 MB)  TX bytes:635660 (635.6 KB)
          Interrupt:16 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3064 (3.0 KB)  TX bytes:3064 (3.0 KB)

DHCP is assigning IP address 192.168.0.10. Browsing to other computers on the home network is working OK.

---

### Post by Peter09 on 2009-03-12
Just to clarify,
can you ping local machines?

---

### Post by Peter09 on 2009-03-12
Can you post the output of the terminal command
```
dig
```

---

### Post by dave31175 on 2009-03-12
I can ping local machines and the router. Dig output follows:

; <<>> DiG 9.5.0-P2 <<>>
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 39232
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 14

;; QUESTION SECTION:
;.				IN	NS

;; ANSWER SECTION:
.			7	IN	NS	j.root-servers.net.
.			7	IN	NS	k.root-servers.net.
.			7	IN	NS	l.root-servers.net.
.			7	IN	NS	m.root-servers.net.
.			7	IN	NS	a.root-servers.net.
.			7	IN	NS	b.root-servers.net.
.			7	IN	NS	c.root-servers.net.
.			7	IN	NS	d.root-servers.net.
.			7	IN	NS	e.root-servers.net.
.			7	IN	NS	f.root-servers.net.
.			7	IN	NS	g.root-servers.net.
.			7	IN	NS	h.root-servers.net.
.			7	IN	NS	i.root-servers.net.

;; ADDITIONAL SECTION:
a.root-servers.net.	7	IN	A	198.41.0.4
a.root-servers.net.	7	IN	AAAA	2001:503:ba3e::2:30
b.root-servers.net.	7	IN	A	192.228.79.201
c.root-servers.net.	7	IN	A	192.33.4.12
d.root-servers.net.	7	IN	A	128.8.10.90
e.root-servers.net.	7	IN	A	192.203.230.10
f.root-servers.net.	7	IN	A	192.5.5.241
f.root-servers.net.	7	IN	AAAA	2001:500:2f::f
g.root-servers.net.	7	IN	A	192.112.36.4
h.root-servers.net.	7	IN	A	128.63.2.53
h.root-servers.net.	851	IN	AAAA	2001:500:1::803f:235
i.root-servers.net.	7	IN	A	192.36.148.17
j.root-servers.net.	7	IN	A	192.58.128.30
j.root-servers.net.	7	IN	AAAA	2001:503:c27::2:30

;; Query time: 368 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Thu Mar 12 08:25:22 2009
;; MSG SIZE  rcvd: 500

---

### Post by Peter09 on 2009-03-12
Hi,
should have given you the command

```
dig @192.168.0.1 
```

---

### Post by dave31175 on 2009-03-12
Here it is. Thanks!

; <<>> DiG 9.5.0-P2 <<>> @192.168.0.1
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43153
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 14

;; QUESTION SECTION:
;.				IN	NS

;; ANSWER SECTION:
.			718	IN	NS	I.ROOT-SERVERS.NET.
.			718	IN	NS	J.ROOT-SERVERS.NET.
.			718	IN	NS	K.ROOT-SERVERS.NET.
.			718	IN	NS	L.ROOT-SERVERS.NET.
.			718	IN	NS	M.ROOT-SERVERS.NET.
.			718	IN	NS	A.ROOT-SERVERS.NET.
.			718	IN	NS	B.ROOT-SERVERS.NET.
.			718	IN	NS	C.ROOT-SERVERS.NET.
.			718	IN	NS	D.ROOT-SERVERS.NET.
.			718	IN	NS	E.ROOT-SERVERS.NET.
.			718	IN	NS	F.ROOT-SERVERS.NET.
.			718	IN	NS	G.ROOT-SERVERS.NET.
.			718	IN	NS	H.ROOT-SERVERS.NET.

;; ADDITIONAL SECTION:
A.ROOT-SERVERS.NET.	718	IN	A	198.41.0.4
A.ROOT-SERVERS.NET.	718	IN	AAAA	2001:503:ba3e::2:30
B.ROOT-SERVERS.NET.	718	IN	A	192.228.79.201
C.ROOT-SERVERS.NET.	718	IN	A	192.33.4.12
D.ROOT-SERVERS.NET.	718	IN	A	128.8.10.90
E.ROOT-SERVERS.NET.	718	IN	A	192.203.230.10
F.ROOT-SERVERS.NET.	718	IN	A	192.5.5.241
F.ROOT-SERVERS.NET.	718	IN	AAAA	2001:500:2f::f
G.ROOT-SERVERS.NET.	718	IN	A	192.112.36.4
H.ROOT-SERVERS.NET.	718	IN	A	128.63.2.53
I.ROOT-SERVERS.NET.	718	IN	A	192.36.148.17
J.ROOT-SERVERS.NET.	718	IN	A	192.58.128.30
J.ROOT-SERVERS.NET.	718	IN	AAAA	2001:503:c27::2:30
K.ROOT-SERVERS.NET.	718	IN	A	193.0.14.129

;; Query time: 427 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Thu Mar 12 08:41:27 2009
;; MSG SIZE  rcvd: 488

---

### Post by Peter09 on 2009-03-12
Hi,
first there appears to be something wrong with the nameserver setup that you are using, your query time is huge, 438ms, mine is 48msec. I suspect that your router has no name servers setup. May be the windows machine has them setup locally.

Do you know how to setup your router and put the name servers in? Your ISP will normally give you the IP addresses of the nameserver to use.

I'm still not sure where the problem lies because without name servers you should not be able to browse the internet, while an ip-address based ping should work.

---

### Post by dave31175 on 2009-03-12
The router was getting the nameservers from the ISP through DHCP. I have edited the router config and added the nameservers manually, however that seems to have made no difference. My query time is only slightly less (369ms). Pinging external hosts by either hostname or IP address still returns "Destination Port Unreachable". And attempting an FTP connection to an external host still returns "Connection Refused". 

I very much appreciate your efforts to help me find a solution. However I'm finding this a bit discouraging. It's certainly a dealbreaker for making Ubuntu my primary OS. Let me know if you think of anything else! :)

---

### Post by rustutzman on 2009-03-12
It doesn't appear to me that there is anything wrong with the Ubuntu computer. I believe it is something in your router setup. The first thing I'd try is resetting the router back to factory specs. Be sure to save out any configuration info needed to connect to the internet prior to resetting.

Russ

---

### Post by dave31175 on 2009-03-13
> **rustutzman said:**
> It doesn't appear to me that there is anything wrong with the Ubuntu computer. I believe it is something in your router setup. The first thing I'd try is resetting the router back to factory specs. Be sure to save out any configuration info needed to connect to the internet prior to resetting.

Russ
Thanks for the idea, but sadly, it didn't work. Same results as before.

---

### Post by dave31175 on 2009-03-13
OK, there's bad news, and there's good news. 

The bad news is I wasted the time of those who tried to help me -- apologies.

The good news is I found the problem. I had forgotten that I had Moblock running from when I tried out Deluge (what a dissapointing BT client after using utorrent), and I also didn't realize Moblock would be so agressive in blocking non-BT connections, even after applying exceptions. In Windows, Peerguardian never caused me this kind of grief!

At any rate, with Moblock turned off, all is well. Again, my apologies to kanikilu, Peter, and Russ, but thanks so much for your efforts in trying to help me!

---

### Post by Peter09 on 2009-03-13
Glad that you have resolved the issue.

---

### Post by jre on 2009-03-14
> **dave31175 said:**
> I also didn't realize Moblock would be so agressive in blocking non-BT connections, even after applying exceptions. In Windows, Peerguardian never caused me this kind of grief!
Probably you already know this... :

In moblock-control you can make exceptions (whitelist) ports. Per default this is already done for 80 (http) and 443 (https) for outgoing TCP connections. You may also add 21 (ftp)
```
WHITE_TCP_OUT="https http ftp"
```

To get a behaviour more similar to Windows PeerGuradian you have to change your blocklist setup. Per default this is quite strict, but you may reduce the number of used blocklists. See /etc/moblock/blocklists.list and /usr/share/doc/moblock-control/README.blocklists.gz

---


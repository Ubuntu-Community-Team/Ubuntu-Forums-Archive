---
title: "Problem with Guarddog and firewall..."
date: 2005-09-24
forum: Desktop Environments
---

### Post by audax321 on 2005-09-24
Hey everyone,

   I am having a problem with Guarddog. I configured it properly and everything is working great. But after a while my internet connection drops. If I disable the firewall from within Guarddog I don't have any connection problems. In order to get the dropped connection back, I either have to have Guarddog reset the firewall or just plain disable it. Does anyone know what might be causing this?

This is the /var/log/messages output I get when the connection drops, otherwise looks normal:

```

Sep 24 20:54:28 localhost kernel: [4350050.859000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=33323 DF PROTO=UDP SPT=1154 DPT=53 LEN=42 
Sep 24 20:54:28 localhost last message repeated 3 times
Sep 24 20:54:28 localhost kernel: [4350050.860000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=33324 DF PROTO=UDP SPT=1154 DPT=53 LEN=42 
Sep 24 20:54:28 localhost kernel: [4350050.861000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=33325 DF PROTO=UDP SPT=1154 DPT=53 LEN=42 
Sep 24 20:54:28 localhost kernel: [4350050.863000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=33327 DF PROTO=UDP SPT=1154 DPT=53 LEN=42 
Sep 24 20:54:28 localhost kernel: [4350050.864000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=33328 DF PROTO=UDP SPT=1154 DPT=53 LEN=42 
Sep 24 20:54:28 localhost kernel: [4350050.869000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=33333 DF PROTO=UDP SPT=1154 DPT=53 LEN=45 
Sep 24 20:54:28 localhost kernel: [4350050.869000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=33333 DF PROTO=UDP SPT=1154 DPT=53 LEN=45 
Sep 24 20:54:28 localhost kernel: [4350050.869000] LIMITED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=33333 DF PROTO=UDP SPT=1154 DPT=53 LEN=45 
Sep 24 20:54:40 localhost kernel: [4350062.217000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=44681 DF PROTO=UDP SPT=1154 DPT=53 LEN=45 
Sep 24 20:54:40 localhost last message repeated 9 times
Sep 24 20:54:48 localhost kernel: [4350070.846000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=69 TOS=0x00 PREC=0x00 TTL=64 ID=53310 DF PROTO=UDP SPT=1154 DPT=53 LEN=49 
Sep 24 20:54:48 localhost kernel: [4350070.847000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=69 TOS=0x00 PREC=0x00 TTL=64 ID=53311 DF PROTO=UDP SPT=1154 DPT=53 LEN=49 
Sep 24 20:54:48 localhost last message repeated 6 times
Sep 24 20:54:50 localhost kernel: [4350072.706000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=69 TOS=0x00 PREC=0x00 TTL=64 ID=55170 DF PROTO=UDP SPT=1154 DPT=53 LEN=49 
Sep 24 20:54:50 localhost kernel: [4350072.706000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=69 TOS=0x00 PREC=0x00 TTL=64 ID=55170 DF PROTO=UDP SPT=1154 DPT=53 LEN=49 
Sep 24 20:54:52 localhost kernel: [4350074.760000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=57224 DF PROTO=UDP SPT=1154 DPT=53 LEN=46 
Sep 24 20:54:52 localhost kernel: [4350074.760000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=57224 DF PROTO=UDP SPT=1154 DPT=53 LEN=46 
Sep 24 20:54:54 localhost kernel: [4350076.181000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=58645 DF PROTO=UDP SPT=1154 DPT=53 LEN=46 

```

My network setup:

Windows Computer + Linux Computer (192.168.1.8 ) both connected through a Netgear Router (192.168.1.1)

I want to switch to Kubuntu, but this is probably going to keep me unless there's a fix. I did not have this problem under Ubuntu.

---

### Post by cwaldbieser on 2005-09-25
[QUOTE=audax321]Hey everyone,

   I am having a problem with Guarddog. I configured it properly and everything is working great. But after a while my internet connection drops. If I disable the firewall from within Guarddog I don't have any connection problems. In order to get the dropped connection back, I either have to have Guarddog reset the firewall or just plain disable it. Does anyone know what might be causing this?

This is the /var/log/messages output I get when the connection drops, otherwise looks normal:

```

Sep 24 20:54:28 localhost kernel: [4350050.859000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=33323 DF PROTO=UDP SPT=1154 DPT=53 LEN=42 
Sep 24 20:54:28 localhost last message repeated 3 times
Sep 24 20:54:28 localhost kernel: [4350050.860000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=33324 DF PROTO=UDP SPT=1154 DPT=53 LEN=42 
Sep 24 20:54:28 localhost kernel: [4350050.861000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=33325 DF PROTO=UDP SPT=1154 DPT=53 LEN=42 
Sep 24 20:54:28 localhost kernel: [4350050.863000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=33327 DF PROTO=UDP SPT=1154 DPT=53 LEN=42 
Sep 24 20:54:28 localhost kernel: [4350050.864000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=33328 DF PROTO=UDP SPT=1154 DPT=53 LEN=42 
Sep 24 20:54:28 localhost kernel: [4350050.869000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=33333 DF PROTO=UDP SPT=1154 DPT=53 LEN=45 
Sep 24 20:54:28 localhost kernel: [4350050.869000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=33333 DF PROTO=UDP SPT=1154 DPT=53 LEN=45 
Sep 24 20:54:28 localhost kernel: [4350050.869000] LIMITED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=33333 DF PROTO=UDP SPT=1154 DPT=53 LEN=45 
Sep 24 20:54:40 localhost kernel: [4350062.217000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=44681 DF PROTO=UDP SPT=1154 DPT=53 LEN=45 
Sep 24 20:54:40 localhost last message repeated 9 times
Sep 24 20:54:48 localhost kernel: [4350070.846000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=69 TOS=0x00 PREC=0x00 TTL=64 ID=53310 DF PROTO=UDP SPT=1154 DPT=53 LEN=49 
Sep 24 20:54:48 localhost kernel: [4350070.847000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=69 TOS=0x00 PREC=0x00 TTL=64 ID=53311 DF PROTO=UDP SPT=1154 DPT=53 LEN=49 
Sep 24 20:54:48 localhost last message repeated 6 times
Sep 24 20:54:50 localhost kernel: [4350072.706000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=69 TOS=0x00 PREC=0x00 TTL=64 ID=55170 DF PROTO=UDP SPT=1154 DPT=53 LEN=49 
Sep 24 20:54:50 localhost kernel: [4350072.706000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=69 TOS=0x00 PREC=0x00 TTL=64 ID=55170 DF PROTO=UDP SPT=1154 DPT=53 LEN=49 
Sep 24 20:54:52 localhost kernel: [4350074.760000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=57224 DF PROTO=UDP SPT=1154 DPT=53 LEN=46 
Sep 24 20:54:52 localhost kernel: [4350074.760000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=57224 DF PROTO=UDP SPT=1154 DPT=53 LEN=46 
Sep 24 20:54:54 localhost kernel: [4350076.181000] DROPPED IN= OUT=eth0 SRC=192.168.1.8 DST=192.168.1.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=58645 DF PROTO=UDP SPT=1154 DPT=53 LEN=46 

```

My network setup:

Windows Computer + Linux Computer (192.168.1.8 ) both connected through a Netgear Router (192.168.1.1)

I want to switch to Kubuntu, but this is probably going to keep me unless there's a fix. I did not have this problem under Ubuntu.[/QUOTE]
Do you know how long the interval is between when you have net access and lose it?  Could it be something like your DHCP lease needs to be renewed but you are blocking it?  

Maybe you could try opening various ranges of ports to see if you can find the range that is the problem, and narrow it down from there.

---

### Post by audax321 on 2005-09-25
It normally happens within a few minutes - anywhere from 1 - 15 minutes after enabling the firewall. I tried opening the port that it is connecting to but then I just get error messages saying that it needs a different port open. For instance, I opened port 1154, then it said it needed 1155, then 1156, then 1157, and so forth. I'll try opening a larger range of ports and see if that does anything. On Ubuntu I used Firestarter and it had an option to allow all outgoing connections, so that may be why I never saw the problem there. Guarddog seems to be a lot stricter than Firestarter though so I like it better...I guess its just being a bit too strict right now  :neutral:

Also, for my LAN config, I have 192.168.1.2/24 added so that it doesn't include the router IP... is that the right notation for it?

Here is something else I just noticed. I opened port 1154 and I could access Google, but couldn't access [www.fedex.com](www.fedex.com) because it wanted port 1196 to be open instead... why would that be?

---

### Post by audax321 on 2005-09-25
Okay, I think I figured out the problem!

Guarddog has these ports that are added to the Local Dynamic Port Range, but I never specified if these were allowed to carry output traffic (I assumed that they were just allowed by default). So I allowed them to carry output traffic and all is well (so far, at least). Also, that notation I had 192.168.1.2/24 seems wrong because it looks like the firewall included 192.168.1.1 in that range. Anyway I had to change that to specify specific computers on my network.  :)

---

### Post by cwaldbieser on 2005-09-25
[QUOTE=audax321]It normally happens within a few minutes - anywhere from 1 - 15 minutes after enabling the firewall. I tried opening the port that it is connecting to but then I just get error messages saying that it needs a different port open. For instance, I opened port 1154, then it said it needed 1155, then 1156, then 1157, and so forth. I'll try opening a larger range of ports and see if that does anything. On Ubuntu I used Firestarter and it had an option to allow all outgoing connections, so that may be why I never saw the problem there. Guarddog seems to be a lot stricter than Firestarter though so I like it better...I guess its just being a bit too strict right now  :neutral:

Also, for my LAN config, I have 192.168.1.2/24 added so that it doesn't include the router IP... is that the right notation for it?

Here is something else I just noticed. I opened port 1154 and I could access Google, but couldn't access [www.fedex.com](www.fedex.com) because it wanted port 1196 to be open instead... why would that be?[/QUOTE]

It's been a while since I used guarddog.  It almost sounds like you are blocking your outgoing *source* ports. That could be a problem, since apps like your web browser will just choose any available port on the source side to make their connection.  You want to make sure you are blocking ingoing and outgoing destination ports.  However, I have noticed some sites that do actually seem to send seemingly random TCP connections to my machine and refuse to finish loading unless they get some sort of answer.  Not sure what the reason is...

Your notation for the router sounds right for a typical home setup.

---

### Post by audax321 on 2005-09-25
Yup that is exactly what was happening. According to Guarddog help, the Local Dynamic Port Range is used for opening outgoing ports for IP addresses that don't specify a specific port. So, the OS just assigns a port from that range. At first I didn't really pay attention to that option and just assumed they were automatically opened. But I had to explicitly add them and everything has been working great for the past few hours. So I'm pretty sure that was it.  :smile: 

But, I don't think my syntax was right. Adding 192.168.1.2/24 caused port 192.168.1.1 to be added as well. What I wanted to do was only enable the dynamic port range for 192.168.1.1, but any requests made by the browser to the these outgoing ports was sent through the Internet zone. So the 192.168.1.1 zone wouldn't work. I then removed that zone and set it up for the Internet zone, but to my surprise that wouldn't work either. Then I started suspecting that 192.168.1.2/24 may be including 192.168.1.1 and it was. After changing it to specify specific IPs on my home network instead everything started working properly.

---


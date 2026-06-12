---
title: "Ubuntu randomly refusing connections"
date: 2005-12-13
forum: Desktop Environments
---

### Post by bsoric on 2005-12-13
Hello everyone

My computer is running Breezy at the moment, it is behind a router which has been configured to let port 80 through. The problem I'm having is that when Netcat is listening on that port, only sometimes do the connections actually work.

I've tried Nmapping myself from 2 shell accounts and attempting to make netcat connections between the shell accounts and my computer. Sometimes the connections work, sometimes they don't. Even the Shieldsup test from Grc.com did this.

I've set my IPTables to automatically accept all traffic, however I'm not sure this has helped. I cannot find any pattern between what I do beforehand and whether or not the connections get accepted.

Does anyone have any thoughts on how to fix this?

Thank you,
Brett

---

### Post by anil_robo on 2005-12-13
I've allowed many ports in firestarter, but still it blocks them sometimes! Could well be a bug, or maybe something to do with my router :(

Stopping firestarter helps in most cases.

---

### Post by bsoric on 2005-12-13
Yeah, I stopped and uninstalled firestarter, and used firehol to clear my Iptables so they just read Accept or whatever.

I have a Belkin 4 Port Cable/DSL Gateway router and I keep having problems with it, so now I'm not sure if it's the router or the computer thats the problem.

The funny thing is the SSH port (22) always reads Open from Nmap, it only seems to be the HTTP port that goes between Open and Closed.

---

### Post by pataphysician on 2005-12-14
are you able to test from behind the router? nmap -p 80 192.168.x.x or whatever. then you could determine if it's the router or the machine that's refusing connections. if youre connecting to your public ip address, it could even be some weird isp activity?

---

### Post by Doomed_Tupperware on 2005-12-14
My GAim refuses all direct connections and Nicotine just kinda sits there listening in on ports, I think we have the same problem, and I don't think its your router either since I just recently installed Ubuntu and that's when the problem started.

---

### Post by bsoric on 2005-12-14
I can connect everytime (so far) from my lan (behind the router), but I still don't know if it's some firewall configuration or the router.

Everytime I port scan from a shell account I scan ports 22, 80, and 4321

22 is always open
80 is sometimes open sometimes closed
4321 is always filtered (Not port forwarded to anywhere)

I have the same settings on the router for ports 22 and 80, so I don't think its that.

---

### Post by bsoric on 2005-12-15
Ooh
Good news possibly.

What I was doing today:

In my terminal- 
sudo nc -lvp 80

In a shell account terminal-
while [ 1 ]; do nc -v XXX.XXX.XXX.XXX 80; sleep 1; done

 [xxx.xxx.xxx.xxx] 80 (http) : Connection refused
 [xxx.xxx.xxx.xxx] 80 (http) : Connection refused
 [xxx.xxx.xxx.xxx] 80 (http) : Connection refused
and so on.

Until I opened my web browser, to see if there were any new responses in this thread.

Whereupon it showed:
[xxx.xxx.xxx.xxx] 80 (http) open

This got me thinking- what if the only reason SSH is always open is that I'm always SSH'd into another computer when I do the scans?

Anyone else think this makes sense?

Brett

---


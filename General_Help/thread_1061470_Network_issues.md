---
title: "Network issues"
date: 2009-02-05
forum: General Help
---

### Post by mojo_man on 2009-02-05
Hi,

I am trying to use a bitorrent client to download files and I get HORRIBLE download time likes 2KB/s!

One of my friends at work told me that the problem is that I have have the streams encrypyted so the ISP's cannot tell that I am downloading a torrent. SO I have enabled that in deluge.

The second suggestion raised tremendous problems. He said I have to use a different port than the default one. He suggested the IRC one. So I tried using:

sudo iptables -A INPUT -p tcp --dport 6667 -j ACCEPT

But the iptables do not show it is:
Starting Nmap 4.62 ( [http://nmap.org](http://nmap.org) ) at 2009-02-05 21:02 EST
Initiating Ping Scan at 21:02
Scanning 127.0.0.1 [1 port]
Completed Ping Scan at 21:02, 0.00s elapsed (1 total hosts)
Initiating Connect Scan at 21:02
Scanning localhost (127.0.0.1) [1715 ports]
Discovered open port 631/tcp on 127.0.0.1
Completed Connect Scan at 21:02, 0.03s elapsed (1715 total ports)
Host localhost (127.0.0.1) appears to be up ... good.
Interesting ports on localhost (127.0.0.1):
Not shown: 1714 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

....

So what am I doing wrong?
And what ports should I use for torrent client?

---

### Post by spiderbatdad on 2009-02-05
patience is sometimes necessary as download speeds will increase over time usually. This is a good guide to torrents. [http://www.dessent.net/btfaq/](http://www.dessent.net/btfaq/)

---

### Post by mojo_man on 2009-02-05
> **spiderbatdad said:**
> patience is sometimes necessary as download speeds will increase over time usually. This is a good guide to torrents. [http://www.dessent.net/btfaq/](http://www.dessent.net/btfaq/)

Okay but why I am having problems opening ports?

---

### Post by spiderbatdad on 2009-02-05
have you enabled the ufw firewall, or are you using another firewall?
What about forwarding the ports from your router, if you use one. That guides makes what I find are good port recomendations. I have never specifically set iptables for bit torrent and generally achieve 300-600 kb/s where there is good seeding.

---

### Post by cariboo on 2009-02-05
Are you running iptables in addition to a router with a firewall?

Jim

---

### Post by mojo_man on 2009-02-05
> **cariboo907 said:**
> Are you running iptables in addition to a router with a firewall?

Jim

I am just a newbie. I have no idea what really is going on. Can someone guide me step by step? 

I cannot see where firewall is and I just read on the internet to open port by command line you have to execute that command I posted.

---

### Post by mojo_man on 2009-02-05
> **spiderbatdad said:**
> have you enabled the ufw firewall, or are you using another firewall?
What about forwarding the ports from your router, if you use one. That guides makes what I find are good port recomendations. I have never specifically set iptables for bit torrent and generally achieve 300-600 kb/s where there is good seeding.


I never enabled the ufw firewall. I can port forward from the router but why in Ubuntu can I know enable a port?

---

### Post by maciu on 2009-02-06
fisrt check if you have ufw enabled```
ufw status
``` if not enabled it ```
ufw enable
``` then simply type ```
ufw allow 6667 
``` then you can check it again with ```
ufw status
```

---


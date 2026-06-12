---
title: "Network keeps crashing"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Burke on 2006-06-05
When I start my computer, I can access my (wired) network fine for approximately half an hour. At that point, it goes down and I have to run 'sudo /etc/init.d/networking restart'. It'll work for about another 5 minutes at that point. 

I have a wireless card, and I thought that might be the problem, but I blacklisted both ndis and bcm43xx. Same problem still. 

Here's an excerpt from my kernel log showing one such cycle, starting at 
'networking restart', and going up to the next crash.

```
Jun  5 17:19:20 localhost kernel: [  429.843571] sky2 eth1: disabling interface
Jun  5 17:19:20 localhost kernel: [  429.862654] sky2 eth1: enabling interface
Jun  5 17:19:22 localhost kernel: [  430.380270] sky2 eth1: Link is up at 100 Mbps, full duplex, flow control none
Jun  5 17:19:31 localhost kernel: [  434.690415] eth1: no IPv6 routers present
Jun  5 17:26:57 localhost kernel: [  593.360488] NETDEV WATCHDOG: eth1: transmit timed out
Jun  5 17:26:57 localhost kernel: [  593.360492] sky2 eth1: tx timeout
```


Anyone have some insight they'd like to share?

EDIT: I think this only happens when I have a (any) torrent client running (and uploading)

---

### Post by Burke on 2006-06-06
Ah, I see this is happening in Windows too. Network problem. Nevermind.

EDIT: Yes, 100 beans! ;)

---


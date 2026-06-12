---
title: "Network stops responding in router but..."
date: 2009-05-23
forum: General Help
---

### Post by nikiiv on 2009-05-23
[COLOR=Black]Here is the set-up - Jaunty - x64 on Pentium D 340 with 4 GB RAM. Network is as:

1. [/COLOR][COLOR=Black]Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express - [/COLOR][COLOR=red][COLOR=Black]driver in use is tg3 - this one is eth0
2. Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express - driver in use is ipq - this one is eth1
This machine is a router, which connects to internet via pppoe (roaring penguins) from eth1 and masquerades all traffic to eth0

The strange thing.. if a torrent client is running on this machine, after a while network stops responding and the only way to get things to normal is to bring down the eth1 interface, bring it up and start pppoe. I tried couple of clients - transmission, deluge, rtorrent, uTorrent under wine

However.. and this is what puzzels me is that if client machine is torrenting (I know that this is not a verb), everything is OK. I even made a test where all machines at home (and I do have several, working machine, laptop, wifes laptop and HTPC) were downloading torrent files all at once up to the capacity of my network connection (20mbps) and guess what.. not a glitch. 

Now at this point the strange idea appeared in my mind.. to install Windows XP under VirtualBox on the router machine and hit the nerwork from there.. and network stopped to respond again..

Any ideas how to deal with this situation? I really would like to have all downloads from this machine, since it also have two big disks as RAID for all my disk space needs and is always on.. 


[/COLOR][/COLOR]

---

### Post by nikiiv on 2009-05-24
A polite bump

---

### Post by nikiiv on 2009-06-02
Another polite bump

---


---
title: "Wireless used to work, now it doesn't"
date: 2006-07-10
forum: Desktop Environments
---

### Post by jpdaigle on 2006-07-10
This question also posted on guruza for 10$, answer it there if you want to collect the reward for it :)
[http://guruza.com/question/231/](http://guruza.com/question/231/)

System: Thinkpad T41, intel ipw2100, Ubuntu Dapper (6.06).

Everything was fine a few months ago in Hoary and in Breezy. I'm not 100% sure the problems started happening with Dapper, but the timeline fits.

The issue is that the wireless network normally works fine for a while (anywhere from 2 minutes to a couple hours), then, out of the blue, I suddenly can't establish any connection to any other hosts, or ping them.

Right after the failure, 'iwconfig eth1' reports that I'm associated to my AP (linksys wrt54gc, the essid is 'daigle' and there's no encryption, not that that makes any difference in the occurence of this problem), with a connection quality of around 85%, standard for my apartment. 'ifconfig eth1' reports that I still have my DHCP-assigned IP, in the 192.168.1. subnet.

At this point I can't establish any TCP connections, nor can I ping anything on my LAN. It gets interesting though: I can kill any running dhclient processes and restart one (or do an ifdown / ifup, which does a release followed by a renew), and I apparently get a DHCPOffer. I get my IP back, meaning somehow broadcast packets are going through, but I still can't connect to anything.

---


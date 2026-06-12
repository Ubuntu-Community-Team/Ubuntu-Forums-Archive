---
title: "Azureus/port forwarding/firewall issue"
date: 2006-08-27
forum: Desktop Environments
---

### Post by jswhite on 2006-08-27
I'm having an odd problem with Azureus lately.  I used to use SimplyMEPIS 3.3 (based off of Debian), now use SimplyMEPIS 6.0 (based on Dapper).  This worked without problem in 3.3, but something's a little fuzzy with 6.0.  No idea why.

I have 2 computers on my network, 1 Mepis, 1 WinXP, both with static IP addresses.  Each computer uses a different port for BT traffic.  Both ports (50000 for me, 40000 for my wife) are forwarded to the respective IP addresses in my router (Linksys Wireless-G).  I have Guarddog installed for my firewall rules.  I created two custom protocols in Guarddog, "Azureus" and "Azureus2".  One allows TCP traffic on port 50000, one allows bidirectional UDP traffic on port 50000.  Both protocols are checked as "allowed" in the protocols tab.  Until upgrading to 6.0, that was all I ever had to do and everything was working as it should.

After upgrading, I'm getting NAT errors and connection errors on all torrents.  If I do a NAT/firewall test, it gives me a NAT error on port 50000.  I'm also not getting all green lights at the bottom like I should.  Speeds are slowed, and all private trackers show me as "unconnectable."  Disabling the firewall completely solves the problem, enabling the firewall again takes me back to the NAT errors.

I'd rather not keep running with no firewall protection at all.  Has anyone else had this issue, or know what I might be able to do to fix it?

---

### Post by spudratic on 2008-03-20
here is what I did set a rule in guarddog for udp port 6881 besides the other ports i opened in deluge.this let me connect to the trackers and dht no problem.this is not my fix I just read it some where.Now I dont know what I'm talking about but it seems to me that guard dog has a problem using the non standard ports.

---


---
title: "VPN with PPTP and MPPE"
date: 2005-09-18
forum: Desktop Environments
---

### Post by Markpy on 2005-09-18
Hi, I am having problems getting this to work. I have installed pptp-linux, pptpconfig and setup the VPN connection with the settings provided to me by the network administrator. I have also setup a proxy configuration in firefox for the connection.

When I start the VPN tunnel everything seems to work, there are no error messages reported.  When I try to go to a website the status message changes from 'looking up www.whatever.com' to 'connecting to www.whatever.com' but then it just times out. When I use wget to fetch google it prints the IP address of Google so the DNS is working correctly but I'm not receiving anything.

I had a similar problem in Windows setting up this VPN as I have a software firewall which I had to setup to allow traffic to/from the VPN. I figured that this is probably what is wrong on Ubuntu so I added the VPN address to my /etc/hosts.allow and still no dice.

If someone could help me with this I'd be grateful,

Thanks.

---

### Post by lonetree on 2005-10-05
what client are you using?

---

### Post by KingBahamut on 2005-10-05
Here is what I ask when talking about VPNs -- 
Is IP Passthrough enabled on your router?
What is the Client your using? 
What is on the other side of the coin, what server and setup?

---


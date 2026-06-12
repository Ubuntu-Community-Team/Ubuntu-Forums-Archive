---
title: "Postfix as a mail gateway / relay server"
date: 2009-05-04
forum: General Help
---

### Post by toMeloos on 2009-05-04
I have a server at home which I connect my laptop to using OpenVPN. I now want to be able to route my outgoing e-mail (smtp) through my home ISP.

First thing I looked at was if I could easily route all traffic for my ISP's mailserver through the VPN connection by pushing the route in OpenVPN. Couldn't figure it out.

Now I'm trying to setup a Postfix open relay mailserver. In Postfix I'm allowing inbound connections from localhost and the 192.168.x.x range. I've also blocked the inbound smtp port from the internet in the firewall to be safe.
I've set the IPS's mailserver as the 'relayhost' but I can't get it to relay any other mails than those domains I set in 'relaydomains'. Can anyone please tell me how I set Postfix to relay everything?

---

### Post by toMeloos on 2009-05-06
*bump*

---

### Post by sahabcse on 2009-05-06
Click [here]("http://sahabm.blogspot.com/2008/08/blog-post.html") for what I have done for postfix setup on ubuntu 8.04

---


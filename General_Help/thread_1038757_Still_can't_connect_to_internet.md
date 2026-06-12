---
title: "Still can't connect to internet"
date: 2009-01-13
forum: General Help
---

### Post by i81b4u on 2009-01-13
Hi, Posted some questions on here a couple of days ago, got a few replies, but i'm still no further with my problem. I've got ubuntu (8.04), got a PIII 512mb of ram, 20gb hard drive, I put a HSF dial up modem in it, the driver i'm using for it is hsfmodem_7.68.00.09oem_i386.deb. Up in the networking box , the two little computer screens, If i click i can go to manual configuration, which i have done and entered username etc etc. Also it has connect via ppp dial up and disconnect ppp dial up. Which seems to work because i can here the modem dial up. If i go to terminal - ifconfig, i get the ppp0 connection, with a ip address, which is my service providers (optusnet). When i ping this ip address it receives an answer. But i can't ping say [www.google.com](www.google.com) or do i have to actually ping their ip address. When i open firefox first time, it is in work offline mode and i have to untick it. Then when i type in an address it comes up (address not found), I have tried different web addresses, but same problem. But i'm sure if i could fix the ping problem, i think firefox would connect. Any help i could get on this would be greatly appreciated. I want to get away from windows and microsh*t altogether, But i don't want to load ubuntu on to my main system until i know how to use it properly, (Hence the old PIII). Thanks heaps,

---

### Post by HermanAB on 2009-01-13
Hmm, it is years since I last used PPP, but I believe that all it gives you is an IP address.  In order to make a connection to the rest of the world, you also need the gateway address (for the default route) and two DNS addresses (to resolve internet host names).  You probably need to call your ISP to get those.

Put the DNS addresses in /etc/resolv.conf:
nameserver w.x.y.z
nameserver w.x.y.z

and make a default route with:
$ sudo route add default gw w.x.y.z

Once that is done, the connection should work.

Hope that helps!

Herman

---

### Post by i81b4u on 2009-01-13
Thankyou heaps, I'm going to go try that now, I'll let you know how i go.

---

### Post by i81b4u on 2009-01-14
Hi, Man your the greatest, two weeks we've been trying to get this thing online and we have done it, thanks to your help. We actually put three DNS addresses in and it worked perfectly.I can't thank you enough, and i'd also like to thank the people that took the time to answer me, Now i can start using ubuntu and put it on my main system in a month or so. I want to get used to it first. So again, I thank all.

---


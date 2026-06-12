---
title: "Dapper bad performance on torrents"
date: 2006-06-09
forum: Desktop Environments
---

### Post by delphinen on 2006-06-09
I have been alway skeptic to think that the operative system, even the client you choose to download a torrent, could really influence in the download speed, until i migrated from debian sarge to ubuntu dapper.

dapper has been perfect so far, it turned my computer on an incredible multimedia desktop / webserver machine. But the problem with torrents is well know as i have seen in this forums, and is not solved.

I have been testing this since 2 months ago, when dapper betas was around.
First, the problems with Azureus. The last CVS version supposedly solves everything, except the bad performance and nat-meaningless?-blocked port warning. I have also tried with BitTornado and gnome Bit torrent (the one that comes with ubuntu). 
Always bad download/upload rates, torrents with 20+seeds download at 1.5k, while i switch to debian, and with azureus 2.2.0.2 i download at 6k+, many torrents at the same time.

I think the problem is something because of ubuntu. I dont know, iptables default configuration or something (does ubuntu comes with iptables?)

If anyone had this problem, or an idea of how to solve it, please help. Its a shame to have a shiny ubuntu well configured working, and because of torrents, use the old rock stable debian sarge.

Thanks in advance.

---

### Post by TeeAhr1 on 2006-06-09
[QUOTE=delphinen]I have been alway skeptic to think that the operative system, even the client you choose to download a torrent, could really influence in the download speed, until i migrated from debian sarge to ubuntu dapper.

dapper has been perfect so far, it turned my computer on an incredible multimedia desktop / webserver machine. But the problem with torrents is well know as i have seen in this forums, and is not solved.

I have been testing this since 2 months ago, when dapper betas was around.
First, the problems with Azureus. The last CVS version supposedly solves everything, except the bad performance and nat-meaningless?-blocked port warning. I have also tried with BitTornado and gnome Bit torrent (the one that comes with ubuntu). 
Always bad download/upload rates, torrents with 20+seeds download at 1.5k, while i switch to debian, and with azureus 2.2.0.2 i download at 6k+, many torrents at the same time.

I think the problem is something because of ubuntu. I dont know, iptables default configuration or something (does ubuntu comes with iptables?)

If anyone had this problem, or an idea of how to solve it, please help. Its a shame to have a shiny ubuntu well configured working, and because of torrents, use the old rock stable debian sarge.

Thanks in advance.[/QUOTE]
iptables is included, but not enabled by default.  You can view your policies with **iptables -L**.

Are your port forwarding settings correct?  Check to make sure everything's in synch, if you haven't already.

---

### Post by delphinen on 2006-06-10
[QUOTE=TeeAhr1]iptables is included, but not enabled by default.  You can view your policies with **iptables -L**.

Are your port forwarding settings correct?  Check to make sure everything's in synch, if you haven't already.[/QUOTE]

what port forwarding? i have a plain adsl pppoe connection.

---

### Post by jvictor on 2006-06-10
To get max d/l speed u need to enable portforwarding on your router. If you are using a Dlink one maybe this may be of some help

[http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-524/BitTorrent.htm](http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-524/BitTorrent.htm)

Google for your routers specific model and the isuue should get solved

---

### Post by delphinen on 2006-06-10
I dont get it, why should i forward torrent ports if im not behind an intranet, just directly connected to internet?

---

### Post by TeeAhr1 on 2006-06-10
You're still behind the modem, which is where port forwarding happens.  I had an alomst-similar experience just this week,  I've been trying to get my modem to forward me ports for weeks, without success.  I'm also pppoa, and it's just me and the modem.

Turns out, the firmware on the modem sucks and there is no available upgrade.  The only way I could get an open port was to set myself up as a DMZ server (basically putting myself "in front" of the modem).  Not a reccomended practice, needless to say.

A good way to tell if that's the problem is to specify in Bittornado the ports you want it to use, set your modem to forward them to you, start a torrent, then go [here]("https://www.grc.com/x/ne.dll?bh0bkyd2").  It's a site that will scan your ports, you'll be able to tell if you're getting a solid connection or not.  Just remember, unless you have an app actively trying for those ports, it will read "closed," so start the torrent up first.  Good luck!

---

### Post by delphinen on 2006-06-10
It says that my 6881 port is open

---

### Post by jvictor on 2006-06-10
OPEN does not mean forwarded. 

Lets try to put it as simple as this, any packet that is meant to reach port # 6881 is forwarded by the ADSL(router/modem) to ur machine. and ur machine runs ur client pgm on that port. So any data that comes in a packet meant for port # 6881 is directly sent to the machine instead of ur router doing any gibbrish on it.

---


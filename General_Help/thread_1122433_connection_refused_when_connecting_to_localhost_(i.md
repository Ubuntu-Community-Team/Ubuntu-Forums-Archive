---
title: "connection refused when connecting to localhost (irssi, bitlbee)"
date: 2009-04-11
forum: General Help
---

### Post by ikacer on 2009-04-11
I'm trying to set up bitlbee so I can run my IM though irssi. The bitlbee guide says "Since BitlBee acts just like any other irc daemon, you can connect to it with your favorite irc client. Launch it and connect to localhost port 6667".
However, when I try to connect to localhost or 127.0.0.1 I get the response,

Unable to connect server localhost port 6667 [Connection refused]
or
Unable to connect server 127.0.0.1 port 6667 [Connection refused]

I'm entering "/connect localhost", but I don't know if this is the right way to go about this. I've also tried xchat and got the same response. Also, I've tried disabling my firewall, but that didn't fix it either. I've also tried different ports.

I'm somewhat new to linux and irc, and don't have the slightest clue what to try next. Any advice?

---

### Post by ikacer on 2009-04-11
ok. I've got it working now. Seems I just needed to restart my computer after installing bitlbee, because when I tried it again this morning I didn't have any trouble at all.

---


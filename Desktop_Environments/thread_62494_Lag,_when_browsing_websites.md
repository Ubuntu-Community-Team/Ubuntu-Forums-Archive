---
title: "Lag?, when browsing websites"
date: 2005-09-04
forum: Desktop Environments
---

### Post by gogomon on 2005-09-04
Hey guys, I was using gnome for a while and FF, and I noticed that when I went to websites it would take a while to sort of load. What I mean is that I type in the address and then about 10-15 secs later the page would load just fine. The same happen with Konqueror in KDE3.4. So now I'm thinking its something with the DNS settings, I have dual boot, ubuntu and winxp and it dosen't happen in XP. Any commands or things I can check? thanks

---

### Post by 5-HT on 2005-09-04
May be an issue with IPv6, have you tried the tips from ubuntuguide.org ?
I noticed that disabling support to IPv6 in Firefox speed things up a bit for me.

To do so, type in the address bar ```
 about:config 
``` and filter for these entries to modify

[quote=ubutuguide]
network.dns.disableIPv6 -> true
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true 
[/quote]

HTH

---


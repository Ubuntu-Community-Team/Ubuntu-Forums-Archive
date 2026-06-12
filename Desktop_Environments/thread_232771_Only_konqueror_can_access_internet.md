---
title: "Only konqueror can access internet"
date: 2006-08-09
forum: Desktop Environments
---

### Post by edcrfv on 2006-08-09
I have a rather strange problem: I can't access internet anymore with any software (firefox, thunderbird, opera, ping, apt-get, ...) except konqueror which works perfectly well (that's how I can post here).
My local network works perfectly well, I can access my local server, my gateway, all the windows computers on the network, but nothing outside while it works when I boot on windows...

Any idea of a solution, or at least an explanation?

btw, I'm on Ubuntu Dapper.

*[edit]changed the title since I found other programs able to access the Internet[/edit]*

---

### Post by edcrfv on 2006-08-09
I've tried some more applications:

_Works_
Kaffeine
Konqueror
aMSN
IE6/wine
Offline Explorer/wine
UltraEdit/wine
totem
mplayer

_Doesn't work_
ping
wget
curl
firefox
thunderbird
opera
ping
gFTP
jFtp
azureus
smartCVS
smartSVN
httrack
vlc

---

### Post by LeonHeart on 2006-08-09
Are you sure your network configuration is correct?
Check it out: System->Administration->Nerworking...
Try switching to static ip mode instead of DHCP.

---

### Post by edcrfv on 2006-08-10
I tried... nothing changed...

It's really strange cause when I ping a domain name, the ip is retrieved from my gateway but the ping doesn't pass trough...

My gateway is a D-Link DSL-G604T that works great as it used to do with this computer+OS until recently. Nothing changed on the router.

If this was a configuration problem, how would some programs be able to deal with it?

---

### Post by zentus on 2006-12-08
I have the exact same problem.  Any ideas anyone?

---

### Post by edcrfv on 2006-12-09
I solved the problem by changing my router's configuration. I disabled DNS relay.

---


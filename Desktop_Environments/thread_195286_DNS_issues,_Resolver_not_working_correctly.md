---
title: "DNS issues, Resolver not working correctly"
date: 2006-06-12
forum: Desktop Environments
---

### Post by elemental666 on 2006-06-12
Here's the situation.  I've got a laptop and a desktop, both running Ubuntu.  These are connected to a Linksys WRT54gs, with stock firmware.  Which is in turn connected to my cable modem.  I've had one heck of day dealing with my cable company.  But I believe everything is right on their side at this point.

The problem is that, on my laptop, every time I try to surf the web I get redirected to the ISPs registration pages.  When I ping google.com it resolves to an ip on my providers network, not google (an yes I know the google.com ips, they all end in .99 and there are only 2, ocassionally a third for connections in the US).

Now, my desktop, also connected to the same router and thus same modem and ip, is what I'm using to post this thread.  So one system gets trapped in the registration stuff because all the internet sites resolve to this registration server (pretty standard for cable ISPs). But the other is good to go.

So how do I "reset" the dns on the laptop?  rebooting doesn't do it, bringing the interface all the way down and rebooting doesn't do it, its setup static to the router so its not a dhcp issue on the pc side, powercycling the router didn't do it either, nor did clearing the cache and cookies and all the other saved info from swiftfox...

I think in windows, this is an ipconfig /flushdns issue.  I've seen this talked about, and from what I researched there isn't an equivilant unless your running a DNS daemon.  Yet, one machine is stuck with this resolution issue...

I dunno what else to do, so I'm askin you.

---

### Post by Stirling on 2006-06-12
So currently the laptop uses the router gateway ip as its dns server address?  I would try statically setting the dns server address to one of your isp's dns servers and see if you can reproduce the issue like that.

---

### Post by elemental666 on 2006-06-12
ya know, I don't know what the dsn server addresses are, or how to check them.  I'm pretty much in the dark concerning DNS on ubuntu...

Where do I get this info?

---

### Post by elemental666 on 2006-06-12
AH HA!!!

GENIUS!!!

found the dns settings in the netwrok config tool, changed them to mach the dns settings of the desktop and bingo, I"m on again.

I'd buy you a beer, RIGHT NOW!  but I dunno where you are...  You have brought to an end a 10hr Broadband nightmare.  Next step for me is to learn how Ubuntu does all its networking.

Thanks again.

---

### Post by jerrylamos on 2006-06-26
'Most every time I boot up, the network DNS shows the router first, followed by the correct DNS.  Firefox tries to use the router as a DNS which doesn't work.

I delete the router DNS and Firefox works fine, until I boot up again....Of course, the Windows 98 and XP systems on the router don't have the problem so I'm ill inclined to change the router settings.

Any way to teach Dapper that the router isn't a DNS?  It's pretty boring to select networking, enter password, select DNS, delete the router every bootup.

Thanks much.

---


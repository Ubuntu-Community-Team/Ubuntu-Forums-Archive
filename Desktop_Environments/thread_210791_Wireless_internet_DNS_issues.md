---
title: "Wireless internet DNS issues"
date: 2006-07-07
forum: Desktop Environments
---

### Post by CookedGryphon on 2006-07-07
I'm using an RT61 chipset wireless card to connect to a netgear router, with 1.0.4.0 drivers and WPA-PSK security. 

It connects to the network fine, gets its IP etc. from dhcp, the gateway is automatically set to 192.168.0.1, I can connect to the administration page on the router, everything looks right until I try a web page. 

Then it takes ages to load eventually coming up with a cannot find server message. 

It works perfectly from a windows laptop which my friend has linked up to the same router so it can't be anything to do with the router's setup.

I can also browse the web using IP addresses (in a limited kind of a way, i.e. no hyperlinks and having to use the admin program on the router to do dns lookups) but for some reason i can't get dns to work :( 

Any help or advice would be appreciated, thanks!

---

### Post by CookedGryphon on 2006-07-07
Please help me, I can't even properly research the issue on the web as I can't access it properly.

---

### Post by roostishaw on 2006-07-07
The same thing was happening to me a few days ago. All I did was, in Firestarter, allow the dns connections (or however you describe them) from 192.168.1.1, or in your case, from 192.168.0.1.

Hope it works...

---

### Post by PriceChild on 2006-07-07
If roostishaw doesn't help, then i read a similar problem a bit ago, where disabling ipv6 fixed their problems.

---

### Post by CookedGryphon on 2006-07-07
thanks for the firestarter tip! I was actually using gnome-lokkit using simple settings so i hadn't noticed, jsut assumed a sane basic setup, but i turned it off and now everythign works.

---


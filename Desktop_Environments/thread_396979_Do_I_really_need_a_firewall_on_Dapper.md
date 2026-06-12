---
title: "Do I really need a firewall on Dapper?"
date: 2007-03-30
forum: Desktop Environments
---

### Post by mister_p_1998 on 2007-03-30
Ive been reading about all these things you should do when you first setup an install of Ubuntu, they all seem to say I need a firewall. I run behind a router sharing with two other windows boxes. I cant even get into my Dapper box from XP INSIDE my network, I have to do all transfers to/from via the Dapper box with Samba. Do I really need a firewall at all behind a router? Ive got Zonealarm on XP monitoring outgoing Apps, but dont think I need anything on Dapper. Am I mistaken?
Steve

---

### Post by scxtt on 2007-03-30
if you're not forwarding any ports from your router to your dapper box (or at all), i don't see the need ...

---

### Post by mister_p_1998 on 2007-03-30
Well Im running Ktorrent, but apart from that, just firefox & Thunderbird.

---

### Post by ComplexNumber on 2007-03-30
> **mister_p_1998 said:**
> Ive been reading about all these things you should do when you first setup an install of Ubuntu, they all seem to say I need a firewall. I run behind a router sharing with two other windows boxes. I cant even get into my Dapper box from XP INSIDE my network, I have to do all transfers to/from via the Dapper box with Samba. Do I really need a firewall at all behind a router? Ive got Zonealarm on XP monitoring outgoing Apps, but dont think I need anything on Dapper. Am I mistaken?
Steve
i would say that you need a firewall for every OS. even more so if a person is running a server. the router acts as a hardware firewall.

---

### Post by mister_p_1998 on 2007-03-30
So I dont need to monitor outgoing app connections then?

Steve

---

### Post by scxtt on 2007-03-30
if you're only allowing torrent ports (6881-6889) through your router - and they have a specific destination - then you should be fine ... if you're not using bittorrent all the time, and don't feel like disabling the torrent ports when not in use you _*can*_ have a software firewall to block those ports when torrents aren't in use ... there's no harm in a software firewall at all, but i don't see it as a necessity, esp. when you're talking about random IPs that connect via bittorrent ...

you could even be a "jerk" and not forward the bittorrent ports, you'd still be able to download - but i'm sure the other users wouldn't like you :-p ...

---


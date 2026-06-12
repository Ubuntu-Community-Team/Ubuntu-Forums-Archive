---
title: "quake3-server on Ubuntu 14.04"
date: 2014-04-21
forum: Gaming &amp; Leisure
---

### Post by jcarson99 on 2014-04-21
Hello,

I'm a little new to running a quake 3 server. I have installed the quake3-server package but I can't seem to get punkbuster to work. 

I've tried pv_sv_enable and sv_punkbuster 1 but they don't seem to work. When I connect to the quake3 server from anywhere on my LAN it lets me join the game without punkbuster enabled. I don't want people connecting without punkbuster enabled.

Anyone know how to get punkbuster working with quake3-server?

Thanks

---

### Post by Christmas on 2014-04-23
As far as I know Punkbuster is obsolete in ioQuake3 (I'm assuming that's what you have installed from the repositories). Even so, Punkbuster would not be included in your server setup (you'd have to download and install it manually from punkbuster.com) so setting it to 1 would have no effect. It may be that variable doesn't actually do anything anymore.

Edit: Have a look [here]("http://ioquake3.org/help/") to see why Punkbuster is not included anymore in ioQuake3. Just make your server without it, there are few players on the Quake 3 servers these days and there aren't cheaters. I suggest though you have a look at [OpenArena]("http://www.openarena.ws/smfnews.php") (**sudo apt-get install openarena openarena-server**), which is a Quake 3 complete clone, with different maps and models, but exactly the same gameplay. Notice that if you install openarena-server, it will run automatically at start-up on the default port, so you may want to stop the daemon or disable it inside /etc/rc2.d.

---

### Post by jcarson99 on 2014-04-23
I'll give openarena a try. Thanks for all the info.

---

### Post by jcarson99 on 2014-04-23
I installed openarena-server and that seemed to work fine at first but I ran into some trouble. I installed both of my brothers custom designed maps which run fine under q3a however textures where missing when using openarena client.

I couldn't connect my q3a client to the openarena server. Is it possible to use the ID software q3a client and connect that to an openarena-server or do you have to have q3a-client/q3a-server or openarena-client/openarena-server?

Thanks

---

### Post by Christmas on 2014-04-23
Yes, the protocols are diferent, so as far as I know you have to use an OA client to connect to the OA server (that comes included in the repositories too, just install the **openarena** package). Regarding textures, the developers of OA work hard to replace all the textures but some are still missing. But the maps in OA that are native have complete textures, with the maps from Quake 3 either find those which have few missing textures or none (there are many out there), or you can find some non-free PK3 files to fill in for the missing textures.

---


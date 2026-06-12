---
title: "routing controll"
date: 2005-11-03
forum: Desktop Environments
---

### Post by tagg3rx on 2005-11-03
Hello ubuntu gurus 

I want to set up my ubuntu box to be my play box and use it to escape a corporate lockdown.  I have 2 NICS in it:

The first i only want it to transmit packets to the remote terminal server (ie the client i use to controll it via VNC)

All other traffic I want to route through the second NIC witch connects to a straight DSL modem outside of the domain.

Is this possible?
If so how do i set it up.

I'm a noob so kISS plz

thanks,
:KS Tagg3rx :KS

---

### Post by mlomker on 2005-11-03
The easiest tool for internet connection sharing is **firestarter**, but if you're just going to VNC into it then you really don't have to share the connection at all.

I guess I don't understand what the question is.  Are you asking how to set up VNC or how to configure your Internet connection?

---

### Post by tagg3rx on 2005-11-03
Ok here is the scenario perhaps the visual will shed light

I'm sitting at my windows xp box taking helpdesk calls and only browsing to work safe web sites and not downloading any torrents or anything fun.  This box is on a priviate IP class that is managed in our domian and all traffic is monotored at the server.

Behind me is my ubuntu box and a clean open DSL line to the outside world - however the stupid DSL modem automaticaly does NAT and i cant disable it.  

So I have 2 nics in the ubuntu box

One plugs into the corporate domain which the only app i want to have access to it is the VNC server so i can sit at my desk and controll it via VNC.

The second NIC i want to pass all other traffic - so i can download torrents - use lime wire - etc... without having that traffic pass across the corporate network.

Seems like it should be simple enough to command eth0 to only talk to the rdesktop server - i just have no idea where to start doing that config.

:KS Tagg3rx :KS

---

### Post by mlomker on 2005-11-03
> Seems like it should be simple enough to command eth0 to only talk to the rdesktop server - i just have no idea where to start doing that config.


There's no need to configure anything in this case.  The two cards will not route between each other by default.    VNC will remote control the box itself and you'll be able to surf out from it.

You'll just assign an IP address to the corporate LAN side with no gateway (default route) set and configure the Internet card with the gateway pointing at your router.

---

### Post by tagg3rx on 2005-11-03
That makes perfect sense

Thanks!

:KS Tagg3rX :KS

---


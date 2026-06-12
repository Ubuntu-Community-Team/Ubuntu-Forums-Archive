---
title: "I need help forwarding port 25565!"
date: 2010-09-24
forum: Gaming &amp; Leisure
---

### Post by Artemis Fowl on 2010-09-24
I sure hope I didn't get the term wrong. Okay, I need to forward port 25565 so that I can create a Minecraft server. I think the port is closed because Minecraft, upon attempting to connect to my server, states that the connection was refused.

---

### Post by blueturtl on 2010-09-26
Post your router make and model, and we'll work from there. :)

---

### Post by Xeronix on 2010-09-26
[http://portforward.com/](http://portforward.com/)


That website I just posted is probably the best thing ever to come around to help with port forwarding. 

Simply find your Router Make and Model, then enter that into the site and it'll tell you how to forward the ports for your specific make and model.

Also,

if you're trying to connect via LocalHost or through your Local Network, (192.168.x.x) you may have to actually open up the port on the firewall of your server aswell.

Should not be too hard with a little bit of google.

---

### Post by ALD0003 on 2011-10-21
ive downlaoded the server and stuf but now were do i get the ip from:?::?::?:

---

### Post by pengyou on 2011-10-22
> ive downlaoded the server and stuf but now were do i get the ip fromyou can open a terminal and:
```
ifconfig
```But perhaps you might find it easier to right-click the network connection icon (should be in the top right corner) and hit "connection information".
Either way, you should get a bunch of useful information...
For the right clicking action:
> 
**IPV4**
IP Address: xx.xx.xx.xx
That's your IP address.
and a bit further down:
> 
...
...
Default Route: xx.xx.xx.xx
That's the router's IP address.

---


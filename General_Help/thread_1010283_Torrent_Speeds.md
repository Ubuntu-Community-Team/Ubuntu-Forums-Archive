---
title: "Torrent Speeds??"
date: 2008-12-13
forum: General Help
---

### Post by FLCL on 2008-12-13
I just recently changed ISP's from SBC (dsl) to Charter Cable with a 10 meg connection. Ever since the change my torrent speeds have been *slower* I have forwarded ports, and have no NAT errors. But even still it is only getting to about 30 down, and thats about where it's capping. My friend who has Charter as well gets around 110 down steady. Im using Azureus, have firestarter installed as well, ports have been opened in it, as well as forwarded in router. What gives?

---

### Post by tigerstripedcat on 2008-12-13
So far, you probably don't have enough info to find out for sure. You should try:

*A different computer (do you have a different computer to try?)
*A different client (ktorrent?)
*A different OS (does it happen in windows? try utorrent)


If any of those work, then you know it's your ubuntu or Azereus setup. If they don't then a couple of possibilities exist.  

* You really don't have ports forwarded properly (even though you think you do/Azereus tells you so)
* ISP is throttling your speeds despite not throttling your friend (it's possible)
* You have a bad connection?

It's really hard to tell at the moment, it can be like 10 different possibilities until you look further.  You need confirmation of it working or not outside of the narrow scope of "ports" to truly understand what the problem is.
TSC

---

### Post by mkvnmtr on 2008-12-13
There are many things to check. I am on a phone line connection and usually get 109 Kb/s from any good source. But sometimes it seems like from the same source it drops a lot. I have about decided that the phone company supplies so much bandwidth to this area. Then if somebody else has used most of it up my speeds will be slower. I think this happens at some colleges.

---

### Post by FLCL on 2008-12-13
I am currently testing it on my windows drive with uTorrent. The speed seems to fluctuate *a lot* it's a strong going torrent with plenty of seeds. Port checks out fine. Im thinking it could be my router thats screwing up my speeds. I've heard issues that a lot of routers will have a problem with the ammount of connections in torrenting and cause it to hang or drag. Excluding the factor that they could be throttling for the moment, could it be the port of choice? I wouldn't think it would matter as long as it is forwarded, correct?

---

### Post by kpkeerthi on 2008-12-13
Use a different torrent port, in a much higher range. E.g. **556881**

---

### Post by FLCL on 2008-12-13
Why such the high port range?

---

### Post by kpkeerthi on 2008-12-14
Because your ISP could throttle the default Bittorrent port range 6881 - 6999

---

### Post by FLCL on 2008-12-22
I never used those ports anyways haha. Anyways, i've tried changing settings in ubuntu but still nothing, i typically about about 10-15 down, whereas Windows i can get full speeds. Very inconvientent, anyone have any other ideas? I am also using Firestarter in ubuntu(hardy) and the ports are open, i have the ports forwarded in the router.

---

### Post by Slim Odds on 2008-12-22
> **kpkeerthi said:**
> Use a different torrent port, in a much higher range. E.g. **556881**

LOL, easy there tiger....

The valid port range only goes to 64K (65535).

---

### Post by kpkeerthi on 2008-12-23
Good catch. One extraneous 5. I meant **56881**.

---

### Post by FLCL on 2008-12-23
Haha, so what do you guys think? Problem in ubuntu or what?

---


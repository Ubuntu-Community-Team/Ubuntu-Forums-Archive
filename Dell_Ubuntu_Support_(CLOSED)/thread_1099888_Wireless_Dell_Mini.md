---
title: "Wireless Dell Mini"
date: 2009-03-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fwalda@waldaweb.nl on 2009-03-18
Good day to all of you!

I received today my Dell Inspiron Mini 9 and I'm trying to get it working with my wireless network. 

Due to problems with two older laptops I only want to use MAC address filtering as a security for my wireless network. Does anybody know how I can disable this in the Dell Ubuntu version 8.04 LTS? And yes, I am aware of the risk, but due to the above mentioned I can not do it any other way.

I use ssid broadcasting, but I just don't see the wireless network. I already switched the channel to a channel under 11 as this seems to give certain trouble as well.

I would be happy if anyone can give me a clue what to do.

Thanks in advance from Tulip country the Netherlands.
Fred Walda

---

### Post by ugm6hr on 2009-03-18
You don't disable or enable MAC filtering from Ubuntu; you do it from the router's setup screen.

As for why you can't "see" your access point (if you do not hide SSID...

Are you certain you can see and connect to the access point from your other laptops?

Can you see any other wifi access points?

---

### Post by sirebral on 2009-03-19
After I got mine I just plugged it into the internet via a wired connection then ran an update.  Wireless worked after that.

---

### Post by fwalda@waldaweb.nl on 2009-03-19
Dear ugm6hr,

the point is, I only want to use MAC control, not the WPA / WPA2-PSK / WEp / etc. The reason is two older laptops who (even with all drivers updates) don't want to work with WPA etc.

So I'm searching for a method to disable the rest on the Ubuntu Mini 9 and only keeping the MAC control. (Sorry if I didn't point that out correctly).

Tours sincerily
Fred

---

### Post by ugm6hr on 2009-03-19
> **fwalda@waldaweb.nl said:**
> So I'm searching for a method to disable the rest on the Ubuntu Mini 9 and only keeping the MAC control. (Sorry if I didn't point that out correctly).

Fred

I am no wifi expert, but I have a feeling you have misunderstood how WEP / WPA work.

As I stated, there is no need to disable it on the Mini, since Network Manager auto-detects the encryption (or lack thereof).

Hence, if you cannot see the access point, it has nothing to do with the encryption settings on NM (since there are none).

I hope that makes it clearer.

---

### Post by anjilslaire on 2009-03-19
ugm6hr is correct. By default, wep/wpa is not "on" in ubuntu. If you have a broadasting SSID on your router, all you need is to add your Mini's MAC Address to your router's approved list and go.

If you can't see the SSID beig broadcast, then that's a whole other issue, entirely. The situation you're describing requires zero configuration on the computer side, and only mninimal configuration on the router side.

---

### Post by sirebral on 2009-03-19
> **fwalda@waldaweb.nl said:**
> Dear ugm6hr,

the point is, I only want to use MAC control, not the WPA / WPA2-PSK / WEp / etc. The reason is two older laptops who (even with all drivers updates) don't want to work with WPA etc.

So I'm searching for a method to disable the rest on the Ubuntu Mini 9 and only keeping the MAC control. (Sorry if I didn't point that out correctly).

Tours sincerily
Fred

That is all I am using is the MAC control from my router.

---

### Post by Cowchip7 on 2009-03-21
> **sirebral said:**
> That is all I am using is the MAC control from my router.

Then you're good to go. Just add your mini's mac address to your router.

---


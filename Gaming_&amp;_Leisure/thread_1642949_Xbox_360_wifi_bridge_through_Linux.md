---
title: "Xbox 360 wifi bridge through Linux"
date: 2010-12-11
forum: Gaming &amp; Leisure
---

### Post by Miryr on 2010-12-11
Hello, this is my first post of them all, however it's under some distress. Recently I upgraded my laptop to a newer model since the wireless was failing; besides surfing the web one thing I used to do on my computer was to use it as an antenna which relayed the wireless signal to my Xbox 360.

The configuration was simple from what I can remember, it was something along the lines of changing a setting to "share with other computers" or something of the sort. Nonetheless, I've hit a snag while doing the same thing on this newer model. Everything seems to be exactly the same, I've even compared them side by side:

*Both of my internet connections have the "Automatic (DHCP)" method in Ipv4 Setting in place.

*The Ethernet connection is set to "shared with other computers" in the Ipv4 Settings.

*The Xbox 360 is set to detect the IP automatically so it does recognize that there's a connection and I can even view the IP address from the Xbox.

*Finally, I also had to turn the computer on before I hit the power on the Xbox, which I do whenever I try to get it to work.

I've tried all manner of settings and they don't seem to work. Nonetheless, at one point or another I managed to accidentally turn Xbox Live on. I don't really know what exactly I did to activate it, but it wasn't anything big so it must be some setting I must've accidentally clicked which returned to its default state once I turned the computer off.

Could anyone please help me find out the last piece of the puzzle? I'd greatly appreciate it.

---

### Post by Miryr on 2010-12-12
Bump

Someone please tell me what I did right so I can reproduce it, or at the very least give me ideas.

---

### Post by Miryr on 2010-12-12
I think I could solve the problem by bridging both connections, but how do I do this? I've scoured Google and can't find a nice tutorial to do so.

---

### Post by Predatorian on 2010-12-30
I am also looking to do this with my xbox. i was going about it the wrong way i believe, because i was attempting to use my netbook as a wireless adapter using IPTables. But so far, the only answer i get from anyone about IPTables is that i have to use NAT, and so far, what im getting with that is Double NAT'ing, and that is screwing up the Xbox Live Connection. There is a script that used to allow my xbox to be routed through the netbook, but it would not reach xbox live servers, and the only error i would recieve was that there was a DNS issue, even though i opened hte correct ports. I am trying to see if this bridging idea works. Thanks for any help.

---

### Post by brunowarne on 2010-12-31
I also faced this problem.One thing i shared with person who sold he 360.He gave me a cd & after installing which problem was solved.I was glad to have that.But now i lost that cd now i have no clue about that cd.What was in it & what was its working profile. I will gather knowledge about it surely

---

### Post by t4thfavor on 2010-12-31
If your linux box is the one with the internet directly connected, you need to plug your Linux box into the network, and then plug in your 360, you can then use the internet connection sharing wizard in something like FireStarter to get the 360 connected.

If you have wifi on your linux box, and you connect through that to the internet, you will need to setup a bridge on your PC between your wlan0, and eth0 ports, then while the wlan0 is connected to the wlan, you will assign an ip to the bridge (probably via dhcp on your router) after, plug the 360 into the eth0 port on your linux box, and you should get an address through your router.

If you want a much cheaper alternative to the 360 adaptor, get an open-mesh mini router for 30USD, and re-flash it with Openwrt (really easy with the ap51 flash prog)
configure it to connect to your wlan, and you will be able to leave it on all the time and not have to mess with your PC everytime you want to play some 360.


A better alternative to the problem you are having is to just get a longer ethernet cable though as direct cable is much better for online games where latency us a factor.

---

### Post by t4thfavor on 2010-12-31
> **Predatorian said:**
> I am also looking to do this with my xbox. i was going about it the wrong way i believe, because i was attempting to use my netbook as a wireless adapter using IPTables. But so far, the only answer i get from anyone about IPTables is that i have to use NAT, and so far, what im getting with that is Double NAT'ing, and that is screwing up the Xbox Live Connection. There is a script that used to allow my xbox to be routed through the netbook, but it would not reach xbox live servers, and the only error i would recieve was that there was a DNS issue, even though i opened hte correct ports. I am trying to see if this bridging idea works. Thanks for any help.

Yeah, lookup how to make an ethernet bridge, It's not that hard at all, and once your all setup, you don't have to touch it again.

---


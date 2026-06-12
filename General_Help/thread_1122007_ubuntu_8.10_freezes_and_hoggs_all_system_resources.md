---
title: "ubuntu 8.10 freezes and hoggs all system resources"
date: 2009-04-10
forum: General Help
---

### Post by slappy95633 on 2009-04-10
Ok so i have been using ubuntu fine and all of the sudden one day i noticed that my system froze when i had my screen saver up so i restarted and then immediately noticed that once the system started up my memory was at 100% and my CPU was at like 65% then after keeping the computer on for a while it locks up... i have tested my ram which i have 1GIG of it and my cpu is also 3.0GHZ HT. i am on the same computer same hdd everything doing thing right know with windows xp (my gaming partition) and it hasent had a problem... any one with any ideas

---

### Post by khelben1979 on 2009-04-10
Are you using the default screensaver which comes with Gnome?

---

### Post by slappy95633 on 2009-04-10
> **khelben1979 said:**
> Are you using the default screensaver which comes with Gnome?

one of them i have not downloaded any new ones i beleave i have it set for black screen... but non the less it dosent only freeze on screen saver it just takes probably like 15 or 20 min after it starts....

---

### Post by slappy95633 on 2009-04-10
also as a update it will even freeze on the login screen if i wait long enough

---

### Post by khelben1979 on 2009-04-10
I wonder if this is the cause of you going from Ubuntu Hardy (8.04) up to Ubuntu Intrepid (8.10)? What do you think?

Also, bad graphics drivers can cause serious problems and this could have been part of an update, too.

If your computer has gotten some type of hardware malfunction, this could also be a sign.

---

### Post by slappy95633 on 2009-04-10
> **khelben1979 said:**
> I wonder if this is the cause of you going from Ubuntu Hardy (8.04) up to Ubuntu Intrepid (8.10)? What do you think?

Also, bad graphics drivers can cause serious problems and this could have been part of an update, too.

If your computer has gotten some type of hardware malfunction, this could also be a sign.

i have always had a bit of a issue with video play and the visual effects and assumed that it was some kidof issue with my grafix card drivers..... but i have the newest ones from ATI

---

### Post by khelben1979 on 2009-04-11
> **slappy95633 said:**
> i have always had a bit of a issue with video play and the visual effects and assumed that it was some kidof issue with my grafix card drivers..... but i have the newest ones from ATI

Unfortunately, having the latest drivers from ATi does not necessarily mean that they are the best one for your computer hardware over there, but I suspect that there could be something else.

You could try experimenting with older drivers from ATi to see if it solves the problem, however, things might get worse if you do this, so it's up to you. Doing a backup of /etc/X11/xorg.conf is always to recommend before doing this and there's always the possibility to change the configuration file so that it uses the free open source (very slow) drivers if the native drivers refuses to work correctly.

---

### Post by sanjio on 2009-04-11
I am fairly new to Linux but I love every minute I spend with it.  I am currently running ubuntu 8.10 on my Eee PC 701 with 2gb if ram,8gb SD and that 4gb SSD.  I get slow downs and freezes from time to time but I think its due to the fact that I don't know how to configure the system to stop saving in the SSD and start using the SD drive. I have also found that I loose the tweakes it took me so long to figure out every time I do updates. I would like to learn to save the important things such as drivers, etc. and how to make the system see my SD as more drive space.  Are these things possible?

---


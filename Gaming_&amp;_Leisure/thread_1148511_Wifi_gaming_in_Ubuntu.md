---
title: "Wifi gaming in Ubuntu?"
date: 2009-05-04
forum: Gaming &amp; Leisure
---

### Post by javyn999 on 2009-05-04
Hey all, I have a question regarding the wireless connections in Ubuntu and their effects on gaming.

I am running an AMD 2.07ghz, 2gb pc2100 ram, Nvidia e-Geforce 6200 256mb AGP4x, with an Atheros wifi card.

I installed Alien Arena, Warsow and Nexuiz, and found that all three of those games have horrible lag spikes every 1 or 2 minutes like clockwork.

I have run the speed and line quality tests on dslreports, my up and download speeds are more than adequate for gaming, and my line quality test shows 0 packet loss.

Seem like the best explanation I've gotten for these lag spikes is the way Ubuntu handles my wifi connection.  Apparently Ubuntu searches for available networks in the area every 1 to 2 minutes, even though I am already connected to my network.  That would make perfect sense as to what is causing these intermittent lag spikes.

So, if anyone out there knows how I would disable Ubuntu from automatically searching for wifi networks I'd really appreciate it.  I don't see why it continues to search once I'm connected to a network anyway. 

Thanks for any help guys!

---

### Post by Bölvaður on 2009-05-04
um... I have played with wifi on xp and this is exactly what I got also, it is barely playable.
also in my ex clan there was a guy playing on wifi (also using xp) and he had worse problems than I had.

fps gaming on wifi is impossible.

---

### Post by Melcar on 2009-05-04
I game on wifi all the time.  No problems except for a little lag here and there.  It really depends on how you set up your network and the quality of the routers/adapters being used.

---

### Post by javyn999 on 2009-05-04
Oh well, not much I can do about the quality of my router since ATT provided it.  And my wifi card is pretty good as far as I know (Atheros).

I guess gaming on the wifi box isn't gonna happen.  :(

Thanks for the replies anyway

---

### Post by Bölvaður on 2009-05-04
gaming is possible, and might be quite good in well.. most games really. But in fps you will notice great lag (unless if you are new to them).

---

### Post by javyn999 on 2009-05-04
What non-fps games out there would you recommend?

---

### Post by drawkcab on 2009-05-05
I have a linksys router and although my latency is a bit higher, no spikes in either linux or xp.  Just say no to the free wireless routers that service providers give you.

---

### Post by Bad Boy Bubby on 2009-05-05
Well I can't talk much about wifi on ubuntu only tried it for a short time so far.  I have been gaming heavily on wifi for years including several pc's at the same time on wifi, it does give me slightly higher ping times I am talking 5 to 10 ms extra but I have rarely if ever had lag spike problems.  My machines are close to my router and always report Excellent wifi Connections.  So reliable gaming on wifi is possible.

---

### Post by jujubees on 2010-03-30
> **javyn999 said:**
> Apparently Ubuntu searches for available networks in the area every 1 to 2 minutes, even though I am already connected to my network.

bump

---

### Post by Ferrat on 2010-03-30
WiFi gaming is more about the signal then the OS, I have 54Mbit WiFi and 85+% signal and have never had any problem gaming WoW, Guild Wars, CS-S, Regnum etc also my router has a gaming mode which priorities game connections.

---

### Post by jujubees on 2010-03-30
> **Ferrat said:**
> WiFi gaming is more about the signal then the OS, I have 54Mbit WiFi and 85+% signal and have never had any problem gaming WoW, Guild Wars, CS-S, Regnum etc also my router has a gaming mode which priorities game connections.


i guess it must be the linux driver for my wifi card, because i don't have the lag in **exact 1-minute intervals **in windows.

---

### Post by clint0n on 2010-03-30
It is network-manager I think. I always used to get the most annoying lag spikes like every 30 seconds and I always thought it was cause I had a cheap wireless card (Ralink "rt61pci"). But since I uninstalled all network managers and just use the command line tools, iwconfig and wpa_supplicant everything works perfect now, I put it in a start up script by the way so I never have to deal with it. You can check out my guide if you want - [http://ubuntuforums.org/showthread.php?t=1426270](http://ubuntuforums.org/showthread.php?t=1426270) .

---


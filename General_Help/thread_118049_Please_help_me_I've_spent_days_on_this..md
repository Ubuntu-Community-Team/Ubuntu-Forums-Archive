---
title: "Please help me I've spent days on this."
date: 2006-01-16
forum: General Help
---

### Post by hanafyaa on 2006-01-16
I'm a newbie. I'm trying to connect an XP machine through a ubuntu machine to a router and have both be able to access the internet. I did it with both in XP very easily but I've read tens of things and I can't seem to get it to work in Linux. I have firestarter to use now. eth1 is my internet connection and eth0 is to the XP machine. The router is 192.168.0.1, eth1 is at 192.168.0.104, what do i do with eth0 address? The big problem seems to be I can't get the machines to ping each other. I think if I could figure that problem out I could get it to work.

---

### Post by Ubuntuud on 2006-01-16
It just worked with me, I started my machine and there was internet...

---

### Post by hanafyaa on 2006-01-16
Sorry I should have added that I can access the internet from the linux machine no problem. I get an error message of the device eth0 is not ready

---

### Post by halfvolle melk on 2006-01-16
So it's like this?

XP--eth0,UBUNTU,eth1--router--internet

Does eth0 have an IP? My back-end computers range from 10.1.1.x and my "eth0" is 10.1.1.1. Hope it helps. Oh, and you can type ifconfig to see what is what.

UBUNTU--eth0,DEBIAN,eth1--internet

---

### Post by pt78 on 2006-01-16
[QUOTE=hanafyaa]I'm trying to connect an XP machine through a ubuntu machine to a router and have both be able to access the internet. [/QUOTE]

Seems strange to me. Why don't you conncect XP machine directly to router? 

However, if you'd like to follow your idea, you would need to setup static (obviously best solution) IP on eth0 (something like 192.168.1.111), something similar on XP machine (e.g. 192.168.1.112) and set up Ubuntu bridge.

---


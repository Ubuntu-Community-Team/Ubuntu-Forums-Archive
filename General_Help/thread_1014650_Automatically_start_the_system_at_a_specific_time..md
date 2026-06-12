---
title: "Automatically start the system at a specific time."
date: 2008-12-18
forum: General Help
---

### Post by fnordcircle on 2008-12-18
Does anyone know of any software packages or unique solutions that will allow me to either startup a system at a given time of the day automatically or, at the least, bring it out of standby or hibernate at a specific time?

I've got an EEE PC running Ubuntu 8.04 that's just a glorified mp3 player most of the time that sits on a shelf in another room that I don't want to have to turn on every morning but I don't want to leave it running 24x7 either.

---

### Post by Tim Sharitt on 2008-12-18
You could see if there is an auto-boot feature in the bios settings, then enable automatic login i suppose.

---

### Post by tornadof3 on 2008-12-18
Many BIOSes have a "wake on lan" feature - perhaps you could set the computer to go into sleep mode and then have another computer in the house ping its IP or something at a set time each day?

---

### Post by Rodney9 on 2008-12-23
I use this code in Alarm Clock

> rtcwake -u -s 32400 -m on

32400 being 9 hours
I set it to happen 9 hours before I wish the pc to wake, then suspend whenever before.

---


---
title: "Clock Problem"
date: 2009-05-09
forum: General Help
---

### Post by abhishekdey1985 on 2009-05-09
Hi, i'm using "UBUNTU 8.10 Intrepid lbex" version. I'm facing a very weird problem regarding the System Clock. Every time i set the clock, after every restart, the System clock shows totally a different Time. Is it anything to do with Hardware clocking mechanism??

First time using Ubuntu as a development environement.

My hardware Configs are as follows:

Intel Core 2 Duo E8400 @ 3.00GHz (45nm Hafnium Series),
2GB @ 667Mhz
Gigabyte GA-G33M-S2L
XFX NVIDIA GeForce 8500GT 1GB

---

### Post by Tony Flury on 2009-05-09
Is your clock synchronised against a time server - that will probably solve the problem. The Real time clocks on PCs are notoriously bad at keeping time when powered off, and sometimes they don't keep the time right at all.

Have a look here : 

[http://www.watchingthenet.com/enable-auto-time-synchronization-in-ubuntu-and-kubuntu.html](http://www.watchingthenet.com/enable-auto-time-synchronization-in-ubuntu-and-kubuntu.html)

---

### Post by paradigm2 on 2009-05-09
> **Tony Flury said:**
> Is your clock synchronised against a time server - that will probably solve the problem. The Real time clocks on PCs are notoriously bad at keeping time when powered off, and sometimes they don't keep the time right at all.

Have a look here : 

[http://www.watchingthenet.com/enable-auto-time-synchronization-in-ubuntu-and-kubuntu.html](http://www.watchingthenet.com/enable-auto-time-synchronization-in-ubuntu-and-kubuntu.html)

Another possibility is a bad CMOS battery.  If this occurs after the computer is unplugged (or a switch is turned off).  But this would usually lose the bios settigns as well and go back to default.

Also there are settings which can change whether or not the time is updated (to the bios clock) upon shutdown.  I'm unsure as to Ubuntu's defaults, but this could be related.

---

### Post by Tony Flury on 2009-05-10
paradigm - you are right - that is what I was alluding to when i said that some pc clocks are not good about keeping time when the PC is turned off - you worded it far better than me.

However if the PC is synchronised with Internet servers, it should not really matter how bad the PC clock is.

---


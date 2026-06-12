---
title: "[SOLVED] No wireless connection"
date: 2008-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by amanda hill on 2008-12-29
:confused:please help I have this Dell inpiron 910 I just got it.I cannot access my wireless internet.I have been on hold with Dell for about 2 hours trying to get some help.I cannot speak with anyone from Ubuntu support.I am so frustrated I wish I had just got windows instead.Please help me get my wireless system up and running I am about to pull my hair out

---

### Post by marsopia on 2008-12-30
Hi amanda!
What linux are you using? Is it a ubuntu preloaded pc or you installed ubuntu on it?
Is the wifi button on?

Mariano

---

### Post by schimschone on 2008-12-30
Dell support is going to be pretty limited.. remember that this will be a learning experience and you will be better for it, no matter how frustrated you are now.

Also I've often noticed that in the past I've needed full access to the repositories.. System> Administration> Software Sources: and make sure you have 'main' 'universe' 'restricted' and 'multiverse' check-marked.. and the CD un-check-marked. This will allow you better access to the software you'll want to use.

Install any updates.. reboot.. then keep going from there. But marsopia is correct everyone will need to know what version of Ubuntu you're using, what hardware (wireless card) your using, and what computer you're using.

schim

oh.. and check out this if you're using 8.10: 
[https://help.ubuntu.com/8.10/internet/C/wireless.html](https://help.ubuntu.com/8.10/internet/C/wireless.html)

---

### Post by armandh on 2008-12-30
910? AKA the mini9? dell remix of 8.04?

first connect wired and down load updates.

then we assume a working wireless lan.
if not go to a known working wlan.

in system>administration>network [connections]
you will need to activate the wireless lan

then on the top bar icon switch to wireless, password [if any], add keyring password 
[if not already done at the previous step]

---

### Post by Talon2 on 2008-12-30
> **amanda hill said:**
> :confused:please help I have this Dell inpiron 910 I just got it.I cannot access my wireless internet.I have been on hold with Dell for about 2 hours trying to get some help.I cannot speak with anyone from Ubuntu support.I am so frustrated I wish I had just got windows instead.Please help me get my wireless system up and running I am about to pull my hair out

I'll assume you are using a Ubuntu pre-loaded Mini 9 which means you are using Ubuntu 8.04 with some specific tweaks.

In the upper right hand part of your screen you should see a little picture that looks like 2 screens.  You can left click or right click on it to see or do various networking related things.  Tell us what information you see when you right and left click on it.

One thing it should tell you is what access points are available.  Have you selected the access point you wish to use?

I have noticed that my Mini 9 wireless will not connect as well as I would like to some access points that are broadcasting signals above 802.11g.  Can you try your mini with an access point that is 802.11g only?

---

### Post by Talon2 on 2008-12-30
This web site may help:

[https://help.ubuntu.com/community/DellMini9#Knows%20issues%20and%20usage%20notes%20for%20all%20Mini%209%20systems](https://help.ubuntu.com/community/DellMini9#Knows%20issues%20and%20usage%20notes%20for%20all%20Mini%209%20systems)

It tells how to cycle the wifi and other tidbits.

Good luck.

---


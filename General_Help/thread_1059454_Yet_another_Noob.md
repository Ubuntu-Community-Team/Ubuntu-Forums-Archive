---
title: "Yet another Noob :|"
date: 2009-02-03
forum: General Help
---

### Post by Greedy1 on 2009-02-03
Well first I'll start by saying that this is my first time running linux. I've just installed Ubuntu 8.1 32bit on a Dell Inspiron E1705

Everything seems to be working except for my wireless card. I'm assuming I need a driver.
I'm needing the simplest  way to install it and although I'm not sure if they are correct here is the results from the network controllers test of  the app  called hardware testing (i got to it from system>administration>hardware testing):

Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

I'm assuming the bottom line is my wireless card, but im still needing a driver :(
Sorry If it sounds like i'm being lazy , i just really dont have a clue of what the hell I'm doing and would greatly appreciate some help.

---

### Post by residualbit on 2009-02-03
Check in system>administration>hardware drivers.

You might see a driver in there.

If not, you need to enable restricted sources...

go to system>administration>software sources

on the first tab, make sure all the boxes are checked except for source code. Hit close, and it will ask you to reload the sources. Reload them, and the check for updates (system>administration>update manager). Install any updates (restart if prompted) and the check for the driver(s) again.

---


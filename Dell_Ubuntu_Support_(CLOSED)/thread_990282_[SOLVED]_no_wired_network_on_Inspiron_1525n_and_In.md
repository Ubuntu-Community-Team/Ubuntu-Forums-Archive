---
title: "[SOLVED] no wired network on Inspiron 1525n and Intrepid 8.10"
date: 2008-11-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by freddybob on 2008-11-22
Just upgraded and Dell Inspiron 1525n from 8.04 to 8.10.  Everything seems to be working except the wired network connection.

The machine is defaulting to a wireless connection even with a network cable plugged in.  'Auto eth0' is set to connect automatically but never does.

Any ideas?

---

### Post by Spooky5 on 2008-11-22
Have you tried turning off the wireless switch on the right side of the laptop?

---

### Post by freddybob on 2008-11-23
Thanks for the suggestion, I hadn't tried that, I have now: with wireless switched off it still does not connect to the wired network.

Edit:  this was almost certainly because the cable had fallen out the back of my router!

---

### Post by vsbabu on 2008-12-25
I have the same laptop - same issues with wireless LED blinking all the time once I upgraded to Intrepid.

Solved now - don't know what solved it, but these are all the steps I did.

- restarted in recovery mode
- edited /etc/network/interfaces and removed all lines related to wifi leaving only two lines related to loopback
- removed the network panel applet (it was giving some error like can't find pan0:avahi
- then I went to network preferences and found that I've TWO wifi connections listed - not sure from where these came up. Deleted all.
- installed lucsview (don't ask me - I saw it in another thread :-)) and ran it once.
- reboot
- add network panel applet
- added new wifi connection - made it as system connection.

all works now.

---


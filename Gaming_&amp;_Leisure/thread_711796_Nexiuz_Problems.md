---
title: "Nexiuz Problems"
date: 2008-03-01
forum: Gaming &amp; Leisure
---

### Post by Neon612 on 2008-03-01
When I load the game the colours are way, way WAY off. I get some funny greens, blues, red, and all sorts of weird colours. 

Also when I change screen resolution it does the same thing. What causes it and how can I fix it?

I've got an ATI something for a video card. 2.4GHz CPU. 2GB RAM.

What could be causing this color problem?

---

### Post by piratesmack on 2008-03-01
ATI and Linux don't work well together. The ATI driver is probably causing the problem

---

### Post by Neon612 on 2008-03-01
The video card is an ATI RADEON HD 2400 Pro

---

### Post by Melcar on 2008-03-01
What driver are you using?  My card using the 8.2 drivers runs Nexuiz fine.

---

### Post by Neon612 on 2008-03-01
I dont know, actually. How would I go about finding out which version I have?

---

### Post by Melcar on 2008-03-01
How did you install the drivers? If you used the Restricted Driver Manager in Ubuntu it's going to be the 8.37 (unless the repos have been updated recently).

---

### Post by exneo002 on 2008-03-01
sudo apt-get install envy 
should work thats a driver manager 
also try getting a nvida or a cheap intel generic for this one purpose nexiuz doesn't require much power for a kickass shooter

---

### Post by Neon612 on 2008-03-01
I didn't install any drivers (At least to my knowledge) in Ubuntu. I figured they would be able to be found on the Windows sector of things.

---

### Post by oceanfree17 on 2008-03-02
Hi Neon,

I'm no expert but I've Nexiux running with an ATI card, so here's my set-up:

1. Under System > 'Administration' > Restricted Drives Manager - check that "ATI accelerated graphics driver is enabled and in use. (If it isn't check it and restart your machine.

2. If you have anything like 'AWN' running, make sure it's off before you play. If you have compiz running - you shouldn't have to turn it off, so leave it as is for now.

Try Nexiuz now, and tell us how you get on. If you're still getting funny colours you may have to change settings under your Multimedia Systems Selector to Video = X Window System (X11/XShm/Xv) - but leave that till you've tried 1 & 2.

Best of Luck

---


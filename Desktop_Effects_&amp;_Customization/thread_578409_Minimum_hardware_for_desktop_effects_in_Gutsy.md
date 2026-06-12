---
title: "Minimum hardware for desktop effects in Gutsy"
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by pjalegria on 2007-10-17
Hi

Can someone tell me what are the minimun hardware recomended for use desktop effects in Gutsy???

Tank You

---

### Post by FredB on 2007-10-17
I'm running Compiz Fusion with a Sempron 3100+ / 1.5 Gb / GeForceFX5200.

But I think a card like a GeForce 4  - or its generation - will be enough.

---

### Post by pjalegria on 2007-10-17
I have one old laptop, HP Omnibook 999mhz CPU and only 256RAM running Gutsy... is better to leave desktop effects off...LOL

Tank You

---

### Post by Martje_001 on 2007-10-17
I've heard it flawlessy worked on a Geforce 3 as well

---

### Post by FredB on 2007-10-17
Really ?

But I think a GeForce4 is really the start for Compiz. Anyway, as long as it supports my GeForce FX5200, I won't complain !

---

### Post by zekica on 2007-10-17
Compiz works on one of my old machines:
Intel P2 533MHz
GForce 4 MX440
256MB SDRAM @100MHz

Running KUbuntu 7.10 RC

And I haven't noticed huge slowdown because of it (maybe 2-3%).

---

### Post by pjalegria on 2007-10-17
But my graphic card is i810 Intel integrated Chipset...LOL
Do you think is enough to run it???

---

### Post by cudaman73 on 2007-10-17
You could always just try it.

If it doesn't work, it's easy enough to turn off...

---

### Post by FredB on 2007-10-17
It looks like i810 is the lowest intel chipset that could be used. But you'll be limited to 16 bits mode. Compiz relies on AIGLX.

[http://fedoraproject.org/wiki/RenderingProject/aiglx#head-43a98eb9adc0264c802bf5918f1cc57bddbbc129](http://fedoraproject.org/wiki/RenderingProject/aiglx#head-43a98eb9adc0264c802bf5918f1cc57bddbbc129)

"
**Known Working**

 ATI: Radeon 7000 through X850 (r100 through r400 generations). 
Intel: i830 through i945.  i810 works, but DRI requires 16 bit depth. 
nVidia: all cards supported by the driver 1.0-9625 or higher. 
Matrox: MGA G550 works with current proprietary matrox driver for Xorg 7.0 or unofficial driver from [http://matrox.tuxx-home.at]("http://matrox.tuxx-home.at/") for Xorg 7.1."

So you're lucky ;)

---

### Post by pjalegria on 2007-10-31
Yes, it works...but should i turn it on or off with my laptop hardware???What do you think about that???

---

### Post by pjalegria on 2007-11-01
Someone can give me a advise...

Tank you

---

### Post by riggits on 2007-11-01
advice: TRY IT. what's simpler than that.

---

### Post by carlos1992 on 2007-11-01
Dude i only have 246 RAM and an integrated Intel graphic card it's an old pc and i run the cube and things like but sometimes it gets slow but normaly i just used for firefox or opera, the other one (the one in the sig) i have all the effects i want (compiz just) a dock and it has never get freeze:lolflag:

---

### Post by c-m on 2007-11-25
lots of people here seem to have the effcts on fine, with lower spec systems.

My c2d with 6200 graphics card just grinds to a halt if i have the effects on, i have no idea why

---


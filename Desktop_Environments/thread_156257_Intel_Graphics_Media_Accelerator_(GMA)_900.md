---
title: "Intel Graphics Media Accelerator (GMA) 900"
date: 2006-04-06
forum: Desktop Environments
---

### Post by TheEclypse on 2006-04-06
My laptop is an Acer 3610.  I have just got DVD playback working on it - however the quality of the image is below what it should be.  I assume this is down to me not setting any drivers for the graphics, and it just using a default.  Does anybody know which drivers I would need to use ?

I am using Breezy with the Suspend2 patch.

---

### Post by openmind on 2006-04-06
Did you run *sudo dpkg-reconfigure xserver-xorg* ?

That will usualy find and set up your card.

---

### Post by TheEclypse on 2006-04-06
[QUOTE=openmind]Did you run *sudo dpkg-reconfigure xserver-xorg* ?

That will usualy find and set up your card.[/QUOTE]
Thanks, I have just given that a go, and I think there may be an improvement.  It still doesnt quite seem sharp enough - but it could be down to the mix between the intergrated graphics and montior - as I am comparing to what I remember seeing on my main computer, which has a decent monitor/graphics card.

---


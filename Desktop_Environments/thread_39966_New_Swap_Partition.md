---
title: "New Swap Partition"
date: 2005-06-07
forum: Desktop Environments
---

### Post by ghostfacepenguin on 2005-06-07
Hello everyone,

I have been looking all over for ways to create a bigger swap partition with out having to reinstall the Hoariest of Hedgehogs! I cannot find anything anywhere, might this be my only recourse, to re-install ubuntu so that I can increase the swap size?

Maybe I don't even need more swap, but when I open apps and do a lot of minimizing/ maximizing etc. it takes a while for things to react and when they do, I get ghastly "trails" from things moving, I would suspect that I need a bigger swap partition, but could be wrong. I have about a gig of ram, but my swap partition is a little under 1x the amount of ram I have. Is this not the norm?

Any suggestion on how to improve system performance is well received, as I am about to start my gaming adventures using ubuntu, I do not want to disaapoint myself and think that ubuntu is not the right choice for this linux newb....

Thanks for any sugestions....

---

### Post by jcooper on 2005-06-07
I would suggest its not your PC "swapping" if you have 1Gb of RAM.

Add the System Monitor applet to your panel, and use it to monitor your CPU, RAM and swap usage. That should show whether it is in fact your pc swapping, rather than anything else.

Post your system specs - it could be an issue with DMA on your hard disk, your graphics driver (specified in xorg.conf), or a completely different problem.

---

### Post by ghostfacepenguin on 2005-06-07
Sorry about not posting the specs...

I am running Dual PIII 933's
with roughly 896 megs of RAM
Asus v7700 Geforce 2 64 meg video card
20.5 gig Quantum HDD
Soundblaster Live sound card

I would think that this system should be more than adequate to run a more stable OS, such as Linux.

I will add the System Monitor to my panel and see what it says...

Thanks for the reply...

---

### Post by jcooper on 2005-06-07
I would agree - it is a more than capable system!

It will be interesting to see if your machine does in fact "swap", or if it is possibly the nvidia driver, or something else.

I'm not sure of any tools to capture system usage information for a given period - perhaps someone else can suggest something?

---

### Post by zAo on 2005-06-07
Do you have DRI/OpenGL enabled? Do you use PAN?

what does `free -m` say?

---

### Post by ghostfacepenguin on 2005-06-07
Jcooper,

I am not sure about the nvidia driver; 

zAo,

Dissapointingly enough I am at work and not in front of the machine to gather this information.

But could you expand a little more on the "DRI/OpenGL enabled" thing and "do you use PAN?"

Thanks for enlightening this n00b!!!

---


---
title: "Need assistance with visual effects"
date: 2009-02-06
forum: General Help
---

### Post by darkwavemaster on 2009-02-06
I have been working on this problem for a few days now.
Running Ubuntu 8.10 on a dell dimension desktop.
1.5 gig ram, geforce 5200fx graphics card

i have an integrated graphics card in my system that i think is causing my problem. I try to enable normal visual effects and it gives me an error message that the effects can not be enabled. I have tried everything. Can someone please assist me?

---

### Post by JECHO on 2009-02-06
have you installed the restricted driver for you graphics card?



> **darkwavemaster said:**
> I have been working on this problem for a few days now.
Running Ubuntu 8.10 on a dell dimension desktop.
1.5 gig ram, geforce 5200fx graphics card

i have an integrated graphics card in my system that i think is causing my problem. I try to enable normal visual effects and it gives me an error message that the effects can not be enabled. I have tried everything. Can someone please assist me?

---

### Post by darkwavemaster on 2009-02-06
Yes, I have installed everything i needed. I even looked at everything i needed to by going through other peoples problems, and there should be nothing inhibiting me from gettin the effects

---

### Post by ArtF10 on 2009-02-06
> **darkwavemaster said:**
> Yes, I have installed everything i needed. I even looked at everything i needed to by going through other peoples problems, and there should be nothing inhibiting me from gettin the effects

Saying what you did might help.

What was the exact procedure you used to install the drivers?

---

### Post by darkwavemaster on 2009-02-06
system > administration > hardware drivers and activated the divers for my nvidia card

i also checked some configurations through the terminal, as i read in other forums, but everything seemed correct

---

### Post by ellalan on 2009-02-06
Have you enabled simple ccsm in synaptics, this will enable you to change visual effects(normal or custom is good enough for compiz).HTH.

---

### Post by darkwavemaster on 2009-02-06
yes i have enabled ccsm

---

### Post by ellalan on 2009-02-06
Look for "simple-ccsm" and enable it.

---

### Post by darkwavemaster on 2009-02-06
i have already enabled this

---

### Post by Jackie999 on 2009-02-06
I found the fix for my nvidia GeForce FX 5500 after following the instructions by marius bock in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107)

I use the version 96 driver and edited the xorg.conf - it's been working fine ever since.

---

### Post by darkwavemaster on 2009-02-07
tried that fix...and to no avail... does anyone need me to post anyhting about my system...or i kno i have seen people in other posts request info recieved from terminal logs...

---

### Post by darkwavemaster on 2009-02-07
i tried that, but to no avail... does anyone need me to post anyhting like logs of info from the terminal?

---

### Post by darkwavemaster on 2009-02-15
bump...can someone please assist me

---

### Post by xualzan on 2009-02-15
Have you tried compiz-check it helped me fix compiz on my fathers PC. Here is a link for you 
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---


---
title: "kubuntu 4.4 on kubuntu 9.10, desktop effects won't work"
date: 2010-03-27
forum: Desktop Environments
---

### Post by SalsaDoom on 2010-03-27
Hi fellas.

Ok, so, this entire setup is fairly non-standard, since for starters I'm using the KDE 4.4 ppa's on 9.10. Its actually been very stable for me however, very few problems. 

Anyway, my customizations continue. I'm using the mainline kernel 2.6.33 kernel from the ppa's, which I need since I'm using the xorg-edgers stuff so I can use the ATI open-source driver. ATI's driver as of 10.3 doesn't support my card (which pisses me off, btw, why the hell not? -- its their damn card!). Now, the card is a "Radeon 5870 Mobility". 

ATI only released windows drivers for this card on 10.3, released 2-4 days ago.. so, yeah its pretty new. But here is the thing, my direct rendering *seems* to be working in linux. Things like glxgears run at around 680fps, glxinfo says "direct rendering: Yes". I havent tested it with anything I know requires opengl yet though. I probably should install a copy of Dominions 3 or something to test. 

But anyway, KDE's desktop effects won't start. From what I've read, if direct rendering = yes then I should be cooking with gas. If I was running gnome, I'd be looking for the compiz blacklist file and poking in that... but does KDE have such a file? I googled but couldn't find anything on it. 

Any suggestions fellas?

Cheers!
SalsaDoom

---

### Post by Chame_Wizard on 2010-03-27
Can you check in the system settings?

---

### Post by SalsaDoom on 2010-03-27
> **Chame_Wizard said:**
> Can you check in the system settings?

.. pardon me? I don't understand what your asking here.. I've gone to system settings and tried to enable it, if thats what you mean. It won't go. 

I did try an opengl game, Dominions 3, and I'm thinking that glxinfo is just plain wrong ;) I got around 3-5 fps in that game and its pretty minimal. 

I didn't realize that glxinfo *could* be wrong. Huh! 3d isn't that important for me right now anyway, It'd just be nice. I'll wait patiently for either ATI or the open source guys to finish up.

Cheers

---

### Post by InfectionZero on 2010-03-30
Can Someone revive this post, Im having the same issue with my Kubuntu installation.

---

### Post by JakeOfOz on 2010-03-31
In the system settings, does it say 'compositing is disabled' ?

---

### Post by InfectionZero on 2010-03-31
Bump

---

### Post by inobe on 2010-03-31
InfectionZero what card are you using ?

```
lspci
```

salsadoom the easiest method is throwing in a cheap 6series and up nvidia card.

i will be honest, ati doesn't do very well producing good drivers for other platforms, i know it's their card and they should be able, this has been discussed numerous times, the hardware is exceptional but it's useless if they don't produce really good drivers.

[http://ubuntuforums.org/showthread.php?t=1436774](http://ubuntuforums.org/showthread.php?t=1436774)

i moved over to nvidia years ago for this very reason, it's been years i waited, although driver support has improved for older ati models they are far behind with current hardware.

---

### Post by JakeOfOz on 2010-03-31
no really, tried the system settings>desktop>advanced  tab? check the 'disable functionality checks' box.

for your video card driver, try the ati site (quickest way is to google 'ati drivers' first hit) select a driver, download, open in terminal as admin (maybe change permissions first).

worked for the ati card in my old laptop.

---


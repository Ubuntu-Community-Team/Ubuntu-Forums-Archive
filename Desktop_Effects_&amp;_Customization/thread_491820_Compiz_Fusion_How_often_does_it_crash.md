---
title: "Compiz Fusion: How often does it crash?"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by jackmc on 2007-07-04
A question for other Fusion-ers. How often does it crash for you? I realise that it is alpha and all, but I was curious to see how often you need to run

compiz --replace or
emerald --replace

The reason I ask is because mine crashes so often that I have launchers in my panel for the above two commands :(, and they get used a few times a day...

---

### Post by BoneSaw on 2007-07-04
mine almost never crashes.

---

### Post by jackmc on 2007-07-04
I've decided to remove and reinstall. Maybe that'll help... I knew it was too unstable :)

---

### Post by avik on 2007-07-04
Yeah, I don't think mine has crashed even once.  That's the issue with alpha software; it'll work for some people and not for others...

---

### Post by Beatbreaker on 2007-07-04
my one hasn't crashed once either since i got emerald to work well with it - my Beryl would crash much more oftern than Fusion has

---

### Post by Happy_Man on 2007-07-04
Compiz Fusion has never crashed for me. Rock-solid, it is.

---

### Post by Seine on 2007-07-04
I couldn't get Compiz or Beryl to work since upgrading to Feisty. But Compiz Fusion installed first go, has never crashed and even survives after upgrades. I'm using GeForce 7400

---

### Post by christhemonkey on 2007-07-04
Compiz Fusion hasnt crashed on me per se, just about 1 in 3 times it fails to start complaining that my graphics card no longer supports textures to the power of 2....

---

### Post by slibuntu on 2007-07-04
Crashes? What crashes?! As alpha releases go, its as solid as an..... emmm.....  very solid thing :)

---

### Post by steveneddy on 2007-07-04
Crashes? I have never had a Compiz-Fission crash yet. Early beryl crashed a lot. Later Beryl good. 

But recently? No crashing in C-F.

---

### Post by hikaricore on 2007-07-04
Wonder if they fixed the 16bit colour issue yet.

---

### Post by reacocard on 2007-07-04
It's been crashing once or twice a day for me with Trevino's packages, so today I switched back to using my backported gutsy debs, we'll see if that's any more stable.

EDIT: the backported debs are here if anyone wants them: [http://syzygy42.tuxfamily.org/dists/feisty/compiz/](http://syzygy42.tuxfamily.org/dists/feisty/compiz/)

---

### Post by christhemonkey on 2007-07-05
Though it seems to use an inordinate amount of memory sometimes...

---

### Post by jackmc on 2007-07-05
I removed all compiz, fusion, beryl, emerald, and desktop effects (most of which shouls already have been done), and reinstalled. It hasn't crashed yet :)

---

### Post by eentonig on 2007-07-05
CF crashes once in a while. Usually every other day.

One thing that is garantueed to make it crash is grouping a few windows together and then switch between them. If I do that to fast, it's bye bye compiz...

But, concedring it's alpha state, it remarkably stable and fast.

---

### Post by Gen2ly on 2007-07-05
One of good bits that can help with stability is to disable the console-framebuffer (you don't need this for x86 anyway) in the kernel.  Compiz-Fusion adds to potential conflicts between the console driver and the xorg driver.

```
  &#9474; &#9474;        Device Drivers  --->                                         &#9474; &#9474;  
  &#9474; &#9474;        Graphics support  --->                                       &#9474; &#9474;  
  &#9474; &#9474;    < > Support for frame buffer devices                             &#9474; &#9474;  
```

I was having locks of the xserver, since I change it... its alright.

---

### Post by Billy_McBong on 2007-07-05
[COLOR="Blue"]i dont think mine has ever crashed
and i even use alot of the  unsupported plugins [/COLOR]

---

### Post by jackmc on 2007-07-08
Well, it's stopped crashing :)

Reinstallation solved the issue - haven't had to restart it once..

---

### Post by cyu6722 on 2007-07-09
on mine, it crashes when I do certain tasks or during random times.. The screen and everything completely freeze and I'd have to do a cold boot.

---

### Post by archiesteel on 2007-07-19
Mine crashes whenever I start Konqueror (Web browsing mode). Kind of annoying, but then again I'm using Trevino's unofficial "bleeding edge" packages...

---

### Post by zakalwe_ukuk on 2007-08-16
Mine crashes every time i try to select or deselect a plugin in ccsm, so i have to do this before starting compiz. It also crashes everytime i try to shut down the comp, although discovered that selecting 'switch user' and then shutting down works better.
Sick of trying to make it work properly now tbh, spent enough hours fannying about. Gonna leave it as it is until 5.03 or 5.04

---

### Post by DMurray on 2008-01-24
Crashes very often here, had to disable to get the system usable.
Video card is Geforce 6800. Beryl in Edgy and Feisty were a lot more stable for my particular setup.
The fact that it doesn't crash for some doesn't mean it is stable, since it is crashing for too many users.
After turning it off, no more crashes. I can live without it, so no big deal.

---


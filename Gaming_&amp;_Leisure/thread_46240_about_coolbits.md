---
title: "? about coolbits"
date: 2005-07-03
forum: Gaming &amp; Leisure
---

### Post by t2kburl on 2005-07-03
I read in the NVIDIA driver readme file that I can enable coolbits for my gpu (GF FX5200) for overclocking it. I have never done anything of the kind with a video card before.
Can anyone help teach me to use it?

btw ... no, I can't just go out and buy a better card at this time

Thanks in advance

---

### Post by rpgcyco on 2005-07-03
Once you enable coolbits (and restart X), you can use the NVIDIA Setting (nvidia-settings) program to autodetect the optimal frequencies. This can take up to and over 1 minute. As for manual changes, it's best to do them in really small changes at a time, only a few MHz.

If artifacts start to appear on your screen, turn down the overclock by a few MHz in the NVIDIA Settings program. And obviously, keep an eye on the temperatures. :)

I'm sure other people can walk you through a bit better, but that should be enough to get you started. Finally, damaging your card by overclocking voids your warranty most of the time, so please be careful.

- Rpg Cyco

---

### Post by t2kburl on 2005-07-03
thanks. I'll give it a go 


my warranty is long passed anyway, so thats no big worry.
I'm a conservative overclocker  ;-)

---

### Post by t2kburl on 2005-07-04
well, I don't think I gained much, but every little bit helps ...

when I ticked it up a notch and hit apply (after 4 or 5 times) nvidia settings just kicked it back down again to the previous setting.
I wonder if it knows its limitations
an extra 25 Mhz from the gpu and 20 Mhz Ram (slightly less gained on 3D settings) won't hurt   :)

---

### Post by rpgcyco on 2005-07-04
> I wonder if it knows its limitations

It's possible I would say, to some extent, else how would the detect settings thing work. Though I doubt it's 100% accurate (and\or safe). :)

> an extra 25 Mhz from the gpu and 20 Mhz Ram (slightly less gained on 3D settings) won't hurt

I strongly suggest not overclocking the 2D Settings. Your just putting more stress on the card when you probably won't even notice it. :)

- Rpg Cyco

---

### Post by t2kburl on 2005-07-04
good point

thanks   :)

---

### Post by tristan on 2005-07-04
I regularly use coolbits to overclock my FX5900XT (GPU 390->500, memory 760->900MHz) for 3D, where it gives Doom3 a boost from 39->43 fps. Certainly not a 20% speed boost that you might expect, but better than a kick in the head.

There's a couple of gotchas though...

1 - The temperature output can rise dramatically. I use a thermaltake passive cooler and using coolbits overclocking the card runs 10degC hotter (70+ deg C) under Doom3. Keep an eye on your temperature!

2 - You can get all sorts of artifacts (maybe even fry your card) if you push the overclocking too far. Even though the nvidia settings can suggest optimal values, on my card these values caused artifacts, so I recommend backing off a bit from them. 

Still, it's great to see nvidia giving us the same opitions as windows overclockers. If they'd just make it so that the coolbits settings were saved so I didn't have to manually adjust the settings each time I want overclocking....

---

### Post by motin on 2008-06-27
> **tristan said:**
> If they'd just make it so that the coolbits settings were saved so I didn't have to manually adjust the settings each time I want overclocking....

I don't know how it was back in 2005, but today you run nvidia-settings with gksudo or sudo and the settings will be stored for the computer. There is also the option of adding "nvidia-settings --load-config-only" to your session autostart as a user.

---


---
title: "No sound in Hoary"
date: 2005-06-03
forum: Desktop Environments
---

### Post by Azmodan on 2005-06-03
After I installed Hoary, I got no sound at all. Except in Frozen-Bubble (I really don't know why only this app have sound). I tried what was on the Ubuntu Guide, on the How to configure sound properly in Gnome section :

[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

Now, even frozen-bubble have no sound.  Any clue ?

---

### Post by nilus on 2005-06-03
Which soundcard?
Which player are you using?
Did you installed the correct codecs?

---

### Post by Azmodan on 2005-06-03
It's the soundcard integrated to an Asus P4P8X motherboard, according to Asus's website it has a                                                          ADI AD1985 SoundMAX 6-channel CODEC

I am not using any player yet, I just get plain no sound.  No sound on start up, no sound when I click on stuff.  No sound when I insert a CD.

Sound do work on Warty (at least with the LiveCD).

---

### Post by nilus on 2005-06-03
Run alsamixer.
Probably it's just the volume set at 0%.

---

### Post by Azmodan on 2005-06-03
[QUOTE=nilus]Run alsamixer.
Probably it's just the volume set at 0%.[/QUOTE]
 No, I checked.  I also just downloaded the Hoary LiveCD, doesn't work either.  Is there a way to return to Warty configs ?

---

### Post by glasscleaner on 2005-06-03
i have a digital output on my sound card, and by defaut alsa take this output instead of the analog one.


maybe is the same for you

---

### Post by Azmodan on 2005-06-04
[QUOTE=glasscleaner]i have a digital output on my sound card, and by defaut alsa take this output instead of the analog one.


maybe is the same for you[/QUOTE]

How do I change that ?

---


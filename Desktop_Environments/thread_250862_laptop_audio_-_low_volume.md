---
title: "laptop audio - low volume??"
date: 2006-09-04
forum: Desktop Environments
---

### Post by mykrob on 2006-09-04
Hi,

i have a new Compaq V5204NR

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=en&tool=prodinfoCategory&product=3197922&dest_page=prodinfoCategory&docname=c00700119](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=en&tool=prodinfoCategory&product=3197922&dest_page=prodinfoCategory&docname=c00700119)

I am actually running Mepis, which i based on Ubuntu, so i hoped that since you guys have a more active community, maybe you could help.

Got my Broadcom wireless working well enough to get by at home, got my 1280x800 resolution (thanks to your forums!), and i have sound. Problem is, even at maximum volume, the sound is very low. KMix reports the sound as HDA Intel, which accoridng the Compaq is High Definition Audio Intel..

Is there anything I can do to get better volume output from this thing?

Thanks,
-myk

---

### Post by Jussi Kukkonen on 2006-09-04
I'm not familiar with kmix, but after testing with alsamixer I found out that I had to set not only Master and PCM, but also a third setting (named after my sound chip IIRC).

 Still, the sad truth is that the laptop headphone outputs are very low power, even for headphones outputs...

---

### Post by mykrob on 2006-09-04
i checked alsamixer, i only have 2 settings, same as Kmix
Master and PCM

KMix is the volume control in KDE

[img]http://img169.imageshack.us/img169/7915/snapshot2jy8.jpg[/img]

-myk

---

### Post by FIONEX on 2006-09-04
Hey man,

I don't know about you but my Acer laptop has low volume in general.  If I blast my speakers in windows, it's lower than my sister's laptop's volume.  Linux seems to be a bit louder in terms of volume.  It could be just your laptop model.

---

### Post by ese5 on 2006-09-05
this apparently is a problem with the HDA driver itself...  and there is no known fix at this time.  search "high definition volume" in the forums for some threads that discuss possible workarounds

---

### Post by mykrob on 2006-09-05
thank you, i will search for that :)

---


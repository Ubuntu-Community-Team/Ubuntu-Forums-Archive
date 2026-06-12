---
title: "frozen bubble \ tux racer sound"
date: 2006-03-27
forum: Gaming &amp; Leisure
---

### Post by click4851 on 2006-03-27
Ok, system sounds are there, music plays on all players, totem does the movie thing. But no sounds from frozen bubble or tux racer? Even tried to click on the frozen bubble sound tab....nothing happens. Running Breezy with a Creative SB Live pci card. Any suggestions...

---

### Post by guine on 2006-03-27
If you have onboard sound in addition to your soundcard that could be causing your problem, I had that happen and everything worked fine once i disabled the onboard sound in the bios.

---

### Post by click4851 on 2006-03-28
I thought I had taken care of that....but I will check again, thanks for the tip.

---

### Post by Toddy on 2006-03-28
With Hoary and Breezy, I found that:

sudo apt-get install libsdl1.2debian-all

fixes the sound problem with games like Frozen-Bubble.

---

### Post by mrbiscuit on 2006-03-28
Ah, well most Applications like Totem and GAIM use ESD or ARTS sound system. However, other applications like Tux-Racer or Frozen Bubble, etc. do not use that. Therefore, open a Terminal and do sudo killall esd. And try re-running the program. You should have results if you open and close it a few times (the program that is)

---

### Post by click4851 on 2006-03-28
toddy/ Mr biscuit thanks, I will try both those the onboard sound was set disabled as I thought so I will let you know.

---

### Post by click4851 on 2006-03-28
how wonderful

Toddy your suggestion got me sound. tux racer sounded good, FB had sound but it was somewhat distorted or choppy.

Mr. Biscuit your suggestion cleaned up the sound so FB sounds perfect, but killing esd everytime doesn't seem very practical. What would you suggest for a long term approach, can I choose between esd and arts, or is that choice made for me.

---

### Post by click4851 on 2006-03-28
I found this link and learned alot about linux sound....

[www.linuxquestions.org/questions/showthread.php?t=308965](www.linuxquestions.org/questions/showthread.php?t=308965)

sounds like I need to configure the ESD system a little. Anybody else have to go this route?

---

### Post by click4851 on 2006-03-28
and this....

[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

dang it and I usually read the farking manual pretty well....

---

### Post by click4851 on 2006-03-28
Curious to see what the other members have done to massage their sound systems ....

---

### Post by mrbiscuit on 2006-03-30
I mean, the killall esd thing isn't really PRATICAL but I haven't found another solution since those games won't work with ESD.

---


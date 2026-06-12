---
title: "Quake 4 sound problems... again"
date: 2006-07-11
forum: Gaming &amp; Leisure
---

### Post by PriceChild on 2006-07-11
Hey there, i think i've fiddled with my systema bit too much...

I've suddenly found after a while of not playing it that the sound doesn't work.

Its garbled.... but ```
quake4 +set s_driver oss
``` causes ALL sound to disappear :(

I've searched around on the net, and supposedly installing libsdl1.2debian-oss instead of -alsa gets it all working. However it doesn't :(

Anyone got any ideas? Pricey

---

### Post by mjziegle on 2006-07-17
Add these lines to you /etc/init.d/bootmisc.sh file before the exit line.
sudo /etc/init.d/bootmisc.sh stop
sudo /etc/init.d/bootmisc.sh start

Worked for me.

#-----------------------
# fix sound for Quake 3 and Enemy Territory
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
#------------------------

---


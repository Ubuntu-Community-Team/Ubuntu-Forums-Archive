---
title: "Advanced Desktop effects Without proprietary driver 10.10"
date: 2010-12-14
forum: Desktop Environments
---

### Post by thewooleymammoth on 2010-12-14
Is it possible to enable the desktop effects without enabling the proprietary driver? Im using an Asus 51vx with Nvidia Geforece GTX 260m and the proprietary drivers kind of suck. My resolutions (although set correctly) are distorting pictures, my dual monitors is being funky and unpredictable... etc. Everything works great without the drivers installed except i cant enable advanced desktop features so my awn looks good :(. I know its just cosmetics, but i love my cosmetics, and they took a loooong time to get perfect.

Sorry if this is a repost but i couldnt find it anywhere. (so much info about advanced desktop effects out there). 

Thanks!

---

### Post by stinkeye on 2010-12-14
If all you want is for Awn to display properly enable compositing for metacity.
**gconf-editor /apps/metacity/general/compositing_manager**

---


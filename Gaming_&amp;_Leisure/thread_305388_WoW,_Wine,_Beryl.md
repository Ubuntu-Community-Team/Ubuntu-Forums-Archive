---
title: "WoW, Wine, Beryl"
date: 2006-11-23
forum: Gaming &amp; Leisure
---

### Post by reiki on 2006-11-23
Just a note here as I've just installed Beryl on Ubuntu Edgy (6.10)
Using wine 0.9.25 with nVidia 9629 drivers

With Beryl running (I do NOT have it starting automatically when I boot) my frame rates are cut in half. I went from 70-80fps to about 30-35 with Beryl active. Same character, same location.

Just an observation. I'm going to try starting Beryl, then using teh Beryl Manager I will switch from Beryl to Metacity and see if the frame rates come back up....

---

### Post by Shatrat on 2006-11-23
> **reiki said:**
>  I'm going to try starting Beryl, then using teh Beryl Manager I will switch from Beryl to Metacity and see if the frame rates come back up....
This is what I do, only with xfce instead of metacity.  
It's also a good idea for playing dvds in full screen because apparently there is a problem with vsync when the video driver is syncing to a dummy frame and then beryl is taking that dummy frame and putting it on the screen out of sync with refresh rate.

I've been looking for some way to make a launcher button or some kind of toggle that will let me quickly switch between beryl and xfce with 1 click instead of right clicking and going through the menu.

---

### Post by aidanr on 2006-11-23
```
#!/bin/bash

killall beryl &&
cd **/home/username/games/wow/**
wine **wow.exe** $1 &&
beryl &
```
change the path to the wow folder and the name of the executable (i don't play wow), and save it somewhere like /usr/local/bin/wow and make it executable

---


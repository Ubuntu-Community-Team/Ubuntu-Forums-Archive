---
title: "ripping ogg2mp3 with sound converter disabled!"
date: 2006-07-15
forum: Desktop Environments
---

### Post by tempo500 on 2006-07-15
hi,

i wanna convert some oggs to mp3 with soundconverter for my portable creative player...only that this option is disabled in the preferences dialog... i am listening to mp3s with rhythmbox all the time... where is the problem? thanx philip

---

### Post by reacocard on 2006-07-15
```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-mad
```
that should fix it

---

### Post by tempo500 on 2006-07-15
thanx for the quick reply, but... it did not change anything.... maybee tomorrow after a restart... thanx, phil

---

### Post by tempo500 on 2006-07-16
ok, figured it out! **gstreamer0.8-lame** with synaptic... thats it. thanx anyway, philip

---


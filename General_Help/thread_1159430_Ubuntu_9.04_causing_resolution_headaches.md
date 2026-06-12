---
title: "Ubuntu 9.04 causing resolution headaches"
date: 2009-05-14
forum: General Help
---

### Post by cavingman on 2009-05-14
So I have 9.04 running just fine, but it wants to default to 1920x1080, which is what I want it to be at "48" samsung tv", but for some reason what it's outputting is actually bigger than 1920x1080, as I cant see the menus or anything. they are completely off the monitor. I can move the mouse up off the screen and click on them, but i can actually see them.

I'm using the nvidia video settings program that came with the 180 (i think) driver, through HDMI on an ASUS en9400gt card to a samsung 48" tv.

thanks!

---

### Post by coffeecat on 2009-05-14
It sounds as though it's putting out 1920x1200, which is the 16:10 resolution for 24" computer monitors, rather than the 1920x1080 16:9 resolution for HD TV screens.

Have a look in System > Adminstration > NVIDIA X server Settings, and then Xserver Display Configuration. See what the Resolution button is saying. Is it set to "auto"? Can you change it to anything else?

---

### Post by cavingman on 2009-05-14
1920x1080 is the highest, all the way down to 400x300. i dont see anywhere to change or select aspect ratio...

1920x1080 is whats its going to on auto, its just too big! or something....

if i set it to 1600x1200 everything fits correctly, but looks like crap :(

---

### Post by cavingman on 2009-05-14
I got it! for some reason 16:9 on my tv is too big for the tv for some reason. if i set the picture size on the actual tv to "just scan", whatever that means, it's perfect.

thanks!

---


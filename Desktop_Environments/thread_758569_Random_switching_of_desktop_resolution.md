---
title: "Random switching of desktop resolution"
date: 2008-04-18
forum: Desktop Environments
---

### Post by quasar277 on 2008-04-18
The desktop resolution switches from 1024x780 to the 'native' 1280x1024 on startup at apparently random boots. 
Once that happens I cannot change the resolution back to 1024x780 (if I click on it on the screen resolution panel, nothing happens), I have to restart and it usually self-corrects itself.
If I set it at 1280x1024, nothing similar happens. It appears it just likes that resolution.

It's not a big problem at all, just a bit annoying sometimes.

I'm using ATI proprietary drivers and have an Neovo F-417 flatscreen

xorg.conf goes attached.

Thanks,
C.

---

### Post by erlyrisa on 2008-04-19
there is no real workaround for this yet....

unless you want to stick with one or the other...

in that case delete all your xorg.conf.1,2,3,4 etc backup files and make sure you only have xorg.conf

what's happening is that at the moment xorg and gnome screen reolution switcher don't co-operate. ---> especially if you have old copies of xorg.conf.1etc lying around.

once you have deleted all your old xorg.conf files - try out switching resolutions again... with a bit of luck gdm won't "fall back" to an old copy.


oh - also have a look into xrandr - the new way to do things.

---

### Post by quasar277 on 2008-04-20
Thank you :)
I'll try erasing/moving backup files since I'm fine with one resolution.

C.

---


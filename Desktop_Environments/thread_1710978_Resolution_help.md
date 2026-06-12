---
title: "Resolution help"
date: 2011-03-20
forum: Desktop Environments
---

### Post by majikme on 2011-03-20
I have a nvidia gforce fx 5200, on 10.10, and i got the drivers and had everything running in a high resolution comfortably. It worked well for about 3 days, when suddenly, i started my computer up and was stuck in an extremely low resolution. I reinstalled the drivers, but the option to go to a higher resolution had disapeared. I started using my windows partition again, when one day i started my ubuntu again and the resolution was back to normal. From then on, it has been hit and miss what resolution i end up in, though the majority of the times i start it up it is very low. Any suggestions?

---

### Post by Krytarik on 2011-03-20
You may try using "xrandr" to set the desired resolution, but it may even be necessary to set up a "xorg.conf" to pass also the correct monitor specs:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Greetings.

---


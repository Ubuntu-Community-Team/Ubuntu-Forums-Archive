---
title: "Typhoon 2001 on Ubuntu 13.04 64 bit"
date: 2013-09-15
forum: Gaming &amp; Leisure
---

### Post by BigSilly on 2013-09-15
Amazing. Still a great game after so many years, but great games never age. Pity it's such a fight to get it running, but at least on Linux with stuff like this, if there's a will, there's a way. ;)

Anyway, I have managed to get this running mostly pretty well on Ubuntu 13.04 64 bit thanks to some guidance around the net. Turns out you need to preload the 32 bit pulseaudio driver to get this to play with sound, but first you have to copy the proper file over to the correct folder. 

You have to copy libpulsedsp.so from the 32 bit libpulsedsp package in /usr/lib/i386-linux-gnu/pulseaudio over to /usr/lib32. Then you can cd into the games folder, and run it with ```
LD_PRELOAD=/usr/lib32/libpulsedsp.so ./typhoon
```. I managed to create a bash script that launches the game with these parameters, and all works pretty well. However...

Sound does work, but is quite crackly and often sounds out of synch sometimes. Sometimes it sounds like it's running too fast or too slow. Can anyone help with improving this? Seems a shame to get this far and not having it running A1. I've not had crackly audio on Linux since about 2007, so I'm not sure how to fix this.

Cheers all. :)

---

### Post by BigSilly on 2013-11-10
Saddo that I am I decided to try this game again on Kubuntu 13.10. Amazingly the tutorial still works and is even better on Kubuntu. There's no audio crackle or anything. So if you still love this game this is worth doing. :)

---

### Post by dannyboy79 on 2013-11-10
if this was a steam game you can edit the properties and run a special command during the game launches.

---

### Post by BigSilly on 2013-11-11
Yeah it's a shame. Such a great game though. It hasn't aged at all. Really pleased you can still get it running one way or another. :)

---


---
title: "Sound in Wine - ALSA or OSS?"
date: 2007-04-25
forum: Gaming &amp; Leisure
---

### Post by cogadh on 2007-04-25
I have been using ALSA fairly successfully with Wine, but I noticed that there are far fewer "fixme" and "err" messages in the terminal when I switch to OSS in winecfg. Before I go to the trouble of messing with a functional Wine, can anyone tell me if there are any advantages of one over the other?

---

### Post by AndrewRiedi on 2007-04-25
As far as APIs in general go, ALSA is quite a bit better for Linux users.

That said, months ago, Wine's OSS driver was way better than the ALSA one.  However, the Wine team has someone working on ALSA and it is improving rapidly.  For instance, he just implemented a mixer in ALSA.  Right now ALSA is probably a little bit worse than OSS, but it is catching up.  By 0.9.37 or so I would bet it will probably be on par with OSS, and after that it will surpass it.  Since you mention ALSA works fine for you right now, just keep it and watch as it gets better with every release of Wine.  Most of his work should be done by the end of summer.

---

### Post by willskills on 2007-04-26
Yep - just to say, if ALSA works for you, stick with it, personally I have to use OSS & Esound to get voice comms & game sounds to work, I can't get it to work with ALSA :)

---


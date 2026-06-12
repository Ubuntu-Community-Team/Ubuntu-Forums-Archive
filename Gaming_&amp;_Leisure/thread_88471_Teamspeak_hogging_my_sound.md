---
title: "Teamspeak hogging my sound"
date: 2005-11-10
forum: Gaming &amp; Leisure
---

### Post by jabb0 on 2005-11-10
hello,

I can quite happily listen to mp3's and play Americas Army at the same time.
However when i throw Teamspeak into the mix , if it is started first it hogs the sound card, and wont let anything else use it.

Now i have noticed a place where i could change the sound device in Teamspeak , currently  it is set to  /dev/dsp 

Does anyone know if i could safely change to something else whch will work?
or
Another workaround.

The thing is that Teamspeak is used by my clan in Americas Army to talk like VoIP, but its not much fun when i can hear them and noth the game, or vice versa - see where i am comin from

---

### Post by ulisse on 2005-11-10
I posted just yesterday something about that, I don't know if it is your case, but take a look here:
[http://ubuntuforums.org/showthread.php?t=88055]("http://ubuntuforums.org/showthread.php?t=88055")

Anyway, if your card supports hardware mixing, you could try to set teamspeak to use /dev/adsp

---


---
title: "Low Audio Output"
date: 2006-01-30
forum: Desktop Environments
---

### Post by h17m4n on 2006-01-30
Ok so I decided to try breezy 3 months after trying out hoary. It feels better and I had an easier time setting stuff up, but I've got one annoying problem. 

The audio output is much lower than what I get in windows, and if I try to increase by simply increasing the PCM volume I get the sound distorted. Right now my speaker's volume is at it's max, and I get the same volume output as if I had it 1/2 the way when using Windows.

I've been browsing these forums and google for about 3 days and still haven't found a fix for this. 

Any help would be greatly appreciated!

---

### Post by christhemonkey on 2006-01-30
run alsa mixer, make sure everythin is turned up
from  terminal:
alsamixer

Also if the speakers are turned up full, they are more likely to distort.

---

### Post by h17m4n on 2006-01-30
But the audio doesn't come out distorted because the speakers at maxed out, it comes distorted from the sound card's output, so the speaker is amplifying a distorted signal.

Even if I lower the speaker's volume and set the PCM volume to max it will come out distorted, so I have to keep it at 85%.

The sound card is a VIA 8235 btw.

---

### Post by h17m4n on 2006-01-31
Ok so I got it fixed. I'm not going to go deep into what causes this, but I'm posting what I did in order to fix it.

Open the terminal and run the following to create a file:

> sudo gedit /etc/modprobe.d/alsa-quirk

Paste the following in the file:

> options snd-via82xx ac97_quirk=1

Save it, close and restart. Done.

---


---
title: "Setting custom sound device in Doom 3?"
date: 2009-08-10
forum: Gaming &amp; Leisure
---

### Post by McTricks on 2009-08-10
I've got a USB headset, and it works for everything else I do (music, firefox, etc...) but it dosn't work in Doom... and that annoys me :P

How do I set it?

It's a Logitech G35 Gaming Headset (REALLY GOOD, BTW)
in the sound preferences page, it says 
"Logitech Logitech G35 Headset UBS Audio (alsa mixer)"

I also have an option for it to be OSS instead of alsa, but I like alsa :P

(btw, I've already tried the OSS setting for doom, and changing the audio device in game)

---

### Post by McTricks on 2009-08-10
Okay, I figured it out myself... I did this...

```
sudo apt-get install asoundconf-gtk 
```

then restarted, then went to "System > Preferences > Default Sound Card" and changed it to "headset"

also, I set the doom 3 sound setting to alsa

now it works :D

---


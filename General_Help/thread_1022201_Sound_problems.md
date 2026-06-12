---
title: "Sound problems"
date: 2008-12-26
forum: General Help
---

### Post by fbjoey on 2008-12-26
I noticed yesterday that I was getting no sounds, I'm not sure if I have ever had sounds on Ubuntu as I only installed it on Monday and didn't try playing any audio till yesterday (I cant remember hearing any sounds on start-up). I tried headphones, I can very faintly hear it in the background but its certainly not listen-able. I also tried pluging the speakers into a different hole and this to my surprise worked but the sounds is really low and not listen-able. Can anybody help?
 Thank you.

---

### Post by namdung on 2008-12-26
In terminal type
```
alsamixer
```
use the arrow keys to increase the volume.

Have u installed GStreamer to play proprietary codecs like avi, mp3 etc.?

The sound controls are in *System-->Preferences-->Sound*. Usually detect works fine.

---

### Post by fbjoey on 2008-12-26
All the sound levels are cranked up to full volume. GStreamer? No I haven't. Should I?

---

### Post by namdung on 2008-12-26
> **fbjoey said:**
> All the sound levels are cranked up to full volume. GStreamer? No I haven't. Should I?

Ubuntu has an *African drum* sound in the Login screen, another one after logging in and another one while logging out by default. If u haven't heard this so far then there's a problem which we need to figure out.

Do u have a sound card? Does it require additional drivers to be installed?

Pls check the Sound settings described earlier to test ur sound.

Pls install GStreamer from *Add/Remove Applications* to play other proprietary music/video files.

---

### Post by fbjoey on 2008-12-26
I just looked and I do have GStreamer :)

I'm pretty sure I have a sounds card as windows audio is perfect. 
How can I find out information about my sound card? 
I think your right about needing a driver but I'm not sure on how to go about it.

---

### Post by fbjoey on 2008-12-26
bump

---

### Post by namdung on 2008-12-26
I reckon u don't have an additional sound card and that ur sound card is in the motherboard. 

If u have a live CD, try to run and see if u hear the sounds. Ubuntu will generally identify the common drivers.

And did u try the Sound settings to see if the settings are correct?

---

### Post by fbjoey on 2008-12-26
Okay, the settings are all on auto-detect. I can hear them with the live cd and without it. its just to quite

---

### Post by namdung on 2008-12-26
> **fbjoey said:**
> Okay, the settings are all on auto-detect. I can hear them with the live cd and without it. its just to quite

So ur sound card is fine it's just that it's a little soft.

Like I asked earlier have u tried the **alsamixer** settings.
Ensure that the PCM and Front are also set to maximum.

---

### Post by fbjoey on 2008-12-26
It was the PCM and front. 
Thanks a bunch mate :D

---


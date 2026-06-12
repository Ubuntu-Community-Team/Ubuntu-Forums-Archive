---
title: "Why is my sound distorted?"
date: 2005-04-17
forum: Desktop Environments
---

### Post by NerftheSmurf on 2005-04-17
So this has been a problem with xmms and, now that i just installed it, mpd. For some reason a certain range of audio comes out muddy. This usually happens with hip-hop songs as well as some techno. Basically there is a very noticable 'muddy' static that comes with certain kinds of base and it makes certain songs sound absolutely horrible.

Now I tried amarok and for some reason I was able to fix this with it's equalizer, even though similar attempts failed with xmms. The problem is when I turn on the equalizing enough to get rid of the static, the volume of the audio is very much reduced. This means I have to turn it up significantly, which makes for jarringly loud system sounds. I eventually moved on because amarok is a pretty big memory hog in the GNOME environment (I tried the kubuntu desktop but encountered problems there that I don't even wanna *think* about right now).

So can anyone tell me how to fix this? I really like mpd and it'd be a shame if I could use it because of something like this. :sad:

---

### Post by Fab on 2005-04-17
i had a smiliar problem after installing alsa
switched back to esd

---

### Post by NerftheSmurf on 2005-04-17
[QUOTE=Fab]i had a smiliar problem after installing alsa
switched back to esd[/QUOTE]
 But xmms uses esd as it's audio output. Also in the mpd config file I tried setting the ao_driver to esd but it's the same thing.

---

### Post by Fab on 2005-04-17
correction:
i used alsa mapped to esd, and switched back to esd only..
one sound that was really ugly was the login sound

---

### Post by xyz on 2006-06-20
How about this:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
...might help?
Good luch!

---


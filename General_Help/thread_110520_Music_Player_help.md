---
title: "Music Player help"
date: 2005-12-31
forum: General Help
---

### Post by Rahu on 2005-12-31
I'm looking for some program that will let me choose to only play songs from a certain artist, or one album of a certain artist(like WMP). Rhythmbox seems to be what i'm looking for, but I cant seem to get it to play mp3 files. Could anyone here suggest something that would allow me to do this?

---

### Post by three_sixteen on 2005-12-31
[QUOTE=Rahu]I'm looking for some program that will let me choose to only play songs from a certain artist, or one album of a certain artist(like WMP). Rhythmbox seems to be what i'm looking for, but I cant seem to get it to play mp3 files. Could anyone here suggest something that would allow me to do this?[/QUOTE]

Rhythmbox will play mp3s just fine.. just make sure you have the right codecs installed :)

---

### Post by audax321 on 2005-12-31
To install the codecs, you have to enable the universe repositories and then in a terminal:

This will install all the gstreamer plugins including the one needed for mp3s: sudo apt-get install gstreamer0.8-plugins
For just the mp3 codec: sudo apt-get install gstreamer0.8-mad

More info here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by dage on 2005-12-31
thanks a lot, I can play all music format now, cool man :d

---

### Post by zodder on 2006-01-01
Thanks. That worked perfectly for this n00b. :)

---


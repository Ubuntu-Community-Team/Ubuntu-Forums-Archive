---
title: "Sox conversion?  ogg -&gt; mp3"
date: 2006-09-17
forum: Desktop Environments
---

### Post by tht00 on 2006-09-17
Alright.  Why won't sox convert to mp3?  I've had this problem before, and as far as I know, I have all the lame libraries that I need. (gstreamer0.8-lame, lame, liblame0).

```
$ sox 01.ogg 01.mp3
sox: Failed writing 01.mp3: Sorry, no MP3 encoding support
```

Yeah... so.. has anyone had luck getting this to work?

---

### Post by MacMan on 2006-09-18
Try this:
Convert the ogg file to wav using sox, then the wav to mp3 using lame.

I haven't found an easier way yet... :-)

Ciao.
-- 
Mac

---

### Post by tht00 on 2006-09-18
> **MacMan said:**
> Try this:
Convert the ogg file to wav using sox, then the wav to mp3 using lame.

I haven't found an easier way yet... :-)

Ciao.
-- 
Mac

Hmm... is this a bug with sox then?  Kinda annoying... I guess I'll just write a script to handle this then.

---

### Post by moore.bryan on 2006-09-18
[I]don't know about sox, but what about the ogg2mp3 converter script?
[http://marginalhacks.com/bin/ogg2mp3](http://marginalhacks.com/bin/ogg2mp3)
[/I]

---

### Post by MacMan on 2006-09-18
> **tht00 said:**
> Hmm... is this a bug with sox then?

If I remember correctly, it's a choice, not a bug.

I don't see the problem: lame is an excellent encoder and the whole process won't take more than 5 minutes per song.

Ciao.
-- 
Mac

---

### Post by ayoli on 2006-09-18
> **moore.bryan said:**
> [I]don't know about sox, but what about the ogg2mp3 converter script?
[http://marginalhacks.com/bin/ogg2mp3](http://marginalhacks.com/bin/ogg2mp3)
[/I]

nice script, works fine, thanks for the hint :)

---

### Post by moore.bryan on 2006-09-18
*glad to help...*

---

### Post by raghav_p on 2006-09-18
you could also try [gNormalize]("http://gnormalize.sourceforge.net/") which is a GUI to normalize.

---


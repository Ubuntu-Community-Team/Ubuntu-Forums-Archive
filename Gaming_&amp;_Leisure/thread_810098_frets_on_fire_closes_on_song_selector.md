---
title: "frets on fire closes on song selector"
date: 2008-05-27
forum: Gaming &amp; Leisure
---

### Post by king vash on 2008-05-27
I have a lot of songs so i use the sorting feature (were you type and it selects only songs that fit the typed string)

and it now closes anytime I press a key with this at the end of my log

```

[1;32m(N)[0m Loaded SongChooser.None in 0.001 seconds
[1;31m(E)[0m exceptions.UnicodeDecodeError: 'ascii' codec can't decode byte 0xb4 in position 3: ordinal not in range(128)
[1;32m(N)[0m 'ascii' codec can't decode byte 0xb4 in position 3: ordinal not in range(128)
[1;34m(D)[0m View: Push: MessageScreen

```

[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=3;t=2251;st=0](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=3;t=2251;st=0)
is about this error, I don't have the library.zip, or an input.pyo, I tried unplugging my usb webcam but that didn't solve it either

I have tried with bot hversion .451 and .541

---

### Post by king vash on 2008-05-29
I'm still having this issue and i've learned it has to do with no standard ascii charactures is their anyway to easily remove them from 3000+ songs?

---

### Post by RubenK on 2008-07-25
Please anyone? I can't find it with the help of google. Nor does the forum offer an ubuntu solution to the problem. I have no idea what to do. Please help, I really want to get cracking on those GH3 songs...

---

### Post by mrv on 2008-11-19
I fixed the problem by changing the Log.py in /usr/share/games/fretsonfire/game as in the attachment, or in short just:```

-  msg = unicode(msg).encode(encoding, "ignore")
+  #msg = unicode(msg).encode(encoding, "ignore")
+  msg = "overridden"

```

It seems the problem was just in the logging code, so it's a rather stupid bug. But I am not sure how common the problem is, it might be worth having a bug report and attachment for it too.

---


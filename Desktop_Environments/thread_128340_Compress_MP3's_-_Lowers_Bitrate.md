---
title: "Compress MP3's - Lowers Bitrate?"
date: 2006-02-11
forum: Desktop Environments
---

### Post by happyponcho42 on 2006-02-11
Does anyone know of a program equivalent to DietMP3 on Window$ that allows me to shrink mp3's by encoding it in a lower bitrate?

:cool:

---

### Post by happyponcho42 on 2006-02-11
[QUOTE=happyponcho42]Does anyone know of a program equivalent to DietMP3 on Window$ that allows me to shrink mp3's by encoding it in a lower bitrate?

:cool:[/QUOTE]

I found LAME to work great:
```
lame -b [bitrate] input.mp3 output.mp3

ex.
lame -b 64 song.mp3 song64.mp3
```

---


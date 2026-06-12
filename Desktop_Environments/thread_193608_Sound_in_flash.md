---
title: "Sound in flash??"
date: 2006-06-10
forum: Desktop Environments
---

### Post by master5o1 on 2006-06-10
How do I get sound in flash...I did everything that it said to do in the wiki (found in the "RestrictedFormats" page... AND it still doesn't have sound...(unless the movies I've been trying to play just don't have sound :D)

---

### Post by BitTorrentBuddha on 2006-06-10
You don't have hardware mixing on your sound card, simple fix.
```
sudo aptitude install alsa-oss
``` and then when you want to browse the internets, just make sure to type ```
aoss firefox
``` (You can replace "firefox" with epiphany or whatever other browser you may use as long as it's preceded by "aoss".)

---

### Post by master5o1 on 2006-06-10
Thanks :D

---


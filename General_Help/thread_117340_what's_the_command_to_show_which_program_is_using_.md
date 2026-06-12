---
title: "what's the command to show which program is using the soundcard?"
date: 2006-01-14
forum: General Help
---

### Post by ice60 on 2006-01-14
hi, i can't remember the command which will show the program using the soundcard. i have done a search but i can't find it. i had a look in system monitor but i can't work it out. BMP won't play.

---

### Post by ice60 on 2006-01-14
i just tried this
```
sudo fuser -v /dev/dsp

```
and there was no output but it says something is using the card. i'll restart it, oh, it was streamtuner :rolleyes:

---


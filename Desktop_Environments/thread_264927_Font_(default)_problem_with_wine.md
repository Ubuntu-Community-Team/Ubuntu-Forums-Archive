---
title: "Font (default) problem with wine"
date: 2006-09-25
forum: Desktop Environments
---

### Post by BirdZerk on 2006-09-25
I installed wine using the  "HOWTO Setup Wine" thread, everything went perfectly, what programs I installed seem to run just fine.  When I installed the last program using wine, the wording for it and the other programs changed to a script font and they are very difficult to read.  Its as if the last program changed a default setting, that the programs use to say, which font they are suppose to use for display.  Is there anyone in this forum that knows how to fix it, or do I need to go to wine website to get this info?

---

### Post by BirdZerk on 2006-09-25
Here is a pic of one of the programs after the font changed
[ATTACH]16335[/ATTACH]

I hope someone can help!

---

### Post by BirdZerk on 2006-09-26
I think I found a solution, I don't know if it is the best way, but it did work.  All I did was remove all the fonts from the file

```
$.wine/c/windows/fonts
```

except the one you want to keep.  I kept the font arial.  I hope this help someone.

---


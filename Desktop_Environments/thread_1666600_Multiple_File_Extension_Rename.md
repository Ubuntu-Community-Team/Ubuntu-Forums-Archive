---
title: "Multiple File Extension Rename"
date: 2011-01-13
forum: Desktop Environments
---

### Post by dontgetshocked on 2011-01-13
Is it possible to do multi file extension rename?i.e. change all .mp3 to mp4... If so how? Also is it just me or does anybody else have a problem changing say their music volume when scrolling thru your browsers bookmarks?

---

### Post by nothingspecial on 2011-01-14
If you mean literally changing the extensions rather than converting the format - 

```
rename -n 's/mp3$/mp4/g'
```

The -n option runs a "test" command without actually doing it. If you are happy with the results remove it and run it again.

---


---
title: "Restoring icons"
date: 2006-09-03
forum: Desktop Environments
---

### Post by greeklegend on 2006-09-03
I wanted to create a custom icon, and decided to chmod /usr/share/pixmaps to 666 so i could write to it...bad move. Everything in the directory turned into a zero-length file, so i delete it and copied /usr/share/pixmaps off the ubuntu CD. Anyway, that got the default ones back, but how do i restore the icons for other programs that i have .deb's for, say thunderbird or gtkpod?
Thanks in advance

---

### Post by cilynx on 2006-09-03
I would just
```

sudo apt-get install --reinstall thunderbird

```
etc...

It's a little overkill, but it isn't destructive and it gets the job done

---


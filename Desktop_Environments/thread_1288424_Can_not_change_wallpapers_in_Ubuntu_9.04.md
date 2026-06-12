---
title: "Can not change wallpapers in Ubuntu 9.04"
date: 2009-10-11
forum: Desktop Environments
---

### Post by drunkenbrawler on 2009-10-11
I am completely new to linux and have Ubuntu 9.4.
I want to change the default wallpaper and so i tried this-
system - preferences - appearance - background
from that i added a pic i wanted as wallpaper and closed the appearances window ( i could not find 'save' or 'ok' button.)
It changes the wallpaper but everytime I shutdown, the wallpaper is restored to default.:(
What should i do? 
I have just started using Ubuntu. I am a regular Windows XP user
thanx

---

### Post by wojox on 2009-10-11
You need to add it to:

```
/usr/share/backgrounds/
```

Alt+F2:

```
gksudo nautilus
```

Then navigate to the above directory and drag and drop your image.

---

### Post by zeroseven0183 on 2009-10-12
Perhaps the picture you're trying to load is located on another partition that is not automatically mounted.

If so, then go ahead with wojox's advise.

---


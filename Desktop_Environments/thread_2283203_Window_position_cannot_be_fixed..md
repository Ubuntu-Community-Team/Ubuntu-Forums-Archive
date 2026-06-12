---
title: "Window position cannot be fixed."
date: 2015-06-20
forum: Desktop Environments
---

### Post by Pri_Joshua on 2015-06-20
I have a deep trouble for a few days. 

I cannot position my VLC media player. Although I have tried ```
vlc --intf dummy --video-x=200 --video-y=100 udp://@232.1.1.15
```
Or configuring in compiz Place window. Where I set that ```
class=vlc
``` or ```
 role=vlc-video
``` and X as 200 and y as 100 still nothing happen. 

Is there any method I can fix VLC player in a position? I can do better in command line.

---

### Post by CantankRus on 2015-06-20
Works in compiz here.
Class is case sensitive.
```
class=[COLOR="#FF0000"]V[/COLOR]lc
```

---


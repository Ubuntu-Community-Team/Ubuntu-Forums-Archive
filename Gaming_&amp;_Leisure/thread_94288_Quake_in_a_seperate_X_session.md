---
title: "Quake in a seperate X session"
date: 2005-11-23
forum: Gaming &amp; Leisure
---

### Post by slide on 2005-11-23
Im using XQF right now to launch quake and I was wondering if there was any way to get it to launch quake3 in a seperate X session? Currently i can do it by hand by using the following cmd,

```
sudo X :1 -ac & ( DISPLAY=:1 quake3 )
```

but this doesn't work if the sudo password isnt cached (so normally i just do sudo ls before so it can cache it). Id really like to just be able to launch it from XQF, and maybe have it ask for the password in a dialogue box like it does for all the other admin type programs. Also, maybe have it so if i exit the game, the X server goes away. Im looking into doing it via bash script but im not too knowledgable with it so if anyones got any suggestions i would really appreciate them. :)

---


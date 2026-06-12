---
title: "Unity effects are glitchy"
date: 2014-09-27
forum: Desktop Environments
---

### Post by Joe_Nat on 2014-09-27
Whenever I maximize/minimize a window, the windows turns black during the effect, and the tilebars have white lines around them. Also the effects seem too fast. I'm on 14.04.1, have a GeForce GTX 645 and am using the proprietary drivers.

---

### Post by CantankRus on 2014-09-27
In unity for the first 100 times you minimize it will minimize slowly,
thereafter the speed increases.
This is to make it obvious to new users where the window minimizes to.

If you are below the 100 minimize count the duration will be 800. 
You can change the duration after the 100 count threshold has been reached from 300 to 800 as well or whatever duration you like.
```
gsettings set com.canonical.Unity minimize-fast-duration 800
```

See the same black with GeForce GTX 550 Ti and nvidia drivers. Driver bug.

---


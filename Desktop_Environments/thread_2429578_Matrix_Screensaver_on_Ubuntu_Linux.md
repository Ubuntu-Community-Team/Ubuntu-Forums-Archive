---
title: "Matrix Screensaver on Ubuntu Linux"
date: 2019-10-20
forum: Desktop Environments
---

### Post by RobGoss on 2019-10-20
Hello everyone is there anyway to install Matrix Screensaver on Ubuntu Linux?

Thanks so much for any help on this

---

### Post by Holger_Gehrke on 2019-10-20
Do you mean a screensaver that simulates the '[Digital Rain]("https://en.wikipedia.org/wiki/Matrix_digital_rain")' from the intro / credits sequences from the Matrix movie trilogy ? There's two of those in xscreensaver, named xmatrix and glmatrix. The latter uses 3D graphics to give the effect depth and tilt it. They can be found in xscreensaver-data-extra and xscreensaver-gl. Obviously they need xscreensaver. How well xscreensaver integrates with your DE of choice I don't know, but it was painless enough on XFCE that I don't remember having to do anything special.

Holger

---

### Post by RobGoss on 2019-10-20
> **Holger_Gehrke said:**
> Do you mean a screensaver that simulates the '[Digital Rain]("https://en.wikipedia.org/wiki/Matrix_digital_rain")' from the intro / credits sequences from the Matrix movie trilogy ? There's two of those in xscreensaver, named xmatrix and glmatrix. The latter uses 3D graphics to give the effect depth and tilt it. They can be found in xscreensaver-data-extra and xscreensaver-gl. Obviously they need xscreensaver. How well xscreensaver integrates with your DE of choice I don't know, but it was painless enough on XFCE that I don't remember having to do anything special.

Holger

Do you mean a screensaver that simulates the '[Digital Rain]("https://en.wikipedia.org/wiki/Matrix_digital_rain")

Yea that's what I mean can I install something like this on Ubuntu mate or Ubuntu

---

### Post by The Cog on 2019-10-20
> They can be found in xscreensaver-data-extra and xscreensaver-gl. Obviously they need xscreensaver. How well xscreensaver integrates with your DE of choice I don't know, but it was painless enough on XFCE that I don't remember having to do anything special.
Actually, on XFCE you don't need to install xscreensaver. Whatever screensaver XFCE uses (I don't know) is able to use those screensavers on its own. For my XFCE all I installed was the screensaver data and gl packages (and the extras). 
```
sudo apt install xscreensaver-{data,gl}{,-extra}
```

---

### Post by RobGoss on 2019-10-20
> **The Cog said:**
> Actually, on XFCE you don't need to install xscreensaver. Whatever screensaver XFCE uses (I don't know) is able to use those screensavers on its own. For my XFCE all I installed was the screensaver data and gl packages (and the extras). 
```
sudo apt install xscreensaver-{data,gl}{,-extra}
```

Bingo **WOW **thanks so much just what I was looking for not to mention there's a ton of good one in this package.

Is this only for XFCE desktops? or can it be installed on Ubuntu also

Now I know why I always come here for help :) Big thanks

---

### Post by The Cog on 2019-10-21
I don't know about other desktops. Some may also need you to install xscrensaver - XFCE seems to have its own and doesn't need that. I have seen screensavers working Ubuntu so I know it's possible  but that's all.

---


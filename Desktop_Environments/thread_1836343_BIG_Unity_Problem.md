---
title: "BIG Unity Problem"
date: 2011-08-30
forum: Desktop Environments
---

### Post by dscarfogliero on 2011-08-30
I was playing around with an application called compiz which I installed online. I didn't like it for some reason and I wanted to go back to pure unity except that the next time I restarted my machine Unity was not there, it was just my background image. I was able to access the terminal and try the command unity --replace and I had no luck. For whatever reason I tried sudo unity --replace except that it only works when I am logged it as root. Any suggestions on how to fix my issue? Thanks for all the help!

---

### Post by stinkeye on 2011-08-31
Did you mean you were playing around with **compizconfig-settings-manager** (ccsm)?
Unity is a plugin for compiz which is a window manager.
Look [**_[COLOR="DarkRed"]here[/COLOR]_**]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html") for help.

These commands will reset your compiz settings if you messed them up using CCSM.
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```

---

### Post by dscarfogliero on 2011-08-31
> **stinkeye said:**
> Did you mean you were playing around with **compizconfig-settings-manager** (ccsm)?
Unity is a plugin for compiz which is a window manager.
Look [**_[COLOR="DarkRed"]here[/COLOR]_**]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html") for help.

These commands will reset your compiz settings if you messed them up using CCSM.
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```
Got it! Thanks so much!

---


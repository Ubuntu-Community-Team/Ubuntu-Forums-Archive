---
title: "Icons do not show in KDE 3.43"
date: 2006-04-11
forum: Desktop Environments
---

### Post by neko18 on 2006-04-11
In all QT/KDE applications none of the toolbar icons seem to show (screenshot: [http://img216.imageshack.us/img216/3566/screenshot5vz.png](http://img216.imageshack.us/img216/3566/screenshot5vz.png)). I believe this happened after I attemped to set KWin as the default window manager (I'm now back to Metacity), but I have done this before with no problems.

I have tried ```
sudo apt-get --purge kdelibs kdelibs4c2 && sudo apt-get install kdebase
``` (which first removes all qt/kde applications and their config files, then reinstalls them), but had no luck.

Any ideas what is causing this and/or how to fix it?

Thanks,
David

---


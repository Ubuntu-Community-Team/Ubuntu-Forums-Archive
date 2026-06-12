---
title: "3D Cube Problem"
date: 2013-03-23
forum: Desktop Environments
---

### Post by Hollowed Skulls Inc on 2013-03-23
Hi. I am having sort of a problem with 3D Cube. Instead of a beautiful... here a picture. I enabled it with Compiz. How do I fix it?
[ATTACH=CONFIG]240481[/ATTACH]

---

### Post by Frogs Hair on 2013-03-23
It might be helpful if you post some pictures of the Compiz settings or a detailed description of what settings you used. If you have used simple rotate cube setting you may have under powered graphics.

---

### Post by Frogs Hair on 2013-03-24
To reset Compiz and start over if needed . ```
sudo apt-get install dconf-tools
``````
dconf reset -f /org/compiz/
``` Reset Unity if Needed:```
setsid unity
```

[http://www.noobslab.com/2011/10/enable-compiz-desktop-cube-in-ubuntu.html](http://www.noobslab.com/2011/10/enable-compiz-desktop-cube-in-ubuntu.html)

---

### Post by Hollowed Skulls Inc on 2013-03-24
Thanks, but it's probably just my graphics card. Does anyone, btw, know what this graphics error is called? I have encountered it with other games and programs, but could never find solutions because the name is absent to me.

---

### Post by Frogs Hair on 2013-03-24
It may be this . [http://en.wikipedia.org/wiki/Screen_tearing](http://en.wikipedia.org/wiki/Screen_tearing)

---

### Post by deadflowr on 2013-03-24
It's an unfortunate bug in 3d windows.

[https://bugs.launchpad.net/compiz/+bug/1024208](https://bugs.launchpad.net/compiz/+bug/1024208)

At least seems to be the most common problem with cube.

AKAIK this is from 12.10 on, but I haven't seen it in 12.04 or older.

---


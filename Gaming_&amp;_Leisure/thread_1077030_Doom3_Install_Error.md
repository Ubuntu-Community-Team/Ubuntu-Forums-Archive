---
title: "Doom3 Install Error"
date: 2009-02-22
forum: Gaming &amp; Leisure
---

### Post by Rallivan on 2009-02-22
Ok, I've followed the sticky in here completely and have searched both the internet and these forums and still cant figure out why I am getting this error when running the install package.

> 
****@testbox:/usr/games/doom3$ sh ./doom3-linux-1.3.1302.x86.run
Verifying archive integrity... All good.
Uncompressing DOOM III............................................................................................
./setup.sh: 274: /home/****/.setup6992: not found
./setup.sh: 279: /home/****/.setup6992: not found
./setup.sh: 290: /home/****/.setup6992: not found
****@testbox:/usr/games/doom3$ 

I have all the game000.pk4 and pak000-004.pk4 files copied to /usr/games/doom3/base.  What am I doing wrong here? I even tried the current installer script and the old version 1302 and 1304.

---

### Post by crazyfuturamanoob on 2009-02-22
I think you should run it as sudo. 

If it doesn't work, then try even older versions.

```

sudo ./doom3-linux-1.3.1302.x86.run

```

---


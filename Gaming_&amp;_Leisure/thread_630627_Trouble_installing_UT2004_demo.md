---
title: "Trouble installing UT2004 demo"
date: 2007-12-03
forum: Gaming &amp; Leisure
---

### Post by Envergure on 2007-12-03
Can't install the UT2004 demo :(

I open the installer ("ut2004-lnx-demo3334.run") and I get as far as entering the install directory.  I leave it as the default (/usr/local/games/ut2004demo and hit "OK."  I get a message "No write permission to /usr/local/games"

All three permissions are set to "read and write" so that's not the problem.

Any help?
Thx!

---

### Post by Vadi on 2007-12-03
**sudo ut2004-lnx-demo3334.run** will give the installer privs to install files there.

Do not, however, launch the game from the installer - quit the installer first, and then launch the game.

There's also a guide for it on ubuntugamersarena.com.

---

### Post by Envergure on 2007-12-03
Didn't work.
This did, though:
```

sudo chmod +x ut2004-lnx-demo3334.run
sudo sh ut2004-lnx-demo3334.run
```

It doesn't run propperly, though.  It shows the splash and then quits.

The terminal said this when I executed it from there with **./ut2004-bin**
```

Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.
```

---

### Post by Vadi on 2007-12-03
Something is up with you video card / video drivers. Do you know what are you using?

---

### Post by Envergure on 2007-12-04
ATI Radeon 9550 SE (256M)

I'm not using the proprietary drivers, though.  When I enable them I get stuck in "low graphics mode."

---

### Post by Envergure on 2007-12-04
ATI Radeon 9550 SE (256M)

Not using proprietary drivers.  If I enable them I get stuck in "Low Graphics Mode."

---

### Post by Vadi on 2007-12-04
Hm

Does Compiz work fine for you?

---

### Post by Envergure on 2007-12-06
Okay, it works now.  Not sure why, though.
I don't know about Compiz.  I can't even get the desktop effects to work.
When I try to turn them on it sais "the composite ectension is not available" and the window freezes.

---

### Post by Vadi on 2007-12-06
Here, give this a try...

[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#)

---


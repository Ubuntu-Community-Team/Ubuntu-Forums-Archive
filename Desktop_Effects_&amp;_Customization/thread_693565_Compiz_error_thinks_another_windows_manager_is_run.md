---
title: "Compiz error: thinks another windows manager is running"
date: 2008-02-11
forum: Desktop Effects &amp; Customization
---

### Post by ashdezign on 2008-02-11
For those experiencing the following error running compiz fusion in Kubuntu:

>  /usr/bin/compiz.real (core) - Error: Another window manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0 I have found several posts in several forums regarding this but none specific to my video card (Nvidia 5500) and none that presented a working solution (none that worked for me at least)

I found in the end the problem was caused by hiding the icons on the desktop. As soon as I hide them and restart compiz will fail and keep failing until I > sudo rm ~/.kde/share/config/kdesktoprcBut as long as I don't hide the icons compiz runs stable.

I have no idea why this should be, nor if it will help anyone else having the same problem with a different graphics card, but for what its worth. If you are hiding the icons on the desktop, try disabling that feature and then run this from konsole: > sudo rm ~/.kde/share/config/kdesktoprcreboot, restart compiz. reboot again and then reset all of your settings; this time NOT enabling desktop icons to be hidden.

---

### Post by beatryder on 2008-02-11
Wow, I had no idea that was causing this problem the whole time!

That is kinda buggy indeed.

---


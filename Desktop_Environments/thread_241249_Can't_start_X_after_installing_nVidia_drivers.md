---
title: "Can't start X after installing nVidia drivers"
date: 2006-08-22
forum: Desktop Environments
---

### Post by wyldeone on 2006-08-22
I just installed today a fresh copy of Dapper Drake x86 on my machine today, did a dist-upgrade, and installed the nVidia binary driverb for my 6800 through apt. I restarted X, and found that it failed with the error:
```
(EE) No devices detected

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reste by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining
```

Since then I have tried changing the driver back to nv, I've uninstalled the nvidia driver, I've reset my xorg.conf to what it was before I installed the nvidia driver, all to no avail. Looking in the log, it appears that it's crashing immediately after loading the graphics driver, though that seems to load fine. I'm pretty stuck here, and any help would be greatly appreciated (note that I have gotten this card to work with the nvidia drivers before.)

---

### Post by cleentrax on 2006-08-22
You may have been bitten by the bad version of xserver-xorg-core. Check out the thread here on the main page for a fix. It involves installing an older version of xserver-xorg-core. Good luck!

---

### Post by wyldeone on 2006-08-22
Nevermind.

I should have looked at the forum before posting, as if I had I would have found out that my inscrutable problem was due to my updating xorg to a broken package rather than installing the nVidia drivers.

Now I want 4 hours of my life back :)

---

### Post by starfury6 on 2006-08-22
lol I registered here specifically to ask about this one and low and behold you guys have a solution for it already.

Excellent community Ubuntu has.

Laters guys.

---

### Post by mommebu on 2006-08-22
> You may have been bitten by the bad version of xserver-xorg-core. Check out the thread here on the main page for a fix. It involves installing an older version of xserver-xorg-core. Good luck!

Looking for this thread, where do I find it?

cheers.

---

### Post by abelthorne on 2006-08-22
[http://www.ubuntuforums.org/showthread.php?t=240957](http://www.ubuntuforums.org/showthread.php?t=240957)

---


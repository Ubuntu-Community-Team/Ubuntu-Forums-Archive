---
title: "Xorg get 90% CPU"
date: 2009-11-06
forum: Desktop Environments
---

### Post by yuinc on 2009-11-06
Hello.

I'm novice to ubuntu, but i'm fast learn.
i'm have kubuntu 9.04, than update to 9.10.

Now Xorg server get 30% of CPU on window move, and 90% on window resize.
I'm check drivers it fine. ATI x1950.
Not make sense with compiz or without it. Still 90% on resize, and resize very slow, so not normally.

The second trouble is small one. I'm edit xorg.conf, add monitor resolution 1440x900. But on load kubuntu ignore it. Looks like conf just ignored. And load from different place.

Sorry for my bad english.

Thank you,
yuinc

**[UPDATE]**

For some who need.
My card is x1950
Drivers 9.3 and lover not installed on 9.10.
Drivers 9.4 and higher not support this card
Used open source radeon driver.
Basically it not configured.
So just need configuration of it.
Now is not much lugs, CPU getted around 20-30%.

---

### Post by rpeters on 2009-12-15
[PROBLEM SHELVED]

Similar high CPU usage problem.

Running Kubuntu-KDE3 9.10 on a Toshiba Satellite laptop (bought Dec.2006).
**lspci** shows
> Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
...

No problem until today.
Last week switched to Gnome display manager and desktop, while using mostly KDE apps.
Today switched back to KDE3 and removed a lot of unused Gnome apps.  Now the desktop takes a while to load a previously-saved session, and **top** shows high CPU usage by Xorg.  With no activity, it goes down to normal. But I can push it up by moving the mouse a lot, resizing a window, scrolling with the keyboard in Firefox, etc.

And another goodie: KDE3 systemsettings now crashes on startup.  Perhaps time to reinstall...

Edit:
After trying to do a few things, I soon discover that:
  -KDE is _really_slow_ when loading anything.
  -it continues to suddenly log out, at unpredictable intervals, particularly when using a Web browser - this started a week ago and is the reason that I switched to Gnome last week.

Looks like my KDE is well and truly knackered.  So, pending reinstallation, I'm back to Gnome.  That's OK.

---


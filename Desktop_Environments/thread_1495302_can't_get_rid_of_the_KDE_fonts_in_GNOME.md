---
title: "can't get rid of the KDE fonts in GNOME"
date: 2010-05-27
forum: Desktop Environments
---

### Post by ptviperz on 2010-05-27
I finally performed my upgrade from Karmic today, everything went smooth and looked great. I decided to check out how KDE looked so I logged out, went into KDE and poked around for a bit then went back to GNOME. All my fonts are now that horrible tiny KDE font and I cannot, for the life of me, figure out how to return the fonts to their previous glory. 

Can anyone, please, point me in the right direction? I've totally removed KDE from my system, I took all the files out of ~.fontconfig and set antialiasing to false in /etc/fonts/conf.avail/10-antialias.conf but still no joy.

[edit] I haven't found the settings to get back to default but I've installed the MS font pack which looks better than the KDE stuff

---

### Post by SlidingHorn on 2010-05-27
> **ptviperz said:**
> I finally performed my upgrade from Karmic today, everything went smooth and looked great. I decided to check out how KDE looked so I logged out, went into KDE and poked around for a bit then went back to GNOME. All my fonts are now that horrible tiny KDE font and I cannot, for the life of me, figure out how to return the fonts to their previous glory. 

Can anyone, please, point me in the right direction? I've totally removed KDE from my system, I took all the files out of ~.fontconfig and set antialiasing to false in /etc/fonts/conf.avail/10-antialias.conf but still no joy.

[edit] I haven't found the settings to get back to default but I've installed the MS font pack which looks better than the KDE stuff

This will get you back to a pure Gnome setup:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by ptviperz on 2010-05-28
> **SlidingHorn said:**
> This will get you back to a pure Gnome setup:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

I did that but it still didn't remove the fonts. It DID, however, remove mysql, phpmyadmin and mediawiki. :)

---

### Post by SlidingHorn on 2010-05-28
> **ptviperz said:**
> I did that but it still didn't remove the fonts. It DID, however, remove mysql, phpmyadmin and mediawiki. :)

well you shoulda told me you wanted to keep those individual components...gotta keep a mental inventory of EVERY package you have installed!!!  ;)  ..kidding -- don't punch me

---

### Post by Kilz on 2010-05-28
Right click on the desktop, select Change Desktop Background, go to the fonts tab, change them to your hearts content. :)

---

### Post by ptviperz on 2010-05-28
> **SlidingHorn said:**
> well you shoulda told me you wanted to keep those individual components...gotta keep a mental inventory of EVERY package you have installed!!!  ;)  ..kidding -- don't punch me

LOL, it was fine, reinstalled them and didn't lose a thing. It did give me a bit of a shock :)

---


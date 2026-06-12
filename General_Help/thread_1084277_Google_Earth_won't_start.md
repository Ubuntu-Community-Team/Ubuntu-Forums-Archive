---
title: "Google Earth won't start"
date: 2009-03-01
forum: General Help
---

### Post by mmace1 on 2009-03-01
I have an ATI Mobility Radeon X2300.  After installing Google earth 5.xx, it would start for a few seconds, then close. 

So, I then installed Google Earth 4.2 from the medibuntu repository - same behaviour.  Maybe 10 seconds before crashing, with a lot of jerky screen refreshes in-between

---

### Post by mmace1 on 2009-03-01
OK.  Turning off compiz-fusion gets rid of the flickering I was also experiencing in the ~ 10 seconds before creashing (had not previously mentioned the flickering).  However, even witth the flickering solved, it still crashes in ~10 seconds after launch.

---

### Post by darco on 2009-03-02
I just fixed my issue on x64...you running x64 too?

darco

---

### Post by mmace1 on 2009-03-02
Nope, just the 32-bit version of Ubuntu.

---

### Post by utherpendragonfly on 2009-03-02
> **mmace1 said:**
> I have an ATI Mobility Radeon X2300.  After installing Google earth 5.xx, it would start for a few seconds, then close. 

So, I then installed Google Earth 4.2 from the medibuntu repository - same behaviour.  Maybe 10 seconds before crashing, with a lot of jerky screen refreshes in-between

[http://ubuntuforums.org/showthread.php?t=52095](http://ubuntuforums.org/showthread.php?t=52095)   <  This thread had a possible solution, but it didn't seem to work for me (copying the 2 files into the GoogleEarth folder in home, as well as copying the files into the .lib folder).

OK, I noticed this weird problem today - I had 2 Google Earth icons under Applications>Internet. And when I tried starting one and then the other, it would start up then crash after 5 or 6 seconds. I opened Synaptic and uninstalled googleearth 4.3. Went back to Applications and one icon still remained. Back to Synaptic, it shows I have no Google Earth installed. So I installed version 4.2 and had the same original problem  Still 2 icons and neither would launch. I haven't even bothered trying to install version 5 with the problems I've seen in other posts.
But just a minute ago I tried again (after uninstalling again and showing 1 icon under Applications). Now Google Earth 4.2 launches fine!

Intrepid, 32 bit.

---

### Post by mmace1 on 2009-03-02
Before I start messing with this fresh install of Ubuntu...(I don't know - Ubuntu seems a bit sensitive but I'm a noob so...) - Is Google Earth still working for you?  Or was it a one-off event?

---

### Post by utherpendragonfly on 2009-03-03
> **mmace1 said:**
> Before I start messing with this fresh install of Ubuntu...(I don't know - Ubuntu seems a bit sensitive but I'm a noob so...) - Is Google Earth still working for you?  Or was it a one-off event?

I used it for ten minutes or so with no problem and then it suddenly quit again.
I guess I will have to wait for a stable Linux version. I just wish I could uninstall it. If Synaptic doesn't show it as being installed, can I do it with the Terminal?

---

### Post by mmace1 on 2009-03-03
I'm not in Ubuntu at the moment, but I recall uninstalling it myself via simply clicking an uninstall file in the Googleearth directory, I forget where that directory was located though...

---


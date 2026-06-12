---
title: "compiz slow resizing and maximising windows karmic"
date: 2009-10-30
forum: Desktop Environments
---

### Post by wardy277 on 2009-10-30
Hi,

I have just upgraded to karmic (fresh install). Everything works fine. I isntalled the latest FGLRX drivers from the restricted hardware drivers.

It installed fine, but when it rebooted, i enabled the usual wobbely windows and desktop cube. I noticed that alt tab, resizing/maximizing windows was really slow. It is near impossible to resize a widow in the normal mode. It takes a second or 2 to think about it before maximizing. Its getting really frustrating now.

I have seen tome threads about this with jaunty, i have tried the patched x server but the ppa doesn't have a karmic version. The ppa with jaunty gets ignored as the karmic one is newer.

Anyone know of a patched version for karmic, or another fix? Even metacity in compositing mode is really slow to alt-tab

Chris

---

### Post by apocalypse80 on 2009-10-30
I got a patched xserver from this ppa

[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill)

The lag goes away, but (exactly like jaunty) it results in a horrific memory leak.

---

### Post by wardy277 on 2009-10-30
thanx for that. How bad is the memory leak? Is there any other way to fix this? Is the open source driver any better? i wish amd/ati would sort out their drivers

---

### Post by apocalypse80 on 2009-10-30
I learned to live with that memory leak throughout the life of jaunty.
It seems that opening/closing windows just keeps on filling up memory (I'm not talking about cache).

In my case (4GB ram), if I really go for it, I'll probably fill it up in 3-4 hours.
Resetting compiz empties the trash or (a solution I found later) opening an app that uses 3d and then closing it - google earth works nicely.
Alternatively a log off or reboot also does the trick.

---


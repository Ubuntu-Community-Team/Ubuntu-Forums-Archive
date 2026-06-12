---
title: "old version/trying to upgrade"
date: 2009-03-10
forum: General Help
---

### Post by eyebrowman92 on 2009-03-10
hi, i've just installed an old version of ubuntu on my desktop (it was all i had) and i'm trying to figure out how to upgrade it. i'm using a linksys wireless device but ubuntu doesn't seem to recognize it, so i can't gain access to the internet.

also, can anyone post the latest repo list so i can upgrade?

---

### Post by Neo_The_User on 2009-03-10
Like a sources.list?

Meh here is mine.

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid main restricted #Added by software-properties


deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid main restricted
deb-src [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid multiverse universe 


deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid-updates main restricted
deb-src [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties


deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid universe
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid-updates universe


deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid multiverse
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid-updates multiverse

deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid-security main restricted
deb-src [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid-security universe
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid-proposed restricted main multiverse universe
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) intrepid-security multiverse

---

### Post by Vadi on 2009-03-10
Keep in mind though that you can't skip versions. You need to upgrade them in order.

So might be easier to order / buy a cd of the latest ubuntu...

---

### Post by eyebrowman92 on 2009-03-10
> **Vadi said:**
> Keep in mind though that you can't skip versions. You need to upgrade them in order.

So might be easier to order / buy a cd of the latest ubuntu...

gah i didn't know this. does anyone know how i could possibly get my wireless network adapter working? i'm in the newtwork settings on ubuntu 5.10 and all i see is ethernet and modem options.

---

### Post by wannadumpwindows on 2009-03-10
You're probably going to have to download things to get your wireless working anyway, is it possible to just download a more recent .iso and burn yourself a new CD?

You're going to spend the time getting wireless to work for basically no reason at all. And on top of that, upgrading 4 or 5 times to get to the current versions is probably going to break some things along the way.

It might just be worth downloading one of the newer .iso's, or ordering a free CD from ship-it.

It'll probably save you a lot of time and trouble if you're able to do it this way.

---

### Post by Neo_The_User on 2009-03-10
> **Vadi said:**
> Keep in mind though that you can't skip versions. You need to upgrade them in order.

So might be easier to order / buy a cd of the latest ubuntu...

or just burn it for free like me.

---


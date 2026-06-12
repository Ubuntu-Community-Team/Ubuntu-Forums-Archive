---
title: "Going from ubuntu to Kubuntu"
date: 2009-12-08
forum: Desktop Environments
---

### Post by benjamonk on 2009-12-08
Hello All,

I considering switching from Ubuntu 9.10 (gnome) to Kubunu 9.10 (KDE) beacuse I have got major screen display / resolution problems in Ubuntu / Gnome which I just can't fix.

If I do this - I get that I need to select the kubuntu-desktop package and everything that goes with it. However, I' assume it's a good idea to remove everything Gnome related as I don't need two GUI's. What's the best / easiest way to remove EVERYTHING I don't need that's Gnome related?

Thanks,

B

---

### Post by 3Miro on 2009-12-08
As I just posted on another thread, Kubuntu is not the stablest of OS systems. In fact, if you are experiencing problems with Ubuntu, you will probably experience them with KDE.

I would suggest, before you mess around with our system, that you download the kubuntu live CD and boot from it. Then make sure the display issue are not present. At the end, it might be an X server issue, present independent of the distribution (hopefully fixable).

Also, if you with to "completely" remove Gnome, consider a clean install from kubuntu live CD.

---

### Post by LuisGMarine on 2009-12-08
Follow this guide if you want to install KDE on Ubuntu.  All you are doing is just changing the desktop environment.  The core Ubuntu system stays unscathed. Anyhow here is the guide on how to install KDE from Ubuntu.

[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

Essentially you can install the full KDE desktop by just opening up Terminal and typing in:

```
sudo apt-get install kubuntu-desktop
```

Although this might leave your menus super cluttered having gnome and kde applications.  If you are keen on moving to KDE please give the Kubuntu live CD a try, and then I would do a fresh install of Kubuntu.

---

### Post by benjamonk on 2009-12-09
Thanks both for your advice - in truth I suspect my problems may be xserver related but i'm willing to try anything at the moment!

---


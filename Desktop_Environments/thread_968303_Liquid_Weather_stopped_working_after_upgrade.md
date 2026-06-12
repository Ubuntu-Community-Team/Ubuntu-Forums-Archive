---
title: "Liquid Weather stopped working after upgrade"
date: 2008-11-02
forum: Desktop Environments
---

### Post by Jason Spaceman on 2008-11-02
I upgraded to Ubuntu 8.10, and installed KDE 4.1 and Superkaramba.  I was using Liquid Weather in Superkaramba to see the weather forecast, but it stopped working after the upgrade.  Whenever I try to run it I get:

> You do not have PyQT installed.  This is a critical dependency for Liquid Weather ++.  Please install it and try again.

I do seem to have PyQT installed though, I checked synaptic and it lists both Python-qt4 and Python-qt3 as being installed.  

Any solutions?

---

### Post by Blackwolf_Oz on 2008-11-03
Using the Add Widgets, select Install from File. Choose SuperKaramba. Click Next and find the lwp-15.0.skz. and Click Finish.

The contents of the skz will be extracted to ~/.kde4/share/apps/plasma/plasmoids/sk_lwp-15.0

You need to modify the file liquid_weather.py. In the method checkDependencies(widget), it tries importing qt libs, which for whatever reason fails. So comment (or remove) out the following (lines 3663-3668)

hey presto it all now works.

Hope it helps:)

---

### Post by sophitialer on 2008-11-03
[img]http://www.top1gaming.com/cosplay/shaiya-1.jpg[/img]See more pics [[color=#800080]click here[/color]](http://www.top1gaming.com/coscontent-153.html).  Want to see more [[color=#800080]cosplayer[/color]](http://www.top1gaming.com/cosplayer.php) ? Show yourself on our forum [[color=#800080]click here [/color]](http://www.top1gaming.com/forum/forumdisplay.php?fid=29).**Recommend : **[[color=#0000ff]Fate Stay Night cosplay [/color]](http://www.top1gaming.com/coscontent-83-8.html)   [[color=#0000ff]Chobits cosplay[/color]](http://www.top1gaming.com/coscontent-46.html)

---

### Post by Jason Spaceman on 2008-11-03
> **legend1264 said:**
> Using the Add Widgets, select Install from File. Choose SuperKaramba. Click Next and find the lwp-15.0.skz. and Click Finish.

The contents of the skz will be extracted to ~/.kde4/share/apps/plasma/plasmoids/sk_lwp-15.0

You need to modify the file liquid_weather.py. In the method checkDependencies(widget), it tries importing qt libs, which for whatever reason fails. So comment (or remove) out the following (lines 3663-3668)

hey presto it all now works.

Hope it helps:)

I can't seem to find the liquid_weather.py file.  When I go to .kde4/share/apps/plasma there is nothing.  When I go to .kde/share/apps/plasma/plasmoids/sk_lwp-15.0 I just see two files, colors.png and lwp-15.0.skz.

---


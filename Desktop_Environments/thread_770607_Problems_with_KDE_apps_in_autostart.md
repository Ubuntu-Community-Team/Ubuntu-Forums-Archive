---
title: "Problems with KDE apps in autostart"
date: 2008-04-27
forum: Desktop Environments
---

### Post by crazy ivan on 2008-04-27
Unfortunately this issue did not get fixed in Hardy.

If I add a KDE application to '/home/../autostart' which creates a systray icon in the panel (amarok, klipper...) theres about an even chance, that it starts perfectly nice, that it doesnt show up at all, or that it shows up in some ugly litte windows beneath the panel.
If I start it from console then, sometime it works perfectly, sometimes I get: "DCOPClient::attachInternal. Attach failed Could not open network socket" and some other stuff and nothing happens.

I tried to solve this problem by restarting the dcopserver in a script.

```
#! /bin/csh

if !( -f /home/ivan/.DCOPserver_ivan-desktop.user.user__0) then
	/usr/bin/dcopserver
endif

/usr/bin/klipper
```

but that lead to ALWAYS having the ugly extra window. I need klipper, since glipper doesnt work anymore. Any ideas for cause or solution for this problem?

---

### Post by crazy ivan on 2008-05-02
Guess Im just coping with this error til next version of ubuntu/gnome..
Funnily the glipper works exaktly then, when klipper wont load - so I always have ONE tool to do the job. Guess its some DCOP difficulties for both of them.. On these rare occasions glipper asks me "glipper has been shut down, do you want to resart it". And then it works...

---

### Post by crazy ivan on 2008-07-03
This DCOP server problem is really frustrating:
When klipper will not load at startup (really random happens 1/20 times, I usually restart), all other KDE apps also start to lagg. Big-Time. Getting grey-screens in kile every 5 minutes..

On the other hand, glipper usually will not load, but that seems to have no effect - except I have to click away the question (do you want to remove glipper from autostart?).

I've crawled the forums, but there seems to be no solution yet, not even an idea of what the problem really is.

---

### Post by crazy ivan on 2008-07-21
There seems to have been some change somewhere. At the moment glipper fails about everytime as does the dict-bar. Klipper is out every 4th time, but - thats the change - now I can get it back, by just running it. Earlier it used to be created in a nasty window... So for me the problem is kind of solved. Still would be nicer if it would not crash at all.

---


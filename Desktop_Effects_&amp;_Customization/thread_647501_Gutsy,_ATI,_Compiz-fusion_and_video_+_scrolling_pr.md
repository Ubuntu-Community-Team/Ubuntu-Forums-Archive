---
title: "Gutsy, ATI, Compiz-fusion and video + scrolling problems"
date: 2007-12-22
forum: Desktop Effects &amp; Customization
---

### Post by melenor on 2007-12-22
Alright i have an ATI X1800, and i have 7.12 installed it works great without compiz enabled once i have compiz enabled scrolling lags and is slow, and when i try to watch a video the screen continually flickers and the video stays on top of all other programs no matter whether it doesn't have focus. Is there any way to fix this,  thank you for your help.

---

### Post by Farenheit on 2007-12-22
I have the same card, and the same problems as you.  Apparently the ATI driver doesn't get along with Compiz very well...or compiz doesn't like the ATI driver.  The only thing you can really do (that I've found) is run metacity instead of compiz when watching videos or playing 3D games.  I saw a post where someone created 2 scripts, one to enable metacity, and one to enable compiz.  Make a file called metacity.sh and paste the following code in it:
```
#!/bin/bash

metacity --replace
```

Then make a file called compiz.sh and paste this code in it:
```
#!/bin/bash

compiz --replace &
```

Then make shortcuts to those files on your desktop, and when you go to watch a video or play a 3D game, click the metacity shortcut.  When you're done, click the compiz shortcut.  I am playing Enemy Territory Quake Wars using this method, and it plays great.  I even saw an idea where you make a script to enable metacity, run quake wars (or any game/app), then re-enable compiz for you,  That script would be: 
```
#!/bin/bash

metacity --replace &
sleep 1
/path_to_game/etqw &&
sleep 1
compiz --replace & 
```

It's all somewhat of a crappy workaround, but I haven't seen a true fix.  You just have to hope they make some code changes soon (because the card works perfectly in Windows).

---

### Post by melenor on 2007-12-22
okay that is a little better, wish there was another work around, also how do you play quake wars on ubuntu do you use wine. also when i play 3d games disable compiz right?

---


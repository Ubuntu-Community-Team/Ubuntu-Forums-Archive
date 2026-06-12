---
title: "need help with D2 launch script"
date: 2008-07-03
forum: Gaming &amp; Leisure
---

### Post by Naegling23 on 2008-07-03
Im almost there...to close to perfect Diablo2 playing.

So, Im working on a script, which looks as follows:

#! bin/bash 
kwin --replace &
sleep 2
xrandr -s 1280x720
sleep 2
wine Diablo2.exe -w &&
sleep 2
xrandr -s 1440x900
sleep 2
compiz --replace &

So, as you can see, im trying to change the resolution of my desktop, launch diablo2, then change it back.  I am only turning compiz off since changing resolutions messes up compiz, but not kwin, so my desktop looks normal when I am done.

The problem that I am having is that diablo2 launches, but the script does not hold, it continues through.  This means that kwin comes in, the resolution changes, and as diablo2 launches, the resolution changes back, and compiz comes back on.  So I'm asking what is wrong with by script that is causing this?  Its odd, because I use the compiz toggle script on almost all of my launchers and have never seen this problem before, the only thing different is the changing of screen resolutions.  I must be doing something wrong.

---

### Post by DoktorSeven on 2008-07-03
Remove the && at the end of the wine line.  & at the end of a command means "execute this, and don't wait for it to end."

With wine, you'll want it to end completely before switching back.

---

### Post by Naegling23 on 2008-07-04
hmm, I removed the &&, the same problem as before, it launches as the screen resolution is changing back.  But then when I exit the game, its changing the resolution to 1280x720 with compiz....dont remember telling it to do that!

---


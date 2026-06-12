---
title: "Diablo, Warcraft II"
date: 2006-08-08
forum: Gaming &amp; Leisure
---

### Post by simukas on 2006-08-08
How to run the games on wine? i installed them but i cna't run it. Do i need to cofigure something? i runned  them on my old arklinux but i can't do it on ubuntu.. 

TnX

---

### Post by holomorph on 2006-08-08
for warcraft II (non-battlenet edition) try the strategus engine, it's pretty sly, lets you play natively using the data off the original CD.

---

### Post by simukas on 2006-08-09
but what about diablo?? and when i try to get stratagus from packages.ubuntu.com i needs stratagus adata witch is  a virtual package and comes with bos with requires stratagus... i'm lost with that

---

### Post by simukas on 2006-08-09
i try to run diablo but waht i get is this...

---

### Post by DoktorSeven on 2006-08-09
I've tried running Diablo but get a crash after the Blizzard logo movie.  I think it's related to [this bug](http://bugs.winehq.org/show_bug.cgi?id=5451), which has apparently been closed as fixed, so maybe the next Wine version will work.

Your problem seems to be different though; a pure guess, but maybe DDERR_INVALIDMODE means it can't switch to the resolution needed?  Try running winecfg and on the Graphics tab tell it to "Emulate a virtual desktop" at 640x480 (IIRC Diablo runs at this resolution).

---

### Post by simukas on 2006-08-10
tnx.. i'll try . that.

one more thing does your movie work in right resolution. mine is squiched . but after the movie i get the error.

---


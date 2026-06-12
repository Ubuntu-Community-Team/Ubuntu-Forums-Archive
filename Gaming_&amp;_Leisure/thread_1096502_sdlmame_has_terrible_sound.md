---
title: "sdlmame has terrible sound"
date: 2009-03-15
forum: Gaming &amp; Leisure
---

### Post by escher on 2009-03-15
I've been poking around with MAME the past few days (used to be big into it, but only under Windows), and I'm having a hell of a time getting things to play nicely.  I've worked through or around everything thus far, but I can't seem to figure out what the heck is going on with the sound in sdlmame.  No matter what I mess with, it's always crackling.  When I was playing with xmame earlier, I didn't have any problems with the sound quality (though there were other issues), and the sound on the box works fine for everything else I've tried (normal games, movies, music).

I've seen a couple random thoughts and suggestions in my searching, but none of them worked (or even made sense).  Any advice would be greatly appreciated.

---

### Post by Firestom on 2009-03-15
The difference between sdlmame and xmame is the graphics library used for it. The first one uses SDL and the second one uses X11. SDL might have some compatibility issues because it is a third party library, while X11 is the default graphics library for Linux. This is why.

I don't know how to fix it. If you don't understand anything the best is not to touch it!

---

### Post by disturbedite on 2009-03-15
try increasing the sound latency.

---


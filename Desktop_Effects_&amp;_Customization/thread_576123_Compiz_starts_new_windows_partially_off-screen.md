---
title: "Compiz starts new windows partially off-screen"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by unimeister on 2007-10-14
I just started up this laptop into ubuntu for the first time in months, only to find that when compiz is running (I run compiz --replace followed by emerald --replace after logging in), new windows which should start in the top left corner will start with the themed area above the menus (the title bar?) off screen, with the menu bar covered by Gnome's menu bar, and the left edge of the window off the left edge of the screen. 

See attachment.  This is the location of new windows before I move them. 

I've narrowed down the problem to compiz.  The problem begins after I run compiz --replace but before emerald --replace.  I've tried Google for answers, but couldn't come up with relevant results.

---

### Post by Faud on 2007-10-14
If you are running compiz-fusion, you can try to enter the "place windows" option and change it from smart (default) to "center". That should start your windows in the center of your screen.

---

### Post by mobiusstrip on 2007-12-07
I'm having a similar problem - to my knowledge, I don't have Compiz (could be wrong about this - Linux n00b here)

When I first installed Gutsy everything was working fine. A few days (and a few updates) later, whenever I open up a window, any sort (firefox, thunderbird, file browser, sound juicer, anything) it opens up at the top left of the screen with the menu bar not visible. I can alt-click and move it of course, but stil.....??

As far as I'm aware I just have a vanilla Gutsy install with the various updates that have been available since. I've added things like gstreamer and a few ripping tools, thunderbird....but nothing that should be messing with the display...

---

### Post by agibby5 on 2007-12-17
Good call, this worked for me.  There are other options in there like cascade, etc.  Thanks!

---

### Post by AJerman on 2007-12-17
Ugh, yes, this annoys the crap out of me. Thanks for the center option. I'll try that.

---


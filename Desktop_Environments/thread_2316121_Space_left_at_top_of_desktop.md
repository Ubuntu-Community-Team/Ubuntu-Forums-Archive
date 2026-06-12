---
title: "Space left at top of desktop"
date: 2016-03-05
forum: Desktop Environments
---

### Post by SlidingHorn on 2016-03-05
Running Xubuntu 14.04 and when I detached a Chrome tab and changed its window size, XFCE seemed to "redraw" my desktop leaving about an inch of space at the top of my screen.  Logging out and back in and restarting did not return to normal settings.  A screenshot can be seen here: [http://imgur.com/a/8P3rq](http://imgur.com/a/8P3rq)

Any suggestions on how to fix this?  Thanks ahead of time!

---

### Post by ajgreeny on 2016-03-05
It is difficult to exactly see what the problem is, but it looks as if the top panel has simply drifted down the screen for some reason leaving some background/wallpaper showing above it.

Try right clicking in the panel across the screen near the top and go to Panel ->Panel Preferences, deselect the Lock panel tick-box and drag the panel by a handle (one at either end) to the correct place at top or bottom of screen, depending on where you want it to be.

---

### Post by SlidingHorn on 2016-03-06
> **ajgreeny said:**
> It is difficult to exactly see what the problem is, but it looks as if the top panel has simply drifted down the screen for some reason leaving some background/wallpaper showing above it.

Try right clicking in the panel across the screen near the top and go to Panel ->Panel Preferences, deselect the Lock panel tick-box and drag the panel by a handle (one at either end) to the correct place at top or bottom of screen, depending on where you want it to be.

I'd figured that since the icons that are usually on the desktop were also moved down and seemed slightly smaller/scaled, it had to be something with lightdm itself.  I was wrong....

Your answer was absolutely correct.  Apparently that's what I get for trying to "outsmart" something simple ;)

Thanks for your reply, and thanks to the rest for looking.  Thread is marked as solved.

---


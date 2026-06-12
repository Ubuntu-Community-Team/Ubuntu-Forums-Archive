---
title: "windows hang for 15 secs every ~3 minutes"
date: 2008-04-13
forum: Desktop Effects &amp; Customization
---

### Post by mnr102 on 2008-04-13
Hello,
After a year+ of good experience w/ Feisty, I did a clean install of Gutsy.  I'm using the default window manager, which I assume is Compiz.  CPU is AMD 64 X2 4600.  The whole desktop (except for the mouse cursor) freezes every ~3 minutes for about 15-20 seconds.  Music continues to play, & mouse will move, but all windows are frozen & don't respond. When it unfreezes, the performance monitor spits out 20 seconds of performance graphs.  I've checked logs for any <system just did it's hang thing!> indication of what's happening, but can't find anything.

Any ideas?  Should I try switching to a different window mgr?  What one do you recommend?  How to switch?

Thanks.

---

### Post by russo.mic on 2008-04-14
Well, Compiz isn't the default WM, but you might have enabled it.  I'm not convinced it's the WMs problem anyway.

Why don't you open a terminal and kill compiz if youv'e got it enabled and see what happens?

ps ax | grep compiz

then, for all the process entries that compiz is using type:
sudo kill (process #)

should do it.  

Good Luck!

---

### Post by mnr102 on 2008-04-20
It appears that this was a compiz problem.  I disabled Compiz & all hangs stopped occurring.  (System > Preferences > Appearance > Visual Effects tab).

---


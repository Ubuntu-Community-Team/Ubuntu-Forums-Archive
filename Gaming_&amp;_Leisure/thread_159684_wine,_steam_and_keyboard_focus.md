---
title: "wine, steam and keyboard focus"
date: 2006-04-13
forum: Gaming &amp; Leisure
---

### Post by tjansson on 2006-04-13
I hope you can forgive me, but posted this messages in dapper development and I now realize that I should have posted here ](*,) 

Here was the question: [http://ubuntuforums.org/showthread.php?t=159680](http://ubuntuforums.org/showthread.php?t=159680)

I have installed wine and steam. It seems to work fine and when i open the steam menu my keyboard is active but, when i start up day of defeat source (dods) I loose my keyboard focus. The rest of the game works fine - I have sound, the 3d effects works, and I can join games. But not use the keyboard.

I tried to open **winecfg** and set the *Graphics -> Emulate a virtual desktop* with 800x600 then it worked fine and can see the whole game in a windows and use the mouse and so forth - but no fullscreen.

So how do I gain keyboard focus when not using *Emulate a virtual desktop*?

---

### Post by siorai on 2006-04-15
Unfortunately, from what I've read, it might not be an easy fix. It seems it has to do with how HL2 calls it's windows. So in full screenmode, wine isn't seeing the type of window that it expects, so that window doesn't get proper focus. Rather sucks because I'm stuck playing in a 1280x1024 window when I could be playing 1680x1050 fullscreen.. :( When I do try to play in a 1680x1050 window, the visible area of the game is only like 640x480 in the upper left corner.. Very frustrating.. ](*,)

---


---
title: "Right Mouse Click no longer working"
date: 2009-05-01
forum: General Help
---

### Post by Ian1 on 2009-05-01
I recently upgraded from 8.10 to 9.04 and it appears that I am no longer able to right click. I can left click and use the center button with no problems but the right click does not seem to be registiring at all. I have an corded, optical, three button mouse and had no problems with it before the upgrade. I don't even know how to begin to fix this so any help would be greatly appreciated.

Thanks,

-Ian

---

### Post by delcypher on 2009-05-01
I'm sorry I'm not really an expert on this but you check if you mouse is actually working by using the command```
xev
```. Running this in the terminal will continuously print out a list X-events (clicking the mouse buttons is one of them).

As a temporary solution you could try and use xmodmap to try and get your mouse button to work.

---

### Post by aextance on 2009-05-04
I don't know if it's exactly the same thing, but when I upgraded my left click stopped working - Thinkpad T30. I've now gone back to using Intrepid through a dual boot, after trying a number of faffy fixes. 

I'd like to try xmodapp, and maybe put a shift key down as my left click. When I do xev, it doesn't register any left clicks. How do you close xev, by the way - especially if your left click isn't working?!?

How does your problem manifest, by the way? When I boot up, a drag box appears on the desktop. I have a suspicion that there is a piece of code somewhere that is effectively forcing the button to be always on. 

I've reported my problem as bug 371563, and my main thread on it is at: 

[http://ubuntuforums.org/showthread.php?p=7209852#post7209852](http://ubuntuforums.org/showthread.php?p=7209852#post7209852)

---


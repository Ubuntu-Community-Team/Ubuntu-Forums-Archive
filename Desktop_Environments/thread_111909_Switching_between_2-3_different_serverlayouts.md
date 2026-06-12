---
title: "Switching between 2-3 different serverlayouts?"
date: 2006-01-03
forum: Desktop Environments
---

### Post by simohell on 2006-01-03
I have two different xorg.conf serverlayouts I've managed to get working well to meet my different needs on my laptop with 915GM. One is using Xinerama and the other is not. I might or might not need another one to plug in a TV.

Now I need to figure the best way to switch between modes.

I probably can define 2 alternative server layouts, but I would need to be able to switch them easily enough. How to make it simple to select the layout at starup?

Some different approaches I can kind of figure out:

1. If I keep to separate xorg.conf files I could rather easily to write a script that simply swithes xorg.conf and xorg.alt files and reboot. 

or

2. With enough help I could do something that lets me choose between layouts during startup and have a timeout in favor of internal LCD only.

or

3. With enough help I could do something to set (swap) the layout-parameter my X and restarting it the way Ctrl-Alt-Backspace does.


But is there any "official" way to switch between serverlayouts while already working in X? I'd like to somehow bind it to my Fn-F5 if possible. 


(Hope you got my point)

---


---
title: "Controling a computer with a usb game controller"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by blithen on 2008-04-06
I'm just talking about using it to control volume or change a song in your music player. Is it possible to bind a controller button to a specific function?

---

### Post by p_quarles on 2008-04-06
Moved to Customization.

The answer is yes, probably. You would need to figure out, first, what signal the game controller sends to X by running:
```
xev
```
in a terminal. From there, the exact how-to would be specific to your window manager.

---

### Post by Visti on 2008-04-06
You could take a look at this: [http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html](http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html)

I haven't tried the xkeycaps command, which seems a lot easier to grasp, but the gist of the old-school way is this: run xev and press a button, write down the number that appears, use xmodmap with that number to remap the key to another key.

I'm sure there must be a graphical tool for this or something, but this is one way. Quite a hassle, though. However, as far as I remember, this only last the x-session in progress, so you'd have to chuck it in a script at startup or something similar.

---


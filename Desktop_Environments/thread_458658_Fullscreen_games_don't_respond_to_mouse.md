---
title: "Fullscreen games don't respond to mouse"
date: 2007-05-29
forum: Desktop Environments
---

### Post by Feba on 2007-05-29
Well i've run into a little problem, whenever I run a game at my screen's native resolution (1280x1024) in fullscreen, my cursor won't move. So far, this has happened in Prenumbra and Savage, it also happened in nexuiz but I was able to solve that one by removing and readding it through Add/Remove. 

I think it might have something to do with compiz or gnome, but I don't know what. 
They work fine in fullscreen as long as they're under 1280x1024. Another problem i've been having with other fullscreen games is that, when I quit them, after they leave fullscreen mode (to close), they show their screen in the upper left hand quarter of the screen, with a black window behind them, and my computer become completely unresponsive until I do a hard reboot.

These are really big problems, so an answer would be very appreciated.

---

### Post by mlind on 2007-05-30
You implied that you're probably using compiz instead of metacity to manage windows. Does this problem occur when compiz is disabled?

Open a terminal window and type
```

metacity --replace

```
Leave the terminal open on desktop and then run your game. Does the problem persist?

I've had similar fullscreen resolution issues as you, but only when running games using wine.
What driver are you using for your gfx card?

---

### Post by Feba on 2007-05-30
I solved the problem by setting System Manager to CTRLALTDEL, and using that to close compiz and compiz.real processes before I play the games. I'm using the nVidia driver in the restricted drivers manager.

---

### Post by mlind on 2007-05-30
> **Feba said:**
> I solved the problem by setting System Manager to CTRLALTDEL, and using that to close compiz and compiz.real processes before I play the games. I'm using the nVidia driver in the restricted drivers manager.

So it's compiz alright. using metacity --replace is IMO better, so that you don't need to kill the compiz process. If you don't use compiz at all, you can always just disable it.

---


---
title: "Battle for Middle Earth"
date: 2007-05-08
forum: Gaming &amp; Leisure
---

### Post by HeavyAl on 2007-05-08
Anyone gotten it to run? It installs fine under wine but spews a bunch of garbage and kicks me back to the prompt when I try and run it. Having played it under windows I don't see what the problem is - it doesn't even use any really high end shader technology as far as I can tell. 

Any help appreciated.

---

### Post by rai4shu2 on 2007-05-08
First of all, Wine can't really handle the vp6 decoder. If you rename/delete all the intro movies, there's still quite a few blitter effects the game tries to do in an actual mission that Wine doesn't yet support.

[http://appdb.winehq.org/appview.php?iVersionId=2713](http://appdb.winehq.org/appview.php?iVersionId=2713)

---

### Post by HeavyAl on 2007-05-08
I see, the vp6 thing is a video format. It's probably used on the main menu screen as well which would probably be the reason why everyone gets kicked out at the main menu. I notice under windows if you set all the visuals to low that the main menu becomes a static image rather than having the video background. I wonder if it would work if the settings were switched to low under Linux. Then again, perhaps the buttons are still some sort of vp6 'hot spots', in which case the crash would still occur since vp6 isn't supported. 

Guess I'll tinker with it some more. Thanks for the input, at least I know what the main culprit is now.

---

### Post by JC_510 on 2007-06-25
Any luck? I'd love to play this on Ubuntu instead of having to dual boot it...

---


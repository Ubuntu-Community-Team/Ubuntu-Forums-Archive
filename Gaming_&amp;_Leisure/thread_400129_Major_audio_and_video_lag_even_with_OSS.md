---
title: "Major audio and video lag even with OSS"
date: 2007-04-03
forum: Gaming &amp; Leisure
---

### Post by Gorthus on 2007-04-03
I know I keep making threads but my problems keep jumping around.

I have the audio set to OSS, I have the newest ATI drivers from their site, and yet Day of Defeat: Source still runs like crap (10 FPS)... There has to be something I am doing wrong!

But there is a new problem... The sound and menus lag now... It used to be fine with just the game lagging and the menus still working, but now I cant even get out of the game without shutting off my PC via the case power button...

---

### Post by Triorph on 2007-04-03
Weird, i was under the impression that alsa is faster than oss, especially for gaming, anyway ATI cards have alot of trouble getting 3d rendering working in linux, so they could be the problem, also it depends on how good your system is, just because you ran it fine in windows doesn't necessarily mean its going to run as fine under wine. I'm not too knowledgeable about ATI cards but as far as i'm aware you should be able to type 'glxinfo |grep direct' and it will tell you if your card is setup for a 3d environment (then again thats for beryl, don't know about dod source)

---

### Post by Gorthus on 2007-04-03
I did that and it said Direct Rendering: No.

Also:
[IMG]http://img503.imageshack.us/img503/7285/errorbn1.jpg[/IMG]

I get that any time I try to run a steam game.

Also also:
Even my GMatrix screensaver lags.

---

### Post by Triorph on 2007-04-04
if direct rendering says no it means your graphics card isn't setup right, also if you're running steam via wine, you will actually have to install it through wine first, rather than just copy it from a windows partition, otherwise there will be missing registry files and stuff (i'm not sure if thats your problem but it does look like it)

as for the fixing of the direct rendering, i don't know the answer but you should try looking up some tutorials for setting up ati graphics cards.

---


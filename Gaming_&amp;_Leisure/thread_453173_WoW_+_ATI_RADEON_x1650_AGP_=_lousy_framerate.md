---
title: "WoW + ATI RADEON x1650 AGP = lousy framerate?"
date: 2007-05-24
forum: Gaming &amp; Leisure
---

### Post by stefaan.dutry on 2007-05-24
I was able to install the drivers for the graphics card

I'm using wine
I copied the folder from a windows installation (now with the latest patch too)
It runs great when you're in an empty space giving you 50-60 FPS

As soon as some other character or enemy is in your image the framerate drops to 8-12 FPS which is not playable for me.

Is there anyone that can give me a way to improve my framerate?

I searched the internet , I've searched these forums, i tried the tweaks, but none of them seems to get me further than this.

If anyone could help me I would be grateful. (a constant framerate of 30 FPS would do)

Under windows i get a framerate of 40-60 FPS. (unless of course it's getting an update of some sort)

---

### Post by hikaricore on 2007-05-25
Stefaan: Wrote a long post, server ate it, not typing it all again. (am tired as hell)

Brief overview:
1. ATI drivers suck, not our fault, ATI write them, better ones soon if you believe them.
2. make sure you have latest drivers from ATI, lower resolution (try 800x600), don't have beryl running, turn all graphic options to low or off (in d3d mode or game will crash).
3. no luck above then check: [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine) for some possible ati fixes

hikari go sleep now

better grammar tomorrow

---

### Post by stefaan.dutry on 2007-05-25
thank you, now i know how to change the options i need to be in d3d mode :p

---

### Post by stefaan.dutry on 2007-05-29
I set all the option to minimum aswel, but that didn't help either.

Sorry for the late response, but I've been rather busy.

Don't look further to help me for now, cause i don't have much time to test it.  I'll get back to looking at the problem once I have more time.  Maybe then there will be new drivers or an update for wine which will help me.

Thanks for your help anyway.

---

### Post by Ferrat on 2007-05-29
That doesn't really feel like a settings problem, what drivers are you using? 

I got alot more FPS on my x800 AGP card then you get and that shouldn't be

---

### Post by stefaan.dutry on 2007-05-29
it's the latest X1600 drivers from ATI.

Somebody told me that it could be i needed to have a driver for AGP seperately.

I'm not at home right  now so i can't copy the exact driver

---

### Post by ShadowFlar3 on 2007-05-31
Have you applied the registry tweak from the hikaricore's link? You shouldn't get such slowdowns ofc, but you shouldn't expect wow to run just as well as on windows anyway. Just make sure you apply the wine registry tweak, xorg.conf fix and set resolution and color stuff to match your desktop in config.wtf file.

Also make sure you have your video card installed properly with

glxinfo | grep rendering

---

### Post by stefaan.dutry on 2007-05-31
I'll post some detailed information in a few days.

I realy don't have time to test things right now. (just made my own guild, busy structuring it and also 2 birthdays coming up in the next days, so that'll take up most of my time).

I did the registry tweak.

I'll post my config.wtf file and the output of that command when i have some time again.  Untill then, do not bother trying to help me, I don't have time to try things out.  Thx anyway :D.

---


---
title: "Linux Games in XBMC?"
date: 2010-06-14
forum: Gaming &amp; Leisure
---

### Post by Kdar on 2010-06-14
I am using XBMC on my HTPC in living room and I was reading this article about linking games inside of XBMC:

[http://lifehacker.com/5523672/turn-your-xbmc-media-center-into-a-video-game-console](http://lifehacker.com/5523672/turn-your-xbmc-media-center-into-a-video-game-console)

This article is for Windows, but I want to do the same in Linux.

I was able to install that plug-in in XBMC, but how do I link some games this way?

I tried to link game like Mahjongg (I linked the file in application menu), but it gave me an error.

Did anyone done this here?

---

### Post by ucal on 2010-06-15
So, help me get some context here.  XBMC is running on your htpc in your living room, hooked up to your TV.  And it allows you to, assuming your running windows, stream games from your PC to your HTPC wirelessly, which are then shown on your TV?  And you want this functionality for linux, which is apparently supported, but you're having trouble with? 

I ask, because this sounds really cool, if that's what's actually happening.  I'll try and help out.

EDIT:  You might get more help over at the XBMC forums though.  

[http://forum.xbmc.org/forumdisplay.php?f=52](http://forum.xbmc.org/forumdisplay.php?f=52)

EDIT EDIT: I see you're already there.  Good luck.

---

### Post by Kdar on 2010-06-15
Well, not exactly.

The Launch plug-in for XBMC (which is like Media Center) helps to launch games from XBMC and apparently running them inside of XBMC.

I do not plan to stream them, it is the games which are already installed on that HTPC.

I saw tutorial of how to do this in Windows (the link in my first post), there it tells, using Laucher plug-in, to find the .exe file of the game for it to work. But what do I link to in the Linux?

---

### Post by hikaricore on 2010-06-15
This has been asked several times on the XBMC Linux forum: [http://forum.xbmc.org/forumdisplay.php?f=52](http://forum.xbmc.org/forumdisplay.php?f=52)
Perhaps searching there might net you a quicker answer.

---

### Post by Grishka on 2010-06-15
> **Kdar said:**
> Well, not exactly.

The Launch plug-in for XBMC (which is like Media Center) helps to launch games from XBMC and apparently running them inside of XBMC.

I do not plan to stream them, it is the games which are already installed on that HTPC.

I saw tutorial of how to do this in Windows (the link in my first post), there it tells, using Laucher plug-in, to find the .exe file of the game for it to work. But what do I link to in the Linux?

hey buddy, you have to link to the program executable. executables are most often stored in /usr/bin on Ubuntu systems, provided you install software from the repositories. basically every program should launch from XBMC, though launching applications that run in a window will exit XBMC fullscreen mode, and show the application on your desktop. so if you want a unified, seamless XBMC system, then you should launch all apps from XBMC in fullscreen mode.

---


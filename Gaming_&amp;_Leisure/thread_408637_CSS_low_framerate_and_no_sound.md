---
title: "CSS low framerate and no sound"
date: 2007-04-13
forum: Gaming &amp; Leisure
---

### Post by luke949 on 2007-04-13
Hi, I installed the latest Wine and I installed steam. I can play and Counter-strike Source and play online, but the framerates are extremely low, noticable to the eye, and I cannot get any sound whatsoever. I can get sound off from websites such as youtube and on gaim, but not in css, starcraft, or Jedi knights II. 

Anyone know how to fix this?

---

### Post by AndrewRiedi on 2007-04-13
You can try a few things.  One is to simply run the game in a different direct3d level.  (-dxlevel 70, -dxlevel 80, -dxlevel 81, -dxlevel 90)

Another is to go [here]("http://http://wiki.winehq.org/UsefulRegistryKeys") and set the [COLOR="Red"]UseGLSL[/COLOR] and [COLOR="Red"]VideoMemorySize[/COLOR] registry keys.

Next, make sure you have the latest wine you can get.  (0.9.35 was released today, Friday the 13th)

Lastly, see [the AppDB]("http://appdb.winehq.org/appview.php?iVersionId=3731") for more information.

---

### Post by Brynster on 2007-04-14
To add to the advice givcen above, the obvious is to ensure you have the latest specific driver for you video card installed. ATI are known to be problematic to install but many people are getting great results once there installed correctlly.

---

### Post by FaceLeg on 2007-04-25
I am having terrible difficulty getting steam to run well also...

My sound, however, is great.  I use OSS with emulation - perfect sound, just like it was on Windows XP.

I think there needs to be a Source & Steam related mega thread, with all problems/fixes.

Just an idea.

---


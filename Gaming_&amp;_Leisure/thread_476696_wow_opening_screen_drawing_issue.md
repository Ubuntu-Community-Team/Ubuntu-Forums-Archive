---
title: "wow opening screen drawing issue"
date: 2007-06-17
forum: Gaming &amp; Leisure
---

### Post by Haruko147 on 2007-06-17
ok, the wow installation went perfectly. As soon as I run wow.exe though, it tries to draw the opening portal screen to varying degrees of success, usually a EULA I cant interact with and textureless surfaces on the general figure of the portal (no movement either). -opengl and -d3d have the same bad results. I cant get to the wtf config for the settings, because that requires I log into a character to create the file, a step I can't reach.

Direct rendering is on, drivers are updated I think (I don't know how to check exactly on linux), and glxgears runs very well. Beryl works perfectly if thats any benchmark, I've got it turned off for trying to run wow at the moment of course. 

Ive also tried the regedit tweak but so far theres no difference with it there or not.

If anyone has at least some way I could analyse what the problem is a bit farther, or even a solution it would be greatly appriciated. Thanks in advance for responses!

---

### Post by ShadowFlar3 on 2007-06-17
You can just go ahead and create a config.wtf file if you don't have one and all the settings will be loaded as specified there.

As of any further advice on what you could be dealing with, no idea. Seems like your drivers are good (what graphics card do you have BTW?) since you can run beryl and glxgears and there's really not much to tweak in  wow options except color depth and resolution, which should be set to whatever you have on desktop. Also add the line SET hwdetect "0" there to prevent the game from trying to auto-detect the settings.

Many people just ignore wow threads because most of the posters just failed to read the sticky topics and follow one of the million wow on wine how-to-guides around the net, but I can see that's not the case with you.

---

### Post by Haruko147 on 2007-06-17
sorry I forgot to mention, graphics card is ATI radeon 9800

but yeah, I realize I might have posted in the wrong spot now, especially after reading the sticky. I dont think config.wtf is the problem, but its worth a shot a this point.  That and Im working on a little pentagram...

---


---
title: "Diablo2 installs w/ CrossoverOffice, won't recognize that the cd is in the drive"
date: 2005-04-10
forum: Gaming &amp; Leisure
---

### Post by lynng on 2005-04-10
Using Crossover Office 4.2.  The install of both Diablo 2 & the LOD expansion went fine, no error messages.  When I try to run it, however, I get a message to "Please verify that your Diablo II Expansion Disc is in your CD-ROM drive, then click on 'Retry'".  The cd is mounted, and Ubuntu puts an icon for it on the desktop automatically, but no dice.  I even tried manually mounting it instead, but so far nothing works.  This is the last app I need to get working to completely dump Windows, on both my brother's machine & mine.  I looked at the forums on Codeweavers, did a Google search, & searched the forums here.  So far, I can find threads where people say they have this issue, but cannot find a solution.  I'd rather not have to use a crack, but at this point I'll try any suggestion.

---

### Post by gil-galad on 2005-04-10
Whats wrong with a crack?

Its not going to recognize the cd because of the disc copying protection most games use.  I believe Cedega has support for this, but with regular wine and crossover you probably have to use a crack.  

I crack all my games anyway, because who wants to put a cd in the drive every time for no reason?

---

### Post by lynng on 2005-04-10
So you're saying the issue is that Ubuntu/Linux can't deal with the copy protection at all?  If you have instructions, I'll give 'em a go.

And so far, I haven't been able to find any info about a crack for the 1.10 version of the game.

---

### Post by gil-galad on 2005-04-10
[QUOTE=lynng]So you're saying the issue is that Ubuntu/Linux can't deal with the copy protection at all? [/QUOTE]

No, the problem is that windows game cd's have some sort of windows-only copy protection that wine does not emulate.  If you burn your own diablo cd, even in windows, the game won't recognize it.  Cedega bought the rights to use this protection in their version of wine.  Anyway, here is a crack for the game.  

[http://megagames.com/cracks/html/c901470_0.htm](http://megagames.com/cracks/html/c901470_0.htm)

---

### Post by lynng on 2005-04-10
I tried all three of the EN cracks, but none seem to work properly.  The last one I tried, the Pitchfork version, brings up a window titled Diablo II, but the window is blank.  And my screen is behaving oddly.  My  1600x1200 resolution is behaving as a virtual desktop where I have to move the mouse & push the edge of the screen around to see the whole desktop.  When I close the empty Diablo II window, the screen returns to normal.

edit:
I followed the Tips & Tricks suggestion on the Codeweavers site to force the game to run inside a window.  That fixed the screen behavior issue, but the Diablo II window is still blank.

---

### Post by lynng on 2005-04-11
I finally got the game screen to at least show up in the window rather than the blank screen.  However, the window screen flickers so badly that I can't see the mouse pointer & the game is unplayable.  There's also no sound.  I have tried every option of the video test w/o improvement, although only the Direct3d options show any game graphics at all.  The directdraw options result in a black screen & a window that has to be killed.  From what I gather from the Crossover forums, some are successfully running the game w/issues, some have the "insert cd" problem, and some have the black window problem.  None of the threads offer a solution.  I have any open ticket w/ Crossover about it, but no response as yet.  I've been to the #crossover channel on IRC, and there will be ~30 people in the room and none of them respond to my questions with so much as a "sorry, can't help."  I don't want to have to pay for yet another Wine app (Cedega) to get the game running when I know people have been successful with it, if at all possible.

---

### Post by TravisNewman on 2005-04-12
It may help you to know that I've NEVER gotten a game to work in Crossover. They work better in plain WINE than they do in Crossover. Cedega is what you want for games. It's cheap, and it works AMAZINGLY for games.

---

### Post by lynng on 2005-04-12
I have changed my xorg setup to use the fglrx ATI driver rather than the default.  This solved the video problems I had with the game, and it is now playable with the exception of no sound.  From the transgaming website, the ATI issue would likely have been a problem with cedega as well, so I am glad I persisted with trying to get it working under CrossoverOffice.

---

### Post by lynng on 2005-04-12
Sweet!  Sound is working after uncommenting the line

HardwareAcceleration = "Emulation"

in .cxoffice/dotwine/config under the dsound section.

---


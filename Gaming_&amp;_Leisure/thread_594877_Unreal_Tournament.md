---
title: "Unreal Tournament"
date: 2007-10-28
forum: Gaming &amp; Leisure
---

### Post by Morokiane on 2007-10-28
I'm having problems getting Unreal Tournament: GOTY running.  Before I installed compiz-fusion & emerald it ran perfect...but now that I have those UT won't run...it starts up but then crashes.  I tried turning off compiz-fusion & emerald, but that doesn't help either.  This is what is in the console after the crash when I go to start a new game.

```
Starting a new game...
Created a new LadderInventory.
UT-Logo-Map.LadderInventory0 giveto UT-Logo-Map.TMale2
Assigned player a LadderInventory.
Initialized moving brush tracker for Level UT-Logo-Map.MyLevel
X Error of failed request:  GLXBadContextTag
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  144 ()
  Serial number of failed request:  13086
  Current serial number in output stream:  13088
Signal: SIGSEGV [segmentation fault]
Aborting.
Segmentation fault (core dumped)

```

---

### Post by ratna4 on 2007-11-02
Same here with Tactical Operations (which uses UT engine)

---

### Post by tenach on 2007-11-18
Have you tried reinstalling UT?  I did that and it somehow fixed itself.

---

### Post by psyopper on 2007-11-19
Just to be sure, please take no offense... Did you turn off Compiz before starting UT? Compiz will not release the video card's 3d/OpenGL hooks forcing the card to continue processing Compiz while trying to process the game.

Also of interest would be exactly how you installed Compiz? Oh, and what video card/driver are you using?

---

### Post by magikx21 on 2007-11-21
I just installed UT through Wine and it works fine while running Compiz but the only working settings is OpenGL at 512x384 using 16bit color. Has anyone got this going in 1024x768 in 32bit color?
Maybe it's my hardware but I doubt it.
AMD Sempron 1.8GHz
nVidia GeForce 4 MX 4000
Running Kubuntu 7.10 x64

---

### Post by tenach on 2007-11-21
I have it working at 1280x800 natively.

---

### Post by magikx21 on 2007-11-22
How did you get it running natively? Also does running it natively fix the speed issue? Running it in Wine it is going really fast and when I try to connect to an online game it gets all messed up because of the speed.

---

### Post by magikx21 on 2007-11-22
Ok I got it running natively but multiplayer seems to be giving me issues. Through Wine I was able to connect to internet games now I can seem to. What happens is it says its loading but just sits there. Had the same issue trying a LAN game, However; I can make this a server and connect my other PCs to it without a problem.

I also have a similar issue with UT2k4 trying multiplayer it starts downloading the files (but really slow) then around 70% the connection fails. Like UT GOTY it can be used as the server though with no problems.

Anyone have a clue what I should do?

---


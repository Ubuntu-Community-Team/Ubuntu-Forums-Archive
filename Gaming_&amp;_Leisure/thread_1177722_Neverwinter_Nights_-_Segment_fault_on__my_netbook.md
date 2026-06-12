---
title: "Neverwinter Nights - Segment fault on  my netbook"
date: 2009-06-03
forum: Gaming &amp; Leisure
---

### Post by Ferrat on 2009-06-03
I know there are lots and lots of thread on NWN and error to it, however after reading as much as possible I just can't get NWN to run, I'm following the installation instructions to the letter from BioWare's homepage and redid it twice following [http://gwos.org/doku.php/guides:64bit:nwn](http://gwos.org/doku.php/guides:64bit:nwn) which is more or less the exact the same way. 

The problem is I'm getting segment fault as soon as I try to launch it, the server works but normal game launch wont, I'm at my wits end here, Battle for Wesnoth, OpenArena, SDLmame etc works without any problems. 

I'm trying to run it on a Compaq Mini 730EO with Ubuntu Remix (same as all the others eee clones) as stated everything else works fine but I just can't get it to start up and checksums are correct from what I can see from [THIS THREAD]("http://nwn.bioware.com/forums/viewtopic.html?topic=347606&forum=72") and permissions are in order as well.

Any other thing I can try? any idea what it could be?

---

### Post by Ferrat on 2009-06-03
Ok gave up on the Linux version, just couldn't get it working, that damn seg. fault was everytime I tried, so installed in with wine instead, works flawless with virtual desktop set to 1024x576 and same setting on NWN (needs to be done manually, automatic sees my res. as 131134 x 64 or something weird like that^^)

---

### Post by Boondoklife on 2009-06-03
What version of NWN do you have? Diamond, gold, etc.

---

### Post by caravel on 2009-06-04
It sounds like you haven't edited the nwn shell script to remove the reference to the lib directory.  If you don't change this, the game will use the SDL libs that it ships with, whereas you must use the SDL libs installed in your system for it to run.

Change this:
```
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
```

To this:
```
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
```

Also try installing the game as a user *entirely* in your ~ directory.  This worked for me and others as it seems that NWN does not work well when installed for mulitple users.

---

### Post by Ferrat on 2009-06-04
Have diamond version not that it matters when I can't even get the online version resources working, and I have done the fix for the SDL in the script etc. only difference with that is with it I get a SDL catch for the segment fault and if I remove it I get just the segment fault. 

Tried installing with the dimond resources from my wine installation, same thing, segment fault om nwmain >_<

---

### Post by caravel on 2009-06-04
Did you check dependecies?

Have you installed it to your ~ ?

What is the graphics chip in that machine?  Have you installed proprietary drivers?

---

### Post by Ferrat on 2009-06-04
Dependencies shouldn't be a problem, it's installed to home directory yes and the graphic chip is a Intel 945GME which runs as it should, got a steady playable FPS when playing NWN through WINE and as stated OpenArena, SDLmame, Battle for Wesnoth, pSX etc all work as they should without any graphic problems. 

Anyone that has NWN running natively under a netbook with Ubuntu Remix?

---


---
title: "Total Extreme Wrestling"
date: 2007-01-30
forum: Gaming &amp; Leisure
---

### Post by Zeikcied on 2007-01-30
I'm trying to get a game to run in Wine.  It's called Total Extreme Wrestling 2005, and it's by Grey Dog Software.  It is written in VB6.  And I did install the VB6 SP5 runtimes from the MS website.

The game uses eLicense, and that part works well enough.  I use my order number and it seems to license it perfectly.  The only problem is it won't launch the game.  I get "Run-time error 429 - ActiveX component can't create object."

Is it possible to somehow configure Wine to have ActiveX?  I tried Ies4Linux, but that seems to have isolated itself from the default Wine directory.  I tried to copy/paste the TEW2005 files over to the Ies4Linux folder, but that's not working.  Probably because Wine is starting it, and not whatever custom script Ies4Linux has.

There may be other issues surrounding this game, unfortunately.  It plays some audio, so I'm sure it'll look for Windows Media Player.  Plus it uses databases, using Microsoft Jet 4.0 and MDAC, although Grey Dog Software provides downloads for those programs.  I'm hoping that the WMP thing won't crash the game.  As I can do without the audio.

I know this post is a bit long winded, but is it possible to get this to work?

---

### Post by Zeikcied on 2007-01-31
I got the game to work, but only partially.  I get the title screen, but I can't actually start a game.  When I hit New Game, it goes to check the database.  Shortly into the database check, I get Run-time Error 75 - Path/File Access Error.  If I try to use the Editor, I get a Run-time Error 339.  It further says that "Component 'ovscombo2d.ocx' or one of its dependencies not correctly registered: a file is missing or invalid."

I figured out how to launch the game using the ies4linux setup by examining the ies4linux launch script, and modifying it to point to the TEW2005.exe file.  I then had to use the export command to install the Jet 4.0, MDAC, and VB6 Service Pack 3 files.  (VB6 Service Pack 6 refuses to install.)

So, the game runs, but I'm still having these errors.  I'm hoping that I can get the whole thing to work, so that maybe I can get TEW2007 and not have to switch to Windows just to play a game for ten minutes.  (A VM might work much better, but I have no idea how to setup a VM, especially since I don't have any Windows install discs seeing as how my computer came pre-installed with it.)

---


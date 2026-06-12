---
title: "Odd problems with nwn under edgy"
date: 2007-02-11
forum: Gaming &amp; Leisure
---

### Post by slickwilly on 2007-02-11
I have an older Sony Vaio, with a onboard Geforce2mx, just finishing reinstalling Edgy after trying to upgrade to newer Nvidia drivers ate my system once again.  That unfortunately is not the problem, here is the problem which was the reason I tried to upgrade my driver.
Neverwinter nights (gold + hotu, patched to 1.68) starts up fine and dandy, however at random intervals, for no good reason I can see, the Opengl window where gameplay occurs will turn a solid color and force me to quit out of the game, and then completely reboot my system before reconnecting to a gameworld for it to function again.  This is rather problematic, as I can sometimes play for 20mins, or sometimes only 5 before this occurs :(  It's pretty odd that i can still see the border around the opengl window, Ie: the text window and the buttons up in the right hand corner, its only the 'gameplay' window that hashes up.  I had XGL/Compiz installed but I removed them in the vain hope that was the problem, no love :(  I tried deleting the ./lib path from the nwn script, and the game would not start at all on the system sdl libraries, argh!  So at this point I have no clue at all what could be causing this to happen, anyone who has had similar problems or an idea as to a solution, I certainly would appreciate any help anyone could provide!

Thanks!

Slick

---

### Post by slickwilly on 2007-02-11
Here is a bit more information, an exceprt from my xorg session error log, cant copy the whole thing as it appears to be quite large, which can't be good, so I copied a section with unique errors in it for more information.  It is as follows:

X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1600988
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1600988
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1600a3e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1600a3e
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1600a3f
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1600a3f
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1600a40
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1600a40
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0xa1


The 166 one is that bloody synaptics driver I think, the others I'm not sure about.


Slick

---

### Post by slickwilly on 2007-02-13
Figured it out, hurrah!  One of my installation disks has a scratch on it apparently which caused a single file in a zip to become corrupt, Tiles_tpa.erf, should have been 77meg was 11.3 meg, downloaded that big honking 1.2 gig nwn resource file, unzipped tiles_tpa.erf and now works smooth as silk, hurrah again!

On a side note though, this is a bit more serious, is anyone else having trouble with NWN corrupting Inodes on their EXT3 filesystem, it does not happen all the time, but every once in awhile after playing the game when I go to bring my system back up fsck pops up and scares the daylights out of me.  Anyone else with similar problem, and/or solution to it?

Thanks,

Slick

---


---
title: "sdlmess and colecovision - this is driving me nuts"
date: 2008-04-02
forum: Gaming &amp; Leisure
---

### Post by beemer on 2008-04-02
Ok - I have sdlmess downloaded and compiled. 

I can do a ./mess nes cart xyz.nes for example ...or I can run a genesis cart.

What I can't do apparently is run anything that needs a bios like coleco or vectrex.  It simply always states:
coleco.rom NOT FOUND
ERROR: required files are missing, the game cannot be run.
Ignoring MAME exception: coleco.rom NOT FOUND
ERROR: required files are missing, the game cannot be run.

or "NOT FOUND" for whatever bios it's looking for.  I've tried explicitly putting in a -rompath and -bp.  I know the bios roms are good because I they will run with other emulators.

I've searched up and down google for help but can't seem to find even any actuall mess documentation that could help.

Help me Ubuntu Community...you're my only hope...

Update - Finally found some info, but still get the same issue.  It appears the mess expects the bios's to be either in sub-dirs of the rompath or within a zip file.  Such that system.img resides within a vectrex.zip and an intv.zip should container the exec and grom bin's.  I've tried both the path and zip file routes and still mess won't see the bios's

Beemer

---


---
title: "OpenMW 0.23.0 Available Now"
date: 2013-02-20
forum: Gaming &amp; Leisure
---

### Post by OpenMW on 2013-02-20
The OpenMW team is proud to announce the release of version 0.21.0! Release packages for Ubuntu are now available via our [Launchpad PPA](https://launchpad.net/~openmw/+archive/openmw). Release packages for other platforms are available on our [Download page](https://code.google.com/p/openmw/downloads/list). This release introduces video playback, improvements to cell load time, and parsing for escape sequences in dialogue and message boxes.

    Check out WeirdSexy's [release video](http://youtu.be/7FtIcIPogpQ).

    **Known Issues:**
    
[list]
[*]No sound when playing videos on OS X
    
[*]Extreme shaking may occur during cell transitions for some users (enable anti-aliasing as a possible workaround)
    
[*]Launcher crash on OS X < 10.8
[/list]


    **Changelog:**
    
[list]
[*]Various dialogue, trading, and disposition fixes and improvements
    
[*]Torch flickering improved to better match vanilla Morrowind
    
[*]Fix for attribute fluctuation when infected with Ash Woe Blight
    
[*]Adjusted activation range to better match vanilla Morrowind
    
[*]Fixes for the Journal UI
    
[*]Fixed crash caused by Golden Saint models
    
[*]Fix for beast races being able to wear shoes
    
[*]Fix for background music not playing
    
[*]Fix for meshes without certain node names not being loaded
    
[*]Fix for incorrect terrain shape on inital cell load
    
[*]Fix for MWGui::InventoryWindow creating a duplicate player actor at the origin
    
[*]Added video playback
    
[*]Added support for escape sequences in message box and dialogue text
    
[*]Added AI related script functions, note that AI is not functional yet
    
[*]Implemented fallbacks for necessary ini values in the importer, unused in OpenMW as of yet
    
[*]Implemented execution of scripts of objects in containers/inventories in active cells
    
[*]Cell loading performance improvements
    
[*]Removed broken GMST contamination fixing mechanism
[/list]


see also:
[*Official Youtube Channel*](http://www.youtube.com/user/MrOpenMW)
[*For New Developers*](http://openmw.org/wiki/index.php?tit...ibution_Wanted)
[*OpenMW Homepage*](http://openmw.org/) 
[*Chat @freenode*](http://freenode.net/ #openmw)

---

### Post by OpenMW on 2013-03-30
The OpenMW team is incredibly proud to announce the release of version 0.22.0! Release packages for Ubuntu are now available via our [Launchpad PPA]("https://launchpad.net/~openmw/+archive/openmw") and for Debian in our [Debian PPA]("http://forum.openmw.org/viewtopic.php?f=20&t=1298"). Release packages for other platforms are available on our [Download page]("https://code.google.com/p/openmw/downloads/list"). This release introduces the long awaited animation feature, many thanks to everyone on the team who has worked to bring this to fruition. Another major feature implemented in this release is support for loading multiple ESM and ESP files. Prepare to travel to Mournhold, Bloodmoon, and beyond into Tamriel Rebuilt and other mods. Other features include the "Dispose of Corpse" button, lights that are more faithful to classic Morrowind, and working active spell icons. The bug fix list for this release is quite extensive, see below.

**PLEASE NOTE:** Starting with this release, you must run the ini importer at least once! This can be done automatically through the launcher.

**Known Issues:**

[LIST]
[*]Extreme shaking may occur during cell transitions for some users (enable anti-aliasing as a possible workaround) 
[*]Launcher crash on OS X < 10.8 
[*]Polish version of Morrowind.esm makes OpenMW crash 
[/LIST]


Check out the [release video]("http://www.youtube.com/watch?v=a-i73Qb3KKw") by the inexorable WeirdSexy.

**Changelog:**

[LIST]
[*]Implemented Active Spell Icons 
[*]Implemented walking, running, and swimming animation 
[*]Implemented support for ESPs and multiple ESMs 
[*]Implemented proper collision shapes for NPCs and creatures 
[*]Implemented lights that behave more like vanilla Morrowind 
[*]Implemented importing BSA files as part of the settings imported by the config importer 
[*]Implemented zoom in vanity mode 
[*]Implemented potion/ingredient effect stacking 
[*]Implemented object movement between cells 
[*]Implemented closing message boxes by pressing the activation key 
[*]Implemented random persuasion responses 
[*]Implemented closing message boxes when enter is pressed 
[*]Use rendered object shape for physics raycasts 
[*]Improved the race selection preview camera 
[*]Class and Birthsign menus options are now preselected 
[*]Disabled dialog window until character creation is finished 
[*]Decoupled water animation speed from timescale 
[*]Changed underwater rendering to more closely resemble vanilla Morrowind 
[*]Hid potion effects until discovered 
[*]Finished class selection-dialogue 
[*]Re-factored Launcher ESX selector into a re-usable component 
[*]Various fixes and implementations for the script compiler 
[*]Fix for a keyboard repeat rate issue 
[*]Fix for errant character outline on water in 3rd person 
[*]Fix for duplicate player collision model at origin 
[*]Fix for dialogue list jumping when a topic is clicked 
[*]Fix to prevent attributes/skills going below zero 
[*]Fix for global variables of type short being read incorrectly 
[*]Fix for collision and tooltip on invisible meshes 
[*]Fix for CG showing in Options when it is not available 
[*]Fix for crash when Alt-tabbing with the console open 
[*]Fix for pick up sound playing when object cannot be picked up 
[*]Fix for moving left or right canceling auto-move 
[*]Fix for gender being swapped (woops!) 
[*]Fix for footless guards 
[*]Fix for waterfalls not rendering at a certain distance 
[*]Fix for crash in "Mournhold, Royal Palace" 
[*]Fix for not finding non-DDS textures 
[*]Fix for some meshes being invisible from above water in Bloodmoon 
[*]Fix for Messagebox causing assert to fail 
[*]Fixes for Launcher file path selection 
[*]Fixes for missing/incorrect UI graphical elements 
[*]Fixes for various transparency rendering issues 
[*]Fixes fo various character generation UI issues 
[*]Fixes for config import in Launcher 
[*]Fixes for various new issues discovered when handling mod content 
[*]Various code cleanup 
[/LIST]



see also:
[*Official Youtube Channel*]("http://www.youtube.com/user/MrOpenMW")
[*For New Developers*]("http://openmw.org/wiki/index.php?tit...ibution_Wanted")
[*OpenMW Homepage*]("http://openmw.org/") 
[*Chat @freenode*]("http://freenode.net/ #openmw")

---

### Post by Perfect Storm on 2013-03-30
How close is the project to the real deal?

---

### Post by OpenMW on 2013-04-13
A rough guess would be one year from now.

---

### Post by ELD on 2013-04-14
Extremely impressive so far though :)

---

### Post by OpenMW on 2013-04-29
The OpenMW team is proud to announce the release of version 0.23.0! Release packages for Ubuntu are now available via our [Launchpad PPA](https://launchpad.net/~openmw/+archive/openmw) and for Debian in our [Debian PPA](http://forum.openmw.org/viewtopic.php?f=20&t=1298). Release packages for other platforms are available on our [Download page](https://code.google.com/p/openmw/downloads/list). This release introduces the initial implementation of NPC movement AI, item repairing, enchanting, levelled items, texture animation, basic particles, and more, along with an extensive list of fixes and improvements. Also as a note, Morrowind's 11th Anniversary is May 1st!

**Known Issues:**

[list]
[*]Extreme shaking may occur during cell transitions for some users (enable anti-aliasing as a possible workaround)
[*]Launcher crash on OS X < 10.8
[*]Polish version of Morrowind.esm makes OpenMW crash
[*]The OS X package for this release will be delayed. Never fear, we still support OS X, our package maintainer is just away!
[/list]


Check out the [release video](http://www.youtube.com/watch?v=aDuLCpltgoM) by the our very own WeirdSexy.

**Changelog:**

[list]
[*]Implemented Item Repairing
[*]Implemented Enchanting
[*]Implemented NPC pathfinding
[*]Implemented NPC travelling AI Package
[*]Implemented levelled items
[*]Implemented texture animations
[*]Implemented fallback settings
[*]Implemented levelup description in levelup dialogue
[*]Implemented armor rating
[*]Implemented companion item UI
[*]Implemented basic particles
[*]Improved console object selection
[*]Fixed player colliding with placeable items.
[*]Fixed Jounal sounds playing when accessing the main menu with the Journal open.
[*]Fixed Bribing behavior
[*]Fixed rendering of bone boots
[*]Fixed NPCs not rendering according to race height
[*]Fixed inverted race detection in dialogue
[*]Fixed two-handed weapons being treated as one-handed
[*]Fixed crash when dropping objects without a collision shape
[*]Fixed handling for disabled/deleted objects
[*]Fixed merchants selling their keys
[*]Fixed game starting on Day 2
[*]Fixed "come unprepared" topic with Dagoth Ur
[*]Fixed Pickpocket "Grab all" taking items not listen in container window
[*]Fixed camera shaking when looking up or down too far
[*]Fixed player position at new game start
[*]Fixed the player not having the correct starting clothes
[*]Fixed merchant gold not changing when transacting
[*]Fixed starting fatigue
[*]Fixed incorrect coin stack behavior
[*]Fixed auto-equip ignoring equipment rules
[*]Fixed OpenMW not loading "loose file" texture packs
[*]Fixes for some NPC rendering issues
[*]Fixed a sail transparency issue
[*]Fixed a crash during character creation
[*]Fixed Tauryon growing in size every time the player enters/exits a nearby house
[*]Fixed NPC stats defaulting to 10
[*]Fixed talk and container dialogue not opening sometimes
[*]Fixed crash when trying to get Rank of NPC without a faction
[*]Various UI fixes
[*]Various scripting improvements
[*]Various mod compatibility improvements
[*]Various code cleanup
[/list]



see also:
[Official Youtube Channel](http://www.youtube.com/user/MrOpenMW)
[For New Developers](http://openmw.org/wiki/index.php?tit...ibution_Wanted)
[OpenMW Homepage](http://openmw.org/)
[Chat @freenode](http://freenode.net/#openmw)

---

### Post by oldrocker99 on 2013-04-29
This. Could. Be. BIG.

---

### Post by Dlambert on 2013-05-01
I cannot wait. Whats next after OpenMW is done for you guys? OpenSkyrim?

---

### Post by ajbader on 2013-05-01
Just waiting for the moment when the game is near completable, with every important functional feature added. Out of all the TES series, Morrowind has been my favorite.

---


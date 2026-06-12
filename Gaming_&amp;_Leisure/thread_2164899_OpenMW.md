---
title: "OpenMW"
date: 2013-08-02
forum: Gaming &amp; Leisure
---

### Post by open-morrowind on 2013-08-02
OpenMW is an attempt to reimplement the popular role playing game Morrowind. It aims to be a fully playable, open source implementation of the game, and shall also be available on ubuntu!
We're proud to announce the release of version 0.25.0! Grab it from our [Downloads Page]("https://openmw.org/downloads/") for all operating systems. With the implementation of SoundGen records and the Wander AI Package, this release introduces stomping NPCs. Note that AI Wander must still be called from the console. SoundGen implementation also means that Creatures make noises. Prepare for squealing scrib nostalgia. SDL2 has also been implemented, which stomps out a lot of mouse focus and other UI bugs. Check over the changelog for the rest of the changes in this release.

**Known Issues:**

[LIST]
[*]Extreme shaking may occur during cell transitions for some users (enable anti-aliasing as a possible workaround) 
[*]Polish version of Morrowind.esm makes OpenMW crash 
[*]Pressing 'j' key during startup freezes the game 
[/LIST]



Check out the [release video]("http://www.youtube.com/watch?v=fTKQaXibMTA") by the spectacular WeirdSexy.

**Changelog:**

[LIST]
[*]Implemented SoundGen for NPCs and creatures 
[*]Implemented AI Package: Wander 
[*]Implemented 64-bit compatibility for OS X 
[*]Implemented Hardware mouse cursors 
[*]Implemented first person animations 
[*]Implemented mouse wheel zoom in third person mode 
[*]Implemented Autorepeat for slider buttons 
[*]Launcher will not start OpenMW when no esm/esp files are selected 
[*]Fixed launcher crash on OS X < 10.8 
[*]Fixed a performance drop in the Census and Excise Office 
[*]Fixed SSCR records not starting correctly 
[*]Fixed handling script names with hyphen characters 
[*]Fixed handling the repeat parameter for AIWander 
[*]Fixed enchanting window to include weapons 
[*]Fixed character being able to move while over-encumbered 
[*]Fixed dead keys 
[*]Fixed mouse not being confined to window when the game is un-tabbed, and other mouse focus issues 
[*]Fixed ini Importer aborting when there is no existing cfg file 
[*]Fixed Dead NPC and Creature collision boxes 
[*]Fixed incorrect sorting of answers in dialogue 
[*]Fixed ini Importrt core dump when given an unknown parameter 
[*]Fixed getting stuck in some doors 
[*]Fix for journal/book rendering 
[*]Fix for draw weapon sound playing when weapon is readied and cell border is crossed 
[/LIST]



see also:
[Official Youtube Channel]("http://www.youtube.com/user/MrOpenMW")
[For New Developers]("http://openmw.org/wiki/index.php?tit...ibution_Wanted")
[OpenMW Homepage]("http://openmw.org/")
[Chat @freenode]("http://freenode.net/#openmw")

---

### Post by Hari5g900 on 2013-08-02
Cool, I've been wanting an open-source Morrowind-like game on Linux and it seems that you guys have just the thing i need. Is it going to be on the sofware center?

---

### Post by open-morrowind on 2013-08-02
Once v1.0 is out, I see no reason why it wouldn't be.

---

### Post by LillyDragon on 2013-08-02
I can't wait to get Morrowind off of Steam eventually, I'd love to see how this project is coming along; it sounds more and more playable with every release. I'm always impressed with the progress, OpenMW team! The thought of enjoying Morrowind on any platform this can be ported too is simply amazing.

---

### Post by King Dude on 2013-08-02
How are you guys avoiding Bethesda's copyright?

---

### Post by TheAbyssDragon on 2013-08-02
> **King Dude said:**
> How are you guys avoiding Bethesda's copyright?
I was curious about this as well. Either way, the engine looks great so far.

---

### Post by King Dude on 2013-08-03
> **TheAbyssDragon said:**
> I was curious about this as well. Either way, the engine looks great so far.
I looked into creating a Zelda game for Linux a few months ago, but I was told that I couldn't do it because of copyright. I can't imagine why it would be different with Morrowind.

---

### Post by LillyDragon on 2013-08-03
Their FAQ explains the legal part pretty nicely : [https://openmw.org/faq/](https://openmw.org/faq/)

None of the game's official assets are included with OpenMW. As far as I can tell, it's an open-source recreation of the engine itself, and is only designed to replace the game's main binary. (EXE) Morrowwind can be really buggy, and sometimes crashes for unexplained reasons, (Possibly a memory leak, according to an Elder Scrolls Wiki.) which were never resolved through official patches. I imagine those were some of the reasons OpenMW was created to fix, and modern OS support, since it doesn't exactly run on Win7 and beyond out of the box. (The Steam release might be a different story, but just looking at the Morrowwind page, it mentions nothing past Windows XP/2000.)

Things like this exist all the time, especially emulators, which are written with fully original code based on research, and they're usually fine as long as no copyrighted code or assets are included in the software. Then there's ReactOS too.

As for fan games, the legality is always in the grey area, and an obvious copyright infringement, but it really depends on what series you're making a fan game of, since not every IP holder enforces their rights. Nintendo stamps out every fan game they're aware of, and it's a miracle that the few still existing haven't been sent a C&D, while SEGA usually does nothing if it's a Sonic fan game. It's really situational and not always worth the risk.

---

### Post by King Dude on 2013-08-04
You know, I had just realized that OpenMW would be a fantastic base for a great Legend of Zelda mod.

---

### Post by mastablasta on 2013-08-06
they did a few engines in similar way. such as for example zdoom and jdoom. you still need to have original wads if you want to play Doom. but you can also play homemade wads.

---

### Post by open-morrowind on 2013-08-07
> **King Dude said:**
> You know, I had just realized that OpenMW would be a fantastic base for a great Legend of Zelda mod.

Well, I encourage you to follow the project and see whether it'll be fitting to your needs. This engine is going to come with an editor and the goal of the OpenMW team is to make modding as easy and complete as possible, we're aiming to make it easy to mod anything in/about the game.

---

### Post by King Dude on 2013-08-07
> **open-morrowind said:**
> Well, I encourage you to follow the project and see whether it'll be fitting to your needs. This engine is going to come with an editor and the goal of the OpenMW team is to make modding as easy and complete as possible, we're aiming to make it easy to mod anything in/about the game.
Well, I'm not sure if I could start a project like that on my own, but I'll certainly present my idea to anyone interested.

---

### Post by open-morrowind on 2013-09-12
The OpenMW team is proud to announce the release of version 0.26.0! Grab it from our [Downloads Page](https://openmw.org/downloads/) for all operating systems. This is the most violent release of OpenMW to date, with the implementation of Melee combat, Lyncanthropy, and Drowning. See below for the full changelog.     
[list]  
[/list]
  Do not miss the [release video](http://www.youtube.com/watch?v=WSr3k9ubR7w) by the mighty WeirdSexy.         
[list]  
[/list]
  **Known Issues:**     
[list]    
[*]Extreme shaking may occur during cell transitions for some users (enable anti-aliasing as a possible workaround)     
[*]Polish version of Morrowind.esm makes OpenMW crash    
[/list]
       **Changelog:**     
[list]    
[*]Implemented Melee Combat     
[*]Implemented Lycanthropy     
[*]Implemented auto-initialization of AI Packages     
[*]Implemented Drowning     
[*]Implemented Data File installation in the Launcher (Mac and Linux only)     
[*]Implemented mouse wheel transitions between first/third person     
[*]Improvements to UI window sizing and input     
[*]Improvements to sliders in the enchanting window     
[*]Fixed already-dead NPCs not equipping clothing/items     
[*]Fixed missing terrain in Tamriel Rebuilt, South of Tel Oren     
[*]Fixed health calculation of NPCs, fixing Heart of Lorkhan acting like a dead body     
[*]Fixed strange behavior when leaving water     
[*]Fixed terrain rendering to more accurately emulate vanilla Morrowind     
[*]Fixed no clip players causing NPCs to leviate     
[*]Fixed door open/close sound not cutting itself     
[*]Fixed no clip player preventing doors from opening     
[*]Fixed keypress during startup freezing the game     
[*]Fixed combat magic stances being available prematurely during character creation     
[*]Fixed naked Dark Brotherhood assassins     
[*]Fixed Rest dialog showing "Until Healed" option when player has full stats     
[*]Fixed invisible equipped torches     
[*]Fixed sheath weapon sound playing when leaving magic stance     
[*]Fixed some boots not producing footstep sounds     
[*]Fixed FPS bar alignment     
[*]Fixed printscreen not working     
[*]Fixed being able to jump while sneaking     
[*]Fixed blank movie variables in Morrowind.ini crashing the game     
[*]Fixed dancing girls in "Suran, Desele's House of Earthly Delights" so they dance     
[*]Fixed repeating idle animations     
[*]Fixed sticking to certain surfaces, improves movement when swimming close to collidable objects     
[*]Fixed animation problem while swimming at the surface of water and looking up     
[*]Fixed capitalization of names in inventory     
[*]Fixed an issue with the spell effect area layout not updating properly     
[*]Fixed a Tamriel Rebuilt crash on load     
[*]Fixed rain sound persisting into new games     
[*]Various compilation fixes    
[/list]

---

### Post by open-morrowind on 2013-12-01
The OpenMW team is proud to announce the release of version 0.27.0! Grab it from our [Downloads Page](https://openmw.org/downloads/) for all operating systems. This release brings the first official release of OpenCS, the OpenMW team's efforts to bring an open source solution for editing content for OpenMW. OpenCS is in an early Alpha state, please take that into consideration when testing! See the full notes below.

Check out the [release video](http://www.youtube.com/watch?v=6ea8NPedKsk) by the indomitable WeirdSexy.

**Known Issues:**

[list]
[*]PLEASE NOTE! There have been changes to the OpenMW config files. The game will not run with old configurations, but your configuration can be updated by simply running the Launcher. If you normally run OpenMW directly from the executable, please re-run the Launcher once to update.
[*]Extreme shaking may occur during cell transitions for some users (enable anti-aliasing as a possible workaround)
[/list]

 
**Changelog:**

[list]
[*]Implemented Acrobatics
[*]Implemented God Mode
[*]Implemented torch extinguishing
[*]Implemented breath meter color change when it is running low
[*]Fixed polish language version of Morrowind crashing OpenMW
[*]Fixed decimal numbers not displaying correctly in the UI
[*]Fixed camera not lowering while sneaking
[*]Fixed ambient sounds playing while the game is paused
[*]Fixed being able to enter third person view with the mousewheel when it should be disabled
[*]Fixed some CDs not working correctly with Unshield installer
[*]Fixed a script instruction to allow the Quick Character Creation plugin to work
[*]Fixed fatigue not regenerating when jumping
[*]Fixed Laire dieing inexplicably in Beshara
[*]Merged the --master and --plugin switches
[*]OpenCS: Implemented a start dialogue
[*]OpenCS: Implemented handling file paths so that files are saved only to the local data cirectory, and only with OpenMW extensions: omwgame/omwaddon
[*]OpenCS: Implemented Saving
[*]OpenCS: Implemented new ESX selector
[*]OpenCS: Implemented enforcing single-instance mode since multiple projects can be open
[*]OpenCS: Implemented record filtering
[*]OpenCS: Implemented default record filters
[*]OpenCS: Proper compiler configuration (currently used only for syntax highlighting)
[/list]


see also:
[Official Youtube Channel](http://www.youtube.com/user/MrOpenMW)
[For New Developers](http://openmw.org/wiki/index.php?tit...ibution_Wanted)
[OpenMW Homepage](http://openmw.org/)
[Chat @freenode](http://freenode.net/#openmw)

---

### Post by King Dude on 2013-12-02
> **open-morrowind said:**
> The OpenMW team is proud to announce the release of version 0.27.0! Grab it from our [Downloads Page]("https://openmw.org/downloads/") for all operating systems. This release brings the first official release of OpenCS, the OpenMW team's efforts to bring an open source solution for editing content for OpenMW. OpenCS is in an early Alpha state, please take that into consideration when testing! See the full notes below.

Check out the [release video]("http://www.youtube.com/watch?v=6ea8NPedKsk") by the indomitable WeirdSexy.

**Known Issues:**

[LIST]
[*]PLEASE NOTE! There have been changes to the OpenMW config files. The game will not run with old configurations, but your configuration can be updated by simply running the Launcher. If you normally run OpenMW directly from the executable, please re-run the Launcher once to update.
[*]Extreme shaking may occur during cell transitions for some users (enable anti-aliasing as a possible workaround)
[/LIST]

 
**Changelog:**

[LIST]
[*]Implemented Acrobatics
[*]Implemented God Mode
[*]Implemented torch extinguishing
[*]Implemented breath meter color change when it is running low
[*]Fixed polish language version of Morrowind crashing OpenMW
[*]Fixed decimal numbers not displaying correctly in the UI
[*]Fixed camera not lowering while sneaking
[*]Fixed ambient sounds playing while the game is paused
[*]Fixed being able to enter third person view with the mousewheel when it should be disabled
[*]Fixed some CDs not working correctly with Unshield installer
[*]Fixed a script instruction to allow the Quick Character Creation plugin to work
[*]Fixed fatigue not regenerating when jumping
[*]Fixed Laire dieing inexplicably in Beshara
[*]Merged the --master and --plugin switches
[*]OpenCS: Implemented a start dialogue
[*]OpenCS: Implemented handling file paths so that files are saved only to the local data cirectory, and only with OpenMW extensions: omwgame/omwaddon
[*]OpenCS: Implemented Saving
[*]OpenCS: Implemented new ESX selector
[*]OpenCS: Implemented enforcing single-instance mode since multiple projects can be open
[*]OpenCS: Implemented record filtering
[*]OpenCS: Implemented default record filters
[*]OpenCS: Proper compiler configuration (currently used only for syntax highlighting)
[/LIST]


see also:
[Official Youtube Channel]("http://www.youtube.com/user/MrOpenMW")
[For New Developers]("http://openmw.org/wiki/index.php?tit...ibution_Wanted")
[OpenMW Homepage]("http://openmw.org/")
[Chat @freenode]("http://freenode.net/#openmw")
Nice

---

### Post by open-morrowind on 2014-01-14
The OpenMW team is proud to announce the release of version 0.28.0! Grab it from our [Downloads Page](https://openmw.org/downloads/) for all operating systems. This behemoth of a release includes many large features, such as Combat AI, Magic, Vampirism, terrain bump/specular/parallax mapping, and many other things. There's also a heap of bug fixes, many thanks to our relentless developers!

Check out the [release video](http://www.youtube.com/watch?v=x9lTWjXAi9s) by the prodigious WeirdSexy.

**Known Issues:**

[list]
[*]Issue #416 Extreme shaking may occur during cell transitions for some users (enable anti-aliasing as a possible workaround)
[*]Issue #1041 Music playback doesn't work on OS X 10.9
[/list]


**Changelog:**

[list]
[*]Implemented Combat AI
[*]Implemented spell casting, ranged, self, and touch magic
[*]Implemented visual magic effects
[*]Implemented Vampirism
[*]Implemented terrain bump, specular, & parallax mapping
[*]Implemented NIF record NiFlipController
[*]Implemented soul gem recharging
[*]Implemented enchanted item glow
[*]Implemented Invisibility/Chameleon magic effects
[*]Implemented Resist Magicka magic effect
[*]Implemented GetLOS, so NPCs can calculate Line Of Sight
[*]Implemented material controllers
[*]Implemented mouse unlocking when in any menu
[*]Implemented Vertex morph animation (NiGeomMorpherController)
[*]Implemented NiBillboardNode handling
[*]Implemented NIF texture slot DarkTexture
[*]Various fixes for equipped torches and candles
[*]Fixes for torches and shields being visible when casting spells
[*]Fix for equipped items not updating right away, on characters and in the inventory
[*]Fix for weather not changing correctly when changing areas
[*]Fix for global map position marker not updating when changing interior cells, eg: Mages Guild teleport
[*]Fix for some textures rendering black in Tamriel Rebuilt
[*]Fix for activation distance to be from the player head instead of the camera
[*]Fix for NPCs holding torches during the day
[*]Fix for some hairs from Vvardenfell Visages Volume I not rendering
[*]Fix for heads of Maormer race in mod by Mac Kom
[*]Fix for walk key release not being handled during cell load
[*]Fix for equipped inventory items not being updated on the HUD when they are changed in dialog
[*]Fix for Launcher writing merged openmw.cfg files
[*]Fix to enable discrete magnitudes for spells with multiple random magnitude effects
[*]Fix to allow negative fatigue level
[*]Fix for particle systems to handle the world space flag
[*]Fix for crash caused by trying to update a model that is not rendered
[*]Fix to not override dynamic stats set via console commands
[*]Fix for equipped inventory icon not appearing immediately when equipped with a keyboard shortcut
[*]Fix for crash when equipping light source with new character
[*]Fix for segmentation fault when starting at Bal Isra
[*]Fix for down arrow console history behavior
[*]Fix for tooltip disappearing when clicking in the inventory
[*]Fix for barter window item category not resetting to All correctly
[*]Fix for replacement model in Graphic Herbalism mod having the wrong orientation
[*]Fix for addon unchecking not being saved in the Launcher
[*]Fix for controllers not affecting all objects in the hierarchy
[*]Fix for being able to talk to NPCs who are in combat
[*]Fix for crash when trying to load a mod with a capital .ESP filename extension
[*]Fix for skills/attributes being capped when set via console
[*]Fix for setting max health through the console to also set the current health
[*]Fix for gameplay keyboard input echoing to the console input box
[*]Fix for fall damage sometimes not applying immediately or correctly
[*]Fix for persuasion window not showing in correct location after maximizing the game in windowed mode
[*]Fix for player skill list forgetting scroll location when increasing experience
[*]Fix for notification window not being large enough for skill level ups with long names
[*]Fix for windows not scaling properly on resolution change
[*]Fix for notification windows staying on screen permanently if too many are activated
[*]Fix for used torches stacking with unused ones
[*]Fix for crash on pickup of jug in Unexplored Shipwreck, Upper level
[*]Fix for quick key menu not picking suitable replacement tool when it is used up
[*]Fix for loading TES3 header data: convert characters to UTF8
[*]Fix for damaged weapon value
[*]Fix for being able to talk to characters with "locked" dialogue
[*]Fix for water effects obscuring spell effects
[*]Fix for animation playing when casting exhausted once-per-day abilities
[*]Fix for Cure Disease potion removing all effects from the player, not just disease
[*]Fix for OpenMW binaries linking to unnecessary libraries
[*]Fix for water not negating fall damage
[*]Fix for drawing a weapon increasing torch brightness
[*]Fix for merchants selling stacks of gold
[*]Fix for incorrect handling of color codes in character names
[*]Fix for NPCs spawning with 0 skill values instead of calculated values
[*]Fix for particles rendering too large
[*]Fix for crash caused by AIWander
[*]Fix for crash when revisiting dock where the starting ship was
[*]Fix for scripts on items in inventory stopping when the containing object crossed a cell border
[*]Fix for merchants equipping items with negative enchantments
[*]Disallowed view mode switching while performing an action due to animation constraints
[*]Code maintenance to unify OGRE initialization
[*]OpenCS: Implemented Info-Record tables
[*]OpenCS: Fix for not being able to open Journal table from the main menu
[/list]

see also:
[Official Youtube Channel](http://www.youtube.com/user/MrOpenMW)
[For New Developers](http://openmw.org/wiki/index.php?tit...ibution_Wanted)
[OpenMW Homepage](http://openmw.org/)
[Chat @freenode](http://freenode.net/#openmw)

---

### Post by King Dude on 2014-01-14
This will be SteamOS compatible, right?

---

### Post by LillyDragon on 2014-01-15
SteamOS is based on Debian, so as long as Debian packages are maintained, I don't imagine that would be an issue.

Also, the progress on this project is very encouraging. I recently went all Ubuntu on this hard drive, and would love to eventually buy Morrowind on Steam, even though I wouldn't be able to play it out of the box. (Always have issues getting the Windows version of the Steam Client cooperating under WINE.) OpenMW looks very playable already in its current state, and I look forward to more updates from the team.

---

### Post by open-morrowind on 2014-03-15
The OpenMW team is proud to announce the release of version 0.29.0! Grab it from our [Downloads Page](https://openmw.org/downloads/) for all operating systems. This release includes the first implementation of the Save/Load feature, which catapults OpenMW closer to being completely playable. Please bear in mind that **the save file format is not yet finalized** and we cannot guarantee forward compatibility of save files until OpenMW 1.0. Some aspects of the game state, such as player controls being enabled/disabled, weather, some creature state including all magic (also used by NPCs), movement of objects between cells (except for the player), and fog of war are not currently saved. Other new features include more combat AI, blocking, area magic, and disease. OpenMW is becoming a hazardous place to be!

Check out the [release video](https://www.youtube.com/watch?v=VoeIaYkc0Do) by the irrepressible WeirdSexy.

**Known Issues:**

[list]
[*]Issue #416 Extreme shaking may occur during cell transitions for some users (enable anti-aliasing as a possible workaround)
[*]Slaughterfish fly. You read that right.
[/list]

 
**Changelog:**

[list]
[*]Implemented most of the Load/Save GUI
[*]Implemented Knockdown
[*]Implemented fatigue decrease when doing physical activities
[*]Implemented melee blocking
[*]Implemented area magic
[*]Implemented combat and combat AI for creatures
[*]Implemented Damage/Restore Skill/Attribute magic effects
[*]Implemented Resistance/Weakness to normal weapons magic effect
[*]Implemented Slow Fall magic effect
[*]Implemented auto-calculating NPC spell list
[*]Implemented Disease contraction
[*]Implemented blood particles
[*]Implemented the rest of the player death feature
[*]Implemented sleep/rest being interrupted
[*]Implemented inventory equip scripts
[*]Implemented display of the version/build number in the launcher window
[*]Implemented a large portion of the Save/Load feature
[*]Implemented AI Packages:Activate, Follow, FollowCell
[*]Implemented levelled creatures
[*]Implemented missing journal backend features
[*]Improved handling of creature Weapons/Shields
[*]Linked movie volume to Master instead of Music volume control
[*]Fix for excess vram usage
[*]Fix for footsteps in first person
[*]Fix for Ascended Sleeper animation issues, related to determining the root animation node
[*]Fix for AI related FPS drop
[*]Fix for music issues on OS X ]= 10.9
[*]Fix for inventory paperdoll obscuring armour rating and rating text display when window is shrunk
[*]Fix for 0/0 charge stat bar display
[*]Fix for werewolf change handling
[*]Fix for NIF filters not working properly with some mods
[*]Fix for invalid orientation crash
[*]Fix for invisible weapons when re-entering an area with NPCs engaged in combat
[*]Fix for magicka depleting when casting an uncastable spell
[*]Fix for creatures not being able to run
[*]Fix for activators working as collision objects
[*]Fix to not reset water level when loading a plugin with no water level record
[*]Fix for AI packages growing exponentially when adding an AI package
[*]Fix for Vivec Informants quest
[*]Fix for bug allowing the player to get unlimited gold
[*]Fix for bug of only receiving 1 gold when picking up stacks of gold
[*]Fix for Dwemer crossbows not being held correctly
[*]Fix for quick keys being able to be configured during character generation
[*]Fix for a crash when equipping the lockpick in the Census & Excise Office
[*]Fixes for errors in .desktop files
[*]Various fixes for script instructions
[*]Various message box fixes
[*]OpenCS: Implemented a referenceable record verifier
[*]OpenCS: Implemented script verifier
[*]OpenCS: Implemented Drag & Drop
[*]OpenCS: Implemented record cloning
[*]OpenCS: Fixed broken code for loading objects
[*]OpenCS: Fixed tables to sort case-insensitively
[/list]


see also:
[Official Youtube Channel](http://www.youtube.com/user/MrOpenMW)
[For New Developers](http://openmw.org/wiki/index.php?tit...ibution_Wanted)
[OpenMW Homepage](http://openmw.org/)
[Chat @freenode](http://freenode.net/#openmw)

---

### Post by Sonic_Hedgehog on 2014-03-16
Keep up the good work!

---


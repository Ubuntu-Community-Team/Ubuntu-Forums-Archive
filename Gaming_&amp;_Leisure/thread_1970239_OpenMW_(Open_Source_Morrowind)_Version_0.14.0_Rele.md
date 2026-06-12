---
title: "OpenMW (Open Source Morrowind) Version 0.14.0 Released!"
date: 2012-04-30
forum: Gaming &amp; Leisure
---

### Post by OpenMW on 2012-04-30
The OpenMW team is proud to announce the release of version 0.14.0! This  release precedes Morrowind’s 10th Anniversary by 2 days! Release  packages for Ubuntu are now available via our Launchpad PPA [https://launchpad.net/~openmw/+archive/openmw]("https://launchpad.net/%7Eopenmw/+archive/openmw") . Release packages for other platforms are available on our Download page [http://code.google.com/p/openmw/downloads/list](http://code.google.com/p/openmw/downloads/list)  . This release brings many notable features, including terrain and  water rendering! A video highlighting many of the new changes in this  release made by our very own WeirdSexy can be found here.

[http://www.youtube.com/user/MrOpenMW](http://www.youtube.com/user/MrOpenMW)


Please note:

    There is a regression in the Launcher in this release, from which  you will observe that the rendering subsystem will default to OpenGL  regardless of what was previously selected. This will be fixed in the  next release. This can be overcome by setting the rendering system  explicitly from the launcher each time, or running the OpenMW binary  directly from the command line, which will select the renderer that has  been set in your config file.
    There is a known issue where a crash may occur underwater with the underwater effect enabled on OS X

Changelog:

    Fix for meshes rendering with the wrong orientation
    Fix for better grabbing of small objects
    Fix to enable toggling of collision rendering
    Updates to be compatible with Ogre 1.8.0 RC1
    Fix for Wireframe mode applying to HUD and Console
    Fix for terrain crashing when moving away from predefined cells
    Fix to allow OS X Launcher to handle spaces in the binary path
    Fix to support TGA textures
    Fix to support wireframe mode in water
    Added water rendering
    Added terrain rendering
    Added ability to render Path Grid
    Added Factions support
    Added Local Map
    Added Compass/Mini-Map
    Added Clothing/Armour redering
    Added Window Pinning
    Added Auto-Equip.
    Added support for containers tracking changes to their contents
    Added several NPC Dialogue Window improvements
    Added backend for a game settings manager
    Added backend for a Spell List and selected spell
    Added backend for NPC holstered/drawn state
    Added a Morrowind.ini Importer (not yet included in the binary packages)
    Refactored the Sound code
    MyGUI updated to version 3.2.0



Website
[http://openmw.org/en/](http://openmw.org/en/)

Download Page 
[http://code.google.com/p/openmw/downloads/list](http://code.google.com/p/openmw/downloads/list)

Forum
[http://openmw.org/forum/](http://openmw.org/forum/)

---

### Post by Enigmapond on 2012-04-30
Awesome...I was waiting for the release. Currently in Skyrim but will happily regress for Ubuntu.. :)

---

### Post by OpenMW on 2012-05-15
Hey, we're back with the bimonthly update.

Our killer-feature this time (yup, we&#8217;ve got one!) is drag&#8217;n'drop by **gus**.  Drag&#8217;n'drop allows you to drop things from your inventory. The code is  not yet perfect, and not everything is fully functional, but folks are  cleaning and improving it.

**jhooks1** got terrain collisions working! You  can test this feature by typing tcl or togglecollisions in the console.  Terrain collisions will be included in version 0.15.0.

With terrain collisions finished **jhooks **is  back to getting Ogre3d-powered animations working. There are still  issues with some creatures like the ancestor ghost, but things are  slowly moving forward.

**scrawl **is a machine, he worked on the following:
-Introduction of a new font (not under GPL, unfortunately, but it&#8217;s better than nothing) for daedric alphabet.
-Improving scrolls/books interaction and rendering.
-Bugfixes and improvement of the GUI : you can now scroll with the mouse wheel!
-Improvements for journal rendering.
-Single quotes now work.
-Opening/taking/closing books/scrolls now work
-Movement is no longer framerate dependent
-You can now talk with creatures
-More spell backend

The quote of the week :
[INDENT][I]
OpenMW just got to a whole new level
because you can now steal Fargoth&#8217;s ring![/I][/INDENT]
Thanks to the propaganda of the PR team, we attracted several future new contributors.

Ho, by the way, if you know some Qt, we are looking for someone to develop the OpenMW Editor. Don&#8217;t be shy, apply!

---

### Post by oldrocker99 on 2012-05-15
Looks VERY impressive, but the inability to kill anything does break a lot of quests:lolflag:

---

### Post by Carpentr on 2012-05-17
It looks very cool, indeed. I'll have to dust off my Morrowind disc sometime.  I'm sure this required a lot of work; it looks like a fun project. Good luck and keep it up!

---

### Post by Erik1984 on 2012-05-18
Just dropping by to say this is a very impressive project. I love Open Source stuff like this. Basically this is how OpenTTD started too. Requiring the original graphicals at first, then the community started making stuff to replace the proprietary graphics. Morrowind graphics are a lot harder to make so I don't expect the same thing happening. Keep up the good work.

---

### Post by OpenMW on 2012-05-28
Version 0.15.0 is out! Release packages for Ubuntu are now available via our [Launchpad PPA]("https://launchpad.net/%7Eopenmw/+archive/openmw"). Release packages for other platforms are available on our [Download page]("http://code.google.com/p/openmw/downloads/list").This version includes a reimplementation of the physics and player movement system, elevating the player from slug to hobbit status. Terrain collision and many newly-implemented GUI elements are also featured in this release. Our very own WeirdSexy has made a release video for your [viewing pleasure]("http://www.youtube.com/user/MrOpenMW").

[B]
Changelog:[/B]
- Reimplemented physics system/player movement
- Implemented terrain collision
- Implemented pulsating lights
- Implemented Magic Effect Bookkeeping, and Feather/Burden effects
- Implemented Book and Scroll windows
- Implemented Inventory, Container, and Trade windows
- Implemented item stacking in containers
- Implemented tooltips for items in the world, and many GUI elements
- Added faction and other information to Stats window
- Fixed Resizing arrow’s background transparency
- Fixed Stats window layout when resizing in the X direction
- Long topics in dialog window now wrap and sort correctly, and other dialogue window fixes
- Fixed terrain handling in non-predefined cells


For the upcoming 0.16.0 release we are planning to implement many skills and attributes. If you want to help out with the project, but are unable to code, we need help discovering the formulas used for skills, magic, and attributes and also testing and confirming the ones that have been described are accurate. For more information see this forum post [http://openmw.org/forum/viewtopic.php?f=6&t=755](http://openmw.org/forum/viewtopic.php?f=6&t=755) and this one as well [http://openmw.org/forum/viewtopic.php?f=2&t=766](http://openmw.org/forum/viewtopic.php?f=2&t=766).

---

### Post by oldrocker99 on 2012-05-28
Wow; this project is moving at a rapid pace.

---

### Post by Dlambert on 2012-05-28
> **oldrocker99 said:**
> Wow; this project is moving at a rapid pace.

And that's a good thing!

---

### Post by Dlambert on 2012-05-28
Pretty soon it will be time for openskyrim! Haha. :lolflag:

---

### Post by Avaritia on 2012-05-29
Keep up the good work guys.

Do you guys have an estimated date when the game will be playable using OpenMW?

---

### Post by Dlambert on 2012-05-29
> **Avaritia said:**
> Keep up the good work guys.
 
Do you guys have an estimated date when the game will be playable using OpenMW?
 
It is playable:) . But full retail quality? Who knows.

---

### Post by OpenMW on 2012-06-11
Hello everyone !

The major news for this update comes via **Mark **(creator of the Crystal Scrolls) : he nearly finished multiple esp/esm support! There are numerous problems, but things are progressing : you'll soon be able to travel to Solstheim!

**garvek**, our new developer who is also part of the dugeonhack project, started working on cmake fixes and making OpenMW compile with MSVC. The DungeonHack team is in the process of deciding whether to help OpenMW reach basic functionality and then base DungeonHack off our engine. Sounds good to me!

**zini **after last week of bugfixes and checking if features from merged branches were working, he has returned to working on the script implementation. Excellent!

**jhooks1 **is continuing work on the physics system. He fixed a bug that allowed players to run up the walls if their speed was high enough.  Unfortunately his work on enabling animations through Ogr3d's system still can't handle robes and some creatures. If someone is an expert in animations then you're  help is welcomed on our forums.

Gentoo overlay for OpenMW has reached alpha status and awaits testing. Big thanks (if it's working correctly) to **edmondo**.

**Gus **added the setangle and setscale instructions but there is still much to be done before his branch is merged into the master.

**Scrawl **has been working his wonders (namely by finishing the Spell window and alchemy windows). He also changed the color of the water to look less tropical and more like in vanilla Morrowind.

[IMG]http://openmw.org/wiki/images/4/4e/016-3.png[/IMG]

[IMG]http://openmw.org/wiki/images/5/5f/016-2.png[/IMG]

Lurkers of the irc channel are reporting that he mentioned:
> I have started rewriting the shader system to allow GLSL. I am a making sort of a library out of it, it will be similar to ogre RTShaderSystem but much better. Then the user can put in a settings file which shader language he wants :PHo, and two more developers **pvdk **and **k1ll **are active again :)

Finally, we are looking for someone who knows QT to start work on developing a replacement to Bethesda's Construction Kit for OpenMW. If you fit the bill it would be a huge help to the project. Any computer science or game design students out there with free time this summer?

---

### Post by Dlambert on 2012-06-11
When completed, will this be included in steam? as almost an addon/mod? Is that one of the goals?

---

### Post by OpenMW on 2012-06-11
It's not one our goals, but I don't think the team would be opposed to it and it certainly would benefit most end users. Bethesda would have to include Vanilla Morrowind and OpenMW (in case OpenMW doesn't work for some users). Who knows what the future holds?!

---

### Post by dagoth_pie on 2012-06-13
I was just going through different games seeking inspiration for terrain generation algorithms the other day when I thought about how awesome it would be to make an engine that could read the esm file and such. Weird that I should stumble accross this a few days later.

I'll make a note to give it a spin sometime.

Oh yeah, I also remember that Morrowind used to crash when making potions, and pressing enter instead of clicking Create potion. Did you happen to fix that? :P

---

### Post by OpenMW on 2012-06-19
> I was... seeking inspiration for terrain generation  algorithms the other day when I thought about how awesome it would be  to make an engine that could read the esm file and such. Weird that I  should stumble accross this a few days later.

Thanks for your reply! Yeah it's exciting to see this functionality in an open source engine. If you enjoy playing around in OpenMW and are experienced with Qt or C++ then join us and help develop with some patches! We could always use more help finishing the engine and editor. 

> Morrowind used to crash when making potions, and pressing enter instead of clicking Create potion. Did you happen to fix that? :razz:
I alchemy skill is still being implemented, but should be out in either the 0.16.0 release or definitely by 0.17.0. Once it's released, you could test it out and see if the bug is still present.

---

### Post by OpenMW on 2012-07-31
Though there won’t be a new release for July, we've had some major improvements.

First, these updates always discuss the difficulty of animating NPC's and creatures. Though we'll still include updates about bug fixes and improvements to the animation system, its development saga is coming to an end. That’s right, the new animation system has been merged into the main branch of the engine and is awaiting testing. jhooks1 and Chris’s work should prove a more effecient animation method and boost OpenMW’s frames per second.

Although OpenMW had animations for awhile, the old system did not use the built in animations system of Ogre3d (OpenMW's renderer). Instead OpenMW manually moved all NPC and creature bones. This was both inefficient and also caused some errors in creature animations. This was especially true for Bloodmoon’s werewolf animations which looked really bizarre. But now we're using Ogre3d and those problems should be behind us.

Chris also improved the handling of the nif file format which was a prerequisite to animating meshes, and anything else related to nifnodes, correctly.

scrawl spent a lot of time working on shaders this month. We employ shaders to render our skybox, water, terrain, and soft shadows. Scrawl refined the first two, resulting in marked visual improvements over the original Morrowind and also reduced the amount of code for our terrain implementation by 75%. THREE CHEERS FOR EFFICIENCY!!!

scrawl's main focus was the creation a new shader library called "shiny", which was also recently merged into the main branch. What does that mean for OpenMW? Well, until now we have been using the Nvidia CG toolkit. This toolkit works with DirectX and OpenGL on all graphics cards. However, only Nvidia cards get good performance with it (which is understandable since its developed by Nvidia). OpenMW needs both DirectX and OpenGL support because Radeon graphics cards (made by amd) lack quality OpenGL drivers. Otherwise we’d just write our shaders in OpenGL. To make matters worse, CG is closed source and available only for Linux, windows, OSX and not BSD.

To avoid using CG many game developers write all their shaders twice: in GLSL for OpenGL and in HLSL for DX or just ignore OpenGL and focus on DirectX. This duplication of work is obviously a waste of time. Scrawl's new shader library called “shiny” allows developers to write a shader once and then compile it as either GLSL or HLSL. A more elegant solution to the AMD graphics cards, will make the lives of developers easier, and allow for many beautiful new shaders in the future. But that’s not all, here’s scrawl detailing the new library’s design and features:
> 
- High-level layer on top of OGRE’s material system. It allows you to generate multiple techniques for all your materials from a set of high-level per-material properties.

- Several available Macros in shader source files. Just a few examples of the possibilities: binding OGRE auto constants, binding uniforms to material properties, foreach loops (repeat shader source a given number of times), retrieving per-material properties in an #if condition, automatic packing for vertex to fragment passthroughs. These macros allow you to generate even very complex shaders (for example the Ogre::Terrain shader) without assembling them in C++ code.

- Integrated preprocessor (no, I didn’t reinvent the wheel, I used boost::wave which turned out to be an excellent choice) that allows me to blend out macros that shouldn’t be in use because e.g. the shader permutation doesn’t need this specific feature

- User settings integration. They can be set by a C++ interface and retrieved through a macro in shader files.

- Automatic handling of shader permutations, i.e. shaders are shared between materials in a smart way.

- An optional “meta-language” (well, actually it’s just a small header with some conditional defines) that you may use to compile the same shader source for different target languages. If you don’t like it, you can still code in GLSL / CG etc separately. You can also switch between the languages at runtime.

- On-demand material and shader creation. It uses Ogre’s material listener to compile the shaders as soon as they are needed for rendering, and not earlier.

- Shader changes are fully dynamic and real-time. Changing a user setting will recompile all shaders affected by this setting when they are next needed.

- Serialization system that extends Ogre’s material script system, it uses Ogre’s script parser, but also adds some additional properties that are not available in Ogre’s material system.

- A concept called “Configuration” allowing you to create a different set of your shaders, doing the same thing except for some minor differences: the properties that are overridden by the active configuration. Possible uses for this are using simpler shaders (no shadows, no fog etc) when rendering for example realtime reflections or a minimap. You can easily switch between configurations by changing the active Ogre material scheme (for example on a viewport level).

- Fixed function support. You can globally enable or disable shaders at any time, and for texture units you can specify if they’re only needed for the shader-based path (e.g. normal maps) or if they should also be created in the fixed function path.Since shiny is designed for the Ogre3d rendering engine, it may have a bright future beyond OpenMW. Huzzah for open source!
Take a look at the new water shader scrawl made using the “shiny” shader library.

[http://wiki.openmw.org/index.php?title=Screenshots](http://wiki.openmw.org/index.php?title=Screenshots)

If all that is not awesome enough, then wait dear readers, because there’s more.

Zini, our fearless leader, finished up the potion usage task so that when drinking a potion the correct sound effect is played. As well as the magical effects drain and fortify. Additionally, zini refactored the action class and the code for dynmaic statistics. While working on refactoring he discovered many unnecessary “includes” in the source code. Don’t worry about what includes are, all you need to know is they cause slow downs in compile times. Many users complain that it takes forever to compile and build OpenMW. Removing these unnecessary “includes” improved build times by nearly half.

Corristo made sure that OpenMW still works for you OSX users out there. There were mac specific bugs that should now be resolved.

We also picked up some new developers. _greye finished his first task (making CreatureStats into a class) in a single day. Then he picked another one (maintenance in the item dropping code) and finished that in a short period of time. Both were very well done, so thank you _greye and welcome to the team!

nhydock, another new developer, has taken the camera control task (which is composed of four or five subtasks).

Reverse engineering formulas is going well with several close to completion (some things still need to checked and verified) thanks to the efforts Myckel, Lazaroth, Tarius, and Epsilon who are designing our formulas. It’s great work and we welcome them to the team. Reverse engineering formulas requires testing to see if they accurately describe Morrowind's behavior. Epsilon is developing scripts to speed up the testing phase exponentially. BrotherBrick is using his powerful server to calculate data points. We still need additional help on this front, so if you have an extra computer and want to run some tests that would be very useful.

And finally, we normally get about 10,000 page views a month, but we were flooded by 2,500 views in a single day after getting on the website slashdot. There is actually a term for this "the slashdot effect" in which smaller projects are talked about on a much larger site, thus causing a major influx in internet traffic. This "slashdot effect" caused our website to crash. But the exposure directly led to new developers and contributors joining the project. So we’d like to say, Thank You Slashdot!

As a result, Igromanowski migrated OpenMW to new servers. The first choice was amazon cloud which looked quite nice, but quickly it became clear that it was insufficient for our needs. At the moment OpenMW.org is on one MyDevil.net server, while bugtracker and forum are on OVH server. In addition OpenMW.org is protected by Cloudflare CDN “proxy”, so it has a better chance of handling the next slashdot effect.  :P

---

### Post by Sarys on 2012-07-31
First of all I'm really really sorry that I post this but I'm lazy so sorry about that.

Okay to the point. So this is free Morrowind? or just patch or something to get it to work on Linux?

EDIT: No need to answer I visited your home page and read from there sorry for the trouble.

---

### Post by QsoftStudios on 2012-08-13
This looks epic :D

---

### Post by miho on 2012-08-14
I for one am very impressed with the massive undertaking this had to have been and I salute you for all the effort you put forth. I'm gonna install this and run around Vvardenfall and have a jolly ol' good time.

---


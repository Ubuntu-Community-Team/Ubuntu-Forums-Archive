---
title: "Open Source Morrowind project in the works"
date: 2010-06-13
forum: Gaming &amp; Leisure
---

### Post by ucal on 2010-06-13
[http://www.moddb.com/mods/openmw](http://www.moddb.com/mods/openmw)
[http://openmw.sourceforge.net/](http://openmw.sourceforge.net/)


It requires ownership of Morrowind to play (That would be some project, getting all the various artists to agree to opensourcing their work >_>), and I don't know how playable it is.  I'm going to download the steam version today and hope those data files work.  Let you know later how it goes.  Sorry if this is old.  But hot damn, this just made my day.

EDIT:

[QUOTE=FAQ]Still on the TODO list

    * any kind of animation or creature movement
    * interactivity and game mechanics
    * exterior cells with landscape
    * moving between cells
    * rendering NPCs (including the player)
    * everything else
[/QUOTE]

Looks like it's got a long way to go, but still.  Day is made.

---

### Post by Grishka on 2010-06-14
it'll take time, but the first step was made. I'm looking forward to it, I've yet to see something comparable to Morrowind in terms of flexibility and potential. open source Morrowind would be sheer POWER. also, I hope that eventually it will be possible to swap data files for some free ones, eliminating the need for Morrowind altogether. or perhaps, in due time, Bethesda will release Morrowind for free, like they did with it's predecessors. anyway, great find.

---

### Post by duke.tim on 2010-06-14
[-o< :lol::shock:8-[[-o<:grin:8-):popcorn: YES!!!! very nice!

---

### Post by cascade9 on 2010-06-15
> run natively on Windows, Linux and MacOS X

[http://www.moddb.com/mods/openmw](http://www.moddb.com/mods/openmw)

If they can get it running natively on linux, I'll be more than happy, even if none of the other features end up happening ;)

---

### Post by Chame_Wizard on 2010-06-15
:o I have Morrowind:GOTY edition.:guitar:

---

### Post by juanoleso on 2010-06-15
i've been watching this for a while and OpenMW development has started to really pickup in the last month or so.  I've been trying to come up with ways I can help, but I can't read or write C++...

Here are the forums: [[COLOR="BLUE"]OpenMW - Index page[/COLOR]]("http://openmw.com/forum/index.php")

and here is the wiki page (it is kept more up to date): [[COLOR="BLUE"]OpenMW Wiki[/COLOR]]("http://openmw.com/wiki/index.php?title=Main_Page")

---

### Post by Sslaxx on 2010-06-16
Interesting, it was looking decidedly unhealthy after the coder decided to re-start the whole thing from scratch (it was originally in D). Hope this gets somewhere!

---

### Post by del_diablo on 2010-06-16
This is interistng. They got a good shot at it.

---

### Post by chewit on 2010-06-16
This looks amazing.

Will be following this closly. Will have to mention this in the Full Circle Magazine/Podcast

---

### Post by OpenMW on 2012-03-28
Hot on the heels of 0.12.0, the OpenMW team is proud to announce the release of version 0.13.0! Release packages for Ubuntu are now available via our [Launchpad PPA]("https://launchpad.net/%7Eopenmw/+archive/openmw"). Release packages for other platforms are available on our [Download page]("http://code.google.com/p/openmw/downloads/list"). This release notably includes functional NPC dialogue, and beautiful sky! There is a new demonstration video on our YouTube channel so check it out. 

 
 Please note:
 - On OSX, the path to the application cannot contain spaces, or the launcher will not work properly (not that many of you are likely running OSX).


 **[SIZE=3]Changelog:[/SIZE]**

 - NPC Dialogue window and mechanics implemented
- Reimplemented sky rendering, added weather effects
- Wireframe mode added
- Fix for sounds broken in 0.12.0
- Fix for 3D sounds
- Added sounds for weather, doors, containers, picking up items, and journal
- Various code cleanup and improvements
- Fixed an Ogre crash at the Dren plantation
- Several launcher improvements
- Added fade to black effect for cutscenes
- Added backend for equipping items
- Fix to stop ASCII 16 character from being added to console on its activation in OSX
- Fixed collision shapes being out of place
- Fixed torch lights not being visible past a short distance
- Fixed some transparency rendering problems
  

**[SIZE=3]Links:[/SIZE]**

[Website]("http://openmw.org/en/")
 [Download Page]("http://code.google.com/p/openmw/downloads/list")
[YouTube Channel]("http://www.youtube.com/user/MrOpenMW")
[Forum]("http://openmw.org/forum/")


[COLOR=Blue][B]
OpenMW is an ambitious project and we can use all the help we can get. If you'd like to help, please register on our forums and announce yourself to the team. Thanks, see you in Morrowind![/B][/COLOR]

---

### Post by Dr.Paneas on 2012-03-29
I want Skyrim for Ubuntu. Do I want that much ????

---

### Post by OpenMW on 2012-04-16
@ Dr. Paneas
No, but you can start with OpenMW. We hope to have to a playable state within the year. Maybe some folks will take the engine and start working on Skyrim (it'll be a while).

Who says it’s not all about looks? Version 0.14.0 is shaping up to be one sexy release. OpenMW is getting terrain rendering, water rendering and clothed npcs… sometimes it’s all about looks.[IMG]http://openmw.org/wiki/images/8/89/014-8.png[/IMG] 

Part of me is going to miss the floating houses, boats, and ruins when terrain is added, but I’ll forget them once I’m running around Morrowind freely.

Here is a screenshot from 0.11.1 compared to 0.14.0. I don't know how to change the size, but you can right click the image and select "view image" it'll take you to our website.  The difference is dramatic. 

[IMG]http://openmw.org/wiki/images/8/89/Openmw_0.11.1_2.png[/IMG]

[IMG]http://openmw.org/wiki/images/4/4f/014-12.png[/IMG]

We have only one outstanding feature left to be completed; clothed NPC's. Other unfinished features have been pushed to 0.15.0, so we should have 0.14.0 released before Morrowind's 10th anniversary on May 1st. 

Raevol got the developers to write about what they are currently working on and what they are about to start. It was a terrific idea and something will likely do more often. 

So from the horse's mouth:

**ACE**
> Working on getting the esm records to save properly, right now some data is lost when saving so I’m working on tracking that down and hopefully being able to make close to byte-perfect copies.
Once I’ve gotten all that worked out I think I’m going to slip back to only being the Windows package maintainer for a while, perhaps see if I can build a new dependency package for windows developers.**jhooks1**
> Right now I am working on clothing/armor.
For .15 I hope to work more on the physics system that I showed off on youtube recently. [http://www.youtube.com/watch?v=0VGQYZwA2Fw&list=PL14E8F94A73754549&index=1&feature=plpp_video](http://www.youtube.com/watch?v=0VGQYZwA2Fw&list=PL14E8F94A73754549&index=1&feature=plpp_video)
I also want to bring in some of Chris’s work on animating creatures. Of course though, if he wants to, he should take the lead in bringing them into openmw. Even if we can’t get Ogre’s animation system working, the way he is applying the bone weights is more efficient and may be able to be implemented into openmw.**Chris** is still trying to insert animations into ogre3d’s animation system and it actually sort of works. The main problem is that .nif file format used for Morrowind’s character models is closed source and have no documentation on how they are designed. To get the animations working Chris needs to reverse engineer everything himself. Take a look at these two videos; [http://www.youtube.com/watch?v=yEZjnIlKqU4&feature=relmfu](http://www.youtube.com/watch?v=yEZjnIlKqU4&feature=relmfu) and [http://www.youtube.com/watch?v=VXfF_hL0G3U](http://www.youtube.com/watch?v=VXfF_hL0G3U) If you have any advice or help to offer, that would be appreciated. 

OTOH collision with terrain works with the new physics jhooks implemented. That’s very good news for 0.15.0.

**zini**
> Working on the world model; data structures and preparations for game mechanics. Basically the non-exciting stuff. Wasn’t planning to do that for 0.14.0. originally, but people are chomping through the exciting stuff (graphics and the user visible parts of game mechanics) so fast, we were on the verge of running out of this kind of tasks that don’t have uncompleted prerequisite tasks.**hircine** worked on the GUI's for containers and the inventory, but his C++ is a little rough so **gus** stepped in to help. Now they have teamed up and everything looks good.

Oh, yes: gus finished with factions. It’s ready! More quests!

**scrawl**
> I’m getting a little annoyed already by the graphics stuff, so I’ll take a break in terms of implementing some GUI elements that I’ve wanted to see for a long time. Mainly:
- Tooltips
- Door markers on the map
- Tooltip for the object that the crosshair points onScrawl’s contributed a lot of amazing work to the 0.14.0 release including the minimap, terrain (with yacoby), better water and even more. We'd clone 7 scrawls, but you know the legal red tape...

---


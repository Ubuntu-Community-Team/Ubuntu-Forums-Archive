---
title: "Good Game Creator?"
date: 2014-04-25
forum: Gaming &amp; Leisure
---

### Post by vivienneanthony on 2014-04-25
Hello

Do anyone know a basic but good free game editor and creator for Ubuntu/Linux? I seen Game Maker but it's not going work. 

I want something that can do 3D game creation no matter which view I choose, multi-platform meaning can export Win/Linux standalones, GUI, some programming. At least free for development.

Also works with Blender, where I can export from and import to the game software.

Vivienne

---

### Post by King Dude on 2014-04-25
[Blender]("http://www.blender.org/") - 3D Modeler
[Ogre]("http://www.ogre3d.org/") - Graphics Rendering Engine
[Newton Game Dynamics]("http://newtondynamics.com/forum/newton.php") - Physics Engine

---

### Post by oldrocker99 on 2014-04-26
We are still waiting for a Linux client for the Unity game engine...

---

### Post by dannyboy79 on 2014-04-26
[http://www.maartenbaert.be/model-creator/](http://www.maartenbaert.be/model-creator/)

[http://www.maartenbaert.be/game-maker-dlls/](http://www.maartenbaert.be/game-maker-dlls/)

---

### Post by Carpentr on 2014-04-26
This site is usually a good place to start:

[http://devmaster.net/devdb/engines](http://devmaster.net/devdb/engines)

Last I heard, Unity was not focusing on bringing their editor to Linux. I hope they change their mind. While many engines such as Unity and Shiva support exporting to Linux, it seems to me that Linux as a platform does not have a real popular WYSIWYG all-in-one game design solution.

You may also want to check out Garage Game's Torque 3D Engine. It was recently open-sourced. The SDK will build on Linux and the engine is made with C++.

[http://www.garagegames.com/products/torque-3d](http://www.garagegames.com/products/torque-3d)

[http://docs.garagegames.com/tge/official/content/documentation/Engine/Linux.html](http://docs.garagegames.com/tge/official/content/documentation/Engine/Linux.html)

---

### Post by JesseJones on 2014-04-28
Has anyone here tried game editor?

I've been looking for a good game creator for linux seeing as I can't use game maker with it. I downloaded the game maker file and extracted the .zip to my /home folder then followed the directions on the download page:

In order to execute Game Editor on Linux unzip the file and type (from a terminal window): chmod +x gameEditor ./gameEditorLinux 

but recieved the error:

chmod +x gameEditor ./gameEditorLinux 
chmod: cannot access &#8216;gameEditor&#8217;: No such file or directory

Then I took the gameEditorLinux out of the /home/gameeditor folder and placed it in the /home folder, same result.

Can someone help me figure out how to install it?

Sorry if this isn't 100% related to OP's request as I don't think it makes 3d games.

---

### Post by Sslaxx on 2014-04-29
There's Godot, for one: [http://www.godotengine.org/wp/](http://www.godotengine.org/wp/) - does 2D and 3D. Rather rough and still needing work documentation-wise, but it's definitely promising.

[http://enigma-dev.org/](http://enigma-dev.org/) is a Game Maker-like development environment. It also supports several versions of the Game Maker file format.

UE4 looks like it'll be promising Linux-wise in the future. It already supports (albeit with some hackery) exporting to Linux, and they've interest (unlike Unity Technologies) to bring the dev tools to Linux natively.

---

### Post by Dane_Jorgensen on 2014-04-30
I'd like to see Unity as well, but doubt it's anytime soon.  UE4 does look pretty cool, but it didn't look free.

---

### Post by Exodus60 on 2014-04-30
Unity would be nice to see

---

### Post by SoulStreamBurst on 2014-05-02
A quick search on video game development tools in Linux, I saw a blog that lists some of the avaible tools for Linux, some are already suggested here. Check it out: [http://pingugamedevelopmer.blogspot.com/](http://pingugamedevelopmer.blogspot.com/)

On a side note: I would like to see Unity or RPG Maker-like tools for Linux, I'm a big sucker especially for JRPGs. :P

Try also HTML5 Game dev.

---

### Post by Dread Knight on 2014-05-03
[B]I strongly recommend doing a simple 2d game first, using HTML5, as your game will pretty much work on any device and won't get locked into proprietary crapware
[/B]Here are some free open source engines:
[www.phaser.io](www.phaser.io)
[www.kiwijs.org](www.kiwijs.org)
[www.pandajs.net](www.pandajs.net)

Regarding using blender, here's a sample from my project [www.AncientBeast.com/viewer](www.AncientBeast.com/viewer)
Basically you do your models and export them as sprite sheets with this blender addon we made [https://github.com/Fweeb/blender_spritify](https://github.com/Fweeb/blender_spritify)
Phaser and blender both have IRC channels on freenode, you can find a lot of fellow developers there and plenty more game dev channels.

---


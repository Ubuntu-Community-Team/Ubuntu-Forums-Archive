---
title: "Linux and gaming"
date: 2009-09-26
forum: Gaming &amp; Leisure
---

### Post by ShishKabab on 2009-09-26
Hello,

Lately, I've seen some letters to game companies, asking them to start supporting Linux. While some would consider the idea, I don't see it happening anytime soon. However, there is an alternative route: the Open Source community could join forces, search the needed components and build its own simulation platform. 

Simulation platform? Yes, platform. A game (which is a simulation) consists of so much more than code. You also need gameplay ideas, graphics, sound, etc. Also, the code should be modular in such a way that its independent of game type, so that the basics to create a game are there, but you can mold it in any way you like depending on what you're creating.

First, we should create a website where users can dump their art, others can improve it, and everyone can freely download it. All content posted on the website should be licensed very freely. In this way, someone with an idea does not need to worry about creating dummy meshes to test his idea, but can simply go to the website to grab the things that roughly matches his imagination.

Second, we should create a modular simulation engine. The core should only know how to start the application, load the needed components and provide some things like scripting support, resource management, and initialize a graphics system (maybe Ogre3D?). The rest of the application should consist of components. One for graphics, one for physics, one for application logic, etc. They should not depend on each other, so each one can be reused for next games and the pieces for the application can be developed independently. It also means that old games could benefit from e.g. a newer graphics system.

Third, we should create tools to easily create content. Most of us aren't familiar with tools like Blender (which IS a great piece of software), but do have ideas for a cool new character, car, or an environment they'd like to see come to life. Because of this, we should create tools to easily create different kinds of content, the way that the MakeHuman project does and integrate it with the aforementioned simulation engine and website.

Also, there are a lot of objects that can be described. A car for example - once you have an idea of what a car is - can be described with a number of parameters. A car has a base with ... space between the wheels. Its roof is ... high and the corners are (not) round. It has ... windows and ... color. Same goes for foliage. Can't this be translated to some sort of script, with a base model and some parameters which the user can edit in a GUI? Maybe constructive solid geometry ([http://en.wikipedia.org/wiki/Constructive_solid_geometry](http://en.wikipedia.org/wiki/Constructive_solid_geometry)) could help here? One additional advantage of this technique would be that the resulting meshes could be as low-res or high-res as you want them to be.

The bottom line is that there are a lot of tools available to create good games. We just need to combine them in a way so that there's no need to reinvent the wheel for every project and the barrier to game development is significantly lowered so the creative minds among us can do their thing.

Of course, I'm willing to help set this up, but I can't do it alone. So, who of you think this is a good idea and would like to help set this up?

Kind regards,
Vincent den Boer

---

### Post by Vadi on 2009-09-26
Sounds awfully big, I don't see it happening without some 'strong' support (ala companies, not come and go volunteers).

---

### Post by j7%&lt;RmUg on 2009-09-26
Maybe a gamedev .deb package? Containing pretty much everything you have listed above, although im not sure if you mean to make it easy to install as one package or to combine all these tools into one application?

Could you elaborate a bit?

---

### Post by tuahaa on 2009-09-26
I think volunteers can do it but to make it a true game you have to have it as a commercial game; they aim to make money and hence are a better quality. Games like Battle for Wesnoth were pretty good volunteer driven games however.

You need somebody to organize your idea...

Linux is growing bigger. In the future we might see game developers creating their games on a multi-platform system...

---

### Post by dagoth_pie on 2009-09-26
You aren't the first to come up with an idea like this, as far as commercial game developers are concerned, we have a multi-platform base for them (OpenGL + OpenAL + PysX + you name it, we've got it), most companies just don't see it as profitable, although I'm keen to see how the HoN sales go, I imagine it'll have the most publicity in Linux circles so it may do great things for statistics...

To be honest you've got a good idea with creating a model database, however, unfortunately programmers seem keener to give away their creations than artists, maybe if a focus of the database, was to generate publicity for themselves, an online portfolio sortof, it would give them more incentive to upload higher quality artwork and there's the CC license to ensure that credit for that artwork is given to them in the credits of any game made with it.

Also, you may want to look into makehuman, its sortof what you described, one mesh, that can be morphed to make many unique models.

I'm completely lacking in talents (besides the ability to absorb knowledge like a sponge) but I'll be happy to help, I doubt I could do much besides send you hundreds of names of game libraries you've already heard of.

If you have some genius way to unite all the seperate game efforts though...

Also, it's only a matter of time before Microsoft can stop hiding the statistics of how many Linux users there are (anyone here actually believe 0.98%?) and once that happens we should hopefully be flooded, but hey, lets have some fun and keep ourselves occupied while we're waiting!

---

### Post by KhaaL on 2009-09-27
my friend, it. like u should present those ideas to the ubuntu gaming team, they have a meeting today

---

### Post by ShishKabab on 2009-09-27
> Sounds awfully big, I don't see it happening without some 'strong' support
We don't have to start big. We could make a small engine keeping modularity and growth in mind, but only cover the basics to make a simple game like a Roll Away ([http://www.youtube.com/watch?v=KzGnvdC2WCc](http://www.youtube.com/watch?v=KzGnvdC2WCc)) clone. This could be realized by around five men pretty easily. That way we'll have a core to expand on and something for people to get exited about. Remember the way the Linux kernel started ;).

> In the future we might see game developers creating their games on a multi-platform system...
The project would also be interesting once developers support multiple platform. While current game companies grow bigger, the quality of their products decrease. Some games are simply bug-infested, others - like GTA4 - only run on super hardware (something for which a lot of people don't have money) and a lot of them simply lack imagination. If a project like this goes right however, we can use an existing core and the community can very easily show their ideas.

> You need somebody to organize your idea..
If there are enough people willing to think about this, we could start a Wiki somewhere to document the functional/technical aspects and strategies of the project.
.

> Programmers seem keener to give away their creations than artists
You're right. I really wouldn't know anything about licensing. Maybe it would be an idea to ask the Blender community what to do once we have a basic engine?

> We have a multi-platform base for them (OpenGL + OpenAL + PysX + you name it, we've got it)
That's exactly my point. The tools are there, we just need an application/library that allows you to easily tie those tools together in a modular way. You could write e.g. a graphics system that renders paged terrain and use it in a number of games, but you could easily swap it for something else depending on your needs. In the end, every application needs to tie them together in a different way. That would be the power of the whole project which I haven't seen yet in other game engines.

> Also, you may want to look into MakeHuman, its sortof what you described, one mesh, that can be morphed to make many unique models.
I know of MakeHuman and I think it's a great project. What we'd need is something more general that can also be applied to other objects like cars and foliage and integrate it with the engine so you could e.g. design content in the simulation itself. However, this is something for later when the foundations are correctly laid out.

---

### Post by Sindwiller on 2009-09-27
Hmm... sounds like a vision of someone who hasn't really done anything in the direction of game development or game art/content before, eh? What you might be looking for is a game engine with magical capabilities, with functionality and versatility spanning from the core of the earth to the (probably) unlimited depths of our universe itself, something that can be used by anyone without demanding previous knowledge; an engine with an idiot-proof graphical interface, which allows the user to change game logic, physics and graphics attributes in 6 clicks while not requiring the user to know anything about the scripting language behind it to call C/C++/whatever functions, which must total the functions in the Linux kernel itself - let alone the tool chain accompanying the engine, which should basically be able to read the user's thoughts and build something according to his imagination. That'd be hard. If not absolutely impossible :)

It's a hard fact that there will be no such thing as an ultimate, idiot-proof game maker, since games differ extremely in game logic, the requirements to the graphics code, how content and logic are deployed, etc. etc. - even more so illustrated by all the programmer-oriented frameworks and basically all the non-existent or crappy tool chains for FOSS games/engines.

For example, if you want to make maps for games like Nexuiz or Warsow, you won't come around using [NetRadiant](http://dev.alientrap.org/wiki/7), whose workflow and general principles are pretty different from, say, creating a simple model in Blender (eg. deployed as a player model in Nexuiz), which again differs a lot from drawing and animating sprites for a 2D game like Wesnoth. Quake maps (Nexuiz and Warsow use Quake respectively Quake 2 engine forks) are built with basic shapes - usually rectangular blocks - which then are sliced up to improve performance in a way that is efficient in first-person shooters. And. and. and. and. and.

Anyway, if you're looking for repositories for free/libre art and content, check out [http://wiki.freegamedev.net/index.php/Free_3D_and_2D_art_and_audio_resources](http://wiki.freegamedev.net/index.php/Free_3D_and_2D_art_and_audio_resources)

It's a list of websites with free/libre game content, textures, models, Blender materials, reference photos, sounds, music and the like.

---

### Post by dagoth_pie on 2009-09-27
> Hmm... sounds like a vision of someone who hasn't really done anything in the direction of game development or game art/content before, eh? What you might be looking for is a game engine with magical capabilities, with functionality and versatility spanning from the core of the earth to the (probably) unlimited depths of our universe itself, something that can be used by anyone without demanding previous knowledge; an engine with an idiot-proof graphical interface, which allows the user to change game logic, physics and graphics attributes in 6 clicks while not requiring the user to know anything about the scripting language behind it to call C/C++/whatever functions, which must total the functions in the Linux kernel itself - let alone the tool chain accompanying the engine, which should basically be able to read the user's thoughts and build something according to his imagination. That'd be hard. If not absolutely impossible 

I suggest reading the original post, that's a common goal for enthusiastic people with no knowledge of game design to create the ultimate engine which, but in this case, it is a modular engine that is the goal, possibly to try set up a community focus on sharing game media. I'll agree that setting up scripts to do the modeling is a bit far fetched, but whats to stop someone making a plugin to assemble say a car, from various components. Wheels, axis, chassis, etc, fit them all together so you have a car model, that could do something along the lines of what skeletal animation does for character models.

I think it's doable, what makes sense to me would be picking a 3d renderer, then writing a layer over top, so that anyone learning to use it, would have to learn the scripting language, but not have to learn C++ or something, even I can do basic scripting, with a lot of time, effort and incentive I could write all the scripts needed for a game, but doing coding is something that takes skill. I think an engine where one only has to install different plugins, then script your entire game, would be the easiest an engine would get. It'd take a while but hey, if someone told you a university student could write a kernel that would become world famous and more stable than the industry giants, would you believe that? No reason not at least attempt it. It could mean that people could tinker and start making something fun after only a few months rather than years. Worst case scenario, project fails, assuming it succeeds, then at least game devs (even commercial ones) would have something to base their games on. That was the original aim wasn't it?

---

### Post by Sindwiller on 2009-09-29
> I suggest reading the original post, that's a common goal for enthusiastic people with no knowledge of game design to create the ultimate engine which, but in this case, it is a modular engine that is the goal, possibly to try set up a community focus on sharing game media. I'll agree that setting up scripts to do the modeling is a bit far fetched, but whats to stop someone making a plugin to assemble say a car, from various components. Wheels, axis, chassis, etc, fit them all together so you have a car model, that could do something along the lines of what skeletal animation does for character models.

I know what you mean and I'm not discouraging people to have visions or to try to fulfill their dreams, but one should have a more realistic take on the picture as a whole before judging imho.

---

### Post by dagoth_pie on 2009-09-29
> **Sindwiller said:**
> I know what you mean and I'm not discouraging people to have visions or to try to fulfill their dreams, but one should have a more realistic take on the picture as a whole before judging imho.

Quite right, lots to consider, hence why I haven't tried something like this, I have neither the skills nor the willpower to do something like this so I've never attempted. You just sounded a little bit ignorant there, no worries though. But you do have to admit, that if someone actually did take it the right direction and start off small, but make it expandable, it would be able to shape up to be the ultimate engine. The problem is dedication, one project thats managing to follow that is Worldforge, they've stuck at it over a decade, and they don't seem to have gone far. But when compared to every other project they've just take a different path
and will end up with a stable base in the end. It could be at the end of their 2 decades of dedication, but they will eventually end up with their goal, which is a scalable MMO engine. Nothing is impossible, but you're right, enthusiasm isn't enough. If it were, the world would be a perfect place...

---

### Post by Sindwiller on 2009-09-30
Technically, creating a modular game engine with scripting support and *nice content development tools* isn't impossible, although very time consuming and laborious. Besides that, FOSS game developers don't really tend to make their games as easily to mod as possible, mostly for simplicity's sake, or on the grounds that the game's code (and eventually media) is already GPL, what the hell would you want even more. Meaning that nobody gives a crap about user-friendly content creation and deployment tools (talking about engine-/game-related stuff like GtkRadiant, other integrated editors, compilers/exporters, etc. - not the bare essentials as Blender or GIMP).

There's that. And the thing with the virtually impossible application which should be noob-friendly and at the same time assemble 3d models for you within 6 clicks.

I'd totally endorse a project aiming to improve things as is though. :guitar:

---

### Post by dagoth_pie on 2009-09-30
I've just had a thought, in terms of easy to use content creation tools... Maybe a good idea would be to keep things minimal, for example, Blender can do practically everything 3D right? Like GIMP can do everything involving images right? But the thing that makes those so difficult to use is that they can do so much... (same goes for Linux I suppose)

My thought is kind of inspired by Glide, the 3dfx OpenGL implementation (I think) which was slimmed down, to only include functions that would be used in games. Maybe a suite of tools, that weren't designed to be feature rich. But rather, could do everything most people would need. Seeing as there would be less to learn, it would be easier to learn....

---

### Post by Sindwiller on 2009-10-01
Well, tools following a similar principle would be the typical tools written for specific game engines for game content tasks. Worldcraft/Hammer/Radiant would be a good example of that. Or Sauerbraten's level editor functionality. A "single", simplified tool for one purpose, making it "unnecessary" for the user to fiddle around with stuff that would hinder the workflow. If you slim the functionality of the tool down to an absolute minimum (as I said, create a car out of a box and four cylinders for example), you'll have a ratio 1 to [way too high] in flexibility/coding labour. Therefore, you would be supposed to write an app specialized for one single little task which really only depends on the game, which is way too much labor for a single program.

My point is though that even the existing tools, which are to some extent minimized in their functionality to serve a certain purpose (eg. create levels, set up particular game logic parameters, textures, etc.), while or BECAUSE they feature some flexibility in what you can do with those, they're not noob-friendly/idiot-proof, because they still force some principles onto the user, which are to be learned first.

The same thing with software like Blender or GIMP. They can serve dozens of purposes, hence why the knowledge you can obtain about their functionality is much bigger and very crucial if you want to use them for your needs. After all, you can't start with eg. organic modelling right away without having any background knowledge, even if you have modelled anorganic objects in the past.

That might sound demotivating, but.... well, yeah, that's what it is. :P Doing stuff for games is hard labour. :popcorn:

---

### Post by ShishKabab on 2009-10-08
Just to be clear. I am not saying something idiot/fool proof should be built. I'm saying that there should be a core that can do basic things like loading components, control the application flow, provide some scripting support. The core and the components would still have to be programmed in a low-level language like C/C++.

Also, the tools shouldn't be fool-proof and don't have to be end products. There could be a code base that a developer can build upon depending on the specific application that's being developed.

Yes, making games is hard labor and I'm not proposing something with which newbies can work, but a base that the community can build upon.

---


---
title: "New FPS game project"
date: 2011-01-10
forum: Gaming &amp; Leisure
---

### Post by gemmahenchmen on 2011-01-10
Hey everyone.

I've decided to start work on a game development project for ubuntu (possibly multi-platform). I'm looking at something along the lines of a FPS, MMORPG of some kind that could be fully or partially open source (depending on the kind of support the project gets). I'm open to ideas at the moment, and any support would be greatly appreciated.

I'm planning to program it using the Java 3D API, but if anyone can recommend a platform-independent or ubuntu-specific way to achieve this that is better, using either C++ or Java (I'm actually more competent in C++, but the Java 3D API seems like my best bet so far), then I'd be happy to hear it.

I have a decent grasp of animation in Blender and such, but if this gets real then animation and design people would be great too.

My current concept for the game is as follows:
Some sort of First Person Shooter. They are my favourite games to play and it saves any extra animation work from making a 3rd person game.
Some sort of MMO, I like the idea of being able to work together with other people and it being really helpful, but not necessarily required.
I don't have a theme yet, but I'm thinking zombies? Nuclear apocalypse? Something where society's collapsed and it's all about collaborating with each other to rebuild fortifications and stuff, but zombies/terrorists/enemy soldiers keep trying to attack you. The idea's probably that there'll be lots of weak enemies that are NPCs but a few real players that are particularly powerful.

If anyone has ideas or is keen to help, then reply here. Until I've got some indication of its success I'm directing my efforts at mastering the 3d API before making a website or anything. This is probably going to be a big project, but I've got the next 3 weeks free to do some intense work to get the wheels going then will supervise and contribute from there.

---

### Post by gemmahenchmen on 2011-01-10
So far upon reading through the j3d documentation, it seems that it's founded on the concept of a "scene graph", which I need to learn about. Is this standard over most 3d APIs or is it wasted time if I choose to use a different method?

---

### Post by jpv89 on 2011-01-10
If you are going to use Java I recommend trying out [JMonkeyEngine]("http://www.jmonkeyengine.com"). It's an open-source engine, with it's 3rd version currently in beta. Being written entirely in Java this ofcourse also means it's multi-platform. It seems to be able to do some really neat things!

---

### Post by gemmahenchmen on 2011-01-11
Thanks! It looks awesome, especially that it has a physics engine built in. I'll see if I can integrate that with the project.

Also, any ideas for the concept of the game?

---

### Post by jpv89 on 2011-01-11
Yea, I got some ideas. I like the idea of a game set in a post-apocalyptic world, but I would suggest something new entirely. About a year back I've witten up the idea of a game set in a frozen-over world, where only a small group of island near the equator aren't affected by the glaciers that dominate the earth. It would be entirely different from some of the post-apocalyptic games out there (fallout, fallen earth to new a few) that are set in a grungy cyberpunk-ish world.

---

### Post by tapasapat on 2011-01-11
A few more words about the technical part.

Choosing to use jME also means that you'll be choosing LWJGL/JOGL over Java 3D. Good choises every one of them, but the way J3D is used is a lot different when compared to the other two. Why I'm saying this is that you might want to think a bit ahead and decide which one you are going to want to master. Java3D is easier to get up and running, but a low-level OpenGL binding like JOGL is a more popular choice and closer to the "real" OpenGL stuff people seem to like to tinker with. I myself am not all that familiar with jME, but considering its LWJGL/JOGL relationship I'd say it's a good choice - if you don't want to write everything from scratch (but where's the fun in that? :D)

So, what I'm saying here is that you can do it with anything you like, but if you maybe want to join some other game/graphics projects in the future, the OpenGL skills you develop with low-level APIs are more likely to be of any real use there. 

In case you weren't already aware of these: 
- [javagaming.org]("http://javagaming.org"): The place for Java language specific stuff
- [gamedev.net]("http://gamedev.net"): A very good place for pretty much anything else. No question goes unanswered here. 

*(...and I thought Java 3D was close to dying. Seems like the newest pre-release build was updated in November. Nice. I'll have to go check that out.)

---

### Post by jpv89 on 2011-01-11
Also, I would be interested in setting up this project with you, although I wouldn't be a lot of help on the programming part. I do have some Java experience, but nothing having to do with graphics. I'm more of an art guy: sketches, mockups, concept art and some basic modelling. So if you're interested give me a shout!

---

### Post by gemmahenchmen on 2011-01-11
@tapasapat
I'll look further into jME then. At the moment I'm wrestling with the multitude of dependencies for my java setup (given that this is my first real java project). If there are any good tutorials out there for jME then if anyone could give me a shout that'd be great. I've got jME installed already, and will give it a go.

@jpv89
The ice-world one sounds pretty cool! How does the gameplay work though? Why is anyone fighting? Limited land maybe? I think it'd be cool to have at least 3 factions the players can choose between, each with their own reason to be fighting.

Also, any concept art would be awesome too! I don't really have a mental image of what it's going to look like, so you can be really creative. Don't bother with 3D models yet, mainly just concept sketches are what I need now.

---

### Post by jpv89 on 2011-01-11
Sure, I'd love to go into more detail. This is what I wrote up about a year back:

In an attempt to fight global warming, scientists created / genetically altered a species of algae to consume the excess carbon-dioxide. First contained in a dozen lakes, the algae escaped as one of the lakes was flooded. As it reached sea the algae spread rapidly over the world's oceans, in it's growth consuming more and more CO2. 

CO2, being a greenhouse gas, has been keeping our planet at a nice temperature for billions of years now. Depleting the atmosphere of too much CO2 would cause the sun's heat to escape the earth too easily, thereby cooling off our planet.

So this is what happened. The only places on earth the ice hasn't reached are some island on the equator, which due to their location have remained ice-free and at medium temperatures. 

On one of the islands is a massive city, with rich suburbs and and nice downtown area. Overlooking the city, against the mountains, are massive favelas (a bit like Rio de Janeiro). I'm guessing the city would be dominated by gangs fighting over territory, where players are the ones who conquer territory for their gang and good tactics have to be employed to achieve victory. This means the neighborhoods would evolve constantly, all depending on the gang that has it in it's power.

If the players would go north or south they'd meet the ice. With dozens of stations scattered throughout the glaciers, these would also be part of the struggle. A captured station would supply the gang with valuable resources to improve their territory in the city.

Same goes for the forests on the island. 



So that was my idea. Tell me what you think!

---

### Post by mdshann on 2011-01-11
jpv89 that sounds awesome I would play that!

---

### Post by gemmahenchmen on 2011-01-11
@jpv89
That sounds awesome! We'll go with that. Now let's see some concept art... :D

---

### Post by AustinTX on 2011-01-11
Sounds like a cool idea.. What about multiple islands? Like 2 or 3 main ones where the different char types (magic caster, gunslinger ect...)come from... And I know this is entirely random but what Ive been hoping to see in a game for a long time is a weapon/magic system like the Materia in Final Fantasy 7. Anyone remember playing it? I still consider it one of the greatest games of all time.

---

### Post by gemmahenchmen on 2011-01-12
> **AustinTX said:**
> Sounds like a cool idea.. What about multiple islands? Like 2 or 3 main ones where the different char types (magic caster, gunslinger ect...)come from... And I know this is entirely random but what Ive been hoping to see in a game for a long time is a weapon/magic system like the Materia in Final Fantasy 7. Anyone remember playing it? I still consider it one of the greatest games of all time.

I haven't played Final Fantasy 7 before. If you can sum it up for me, then we might be able to implement it.

---

### Post by jpv89 on 2011-01-12
I personally think FPS-style combat would fit this theme best. I've been longing for an FPS game that offers more than just rounds and rounds of fighting other people and for an MMO whre you don't have to hit enemies for over a minute to kill them. Some fast-paced FPS action is just what the gaming world needs, in my opinion. However, I'm aware of the technical problems that arise when combining FPS with MMO. Nothing is unsolvable though.

---

### Post by jpv89 on 2011-01-12
Just a quick sketch of a player in cold-weather clothing. When on the ice the weather can be brutal, limiting visibility severely thus giving combat a little more tension. Someone might just sneak up on you with a knife.

---

### Post by ivarn on 2011-01-12
As a person who love games, I really wish there could be more (or atleaset 1) fps game that's not doom or quake based.
We have like 100 of them already.
What we need is more GTA, APB and Red Dead Redemption type of games.
Just to give you something you can work from.

EDIT: You should not make it available for windows or mac.
If this turns out to be an awesome game, it can open up peoples eyes for linux.

---

### Post by gemmahenchmen on 2011-01-12
@jpv89
I like the look of that sketch. I think that we should somehow make it so everyone's character is extremely customizable. Also, each of the 3 factions should dress very differently so it's easy to tell them apart. Keep going with sketches like that, keeping in mind the different factions, and also maybe some scenery and environments too.

Also, always being heavy blizzard will be really helpful for the graphics, believe it or not, because then people can see less detail, saving tons of work.

@ivarn
I agree about too many generic, bunny-hopping, spray-and-pray kind of FPS games. I think it will have some of the general elements of GTA style games, but without making it based on crime and inevitably R rated.


On the programming side, where I'm currently at is at an environment with objects that you can walk around. I haven't yet worked out how to establish a floor or an object that you can't walk through though. I've conclusively decided to use jME3 (jMonkeyEngine3, it's currently in alpha, so it may be unstable, but I like to be on the cutting edge :P).

Finally, if anyone else has contributions to make then please give them here. All the comments really helps the project pick up steam. I also think we're not far away from a first, early, early alpha (i.e. a room you can walk around in with people in snowsuits).


EDIT: If I'm not going to open it up to the windows public, we should at least offer a demo version? Since it's going to be a Java game, I can make it an applet on the Internet so that anyone can play it. In fact, we could make it an android app as well. Unless it's an amazing game, I don't think anyone will switch for it. 
Perhaps it could have a limited, applet version that anyone can play on the internet, and a full, downloaded version that's only for linux.

---

### Post by ivarn on 2011-01-12
Yea make it as open as possible for linux users so that people can use the game for future projects, and so that people can rebuild and make more maps, mission packs  and objects.
It's also a good idea to make one friendly version and one version for men with sexy hoes, strip bars etc.. That will make the game super cool for 2 types of people.
Also, I have an idea for windows users.
Since it's java you can make a online version of the game.
In this version you will can give them enough to make it playable but only with one mission. To make the online version smaller, do not let it be open world.
The online version ending must include a video of cool things you'll miss.
Also, close the source to GPL license so that windows people can''t copy the stuff and make a windows version legally.

---

### Post by gemmahenchmen on 2011-01-12
> **ivarn said:**
> 
Also, I have an idea for windows users.
Since it's java you can make a online version of the game.
In this version you will can give them enough to make it playable but only with one mission. To make the online version smaller, do not let it be open world.
The online version ending must include a video of cool things you'll miss.
Also, close the source to GPL license so that windows people can''t copy the stuff and make a windows version legally.
I don't want to have to force people to move to ubuntu to use it. I think it's best for it to be freely available to everyone to start with, and since it'll be an MMO, we can cut off server support for the original, available-to-all version, release version 2, then make it the same as version 1 for the windows users but with tons of cool new features for the linux users. This means that no-one will be angry that the windows version got worse, because it didn't. The linux one just got better :P

Also, what should we call the game? Theme is ice-age-apocalypse. Any ideas?

---

### Post by jpv89 on 2011-01-12
I think we should keep it simple:

Frozen.

---

### Post by gemmahenchmen on 2011-01-12
> **jpv89 said:**
> I think we should keep it simple:

Frozen.
I like it.

For an update, if anyone's making 3d models, I need them in one of the following formats:

[LIST]
[*].obj, and provide your own texture, and material if you can (if you don't know about this, I can use a standard one)
[*].mesh.xml, this one bundles everything into one easy-to-use object, but isn't nearly as well supported by animation tools. If you can make it like this but not .j3o, then do
[*].j3o, this is a custom file type for jME. It would be the best possible way to do it if you made the files in the form of an asset pack for jME.
[/LIST]
What I'm expecting, really is for most of them to be .obj. It's a good, generalized format which everything should be able to export.

Still, if sketching is more your style then we still need concept art. Jpv89, more like the one you've done is great.

---

### Post by ivarn on 2011-01-12
That name is too simple I think.
If you google the game you will get 100 hits that aren't even related, and maybe the game will appear on page 22.
So call it something original but easy to say, remember and type.
What about Open Frosty or Frostration or something like that?
Or you can call it Cold Blood, but I think that game already exists:)

---

### Post by gemmahenchmen on 2011-01-12
Frozen Fury maybe?

On the technical side, does anyone know how to preview a scene in jME so that I can see where all the starting objects will be? At the moment I have to guess where it will be and adjust based on where it was, which is ok with around 10 objects, but when it gets up to the hundreds or even thousands in the full game it will get really annoying.

Also, watch this space for an alpha preview (don't expect anything amazing, it's a proof of technological concept). Should be here in about an hour.

Finally, I'll be throwing up a site, probably in the next 24 hours. I think that when this thread gets too long to manage, we can shift our communications to the new site.

---

### Post by jpv89 on 2011-01-12
Want me to set up a wordpress blog/forum?

---

### Post by gemmahenchmen on 2011-01-12
> **jpv89 said:**
> Want me to set up a wordpress blog/forum?
That would be great. Make both of us admins. I need to focus on the code. This is no simple problem... Nearly 400 lines of code already and it's just a scene with some cubes!

EDIT: Also, what time zone are you in, so we can find the best times to collaborate?

---

### Post by jpv89 on 2011-01-12
European Central Time, yourself?

And I set up a free temporary forum at [http://frozenproject.freeforums.org](http://frozenproject.freeforums.org). We can use that untill I get a better permanent hosting.

---

### Post by jpv89 on 2011-01-12
how's the code coming along by the way?

---

### Post by gemmahenchmen on 2011-01-12
NZST, so GMT+13. 
12 hours apart, that's bad luck.

Anyway, I've registered on the forum as gemmahenchmen.

In terms of the code, I've got a basic proof-of-concept going, I'm now implementing a nifty physics engine. I'll either be done in about 30 mins or will just upload it without the engine and update later.

---

### Post by gemmahenchmen on 2011-01-12
The moment we've all been waiting for... *drumroll*

The alpha release!

As I've said earlier, it's a basic proof-of-concept, with colored cubes (enemies) and random obstacles, set in a little town.

EDIT: BTW this one doesn't yet have the physics; it was harder than I expected.

---

### Post by jpv89 on 2011-01-12
I think I'm missing all the dependencies. Did you build them into the jar?

---

### Post by gemmahenchmen on 2011-01-12
> **jpv89 said:**
> I think I'm missing all the dependencies. Did you build them into the jar?
No... I'll get onto that now.

---

### Post by J697 on 2011-01-12
Wow, this looks interesting :D

---

### Post by gemmahenchmen on 2011-01-12
I've made an updated one, but it's huge, 43mb. Way over the upload limit. Any ideas?

---

### Post by jpv89 on 2011-01-12
We should probably set up some SVN then. Google code perhaps?

---

### Post by Finalfantasykid on 2011-01-12
I'm pretty decent at Java, although I'll admit I have done next to no 3d programming.  I'm quite good at 2d sprite based programming though :D

I might be interested in this, so I'll bookmark this thread and see where it goes.  If you want to contact me, email me [email]finalfantasykid13@gmail.com[/email]

---

### Post by gemmahenchmen on 2011-01-12
> **jpv89 said:**
> We should probably set up some SVN then. Google code perhaps?
That'll work. Could you set that up? I'll get back to working on the physics engine until you're done.
[QUOTE=Finalfantasykid]I'm pretty decent at Java, although I'll admit I have done next to no 3d  programming.  I'm quite good at 2d sprite based programming though :grin:[/QUOTE]
Any thing's helpful, really. Do you know anything about networking using java, i.e. server connections? That would be VERY useful, as this is going to be an MMO.

---

### Post by Ahava591 on 2011-01-12
I've never done any game work and know absolutely no Java; I can do basic Python stuff.

But if you can think of a way for me to help, please let me know.


I think a cool idea would be to have little computers to use. Maybe they could be used to access the player-characters' inventory, bank account, etc. by walking up to them and pressing a key on the keyboard that's mapped to "use item?"

-I've always wanted in the Fallout series, (especially Fallout 3,) to have computer networks in the game world where you can get intelligence on enemy factions, something like that. Maybe implement a stripped down version of bash in the game?
Or have a quest/mission where you need to disable an enemy bases' defenses by cracking into their network by finding a password on an assassins' body that attacked you, that sort of thing.


Good luck!

---

### Post by Finalfantasykid on 2011-01-12
^Very little if any.

---

### Post by J697 on 2011-01-12
I can code C very well, I also can code assembly mips. I doubt any of that would be too useful for a game though.

---

### Post by JuicyCouture on 2011-01-12
simpsons did it

---

### Post by gemmahenchmen on 2011-01-12
> **Ahava591 said:**
> I've never done any game work and know absolutely no Java; I can do basic Python stuff.

That's still OK. There's a lot of work that goes into a game like this. At this second I don't know what I need you to do, but keep an eye on this thread.
Also, if you have any specific knowledge in networking or 3d graphics or server applications then tell me, and it'll be easier for me to give you tasks.

> **Ahava591 said:**
> 
I think a cool idea would be to have little computers to use. Maybe they could be used to access the player-characters' inventory, bank account, etc. by walking up to them and pressing a key on the keyboard that's mapped to "use item?"

I can do that, probably. I know that there exist really low spec-requirement bash systems, and I'll try to throw that in once everything else is sorted.
> **Ahava591 said:**
> 
Or have a quest/mission where you need to disable an enemy bases' defenses by cracking into their network!
It'd be fun to throw in some realistic basic hacking into the game. I'll keep that in mind in the future.

> **Finalfantasykid said:**
> ^Very little if any.
What specific knowledge do you have? I'm certain there's something you can help with.


I'm really happy about the number of people that are offering support! Thank you all.

EDIT: One more thing, if anyone with specific knowledge about jMonkeyEngine3 can tell me how to make Spatial objects work with collisions, then please tell me. I keep getting null pointer exceptions.

---

### Post by jpv89 on 2011-01-12
[http://code.google.com/p/frozenproject/](http://code.google.com/p/frozenproject/) There we go. Not sure how the entire thing works though, but it has svn. Go to the 'Source' tab.

---

### Post by gemmahenchmen on 2011-01-12
> **jpv89 said:**
> [http://code.google.com/p/frozenproject/](http://code.google.com/p/frozenproject/) There we go. Not sure how the entire thing works though, but it has svn. Go to the 'Source' tab.
How do I upload to it?

EDIT: I think you need to make me an owner. My google account is [email]am.i.will@hotmail.co.nz[/email]

---

### Post by jpv89 on 2011-01-12
Sure, done.

---

### Post by gemmahenchmen on 2011-01-12
It's uploading. Might take a while cause it's big, and my internet is slow. Keep checking.

---

### Post by Ahava591 on 2011-01-12
I'm a computer networking student in college; let me know what do you need and I'll do whatever I can.

---

### Post by gemmahenchmen on 2011-01-12
The upload failed. I think it timed out.

Just download and install jME ([http://jmonkeyengine.org/downloads/?did=2](http://jmonkeyengine.org/downloads/?did=2)) then download the jar I already uploaded. I'll put the .jar on the svn too.

---

### Post by gemmahenchmen on 2011-01-12
> **Ahava591 said:**
> I'm a computer networking student in college; let me know what do you need and I'll do whatever I can.
To start with, you can be part of our early open Alpha 

Download the .zip ([http://code.google.com/p/frozenproject/downloads/list](http://code.google.com/p/frozenproject/downloads/list)) and download the jME SDK (needed to run the .jar) from here [http://jmonkeyengine.org/downloads/?did=2](http://jmonkeyengine.org/downloads/?did=2), then extract it and read the readme. It'll tell the rest.

---

### Post by Finalfantasykid on 2011-01-13
> What specific knowledge do you have? I'm certain there's something you can help with.

I would probably be not to bad at doing UI stuff like menus and the HUD.

But I am pretty busy at the moment with University, but possibly during the summer I will have to to get involved in this.  I will monitor the progress of this project, and maybe get involved in some of the discussions until that time :)

---

### Post by gemmahenchmen on 2011-01-13
> **Finalfantasykid said:**
> I would probably be not to bad at doing UI stuff like menus and the HUD.

But I am pretty busy at the moment with University, but possibly during the summer I will have to to get involved in this.  I will monitor the progress of this project, and maybe get involved in some of the discussions until that time :)
For now, could you try installing and playing with the alpha game? I don't know if it works on other people's machines, to my understanding no-one's tried yet.

---

### Post by ivarn on 2011-01-13
This is weird. I can't open the file.
I have OpenJKE 6 installed, and that's the program I use to open all my java files with.

Any idea?

---

### Post by gemmahenchmen on 2011-01-13
> **ivarn said:**
> This is weird. I can't open the file.
I have OpenJKE 6 installed, and that's the program I use to open all my java files with.

Any idea?
I can't open it either through double-clicking; try the command line option:
```
java -jar Frozen-0.0.2.jar
```I think there's something I need to do to make it work with OpenJDK

EDIT: Don't forget to download jME, it's needed for the dependencies.

---

### Post by jpv89 on 2011-01-13
Why don't you just commit the entire source, including libraries, to the SVN?

I can recommend the RabbitVCS subversion client:
```

sudo add-apt-repository ppa:rabbitvcs/ppa && sudo apt-get update
sudo apt-get install rabbitvcs-nautilus

```And then restart nautilus
```

killall nautilus

```

---

### Post by gemmahenchmen on 2011-01-13
> **jpv89 said:**
> Why don't you just commit the entire source, including libraries, to the SVN?

I can recommend the RabbitVCS subversion client:
```

sudo add-apt-repository ppa:rabbitvcs/ppa && sudo apt-get update
sudo apt-get install rabbitvcs-nautilus

```And then restart nautilus
```

killall nautilus

```
I need to sleep now, will work on that tomorrow. It isn't obvious how it works, could you offer a quick tutorial?

---

### Post by ivarn on 2011-01-13
the terminal gave me a weird error when I tried to run the jar file from there.
> Could not find the main class: mygame.Main. Program will exit.
but I found it when I extracted the frozen jar file. SO this was an odd error message.

---

### Post by DangerOnTheRanger on 2011-01-13
I'm sorry to burst everyone's bubble, but this game won't have MMO capability unless someone chips around 200-500$ a month for infrastructure.

---

### Post by jpv89 on 2011-01-13
Hey you're not bursting any bubbles, development of something like this would take years, and servercosts are the least of our worries right now. We're gonna start off small, setup a first milestone and we'll see where we will get from there. Thanks for thinking with us though.

---

### Post by gemmahenchmen on 2011-01-13
> **DangerOnTheRanger said:**
> I'm sorry to burst everyone's bubble, but this game won't have MMO capability unless someone chips around 200-500$ a month for infrastructure.
To start with, we're going to do this with point-to-point multiplayer, i.e. one player hosts the game, others join, then they play and results(xp etc.) are uploaded to a server. I believe I can do that simply with my old computer running an efficient linux build, and a dedicated IP address. That's really looking more like $100 a year for the early solution. By that point we will probably have enough contributors that we can just donate something in the field of $10 and get it running.

By the time we have so many players that we NEED MMO capability and not just player-hosted games, we will have enough users that we can establish some kind of "premium" system to pay for server costs.


Ok, now for a project update:
It seems like something is badly wrong with the .jars that jME is automatically creating. At this point, I'm going to start compiling the .jars manually and including all dependencies. My only issue is that I have trouble when I upload large files, it seems to fail, but a larger number of smaller ones work. I'm going to try the RabbitVCS solution for now, and see if it will work.

---

### Post by jpv89 on 2011-01-13
Have you worked with sofware versioning before? If not, I can give you a little explanation if you'd like, although there are probably tons of tutorials on the internet.

---

### Post by gemmahenchmen on 2011-01-13
> **jpv89 said:**
> Have you worked with sofware versioning before? If not, I can give you a little explanation if you'd like, although there are probably tons of tutorials on the internet.
I've never worked with SVN or any such uploading tools, all of the projects I've done before have been in-house. A tutorial on RabbitVCS would be helpful.

---

### Post by DangerOnTheRanger on 2011-01-14
> **gemmahenchmen said:**
> To start with, we're going to do this with point-to-point multiplayer, i.e. one player hosts the game, others join, then they play and results(xp etc.) are uploaded to a server. I believe I can do that simply with my old computer running an efficient linux build, and a dedicated IP address. That's really looking more like $100 a year for the early solution. By that point we will probably have enough contributors that we can just donate something in the field of $10 and get it running.

By the time we have so many players that we NEED MMO capability and not just player-hosted games, we will have enough users that we can establish some kind of "premium" system to pay for server costs.




Client-server with a player hosting is very dangerous, as well as very slow. The host can easily cheat, and his outbound connection is probably going to be under 200 Kb/ps. To slow for multiplayer.

---

### Post by thatguruguy on 2011-01-14
Animals which would evolve to be even more dangerous in the world described for this game:

Polar bears
Arctic wolves
Timber wolves
Siberian tigers
Seals
Orcas

Just throwing that out there.

---

### Post by thenickrulz on 2011-01-14
sounds like a great game jpv89:D

---

### Post by jpv89 on 2011-01-14
> **thatguruguy said:**
> Animals which would evolve to be even more dangerous in the world described for this game:

Polar bears
Arctic wolves
Timber wolves
Siberian tigers
Seals
Orcas

Just throwing that out there.

You forgot penguins! :P

We have our main website up and running now, although a lot still needs to be done:
[http://frozenproject.org]("http://http://frozenproject.org"). You can also follow us on twitter: [@frozenproject]("http://twitter.com/#%21/frozenproject").

---

### Post by gemmahenchmen on 2011-01-15
At the moment multiplayer isn't the top of the priority list...

The development's going really well for how early we are and that this is my first jME project. Don't forget to check out our project from SVN on [http://code.google.com/p/frozenproject](http://code.google.com/p/frozenproject). I'll probably be throwing out an update today, maybe 2. Milestone 1 is coming up, too, and that should be out in a few days.

Back to multiplayer, can anyone suggest a cost-effective solution for a small number of players? I doubt that we'll have more than 20 users online at one time until we at least reach beta.

---

### Post by Finalfantasykid on 2011-01-15
^ I have a webserver with DreamHost which we could probably use.

EDIT:  I can't seem to be able to run the game.  I get this:

```
david@david:~/code/frozenproject/trunk/test$ java -jar Frozen-0.0.5.jar
15-Jan-2011 9:00:40 PM com.jme3.system.JmeSystem initialize
INFO: Running on jMonkey Engine 3 Alpha 0.6
15-Jan-2011 9:00:40 PM com.jme3.system.Natives extractNativeLibs
INFO: Extraction Directory #1: file:/home/david/code/frozenproject/trunk/test/lib/
15-Jan-2011 9:00:40 PM com.jme3.system.Natives extractNativeLibs
INFO: Extraction Directory #2: /home/david/code/frozenproject/trunk/test
15-Jan-2011 9:00:40 PM com.jme3.system.Natives extractNativeLibs
INFO: Extraction Directory #3: /home/david/code/frozenproject/trunk/test
15-Jan-2011 9:00:40 PM com.jme3.system.lwjgl.LwjglAbstractDisplay run
INFO: Using LWJGL 2.5
15-Jan-2011 9:00:40 PM com.jme3.system.lwjgl.LwjglDisplay createContext
INFO: Selected display mode: 640 x 480 x 0 @0Hz
15-Jan-2011 9:00:40 PM com.jme3.system.lwjgl.LwjglAbstractDisplay initInThread
INFO: Display created.
15-Jan-2011 9:00:40 PM com.jme3.system.lwjgl.LwjglAbstractDisplay initInThread
INFO: Adapter: null
15-Jan-2011 9:00:40 PM com.jme3.system.lwjgl.LwjglAbstractDisplay initInThread
INFO: Driver Version: null
15-Jan-2011 9:00:40 PM com.jme3.system.lwjgl.LwjglAbstractDisplay initInThread
INFO: Vendor: NVIDIA Corporation
15-Jan-2011 9:00:40 PM com.jme3.system.lwjgl.LwjglAbstractDisplay initInThread
INFO: OpenGL Version: 2.1.2 NVIDIA 260.19.06
15-Jan-2011 9:00:40 PM com.jme3.system.lwjgl.LwjglAbstractDisplay initInThread
INFO: Renderer: GeForce Go 7900 GS/PCI/SSE2
15-Jan-2011 9:00:40 PM com.jme3.system.lwjgl.LwjglAbstractDisplay initInThread
INFO: GLSL Ver: 1.20 NVIDIA via Cg compiler
15-Jan-2011 9:00:40 PM com.jme3.system.lwjgl.LwjglTimer <init>
INFO: Timer resolution: 1000 ticks per second
15-Jan-2011 9:00:40 PM com.jme3.renderer.lwjgl.LwjglRenderer initialize
INFO: Caps: [FrameBuffer, FrameBufferMRT, FrameBufferMultisample, OpenGL20, OpenGL21, ARBprogram, GLSL100, GLSL110, GLSL120, VertexTextureFetch, FloatTexture, FloatColorBuffer, VertexBufferArray]
15-Jan-2011 9:00:40 PM com.jme3.asset.DesktopAssetManager <init>
INFO: DesktopAssetManager created.
15-Jan-2011 9:00:40 PM com.jme3.renderer.Camera <init>
INFO: Camera created (W: 640, H: 480)
15-Jan-2011 9:00:40 PM com.jme3.renderer.Camera <init>
INFO: Camera created (W: 640, H: 480)
15-Jan-2011 9:00:40 PM com.jme3.input.lwjgl.LwjglMouseInput initialize
INFO: Mouse created.
15-Jan-2011 9:00:40 PM com.jme3.input.lwjgl.LwjglKeyInput initialize
INFO: Keyboard created.
15-Jan-2011 9:00:40 PM com.jme3.audio.lwjgl.LwjglAudioRenderer initialize
INFO: Audio effect extension version: 1.0
15-Jan-2011 9:00:40 PM com.jme3.audio.lwjgl.LwjglAudioRenderer initialize
INFO: Audio max auxilary sends: 2
15-Jan-2011 9:00:40 PM com.jme3.material.MaterialDef <init>
INFO: Loaded material definition: Default GUI
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Gui Node)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (BitmapFont) attached to this node (Statistics View)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (Statistics View) attached to this node (Gui Node)
15-Jan-2011 9:00:41 PM com.jme3.scene.Node attachChild
INFO: Child (null) attached to this node (Root Node)
15-Jan-2011 9:00:41 PM com.jme3.material.MaterialDef <init>
INFO: Loaded material definition: Terrain
15-Jan-2011 9:00:41 PM com.jme3.asset.DesktopAssetManager loadAsset
WARNING: Cannot locate resource: Textures/Terrain/TextureMapBetter.png (Flipped) (Mipmaped)
15-Jan-2011 9:00:41 PM com.jme3.app.Application handleError
SEVERE: Uncaught exception thrown in Thread[LWJGL Renderer Thread,5,main]
java.lang.NullPointerException
    at com.jme3.material.Material.setTexture(Material.java:301)
    at mygame.Main.simpleInitApp(Main.java:176)
    at com.jme3.app.SimpleApplication.initialize(SimpleApplication.java:186)
    at com.jme3.app.SimpleBulletApplication.initialize(SimpleBulletApplication.java:52)
    at com.jme3.system.lwjgl.LwjglAbstractDisplay.initInThread(LwjglAbstractDisplay.java:134)
    at com.jme3.system.lwjgl.LwjglAbstractDisplay.run(LwjglAbstractDisplay.java:183)
    at java.lang.Thread.run(Unknown Source)
Inconsistency detected by ld.so: dl-close.c: 736: _dl_close: Assertion `map->l_init_called' failed!
```

I think I must be missing a png file somewhere.  Maybe someone forgot to add when they did a commit?

---

### Post by gemmahenchmen on 2011-01-15
> **Finalfantasykid said:**
> ^ I have a webserver with DreamHost which we could probably use.
That would be great! We're not at the multiplayer stage yet but keep in touch for when we need it. Create an account on [http://frozenproject.org/](http://frozenproject.org/) and check out everything going on. Check out the game on SVN too, we want as many people as possible to test it.

To everyone else, our main needs for contributors are still:

[LIST]
[*]Graphics people: We need concept art, 3d models, textures, animations.
[*]jME people: We need 1 or 2 people to assist me in the development of this game. If this is you, ideally you should have a good working understanding of Java, and either basic knowledge of jMonkeyEngine or a willingness to learn it over a short period of time (have a look at the tutorials at [http://jmonkeyengine.org/wiki/doku.php/jme3#tutorials_for_beginners](http://jmonkeyengine.org/wiki/doku.php/jme3#tutorials_for_beginners))
[*]Ideas people: The more ideas, the better. Preferably, as this in early stages, ideas that aren't too difficult to implement and can be used straight away.
[*]Testing people: Once again, we need as many of you as we can get. Check out the latest version of the game on SVN (noting that I update it regularly, averaging once a day) and play around with it, pointing out any major errors, but remembering that it is still in very early stages.
[/LIST]
The latter two don't take a lot of effort, but will help enormously.

---

### Post by Finalfantasykid on 2011-01-16
^ Did you see my edit?

EDIT:  Yay, one of the recent commits fixed it :)

Also could you add an account for me on svn?  I have something to commit :D

---

### Post by jpv89 on 2011-01-17
> **Finalfantasykid said:**
> ^ Did you see my edit?

EDIT:  Yay, one of the recent commits fixed it :)

Also could you add an account for me on svn?  I have something to commit :D
So you wanna get involved eh? :) What's your specialty?

---

### Post by jpv89 on 2011-01-17
> **Finalfantasykid said:**
> ^ Did you see my edit?

EDIT:  Yay, one of the recent commits fixed it :)

Also could you add an account for me on svn?  I have something to commit :D
So you wanna get involved eh? :) That's awesome. What's your specialty?

Oops, double post..

---

### Post by Finalfantasykid on 2011-01-17
[QUOTE=Finalfantasykid]I would probably be not to bad at doing UI stuff like menus and the HUD.

But I am pretty busy at the moment with University, but possibly during  the summer I will have to to get involved in this.  I will monitor the  progress of this project, and maybe get involved in some of the  discussions until that time :smile:[/QUOTE]

Thats what I said a couple of pages ago :P

What I want to add right now is pretty basic, a Makefile w00t!

---

### Post by jpv89 on 2011-01-17
Alright, sounds good :) why don't you register at the website ([http://frozenproject.org](http://frozenproject.org)) and sign up at the svn: [http://code.google.com/p/frozenproject/](http://code.google.com/p/frozenproject/). Let's get some discussions going on the site.

---

### Post by Finalfantasykid on 2011-01-18
Ok I joined the frozenproject site, but I'm not sure how to join the google codes site.

---

### Post by jpv89 on 2011-01-18
Ah yes, I added you to the google code project. :)

---

### Post by pshyco on 2011-01-22
This is interesting. I tried to download the game from the google code page and i got the same error that *ivarn* got 

"Could not find the main class: mygame.Main Program will exit."

I was wondering it anyone figured what the problem with that was. I do find the file as he does. It is Frozen-0.0.2.jar that I'm trying to run. 

I'm willing to help in testing this, its a interesting idea. I hope this keeps going so i can see what comes out of it.

---

### Post by DeviantGuy on 2011-01-22
If you would like, I can make a trailer of the game.

---

### Post by Quadunit404 on 2011-01-22
Just tried out Frozen. Here's some problems I encountered:

- Will not start up if you set variables like VSync and Anti-aliasing. Might want to fix that.
- If I get it to start, it crashes immediately.

By the way, you may want a logo if you don't have one already.

---

### Post by Finalfantasykid on 2011-01-22
^Which version of the game are you guys trying to play?  The latest svn version works for me.  The one which is downloadable on google code is a little older.

EDIT: The latest version is 0.0.7.1

---

### Post by Quadunit404 on 2011-01-22
0.0.7.1 is the version I'm trying to play. This is the error I'm getting:

```
SEVERE: Uncaught exception thrown in Thread[LWJGL Renderer Thread,5,main]
java.lang.NullPointerException
	at mygame.Main.makeBuilding(Main.java:398)
	at mygame.Main.initAll(Main.java:265)
	at mygame.Main.simpleInitApp(Main.java:240)
	at com.jme3.app.SimpleApplication.initialize(SimpleApplication.java:186)
	at com.jme3.app.SimpleBulletApplication.initialize(SimpleBulletApplication.java:52)
	at com.jme3.system.lwjgl.LwjglAbstractDisplay.initInThread(LwjglAbstractDisplay.java:134)
	at com.jme3.system.lwjgl.LwjglAbstractDisplay.run(LwjglAbstractDisplay.java:183)
	at java.lang.Thread.run(Thread.java:636)
Inconsistency detected by ld.so: dl-close.c: 736: _dl_close: Assertion `map->l_init_called' failed!
```

---

### Post by pshyco on 2011-01-22
Well, I now know that i was trying an old version. I'll try the svn version and see what if i can get it to run.

---

### Post by Quadunit404 on 2011-01-22
Okay, so I compiled Frozen from source and it automagically worked. Huh...

---

### Post by pshyco on 2011-01-22
The new version works for me. It looks good to me for the stage its at. 
I'm not good for coding help, but if you need any help with physics equations, im good there.

---

### Post by pshyco on 2011-01-26
I've been thinking, and got a few ideas that might be good for the game. I was thinking that you could use blimps for long distance travel, the density of air being higher in the colder environment they would be more practical. Also they have an ability to look cool. 

In certain places maybe sailing snow ships to get around. Not wasting fuel and still traveling fairly fast would be an advantage in possible tundra type environments. Fuel could then be used for heat.

I can do a bit of story writing it you want. Other than that I would be up for being a consistent tester for your stuff.

---

### Post by jpv89 on 2011-01-26
Sure, why don't you register at our website and we can get some discussion going about the story? I'll post what I had in mind so far on the Wiki or the Forums.

---

### Post by gemmahenchmen on 2011-01-26
> **pshyco said:**
> I've been thinking, and got a few ideas that might be good for the game. I was thinking that you could use blimps for long distance travel, the density of air being higher in the colder environment they would be more practical. Also they have an ability to look cool. 

In certain places maybe sailing snow ships to get around. Not wasting fuel and still traveling fairly fast would be an advantage in possible tundra type environments. Fuel could then be used for heat.

I can do a bit of story writing it you want. Other than that I would be up for being a consistent tester for your stuff.
Story writing is helpful. As a group we haven't discussed this yet, but the goal is to get a gritty, real world feel for the game in my mind. So ramshackle style boats that look like they could have been put together by a few survivors would be good, nothing that looks fantasy.

On a related note, if we can get one or more people working on concept art then that would be excellent. I've recently finished my holidays, so development will be slower, but with some awesome looking 3d models the game can start to get really good. I might try to contribute some myself later, but for now development's my focus.

Lastly, let's get a vote going: Should shadows be put off until 0.2.0? I think so, because I'm unable to test them on my current setup, and the coding effort might be better put to use adding features like moving enemies etc.

---

### Post by Finalfantasykid on 2011-01-26
^I can't run the zip version of the game either, and I have a dedicated nvidia graphics card, so I think there must be something else wrong with it.

---

### Post by Quadunit404 on 2011-01-26
> **Finalfantasykid said:**
> ^I can't run the zip version of the game either, and I have a dedicated nvidia graphics card, so I think there must be something else wrong with it.

Apparently you need to build it from source. Run:

```
sudo apt-get install gcj
cd /path/to/Frozen
cd test
make
chmod +x Frozen-<version>.jar
```

It should then run. Obviously you need to change /path/to/Frozen to the actual path. Just be aware that right now it's one room big with about three rainbow-colored buildings :lol:

---

### Post by Finalfantasykid on 2011-01-26
^Actually thats not quite the most up to date version.  The one in test/ is version 0.0.7.1, whereas the one in share/ is version 0.0.8, which includes the shadows.  It runs for about 1 or two frames, then I get an error.

---

### Post by gemmahenchmen on 2011-01-27
> **Finalfantasykid said:**
> ^Actually thats not quite the most up to date version.  The one in test/ is version 0.0.7.1, whereas the one in share/ is version 0.0.8, which includes the shadows.  It runs for about 1 or two frames, then I get an error.
Clearly there's something wrong with my code. In the next few days I'll upload 0.1.0, including source code.

---

### Post by dudetime on 2011-01-28
that does seem like a good idea for a game and it peaks my intrest so i'll keep tabs on it. btw zombies great idea

---

### Post by Finalfantasykid on 2011-01-28
> **gemmahenchmen said:**
> Clearly there's something wrong with my code. In the next few days I'll upload 0.1.0, including source code.

I look forward to that :D

---

### Post by gemmahenchmen on 2011-02-05
0.1.0 and source code are now online!

There has been a lull in development in the last 10 days because I've  been really busy, but now I've finally uploaded to 0.1.0 code to the  SVN. Anyone can now have a look through the code, and that's going to be  important, because we need developers.

Now that it's up, everyone  should check it out and play around with it. Also, now that development  will start picking up again, we need more discussion and help. What  should be in 0.2.0? Go to frozenproject.org to contribute, the main purpose of this thread is to get interest in the project for new people, now that we have our own site (not to say that anyone should stop posting here, I'm just going to post my updates in parallel to both).

In addition, I'm going to have a new, better computer that will  allow me to build better graphics features into the next version.

For now, I'm getting to work on having interactive enemies, and building another map, set in a broken down city.

---

### Post by Quadunit404 on 2011-02-05
Just built the newest version.

Maybe you could make it so that you CAN'T go out of bounds? Because I did so twice :wink:

---

### Post by Finalfantasykid on 2011-02-06
I can't seem to be able to create new topics on the game website, so I'll post it here:

SimpleBulletApplication is depricated, and according to the documentation should be replaced with BulletAppState:
stateManager.attach(new BulletAppState());

[http://jmonkeyengine.org/javadoc/com/jme3/app/SimpleBulletApplication.html](http://jmonkeyengine.org/javadoc/com/jme3/app/SimpleBulletApplication.html)
[http://jmonkeyengine.org/javadoc/com/jme3/bullet/BulletAppState.html](http://jmonkeyengine.org/javadoc/com/jme3/bullet/BulletAppState.html)

---
Also while Im at it, maybe I'm the only one who is getting this, but I am getting brutal performance in the game(0 fps although it slowly improves as time goes on).  I've traced the problem to the physics, and the biggest culprit are the bricks.  I removed them from the game for testing, and I got  like 200+ fps after a few seconds.  Maybe replacing with BulletAppState will actually fix this though.

---

### Post by 501st_alpha1 on 2011-02-06
This sounds cool! (Excuse the pun..) I'd like to help out if I can. Right now I will mainly be a tester. I do have some experience in Java, but not much. I may eventually help with coding, but that will be after my Java skills have improved, which probably won't be at least until summer, when I'll have more time.

P.S. I downloaded it, and I'm getting the same error mentioned above ("Cannot find main class... program will exit.").

---

### Post by gemmahenchmen on 2011-02-07
> **501st_alpha1 said:**
> This sounds cool! (Excuse the pun..) I'd like to help out if I can. Right now I will mainly be a tester. I do have some experience in Java, but not much. I may eventually help with coding, but that will be after my Java skills have improved, which probably won't be at least until summer, when I'll have more time.

P.S. I downloaded it, and I'm getting the same error mentioned above ("Cannot find main class... program will exit.").You need to download the project from SVN. Look earlier in this thread to find out how. Someone should write a brief explanation of how to do that, and we should sticky it on the site.

> **Finalfantasykid said:**
> I am getting brutal performance in the game
Everyone seems to. I figured it was because my computer was slow- I'll see how it runs when i've got my new machine.
> **Finalfantasykid said:**
> Maybe replacing with BulletAppState will actually fix this though.I didn't know about that- there was something to do with the collidable height maps that preferred SimpleBulletApplication, but given how relatively poor the height maps look, I'll replace that when a second map is made.

On that topic: Anyone out there either a 3d modeller or know of a site with free 3d models of buildings and such? I could probably make it to some extent myself, but it would be great to have a skilled modeller make them. I'm planning to roll out a second map that looks a lot better and has some improved elements such as sky, light bulbs producing light, shadows, shaders etc. in the next 2-4 weeks depending on A) If anyone can provide models and textures and B) If I run into any problems transitioning into a new computer. This new map will probably be 0.2.0, because of the graphics engine upgrades.

Also, does anyone know about making GUIs in java? I think it'd be great to have a game-like GUI (so ideally probably not standard Ubuntu GUI style, more like what you see in Call of Duty) to select various things such as map, game type etc. in the future. I'm not going to invest time in learning that when the game development is more important, but it'd be great if someone else could make that.

Finally, @Finalfantasykid, do you want to be added to the list of contributors on the site? If so, come up with a role for yourself so that I can better assign tasks.

---

### Post by Finalfantasykid on 2011-02-07
^GUI design was the thing I think I might be be suited for on the project.  I'm in University right now, but I can probably spare a day here or there to work on it.

EDIT: It seems JmonkeyEngine can plug into this GUI api quite nicely. [http://jmonkeyengine.org/2010/04/06/jmonkeyengine-3-0-gets-a-very-nifty-gui/](http://jmonkeyengine.org/2010/04/06/jmonkeyengine-3-0-gets-a-very-nifty-gui/)  This would be a really easy way to get a gui going, but the downside to using this one is that it won't be that unique.  I could also work on the GUI from scratch.  Both ways I think would be good choices.  I'm actually leaning a little bit more towards making it from scratch, since that will ultimately give us more freedom, and we can probably do some much cooler stuff with it.

---

### Post by gemmahenchmen on 2011-02-07
> **Finalfantasykid said:**
> ^GUI design was the thing I think I might be be suited for on the project.  I'm in University right now, but I can probably spare a day here or there to work on it.

EDIT: It seems JmonkeyEngine can plug into this GUI api quite nicely. [http://jmonkeyengine.org/2010/04/06/jmonkeyengine-3-0-gets-a-very-nifty-gui/](http://jmonkeyengine.org/2010/04/06/jmonkeyengine-3-0-gets-a-very-nifty-gui/)  This would be a really easy way to get a gui going, but the downside to using this one is that it won't be that unique.  I could also work on the GUI from scratch.  Both ways I think would be good choices.  I'm actually leaning a little bit more towards making it from scratch, since that will ultimately give us more freedom, and we can probably do some much cooler stuff with it.
If making it from scratch is practical then it's probably better. See how hard it is.

---

### Post by Modplanman on 2011-02-07
> **gemmahenchmen said:**
> 
On that topic: Anyone out there either a 3d modeller or know of a site with free 3d models of buildings and such? I could probably make it to some extent myself, but it would be great to have a skilled modeller make them. I'm planning to roll out a second map that looks a lot better and has some improved elements such as sky, light bulbs producing light, shadows, shaders etc. in the next 2-4 weeks depending on A) If anyone can provide models and textures and B) If I run into any problems transitioning into a new computer. This new map will probably be 0.2.0, because of the graphics engine upgrades.


[http://opengameart.org/](http://opengameart.org/)

[http://media.ryzom.com/](http://media.ryzom.com/)

[http://creativecommons.org/](http://creativecommons.org/)

[http://mocap.cs.cmu.edu/](http://mocap.cs.cmu.edu/)

Plunder away.

---

### Post by gemmahenchmen on 2011-02-07
> **Modplanman said:**
> [http://opengameart.org/](http://opengameart.org/)

[http://media.ryzom.com/](http://media.ryzom.com/)

[http://creativecommons.org/](http://creativecommons.org/)

[http://mocap.cs.cmu.edu/](http://mocap.cs.cmu.edu/)

Plunder away.
That's great! Especially the motion capture one- I'll look into using that for animation.

EDIT:
So I've been looking through opengameart.org and have found some  models which could be good to use for the project. Here's a list below:


Some modern soldiers, they could be the army faction. This page is for the textures, but links to models for all of the models:
[http://opengameart.org/content/250-modern-uniform-and-armor-textures-ufoai](http://opengameart.org/content/250-modern-uniform-and-armor-textures-ufoai)


Some  ruined building parts. There seem to be a lot of them, so they could be  the basis for a map (we'd just have to add snow to the textures):
[http://opengameart.org/content/destroyed-walls-3d-models](http://opengameart.org/content/destroyed-walls-3d-models)


A load of 3d weapons for the FPS view (looks like they come with arms too):
[http://opengameart.org/content/fps-weapons](http://opengameart.org/content/fps-weapons)
Anything else anyone suggests can be added on the site too so everyone can see it.


A reminder for anyone new joining, the site is frozenproject.org.
Also, Finalfantasykid, I think the reason you can't post may be because it's admin-only. I'll check and try to make it free to post.

---

### Post by 501st_alpha1 on 2011-02-07
> **gemmahenchmen said:**
> You need to download the project from SVN...

Right... I knew that! :oops:

However, I have a new problem. Whenever I attempt to test it, it crashes on startup.
Just to be clear, it's the files under svn/trunk/share/ on the Google Code page right? I tried both 0.0.8-test and 0.0.8.1, with the same result for each.

---

### Post by gemmahenchmen on 2011-02-08
> **501st_alpha1 said:**
> Right... I knew that! :oops:

However, I have a new problem. Whenever I attempt to test it, it crashes on startup.
Just to be clear, it's the files under svn/trunk/share/ on the Google Code page right? I tried both 0.0.8-test and 0.0.8.1, with the same result for each.
You had to compile it from source. You must be running the .zip ones, which don't work. I'll just made a .zip of it which works. It's called Frozen-0.1.0.zip, under svn/trunk/share/

---

### Post by 501st_alpha1 on 2011-02-08
> **gemmahenchmen said:**
> You had to compile it from source. You must be running the .zip ones, which don't work. I'll just made a .zip of it which works. It's called Frozen-0.1.0.zip, under svn/trunk/share/

Thanks, I downloaded the .zip, and it runs successfully. I have four notes: first, when I first start it up, it runs at single-digit fps, however, after a couple minutes, it gets up to around 40-60. Secondly, the move speed is a little fast.. I assume that's still a work in progress? Third, a couple of the smaller objects have no collision detection. Finally, the textures on the large building kind of flicker.

Otherwise, good job so far! This is a great start!

One more question: where would be the best place to post feedback? I looked on the project's forum page, but I don't see any forums listed. I assume one must join first? Would you rather I post there or here? (Or does it matter?)

Edit: I just right-clicked, the cannon-ball is awesome! Is it supposed to originate from the camera? (It doesn't seem to.) Also, is left clicking supposed to do something?

(Sorry if I'm overwhelming you with questions...)

---

### Post by gemmahenchmen on 2011-02-08
> **501st_alpha1 said:**
> Thanks, I downloaded the .zip, and it runs successfully. I have four notes: first, when I first start it up, it runs at single-digit fps, however, after a couple minutes, it gets up to around 40-60. Secondly, the move speed is a little fast.. I assume that's still a work in progress? Third, a couple of the smaller objects have no collision detection. Finally, the textures on the large building kind of flicker.

Otherwise, good job so far! This is a great start!

One more question: where would be the best place to post feedback? I looked on the project's forum page, but I don't see any forums listed. I assume one must join first? Would you rather I post there or here? (Or does it matter?)

Edit: I just right-clicked, the cannon-ball is awesome! Is it supposed to originate from the camera? (It doesn't seem to.) Also, is left clicking supposed to do something?

(Sorry if I'm overwhelming you with questions...)
There's no problem with asking lots of questions, I'd rather you did than just act confused.

First, the low fps to start with is because it's currently using a dated physics engine, I'm currently working on replacing it.

The cannonball isn't supposed to originate from the camera, it's supposed to originate from a point in the sky and destroy the brick wall.

The flicker on the large building is because there's something wrong with the model. Maybe joost (jpv89) will fix it, or we'll just use different models.

Feedback can go either here or on the site. To get access to the forums on the site, you need to create an account then join the group "contributors", then you should be able to post. I'd prefer to have posts on the site when there are a lot of contributors, but for now I don't really care. I check both.

The move speed can be changed whenever we want. For now, fine-tuning it isn't worth the effort.

All the objects have collision detection except for the "enemies", the colored boxes. Also, that's what left click is for. If you aim at one of the colored boxes and left click, it puts a red mark on it where you would have hit.

Finally, if you create an account on the site, either use the same login you use here or tell me who you are. I'd like to be able to tell who I'm talking to on the site and thread here.

---

### Post by 501st_alpha1 on 2011-02-08
Okay, sounds good.

I registered at the site as 501stalpha1, since it won't allow punctuation. I'm still waiting on the activation email, so I can't access the forums yet.

---

### Post by SirDakkalot on 2011-02-09
This looks interesting. I don't think I'd be able to help much on the programming side of things, but I'm an amateur writer, so I could maybe help out a bit with story, dialogue, character concepts etc.

---

### Post by 501st_alpha1 on 2011-02-09
Hmm... I still haven't gotten the activation email, and it won't let me log in until I activate. Any ideas?

---

### Post by gemmahenchmen on 2011-02-10
> **SirDakkalot said:**
> This looks interesting. I don't think I'd be able to help much on the programming side of things, but I'm an amateur writer, so I could maybe help out a bit with story, dialogue, character concepts etc.
That's good, we don't really have much of a story going except for the basic premise. Create an account on the site at frozenproject.org and post what you come up with. Since the project's so small, chances are we'll use whatever you suggest.

> **501st_alpha1 said:**
> Hmm... I still haven't gotten the  activation email, and it won't let me log in until I activate. Any  ideas?
I don't know. Joost was managing the site, but I haven't had any contact  with him for a couple of weeks. I'll have a look into it. For now,  posting here is fine.

---

### Post by SirDakkalot on 2011-02-11
> **gemmahenchmen said:**
> That's good, we don't really have much of a story going except for the basic premise. Create an account on the site at frozenproject.org and post what you come up with. Since the project's so small, chances are we'll use whatever you suggest.

I haven't had much of a chance to think on it, really. I was mainly waiting for a reply. I'd like to hear some of your guys ideas on what you're looking for before I put some really heavy thought into it. First of all, I need to know what kind of gameplay you're going for. Is it open-world or something more along the lines of Global Agenda? I also need to know if you'd prefer accessibility (Make it easier for the player to step into his character's shoes etc.), something more open, or a deeper storyline. I also need to know if there's going to be quests and such, and how many factions there will be.

Note that I'm tired, so I might just be spouting gibberish.

---

### Post by gemmahenchmen on 2011-02-12
> **SirDakkalot said:**
> I haven't had much of a chance to think on it, really. I was mainly waiting for a reply. I'd like to hear some of your guys ideas on what you're looking for before I put some really heavy thought into it. First of all, I need to know what kind of gameplay you're going for. Is it open-world or something more along the lines of Global Agenda? I also need to know if you'd prefer accessibility (Make it easier for the player to step into his character's shoes etc.), something more open, or a deeper storyline. I also need to know if there's going to be quests and such, and how many factions there will be.

Note that I'm tired, so I might just be spouting gibberish.
What I think we should have is an open-world game with a storyline running underneath it, but allowing the player to make all kinds of choices along the way, so that they can invent their own character. The plan is for it to be MMO, so there are mostly real players you interact with.

---

### Post by gemmahenchmen on 2011-02-20
Just reminding everyone that this project is still alive and kicking. :P

I'm working on rolling out 0.2.0, which should include a number of new features for sure, such as a new map, the ability to choose between maps (this is largely resting on  for making the GUI), enemies that are humans not cubes, and possibly some sort of proper interaction with enemies, such as shooting them, them shooting back etc. This will probably take the form of them always facing towards you to prove tracking to work, and them either disappearing or carrying out a death animation when they're shot.

On top of this, which will mostly be done by me, I want to add a few more features for the community to do. Here are some ideas I had, which any of you might be able to help with:

[LIST]
[*]Suitable 3d models: people, buildings or objects
[*]Storyline: At the moment we have a concept, but no storyline. Come up with whatever you want, and chances are we'll use it if it's good.
[*]Coding features: Since I've been so busy lately, my coding time has been limited. If anyone else cares to implement any extra features like shadows, skies, multithreaded physics, multiplayer etc., any of these would be great and extremely helpful. If there is any help here it'll rapidly accelerate the development.
[/LIST]

---

### Post by gemmahenchmen on 2011-04-04
It took nearly a month, but version 0.2.0 is finally done, and it's a big update. Here are the new features I've implemented:
 
[LIST]
[*]Added animated enemy that follows the player and stops when within a certain distance
[*]Added good shadow rendering using PSSM
[*]Added better lighting (diffuse lighting and ambient lighting)
[*]Moved to more recent physics engine over deprecated SimpleBulletApplication
[*]Added new map
[*]Added sky
[/LIST]
 In practice this means that there has been a huge improvement in  graphics quality, and I've figured out how to make animated models move  and respond to user input, so this project isn't far from being a proper  game. There are still a few minor bugs, such as:
 
[LIST]
[*]Jumping is glitchy
[*]The enemy walks on the spot for a moment before stopping when it enters a certain distance from the player
[*]Sometimes the player's view vibrates up and down at certain locations
[/LIST]
 If you notice any other bugs, point them out.
 From now on, rather than saving every new feature up for a major  release, I'm going to start releasing weekly updates so it's more  obvious that development's happening and community interaction can be  more frequent.
 You can download the source and assets with an SVN checkout, you can download the game jar on its own from [here]("http://frozenproject.googlecode.com/svn/trunk/test/Frozen-0.2.0.jar").
The website for the project is frozenproject.org, the project files are hosted at [http://code.google.com/p/frozenproject/](http://code.google.com/p/frozenproject/)

---

### Post by kailkitsune on 2011-04-04
Well this is interesting, I'll be downloading the source later tonight when my router isn't bogged down with my other computers.

I'm no programmer (yet), but i do have one heck of an imagination. If you need any thoughts on story line let me know, I've been righting short stories for years and I'm looking to do something more. I've got a good bit of time on my hands at night so pitching ideas, or righting out dialoge and plot sounds like a good way to use my time then.

send me a pm if your interested in the help ^_^

---

### Post by Ezeh on 2011-04-06
This is looking fantastic!
All the best with development :)

---

### Post by kn0w-b1nary on 2011-04-12
> **kailkitsune said:**
> I'm no programmer (yet), but i do have one heck of an imagination. If you need any thoughts on story line let me know, I've been righting short stories for years and I'm looking to do something more. I've got a good bit of time on my hands at night so pitching ideas, or righting out dialoge and plot sounds like a good way to use my time then.
 
send me a pm if your interested in the help ^_^
 
Same thing here, am willing to spend time brainstorming. :)

---

### Post by kseise on 2011-04-17
I just went to check it out, but your website is down.  The homepage says that the account is not active.

---

### Post by mips on 2011-04-17
Screenshots?

---

### Post by m0a0t0 on 2011-04-19
Hi, I thing the new lighting has some problems. Occasionally all the models will go black.
This is the output:
```

19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform g_WorldViewMatrix is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform m_UseMaterialColors is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform m_Ambient is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform m_Diffuse is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform m_Specular is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform m_Shininess is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform g_CameraPosition is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform g_WorldMatrix is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform m_UseMaterialColors is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform g_NormalMatrix is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform m_HardwareShadows is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform m_FilterMode is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform m_PCFEdge is not declared in shader.
19-Apr-2011 10:22:16 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform m_VertexColor is not declared in shader.
19-Apr-2011 10:22:30 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform g_CameraPosition is not declared in shader.
19-Apr-2011 10:22:30 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform g_WorldMatrix is not declared in shader.
19-Apr-2011 10:22:30 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform m_UseVertexColor is not declared in shader.
19-Apr-2011 10:22:30 com.jme3.renderer.lwjgl.LwjglRenderer updateUniformLocation
INFO: Uniform m_UseMaterialColors is not declared in shader.

```

Other than that it looks cool so far! Maybe you should split the code into different files though? :P

---

### Post by gemmahenchmen on 2011-04-20
> **m0a0t0 said:**
> Hi, I thing the new lighting has some problems. Occasionally all the models will go black.
Are your graphics drivers fully updated? I don't get that problem on my machine.
> **m0a0t0 said:**
> Other than that it looks cool so far! Maybe you should split the code into different files though?
Not really the top of my priorities at this point - as it is a very early stage the code's messy, but I'll organize it more efficiently when all of the main functionality has been done.
> **kseise said:**
> I just went to check it out, but your website is down.  The homepage says that the account is not active.
I'm aware of this, someone else is running the site and he is aware of the issue. Hopefully it will be back up soon.
> **kn0w-b1nary said:**
> Same thing here, am willing to spend time brainstorming. :)
Great, post any ideas you have in this thread.
> **mips said:**
> Screenshots?
Sure, they're attached below. The third is showing off the water effect, but it's not yet in the latest release, which is available here: [http://code.google.com/p/frozenproject/source/browse/trunk/test/Frozen-0.2.0.jar](http://code.google.com/p/frozenproject/source/browse/trunk/test/Frozen-0.2.0.jar)

---

### Post by kaisix on 2011-08-14
Dead?

---

### Post by Dlambert on 2011-08-14
> **jpv89 said:**
> Sure, I'd love to go into more detail. This is what I wrote up about a year back:

In an attempt to fight global warming, scientists created / genetically altered a species of algae to consume the excess carbon-dioxide. First contained in a dozen lakes, the algae escaped as one of the lakes was flooded. As it reached sea the algae spread rapidly over the world's oceans, in it's growth consuming more and more CO2. 

CO2, being a greenhouse gas, has been keeping our planet at a nice temperature for billions of years now. Depleting the atmosphere of too much CO2 would cause the sun's heat to escape the earth too easily, thereby cooling off our planet.

So this is what happened. The only places on earth the ice hasn't reached are some island on the equator, which due to their location have remained ice-free and at medium temperatures. 

On one of the islands is a massive city, with rich suburbs and and nice downtown area. Overlooking the city, against the mountains, are massive favelas (a bit like Rio de Janeiro). I'm guessing the city would be dominated by gangs fighting over territory, where players are the ones who conquer territory for their gang and good tactics have to be employed to achieve victory. This means the neighborhoods would evolve constantly, all depending on the gang that has it in it's power.

If the players would go north or south they'd meet the ice. With dozens of stations scattered throughout the glaciers, these would also be part of the struggle. A captured station would supply the gang with valuable resources to improve their territory in the city.

Same goes for the forests on the island. 



So that was my idea. Tell me what you think!

Thats a great game idea

---

### Post by Quadunit404 on 2011-08-15
> **kaisix said:**
> Dead?

Unfortunately. In my opinion this had potential and a lot of it.

---

### Post by BrianDK on 2011-08-15
> **gemmahenchmen said:**
> Hey everyone.

I've decided to start work on a game development project for ubuntu (possibly multi-platform). I'm looking at something along the lines of a FPS, MMORPG onlinecdkeyseller.com of some kind that could be fully or partially open source (depending on the kind of support the project gets). I'm open to ideas at the moment, and any support would be greatly appreciated.

I'm planning to program it using the Java 3D API, but if anyone can recommend a platform-independent or ubuntu-specific way to achieve this that is better, using either C++ or Java (I'm actually more competent in C++, but the Java 3D API seems like my best bet so far), then I'd be happy to hear it.

I have a decent grasp of animation in Blender and such, but if this gets real then animation and design people would be great too.

My current concept for the game is as follows:
Some sort of First Person Shooter. They are my favourite games to play and it saves any extra animation work from making a 3rd person game.
Some sort of MMO, I like the idea of being able to work together with other people and it being really helpful, but not necessarily required.
I don't have a theme yet, but I'm thinking zombies? Nuclear apocalypse? Something where society's collapsed and it's all about collaborating with each other to rebuild fortifications and stuff, but zombies/terrorists/enemy soldiers keep trying to attack you. The idea's probably that there'll be lots of weak enemies that are NPCs but a few real players that are particularly powerful.

If anyone has ideas or is keen to help, then reply here. Until I've got some indication of its success I'm directing my efforts at mastering the 3d API before making a website or anything. This is probably going to be a big project, but I've got the next 3 weeks free to do some intense work to get the wheels going then will supervise and contribute from there.

Mate would gladly try this:P

---

### Post by Sofox on 2011-08-16
I'm no expert with this sort of stuff, but if you started it as a Doom3 mod it would become standalone when the engine becomes open source.

Though to be honest, I don't think it's very good at open world stuff.

---

### Post by Dr. Awesome on 2011-08-16
This is exactly the sort of thing I've been looking into for a while now. Unfortunately, I'm still a rookie at all this programming and such, I just started reading a book about Python, so what I'm really looking for is to sort of "be in the loop" with this, just so I can get some experience? If that's okay, I don't want to be much of a hindrance.

Just being notified of what's being done (and how, some of the times) would be great. Also, I'm completely unfamiliar with any of these programming languages, but I'm willing to learn if they're a better choice than Python.

---

### Post by DangerOnTheRanger on 2011-08-16
> **Dr. Awesome said:**
> This is exactly the sort of thing I've been looking into for a while now. Unfortunately, I'm still a rookie at all this programming and such, I just started reading a book about Python, so what I'm really looking for is to sort of "be in the loop" with this, just so I can get some experience? If that's okay, I don't want to be much of a hindrance.

Just being notified of what's being done (and how, some of the times) would be great. Also, I'm completely unfamiliar with any of these programming languages, but I'm willing to learn if they're a better choice than Python.

I think this project is dead, unfortunately :(
However, I'd be happy to let you on the team of my Python game project ([http://openblox.sourceforge.net]("http://openblox.sourceforge.net/")) as a programmer - most of the code is pretty simple, and it's 100% pure Python, save for some Cg shaders.

---

### Post by Dr. Awesome on 2011-08-16
> **DangerOnTheRanger said:**
> I think this project is dead, unfortunately :(
However, I'd be happy to let you on the team of my Python game project ([http://openblox.sourceforge.net]("http://openblox.sourceforge.net/")) as a programmer - most of the code is pretty simple, and it's 100% pure Python, save for some Cg shaders.
That would be awesome :D As long as there's other programmers who will tolerate my being new. How do I sign up?

---

### Post by DangerOnTheRanger on 2011-08-16
I'll send you PMs on how to do that - I don't want to hijack this thread :)

---

### Post by gemmahenchmen on 2011-08-25
I'm thinking of reviving this, since suddenly there seems to be so much interest. It was just put on hold because my workload suddenly skyrocketed, but I'm moving back to doing this in weekends. I've been working some more on this, and it's almost at a point where i can just plug in contributors' 3D models etc.

If anyone's interested in this, continue to post here. The old site's gone, so this will be the main line of communication. I'd like to hear that people are still willing to contribute.

---

### Post by kunal00731 on 2011-08-25
Hi [COLOR=Black]** gemmahenchmen** ,

I have been following this project of  yours  for a long time now, previously i was not a member of this site, though today i have become one. The development of your project was really brilliant. Seen the screen shots also, they look good. 

I am a software professional from India and work in Cognizant Technology Solutions, i have some experience in bash, python  and perl . 

Right now i am working in Java.

Currently I am a little busy with my deliverables but  if you do need any help from me, i will be glad to do so, to the best of my knowledge. 
[/COLOR]

---

### Post by Furcifer on 2011-10-12
Fps ftw!!!

---


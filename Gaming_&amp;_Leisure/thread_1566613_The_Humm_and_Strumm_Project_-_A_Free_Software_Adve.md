---
title: "The Humm and Strumm Project - A Free Software Adventure Game"
date: 2010-09-02
forum: Gaming &amp; Leisure
---

### Post by PatrickNiedzielski on 2010-09-02
Hi all,

While this project has existed for a little while now, I think it is time to clarify our principles and maybe to get the word out a little more.  Now, we have a new website, a final look, and some good code under our belt. I feel that this is the best time to explain our goals and reasons for this project.

Please note, I am cross posting this on several different forum sites. It will also be copied onto our wiki with some slight edits, so it will be able to be accessed in the future.

[img]http://hummstrumm.googlecode.com/svn/website/res/logo-large.png[/img]
[Our Homepage](http://hummstrumm.blogspot.com/)

**What is Humm and Strumm?**

Humm and Strumm is two things: a Free Software project meant to fill a niche that has not been filled before in the Free Software community, and the game which we will produce.

Our project is open and transparent. We try to make all design decisions available for comment. Any development news is reported on our blog. Our project is active. We are driven to create the game, and looking for any help (be it in development or just in spreading the word around). We are friendly. Email anyone on the team, and we will get back to you as soon as we can. Our hummstrumm-user mailing list is open to the public. Contributors just need to join our hummstrmm-contrib mailing list and send us a patch or file. It's that simple. Even if it is just to tell us that you await our releases, we would love to hear from you.

The game itself is something we have not seen in the Free Software community before: a multiplayer, 3D, cartoon adventure game, in which players much defeat the evil Dr. Geoff before he takes over the world. This is an experiment. Traditionally, Free Software games have not been plot based. Look at [SuperTuxKart](http://supertuxkart.sourceforge.net/), [OpenArena](http://openarena.ws/smfnews.php), or [Lincity-NG](http://lincity-ng.berlios.de/wiki/index.php/Main_Page). These are all great games, which show what Free Software is capable of. But our game has a plot, one which will be available completely online within the next month or two. What does this mean? It means anyone can read the plot without playing the game. It means that our game will be, and is currently being, released before everything is the plot is done. The user may have an incomplete product, which may taint their view of it. We feel that this is not so, and we want to pave the world for other adventure games of professional quality in the Free Software community.

**What are your goals?**

The Humm and Strumm Project is based on three pillars: openness, inclusiveness, and friendliness.

Openness: We want to get the word out, and we realize that in such a small project, a few teasers are not going to do this. We feel that the more open we are, the more likely people will be to follow our development or even contribute. Sure, we could take the path of the [Morevna Project](http://morevnaproject.org/), which looks like a great anime project, but is [not completely open](http://morevnaproject.org/2010/06/25/private-or-not-private/). Humm and Strumm, though, will take an open approach, and publish everything we do immediately.

Inclusiveness: This pillar is perhaps the simplest, but it has the most far reaching consequences. We want to include anyone in our project and community. Developers, artists, power users, users of Windows, users of Linux, users who aren't sure which Operating System they use. To me, one of the most amazing parts of Free Software is the ability to bring people together. We aim not to block anyone's entry into the project. Simple, right?

One of the consequences of this is that we want anyone to be able to play our game in their native language. While this certainly is not possible for everyone, it is definitely possible for many of the world's languages. From a technology point of view, this means supporting Unicode (which will be in our next release) and reading translation files. From a translation point of view, this means collaborating with people from across the world to make a good project. Hence, inclusiveness.

Another consequence is that we want the game to be able to take advantage of new hardware but not penalize users of old hardware. Of course we want the greatest experience for our users, but we also do not want to exclude anyone if their computer is not a new, 2010, multicore computer.

Friendliness: This should go without saying, but it cannot. Users and developers should not feel afraid to ask for help or contact us personally. There will be the occasional butting of heads, but we want to remain as civilized as possible. Not only does this look good for us, but it helps keep the project afloat.

**So this is just a game, right?**

No! This project hopes to deliver an engine, too! You are probably asking why we are making a game engine from scratch. The answer is simple: learning, elegance, and scalability.

Learning: Yes, one reason is to learn how it is done. Both development members on our team have good development experience; this is not an attempt by someone new to development to create the next best game engine to rival Crysis. While it is an ambitious product, it is well thought-out and planned.

Elegance: Take most open source "game engines" as an example here. Usually, they are not in fact game engines, but rather graphics engines with various other technologies tacked on as an afterthought. [Ogre3D](http://www.ogre3d.org/) and [Irrlicht](http://irrlicht.sourceforge.net/), as good as they are at 3D graphics, were not designed with audio, extended input, and video. Certainly one can do these with either engine, but the support is not built-in, and the projects which one must force into service were not designed to be used with Ogre or Irrlicht specifically, and often require hacks and data duplication to work fully. It is hard to fully integrate these external libraries. [SDL](http://www.libsdl.org/), on the other hand, does integrate many of these things, but it is not as good at 3D as Irrlicht or Ogre. You have to code much of the OpenGL yourself -- not acceptable in a game engine. The Humm and Strumm Engine aims to tackle this, by integrating everything in the design.

Scalability: None of the above mentioned game engines scale terribly well. Ogre scales very well upwards, but not so well downwards (as shown by my machine and other machines I have tested it on, which are not low end machines by any means). Irrlicht, on the other hand, was aimed at being fast for middle to low end machines, and provides some nifty features for computers like mine which no other engine can do as quickly. It too, though, fails at scaling in the opposite direction. We believe this to be completely possible; in fact, it is one of the backbone points of our design.

**Who is on the project?**

I am Patrick Niedzielsk, one of the developers of the game engine. I work on anything that needs to be done within the engine, and currently package the engine for each release.
Email: [email]PatrickNiedzielski@gmail.com[/email]

My codeveloper is Ricardo Tiago. While I am working on the framework of the engine, and various bits and pieces that need to be done, Ricardo is our graphics man.
Email: [email]RTiago@gmail.com[/email]

We also have a new addition, an artist named Saad Butt. With the next release, he will have concept art from which to work, and soon after, we should have some great models.
Email: [email]butt.sahib911@gmail.com[/email]

**Where can I find out more?**

First and foremost, you can visit [our website](http://hummstrumm.blogspot.com/), from which you can find most all the information on our project.

Second, post here. I will reply to any posts. Ask something specific, tell me you like the idea, tell me you don't like the idea, whatever.

Third, contact one of us. We will get back to you as soon as possible.

Finally, if any of you are interested in development updates from us, [subscribe](http://feeds.feedburner.com/hummstrumm) to our blog or like us on [Facebook](http://www.facebook.com/pages/The-Humm-and-Strumm-Video-Game/226199767138).

Best regards from all of us,
The Humm and Strumm Project

---

### Post by Naiki Muliaina on 2010-09-02
Good stuff, I agree with you on some of the Linux game engines not really be game engines. Blender / Crystal Space strikes me as doing a better job than most on a high end level. As a thought on that, are you aiming for high end gaming with plush graphics or the indie game level or the level of half the games in the Ubuntu repos?

---

### Post by PatrickNiedzielski on 2010-09-02
Naiki,

Thanks!  I've played a little with the Blender Engine in the past, but I found it way too slow!  For all the amazingness of Blender, being a game engine is not one of its strong points.

For graphics, we want as good as we can get, but we don't want to drop support for lower end machines.  These goals are contradictory, but it is possible to make some sacrifices on both, and get a nice balance.  I believe the best way to reach this compromise is, in our engine, dynamically turn off some features or decrease quality.  The user can go in a dialog and then fine tune the settings themselves If They Desire, but the game should not penalize any user.  We want to stick to this belief as much as possible.

As you pointed out, many Free Software games are not at professional quality, regardless of if they are good games by any other standard.  I'm not sure if we are up to coding the next greatest thing in game development, but we don't want it to look blocky and old.  If Humm and Strumm can show that we can make a good looking game, then we can show that anyone can.  Saad is a very good modeler, he has shown with his artwork on his DeviantArt page.  Once I upload the concept art, we can start talking about how to make how to make resources that both look good and scale.  It may be that we have to create two sets of resources.

Thanks for your interest!

---

### Post by Naiki Muliaina on 2010-09-02
Ahh cool, so your aiming at the indie level. Personally I love games like Machinarium, Osmos, Irukandji, and the likes. If World Of Goo had the best top level Half Life 2 graphics, it wouldn't have been as half as enjoyable. I love clean crisp graphics, and I shall admit, looks are important to me. I cant play squared off SNES era games. But good graphics doesn't mean everything needs to look like Half Life 2 :)

I look forward to seeing what comes from your project. :popcorn:

---

### Post by DrMelon on 2010-09-02
Sounds good. I'm a small-time game developer, and a Linux based game engine is something I have sorely missed.

---

### Post by PatrickNiedzielski on 2010-09-02
> **Naiki Muliaina said:**
> Ahh cool, so your aiming at the indie level. Personally I love games like Machinarium, Osmos, Irukandji, and the likes. If World Of Goo had the best top level Half Life 2 graphics, it wouldn't have been as half as enjoyable. I love clean crisp graphics, and I shall admit, looks are important to me. I cant play squared off SNES era games. But good graphics doesn't mean everything needs to look like Half Life 2 :)

I look forward to seeing what comes from your project. :popcorn:

Well, aren't those games 2D?  Humm and Strumm will not be quite at the level of Half Life 2, but it will be fully 3D.  Graphics wise, I hope for it to be comparable to the new Spyro games (at its best):
[img]http://media.teamxbox.com/games/ss/1448/1157040851.jpg[/img]

We definitely have the artistic resources to do this, and I believe in our coding ability. ^_^

Thank you for your support, and I encourage you to subscribe to our feed from the main site; you'll get development updates, and as they start rolling out, concept art and screen shots!

Thanks!

---

### Post by PatrickNiedzielski on 2010-09-02
> **DrMelon said:**
> Sounds good. I'm a small-time game developer, and a Linux based game engine is something I have sorely missed.

Humm and Strumm will be a cross platform game, as much as we can make it.  For now, all our development is on GNU/Linux (I use Debian, so there will definitely be a package for Ubuntu.)  This should simplify a lot for us and other developers.  Our engine is licensed under the GPLv3 (or later), though, so any derivative games will have to be licensed similarly.

Despite this, if you want to you our engine when it is complete, please feel free to!  It will not be coupled to our game in any way, and by design, new file formats and such can be easily implemented.

---

### Post by Naiki Muliaina on 2010-09-02
Cool. The current Spryo games look pretty cool. Good look good sirs! :)

---

### Post by PatrickNiedzielski on 2010-09-03
Thanks, Naiki!

---


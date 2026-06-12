---
title: "::: Z E R O 2 D ::: open source fighter engine -- seeking contributors!"
date: 2009-10-01
forum: Gaming &amp; Leisure
---

### Post by TheBuzzSaw on 2009-10-01
[img]http://smashnexus.net/remote/zero2d_medium.png[/img]

[http://code.google.com/p/zero2d/](http://code.google.com/p/zero2d/) -- SVN is active!
[http://www.zero2d.com/](http://www.zero2d.com/) -- Get involved here!

--- --- ---

We have an IRC room as well. :)
The server is irc.acidchat.net. The channel is #zero2d.

--- --- ---

This has been a long time coming. I have always wanted to make my own PC game fighter inspired by Super Smash Bros. king-of-the-hill platformer style combat. Here are the important facts surrounding this project:

* Zero2D will be built in the spirit of MUGEN. It will operate as a generic engine and allow the community to add characters and stages freely.
* Zero2D will be written in C++ for optimal performance and guaranteed support for the big three (Windows, Macintosh, and GNU/Linux).
* Zero2D will be a 2D fighter using sprites. This is to ensure that anyone can contribute to the fighter/stage rosters.
* Zero2D will be open source. Programmers can contribute to the engine, while the rest of the community will help form characters and stages (no programming knowledge will be necessary).
* Zero2D will pave the way for a truly competitive smash fighter. By having absolute control over all aspects of the game, true balance can be attained! (Of course, people can also make insanely broken characters for their own leisure.)
* Zero2D will offer superior online play. LAN play will also be an option. (Screw you, Blizzard!)

--

I wasn't sure whether to put this in Gaming or Programming. It is a game project that has garnered much support (artists, musicians, etc.) but only has a bare-bones engine in the works.

---

### Post by donkyhotay on 2009-10-01
If it's in the wrong place an admin will move it for you but since it is a game it's probably in the right place. I wish you luck on the project, looks like a good idea and I hope it actually gets somewhere but I will tell you from experience keeping an open-source gaming project alive is *alot* of work and many of them die out.

---

### Post by TheBuzzSaw on 2009-10-01
> **donkyhotay said:**
> If it's in the wrong place an admin will move it for you but since it is a game it's probably in the right place. I wish you luck on the project, looks like a good idea and I hope it actually gets somewhere but I will tell you from experience keeping an open-source gaming project alive is *alot* of work and many of them die out.
Yeah, I am fairly optimistic. I'm not a 17-year-old with a "really cool idea". I am a senior college student who has already begun serious work on the project. I have people working on art and music. I expect to fly solo for long stretches, but I am ready. :)

---

### Post by j.bell730 on 2009-10-01
Oooh, I'm impressed. Looks quite nifty. I'm contemplating hopping onto your IRC channel to see if there's anything I can do (I am not a programmer, sadly).

---

### Post by Clopin on 2009-10-02
I'm still at the first stages with C++ **and** SDL, but I'd love to help out with whatever I can.

---

### Post by MaximB on 2009-10-02
I few questiong if I may...

We already got Mugen, and while only the earlier versions support Linux it's working...
What makes your project better the Mugen ?
Could your enigine use Mugen's characters/spirits/stages/sounds/whatever ?

I've also heard of a similar project (forgot it's name) that intends to create a Linux version.

P.S
Now that elecbyte is revived there might be a chance for an official current Linux version.

---

### Post by TheBuzzSaw on 2009-10-02
> **Clopin said:**
> I'm still at the first stages with C++ **and** SDL, but I'd love to help out with whatever I can.
Take a look at the code. I'm sure you'll find it is far from intimidating (though I really ought to put more comments in).

> **MaximB said:**
> I few questiong if I may...

We already got Mugen, and while only the earlier versions support Linux it's working...
What makes your project better the Mugen ?
Could your enigine use Mugen's characters/spirits/stages/sounds/whatever ?
While I did take *some* inspiration from MUGEN (primarily just the idea of letting the community add characters/stages freely), the underlying premise of the game will be quite different. MUGEN was designed to mimic Street Fighter, Marvel vs Capcom, etc. Zero2D aims to mimic the Super Smash Bros. series (and more recently, TMNT Smash Up) in that the players are free to roam (platformer style), and the objective is to KO the opponent off the stage, not reduce health to zero.

My goal is not so much to be "better" than MUGEN so much as it is to simply serve another audience. For years, I was a competitive Super Smash Bros. Melee player. I traveled to several states competing with the best and make quite a bit of money doing it. As a result, I have a particular fondness of smash combat. :)

---

### Post by MaximB on 2009-10-02
...And I was hoping for some fighting game engine...

---

### Post by TheBuzzSaw on 2009-10-02
> **MaximB said:**
> ...And I was hoping for some fighting game engine...
What is that supposed to mean?

---

### Post by MaximB on 2009-10-02
> **TheBuzzSaw said:**
> What is that supposed to mean?

Like updated MUGEN clone, so I can use the spirits/stages/fighters ... you know...
Not like Super Mario...

---

### Post by TheBuzzSaw on 2009-10-02
> **MaximB said:**
> Like updated MUGEN clone, so I can use the spirits/stages/fighters ... you know...
Not like Super Mario...

You said yourself that a potential MUGEN update is in the works. Why would you want me to make another MUGEN?

LOL! Have you played SSB? It is one of the most fantastic games with extremely large followings. You can find a smash tournament just about every weekend in any part of America. I don't know many other games that feature that. ;)

---

### Post by BigSilly on 2009-10-02
I can't wait to see what this brings for Linux gamers! We're all massive Smash Bros. fans in our house. Thanks for letting us know of your project. This could really rock...

:guitar:

---

### Post by hessiess on 2009-10-02
Make it resolution independent, i.e. DONT use SDL without OpenGL. Also make sure you anti alias your graphics, theare is no reason whatsoever for using 1 bit transparency any more.

---

### Post by TheBuzzSaw on 2009-10-02
> **hessiess said:**
> Make it resolution independent, i.e. DONT use SDL without OpenGL. Also make sure you anti alias your graphics, theare is no reason whatsoever for using 1 bit transparency any more.
It should be fairly resolution-agnostic. And yeah, I am using SDL_image and PNG images. :)

I am in a 3D graphics course learning OpenGL at the moment. For now, the engine will be pure SDL, but I could probably make the changes over the next couple months.

---

### Post by hessiess on 2009-10-02
> **TheBuzzSaw said:**
> It should be fairly resolution-agnostic. And yeah, I am using SDL_image and PNG images. :)

I am in a 3D graphics course learning OpenGL at the moment. For now, the engine will be pure SDL, but I could probably make the changes over the next couple months.

Using OpenGL for 2D game development is trivial and will give you a huge performance boost, espetily if you are doing resolution independence. Software implementations of Bilinier image filtering are VERRY slow. 

For an example of using OpenGL for 2D, take a look at the qr_renderer source file in Quad-ren.

With SDL, you need to pass the SDL_RESIZABLE flag and catch window resize events.

In my opinion, SDL is far to low level for what it is commonly used for, you will just end up re inventing loads of boilerplate code like scene graphs and so on.

---

### Post by TheBuzzSaw on 2009-10-02
I believe you, but you gotta work with me on this. I either need you to join the project and revamp the engine core, or me to finish my graphics course and do it myself. I cannot magically conjure up the knowledge for this project. :P

As it stands right now, I am very comfortable using SDL, but I have virtually no OpenGL exposure yet. So, I am using pure SDL for now.

---

### Post by hessiess on 2009-10-02
> **TheBuzzSaw said:**
> I believe you, but you gotta work with me on this. I either need you to join the project and revamp the engine core, or me to finish my graphics course and do it myself. I cannot magically conjure up the knowledge for this project. :P

As it stands right now, I am very comfortable using SDL, but I have virtually no OpenGL exposure yet. So, I am using pure SDL for now.

As you know SDL, would you mind reading through the Tutorial pages for my Quad-ren graphics engine and giving feedback, it is designed to provide a very easy to use API for creating resolution independent 2D games.

[http://quad-ren.sourceforge.net/index.php?section=Tutorials](http://quad-ren.sourceforge.net/index.php?section=Tutorials).

---

### Post by MaximB on 2009-10-02
> **TheBuzzSaw said:**
> You said yourself that a potential MUGEN update is in the works. Why would you want me to make another MUGEN?

LOL! Have you played SSB? It is one of the most fantastic games with extremely large followings. You can find a smash tournament just about every weekend in any part of America. I don't know many other games that feature that. ;)

Yep, potential they are working on a Linux client this very moment, but they might not + it's not a FOSS.

But keep your project going, I see you already got a lot of people that can't wait to try it out.

---

### Post by TheBuzzSaw on 2009-10-02
I like MUGEN's ability to use just about any character in existence, but I am not a fan of the classic fighter gameplay.

---

### Post by juancarlospaco on 2009-10-02
*I dont like to contribute with Windows as you say...*

---

### Post by TheBuzzSaw on 2009-10-08
I've been posting updates to the SVN. If you're not interested in code, I am certainly open to other contributions such as a art, music, and ideas. :)

> **juancarlospaco said:**
> *I dont like to contribute with Windows as you say...*
I'm not sure I follow this...

---

### Post by 569874123 on 2009-11-08
Looking forward to this.

---

### Post by TheBuzzSaw on 2009-11-26
I am almost done with my course in OpenGL. I now know enough to make the engine much more efficient/powerful. I'll be uploading the new engine code base soon. :)

---

### Post by Ericj1186 on 2009-11-27
I logged in for the first time in a while and saw a thread dedicated to ZERO2D, and I almost messaged you.

Can't wait to see the finished product.  How versatile is the engine, exactly?  One of my favorite fighting games of all time is Fire Pro Wrestling Returns for PS2 just because of how much customization you can actually do.  The game is so open that I can create a straight-up MMA card using all custom fighters, a boxing card, a karate card, and a pro wrestling card, without any manipulation of the actual coding or engine; it's all there for you.  Customization, along with a steep learning curve, has made that game one of the best fighters you can play.  Will Z2D have that much depth or will it stick to a Smash-like fighter?

---

### Post by TheBuzzSaw on 2009-11-27
Well, the engine will be all about numbers. The core engine will focus on king-of-the-hill combat (smash). The numbers will dictate how that is accomplished. Gravity, momentum, character hits, etc. can all be tweaked at your leisure. This can make for some rather unique gameplay experiences, but the king-of-the-hill aspect will reign supreme in all cases.

---

### Post by PrimoTurbo on 2009-11-27
Sounds interesting, hope you get a chance to complete this project to a stable/usable form. Unfortunately I am unable to help due to time constraints and my own projects, etc. Best of luck.

---

### Post by TheBuzzSaw on 2009-12-08
[http://www.youtube.com/watch?v=60uDZ2a7Q5Y](http://www.youtube.com/watch?v=60uDZ2a7Q5Y)

---

### Post by Hard Core Rikki on 2009-12-09
Is there a design paper documenting general aims and practical/possible ways or code to fulfill those ?

---

### Post by TheBuzzSaw on 2009-12-16
I decided to give this project some breathing room.

[http://www.zero2d.com/](http://www.zero2d.com/)

02d == serious business :P

> **Hard Core Rikki said:**
> Is there a design paper documenting general aims and practical/possible ways or code to fulfill those ?

There is a project overview here: [http://www.zero2d.com/community/showthread.php?tid=35](http://www.zero2d.com/community/showthread.php?tid=35)

It's basically the same thing as the first post.

I'm not sure what you're asking.

---

### Post by .kelp on 2009-12-19
Wow, this project sounds great.
I wish I could contribute anything but I'm neither coder nor artist, so all I can do is wish you good luck.
Keep up the good work! :)

---

### Post by TheBuzzSaw on 2010-07-09
Just a note to interested followers of the project: the SVN active now. We now have two dedicated developers, so progress is being made daily. We're shifting the engine over to OpenGL 3 with shaders. This gives us the necessary control to render everything the sprites with status-ailments and whatnot.

---

### Post by JDShu on 2010-07-09
Good luck on your endeavors :D

---


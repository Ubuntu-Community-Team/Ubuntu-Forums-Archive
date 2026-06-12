---
title: "Bringing More Games To Linux..."
date: 2007-06-05
forum: Gaming &amp; Leisure
---

### Post by DeadSuperHero on 2007-06-05
I've had this idea for a while now, and I think I might as well get started on it. I don't really know that much about programming in Linux, but I can usually look at source code, and find out what everything does.
So, here's the idea: create an app that gets games out to Linux users through a client. It would most likely be based off of Automatix, or the "Add/Remove Programs" app. 

**Project Centrifuge**

The client would be pointed to a large repository of games in different genres:
-Adventure (Free Games made with AGS, and such)
-Demos (Demos of commercial Linux games, like Vendetta Online, or maybe some of the demos from Loki Games)
-FPS (Free First Person Shooters)
-MMORPG (Eternal Lands and such)
-Platform (Mario clones)
-Desktop (Solitaire, Blackjack, Pinball)
-RPG (Role Playing Games)
-Strategy (Games similar to Command and Conquer or War/StarCraft)
-Sports (Football, etc)
-Racing (Tux Racing, etc)
-Simulation (Flight sims and such)
-Tycoon (SimCity clones)
-Other (For whatever else doesn't quite fit in the other categories)
-Engines (Required engines to play AGS games, Unreal/Quake based games, etc)

It's all just in an idea form right now. I've been playing with Automatix a little, and I would like to get this project started, and with community support, it could become a terrific product!
Sadly, I don't know all there is to coding (like I said before), so I would be more than happy to get a coding team together to:
1) Build the client so that it's not just some rip-off of Automatix
2)Maintain repositories.
3) Constantly improve the code, to make it better for the user.
Lets face it, there's actually quite a lot of free games for Linux out there. The problem is:
1) They don't know about it.
or
2) They don't know how to unpack it and run it, getting the game engines set up can be a hassle, etc.
3) It would be good for the Linux gaming community in general.

If anyone's interested in this, and wants to give their time and effort to make this project into a reality, feel free to PM me. I think it'd be great.

---

### Post by hikaricore on 2007-06-05
I've nothing against your idea (aside from my issues with install scripts) but you've posted it multiple times across the forums, and once even in the wrong place.

Good luck, but please keep it confined to a one/a couple threads if possible.

Also there's been a script like this at: [http://www.ubuntugames.org/](http://www.ubuntugames.org/)

For quite awhile now, not sure if it's up to date, but it exists.  ^_^

---

### Post by DeadSuperHero on 2007-06-05
My apologies. Though, those two other threads were about a client that was in development to run AGS games. 
In any case, I'm going to look more into how Automatix works. It seems to have the downloads scripted in, rather than a live repo. Hmmm...
Time to read up on XML, and .deb packaging, I suppose.
I'll also look into maybe using a repo, for convenience.

---

### Post by Extreme Coder on 2007-07-06
Have you made any progress?
I had a similar idea, it would be nice to see whatever you reached.
IMO, this should be something where you can browse games, see reviews,ratings, and screenshots, and just click&install to run the game.
A great evolution of this idea would be that this program replacing the need for packaging games in distros :D

---

### Post by cmat on 2007-07-06
Games are what are really keeping people I know from GNU/Linux. I'm not really a hardcore gamer but I occasionally play them and tinker with the Quake 3 engine. But by getting devs to make linux games, your basically telling them to ditch the time saving DirectX and publish games for a very small division of PC users. The games out there are up to par with playstation graphics that run nativity.

---

### Post by DeadSuperHero on 2007-07-13
Thought I'd bump this back up with the latest details.
I'm first going to say that I'm not a very good programmer right now. I only know how to manipulate existing code to suit my needs, rather than building from scratch.
I've got a VERY rough version that sort of works. Meaning, it's just basically Automatix with a few games in it, with a different name and logo, and nothing else. I would love to get a team started eventually.
I've also registered it on Launchpad, so you can check back there for updates:
[https://launchpad.net/centrifuge](https://launchpad.net/centrifuge)

Quick question, however: Should I base this off of Automatix, or the Add/Remove Programs app?

---

### Post by cogadh on 2007-07-13
I would not base it on Automatix, it would be better to base on an actual application, instead of something that is basically a complicated install script.

---

### Post by DeadSuperHero on 2007-07-13
Alright, I'll just use the "Add/Remove Programs" as a basis for work, maybe...

EDIT: Here is a mockup of what I think it should look like. Give me your opinions, please.

[IMG]http://www.2dadventure.com/ags/mockup.PNG[/IMG]

EDIT: Got a little lazy, didn't bother to make real icons. Sorry!

---

### Post by Cappy on 2007-07-13
Having read the code for UGI I would definitely use a repos instead. UGI isn't bad, but there are too many problems that can occur if you extract and install from a tar.gz.
The problem is that you would have build a debian for each game, i386 and amd64 (if it is possible) and it could be a work to mantain (but so is any other method). I bet [http://www.getdeb.net/](http://www.getdeb.net/) would be willing to help though, seeing as it already has quite a recent game library.

If you built a program like this you would want to write the front end in python with the back-end simply using apt to install since your repos would be in the sources.lst.

Also see my program getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
since it would be a perfect addition for this type of program. I'm going to release a new version in the next couple of days.

---

### Post by DeadSuperHero on 2007-07-13
Cappy, I'll definately check it out tonight, thanks. :)

---

### Post by Kymus on 2007-11-14
If I wasn't just now starting to learn programing, I'd be willing to help :P

I can't speak for all the technical details, but at least on the surface it sounds like a great idea :D

---

### Post by Kymus on 2007-11-14
> **hikaricore said:**
> Also there's been a script like this at: [http://www.ubuntugames.org/](http://www.ubuntugames.org/).

Uhm... is there a site like that in English? All I'm seeing is Spanish.

I took Japanese and Chinese as a second language instead of Spanish :P

**edit**: found it :P

[http://www.ubuntugames.org/en/UbuntuGames](http://www.ubuntugames.org/en/UbuntuGames)

---


---
title: "If theres a FreeCiv, is there a FreeCenturi?"
date: 2007-06-12
forum: Gaming &amp; Leisure
---

### Post by PremierSullivan on 2007-06-12
Hi, Theres a program called FreeCiv which is a free version of the civilization series.  Has anyone heard of an equivelent open source version of Alpha Centuri, Sid Meyer's other cult hit?  If such a project does not exist, I might take the time over the summer to make it...

---

### Post by brownknight on 2007-06-12
i am not aware of the free version of alpha centuri but if you are making one then that's fantastic! i like that game.

---

### Post by Big Bear on 2007-06-12
I'd play that and if it's good fun I might even donate money to it ;)

---

### Post by hikaricore on 2007-06-12
If you make this project a reality, let me know and I'll add you to my [Community Games]("http://ubuntuforums.org/showthread.php?t=453980") list.  ^_^

---

### Post by PremierSullivan on 2007-06-12
Its nice to hear a positive response. I've programmed a few similar games in the past, but they have been crippled by the terrible inefficiencies of Java (which is other wise a fantastic programming language).  I will therefore learn C++ and begin coding the game. Once I have a solid base, I start asking for other people's collaboration.  Help in programming the AI would be helpful-- SMAC had great AI and I'm not sure I know how to write that.

Now, about gameplay.  Without straying to far from the game's original vision, I'd like to implement a few changes... I'll see what it comes down to, but I'll start with just replicating the game.  I may make two versions, one similar to the original, and one more to my tastes, and invite others to mod the game also.  

Now, the fun part, what should the 7 (etc) factions be?  In the original game there was...
The greedy mogol
The religious nut
The mad scientist
The Socialist egomaniac
The hypocrytical peacekeeper
The war mongeror
The environmentalist (who actually wasn't that bad of a person, now that I think of it)

Anyway, I don't want to rip off the original game, so maybe we could explore some variation on these themes?  I could program the game so that users could write their own factions (which was possible in the original with the expansion pack, which, sigh, I never really got to play).  Anyway,  the 7 SMAC factions will be a starting point, but I expect a few dozen interesting nations in FreeCentauri.

BTW, FreeCentauri: Great name, or the greatest name?

---

### Post by PremierSullivan on 2007-06-12
Oh, one more thing, could someone recomend a cheat sheet for C++ development, and give me some pointers on getting programs to compile and run?  that's more frustrating than learning the language to me.  What are the good IDEs?

---

### Post by Big Bear on 2007-06-12
Maybe ideas for a tech tree as well for those of us not good with names?  I think I still have my tech tree poster from the game somewhere too haha!

---

### Post by Tyke91 on 2007-06-12
i think the factions were fine

perhaps more technologies and weapons? ;)

---

### Post by engla on 2007-06-14
By the way, freeciv is made so that different rulesets or whole modpacks can be created for it. It should be possible to make a whole alpha centauri mod for freeciv if the rules are not too different.

The only problem I know of is the AI, which is not so easy to customize in freeciv. Still, freeciv could be a better starting point. It could also be too complicated to start from, it is huge :(

---

### Post by The Noble on 2007-06-15
> **PremierSullivan said:**
> Oh, one more thing, could someone recomend a cheat sheet for C++ development, and give me some pointers on getting programs to compile and run?  that's more frustrating than learning the language to me.  What are the good IDEs?

i don't really program, but from what I hear in the programming forums, just using gedit and g++ could be the answer. This would give you some really good code at least. If you really want an IDE I would use Anjuta.

---

### Post by charlieg on 2007-06-15
> **engla said:**
> By the way, freeciv is made so that different rulesets or whole modpacks can be created for it. It should be possible to make a whole alpha centauri mod for freeciv if the rules are not too different.

The only problem I know of is the AI, which is not so easy to customize in freeciv. Still, freeciv could be a better starting point. It could also be too complicated to start from, it is huge :(

I think you want to be using Freeciv as a starting point.

It will be much easier to help make Freeciv a bit more moddable (i.e. create a mod and "challenge" the developers or post patches to suit your mod a bit better) than to create it from scratch.  Freeciv has been in development for, what, 10 years now?  Do you think you could honestly replicate their progress in any realistic time frame?

Don't start from scratch.  You'll be years away from anything tangible.  Keep your load low - make a Freeciv mod.  At the very worst, it could serve as an [excellent] prototype if you do require to diverge the codebase a little bit in order to gain the functionality you need.

---

### Post by engla on 2007-06-15
I have to say that the Extras and mods to freeciv are in a sorry state. But I just ran the ancients mod to 2.0 and it seems to work, new units, techs and graphics etc.

[http://freeciv.wikia.com/wiki/Extras](http://freeciv.wikia.com/wiki/Extras)

---

### Post by PremierSullivan on 2007-06-15
> **engla said:**
> By the way, freeciv is made so that different rulesets or whole modpacks can be created for it. It should be possible to make a whole alpha centauri mod for freeciv if the rules are not too different.

The only problem I know of is the AI, which is not so easy to customize in freeciv. Still, freeciv could be a better starting point. It could also be too complicated to start from, it is huge :(

Theres some basic differences between Civ and Centauri... i'd rather start anew, and port in any code that would be useful, like the pathfinding algorithm*

*btw, I don't know how to make pathfinding, I guess I'll look it up.

---

### Post by charlieg on 2007-06-15
You'd rather start anew because there are basic differences?  What differences?  Honestly, Freeciv has tens of thousands of man hours of development under it's belt.

Of course, this is the nature of open source, start anew if you like, but there are two paths to creating a playable game here and you seem to want to choose the long, arduous one.  Just be aware that is the decision you make!

---

### Post by Stormspireiv on 2007-06-16
Personally, I could never "get into" freeciv or even the commercial Civilization series...I am just way too hooked on Alpha Centauri.  I do know that if there was a "FreeCentauri" written from the start to be more like SMAC, I would embrace it wholeheartedly.

---

### Post by The Noble on 2007-06-16
I do have to agree that the FreeCiv project has made the game so...archaic? I don't know the right word, but it feels quite different than playing Civ 3 or 4.They may be trying to mimic Civ 1 and 2, but it feels like a pain to set up and a lot of the options are uncomparable to the real series. Even worse, I find that the personality of the civlizations are bland and nonexistant. 

This does not mean it should be rewritten, but it does has a totally different feel from the Alpha centauri games. Maybe FreeCiv only needs a new GUI and new set of sprites, but I think a rewrite could actually garner that twinge of rememberance of playing the real games. The final decision is up to you, but I do want to say that I see where you get that feeling of "it needs to be started from scratch." 

Either way you go, just make sure you take as much as you can from their project. Their pathfinding and AI code are very good, so at least take that. Good luck, and make sure you update us from time to time. You may actually get some more people on board if you really show that you are serious and make some code.

Just make sure you plan, plan, plan...

---

### Post by ZylGadis on 2007-06-16
I see no reason not to do it in Java. The terrible inefficiencies you mention are a thing of the past (Java < v5). Java5 had so many optimizations to the VM that it is in fact faster than C++ in some cases. Java6 has even more optimizations.

The biggest (still remaining) problem with Java is its memory consumption. If you are willing to take that hit, you can do a full-blown Java game. Freecol is java-only, for example, and it is a great game (not to mention it is portable across platforms).

Rant about Java ends here.

I am making a different game, and my summer is completely taken over by other things, but in the autumn I can help with an Alpha Cent**a**uri clone, provided the license is good (i.e. GPLv3 or similar). AI is not a problem (one of my PhD minors is AI), neither is pathfinding (which is actually AI), etc.

Just show that you are serious. [http://producingoss.com/]("http://producingoss.com/") might be helpful in that respect.

---

### Post by engla on 2007-06-16
of course it is archaic if that is what you mean by it. FreeCiv was started when Civ 1 was the only civilization game, and then it was updated after civ II was released. As it is now, it is like Civ 2 with some extra features and rules, but mostly consistent and very similar..

From this point it will evolve freely (albeit very very slowly right now), with things like complex governments etc.

---

### Post by Zannax on 2007-06-18
So PremierSullivan, you don't know c++, you don't know how to do pathfinding and nevertheless you want to write the game from scratch...
Fine: that's the spirit! ;)

Good luck!

---

### Post by KIAaze on 2007-06-18
> **PremierSullivan said:**
> Oh, one more thing, could someone recomend a cheat sheet for C++ development, and give me some pointers on getting programs to compile and run?  that's more frustrating than learning the language to me.  What are the good IDEs?

Look at the bottom of this thread for a list of IDEs:
[http://ubuntuforums.org/showthread.php?t=455376]("http://ubuntuforums.org/showthread.php?t=455376")

And I would also recommend first trying to do simple things in C/C++ before starting this project, altough you can (and certainly will anyway) also learn it along the way.

[I have to agree with you, getting things to compile can sometimes be harder than coding... ^^
But with the time, you'll learn how to solve compilation errors.]

---

### Post by engla on 2007-06-23
By the way, the answer to the question in the topic is yes, but it's seemingly abandoned:
[The Freeciv AlphaCentauri Project]("http://freecivac.sf.net/")

---

### Post by charlieg on 2007-06-23
Oh lord... somebody here is going to come crashing down to earth with a very heavy bang.  If you don't know C++, that means you probably don't know how much hard work it is to write even basic applications in C++.

Good luck with this project.

That FreecivAC looks interesting even though it is abandoned.

---

### Post by vem0m on 2007-06-24
Well you can play Alpha Centuri native on linux if you all didn't know there is a loki installer for it. :)

---


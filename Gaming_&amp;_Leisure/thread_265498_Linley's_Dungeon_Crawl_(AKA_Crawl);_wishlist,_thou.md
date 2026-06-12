---
title: "Linley's Dungeon Crawl (AKA Crawl); wishlist, thoughts, commentary."
date: 2006-09-26
forum: Gaming &amp; Leisure
---

### Post by em3raldxiii on 2006-09-26
First off, anyone who has not tried *Crawl* aught to.  You can [FONT="Courier New"]sudo aptitude install crawl[/FONT], or use your favorite package manager like *Synaptic* to get it.

Very briefly, it is a spectacularly detailed ASCII terminal game that many MANY would argue is the best *roguelike* game ever coded.  It should be noted that after playing this game periodically over the last month or so, I am now aware that this game is ... amazing.  If you want to learn more about the game, there are some good resources at the following pages:

&#8226; [Nice page of Crawl hints & stuff]("http://www.swallowtail.org/crawl/hints.shtml")
&#8226; [Wikipedia entry for Crawl]("http://en.wikipedia.org/wiki/Linley's_Dungeon_Crawl")
&#8226; [13 Steps to Crawl]("http://www.digital-eel.com/13steps/")

Any other links you can find would likely be helpful.

I decided to create this thread to honor the game, and to spark a little interest in it.  Also, perhaps I can have some of my own concerns addressed regarding the game.

```

**_For Complete Newbies to Crawl_**
1.  You will die a lot.  Many times.  Do not be discouraged.
2.  Start out with something like a Troll Berzerker - they naturally heal quickly, and a Berzerk Troll is almost unstoppable (keys:  **a** followed by **shift-a**).
3.  Magic-oriented characters should be reserved for when you understand the game's intricacies.
4.  the **?** key (shift-/) shows you a list of hotkey commands.
5.  FOOD.  Especially for Trolls.  If you find it, hoard it.  If you are *hungry* or *starving* and have no food in your inventory: kill something (basically just "bump" into monsters repeatedly until they die), then step on their body if they left one, then hit **shift-d**, then **y** to confirm, then **e** to eat the chunks.  Orcs often generate *several* chunks that are edible.  Trolls (among a few others) can eat these chunks even when you are not hungry.  It is a VERY good idea to keep yourself WELL-FED, because it is very easy to starve to death.
6.  You cannot save your game (except when leaving a session), so you cannot save your game "in case you die".  If you die, that's it.  You're dead.  You have to create a new character and start from square one.
7.  Potions and Scrolls (among other things) are randomly generated at the beginning of play, so there is *absolutely no sense* in writing down the names of these objects.  Pure lunacy, and a very fast track to a LOT of scibbled & crumpled pieces of scrap paper.  Once you drink/read one, you generally know what it's for, and will always know for the rest of that character's lifespan.  There are a HUGE number of these types of items.

```

I am sure I could think of more, but I can't right now.

I REALLY REALLY REALLY would love to have a way to back-up my character now and again.  I mean, you spend a cumulative number of hours playing the game and *just* barely making it through a number of battles, amass a couple of *truly* unique items, maybe you can *finally* use that spell you have been trying to build up the skills to use, and poof - killed by a stupid Orc Wizard that blinks around so fast you can't whack him.  Ugh.  Or maybe get shot to death by a crappy Centaur because you're out of magic or are poisoned, or some such.  Or worse ... starve to death at dungeon level 14.  Hell, I feel lucky even MAKING it to dungeon level 14 ... EVER.  So if anyone knows of a sneaky underhanded method of doing so ... I beg you ... tell me!  I tried backing up all my *bones* files 'n' stuff, but to no avail.  I am just too dumb.  Haha.  I am completely aware that this is supposed to be a "feature" of this sort of game, but I find it works to the game's *detriment* that I have no way of backing up a character against accidental (stupid) death.

Anyway, aside from that ONE (rather huge) pet peeve, I think **Crawl** might just be the greatest game EVER coded.

:D

---

### Post by Stew2 on 2006-10-01
It is a cool game isn't it? Harkens back to the days before high powered processors and smokin video cards :) . Very addictive. Unfortunately, I don't know how to save your character from deletion when you die. It's very easy to do in Windows, but I can't seem to find the same files in Ubuntu to back them up :confused: 

Regards,
Stew2

---

### Post by B0rsuk on 2006-10-02
Survival tip: play a troll. Or minotaur, or hill orc. NOT an ogre, they totally suck. Find amulet of rage or pick Trog as your deity. Okawaru, Makhleb or Yrr(..) is not bad, too.

For advanced crawl players, I recommend crawl 'stone soup' - most recent version of crawl. You have to compile it yourself.

[http://prdownloads.sourceforge.net/crawl-ref/stone_soup-0.1.2-src.tbz2](http://prdownloads.sourceforge.net/crawl-ref/stone_soup-0.1.2-src.tbz2)

The newsgroup where Crawl rules supreme is rec.games.roguelike.misc . Lots of crawlers there, and developers actually read it. You can access it via google groups, too.

[http://groups.google.com/group/rec.games.roguelike.misc](http://groups.google.com/group/rec.games.roguelike.misc)

---

### Post by lotusleaf on 2006-10-16
Lots of spoilers:
[http://www.eleves.ens.fr/home/grasland/crawl/index.html](http://www.eleves.ens.fr/home/grasland/crawl/index.html)

And dougsko (thanks!) on Freenode IRC shared this with me:

```
diff -r dc400b26-src-mine/source/AppHdr.h dc400b26-src/source/AppHdr.h
380c380
<     #define SAVE_DIR_PATH       ""
---
>     #define SAVE_DIR_PATH       "/opt/crawl/lib/"
Only in dc400b26-src-mine/source: crawl
Only in dc400b26-src-mine/source: Dragongras1000.00a
Only in dc400b26-src-mine/source: Dragongras1000.01a
Only in dc400b26-src-mine/source: Dragongras1000.02a
Only in dc400b26-src-mine/source: Dragongras1000.03a
Only in dc400b26-src-mine/source: Dragongras1000.04a
Only in dc400b26-src-mine/source: Dragongras1000.sav
diff -r dc400b26-src-mine/source/food.cc dc400b26-src/source/food.cc
71,73c71,72
<      
<       //I commented this out
<     //you.hunger -= hunger_amount;
---
>
>     you.hunger -= hunger_amount;
Only in dc400b26-src-mine/source: morgue.txt
diff -r dc400b26-src-mine/source/player.cc dc400b26-src/source/player.cc
3182,3183d3181
<     fatal = 0;
<
3187,3190c3185
<     you.hp += hp_loss;
<
<     if (you.hp > you.hp_max)
<         you.hp = you.hp_max;
---
>     you.hp -= hp_loss;
3205c3200
<     //you.magic_points -= mp_loss;
---
>     you.magic_points -= mp_loss;
diff -r dc400b26-src-mine/source/religion.cc dc400b26-src/source/religion.cc
56,67c56,67
<     " glows silver and disappears.",
<     " glows a brilliant golden colour and disappears.",
<     " rots away in an instant.",
<     " crumbles to dust.",
<     " is eaten by a bug.",    /* Xom - no sacrifices */
<     " explodes into nothingness.",
<     " is consumed in a burst of flame.",
<     " is consumed in a roaring column of flame.",
<     " glows faintly for a moment, then is gone.",
<     " is consumed in a roaring column of flame.",
<     " glows with a rainbow of weird colours and disappears.",
<     " evaporates."
---
>     {" glows silver and disappears."},
>     {" glows a brilliant golden colour and disappears."},
>     {" rots away in an instant."},
>     {" crumbles to dust."},
>     {" is eaten by a bug."},    /* Xom - no sacrifices */
>     {" explodes into nothingness."},
>     {" is consumed in a burst of flame."},
>     {" is consumed in a roaring column of flame."},
>     {" glows faintly for a moment, then is gone."},
>     {" is consumed in a roaring column of flame."},
>     {" glows with a rainbow of weird colours and disappears."},
>     {" evaporates."}
Only in dc400b26-src-mine/source: scores 
```

The complete source to Dungeon Crawl may be obtained from [http://www.dungeoncrawl.org](http://www.dungeoncrawl.org)

---

### Post by skymt on 2006-10-16
Crawl's great, but I still prefer ADOM and ToME. 8) 

Wow, that was geeky.

---

### Post by lotusleaf on 2006-10-17
By the way, there's now an Unofficial Dungeon Crawl IRC Channel on Freenode in #crawl:

[irc://irc.freenode.net/crawl](irc://irc.freenode.net/crawl)

Come in and chat with other players! :)

---

### Post by KhaaL on 2006-10-17
aww, I love roguelikes but I rather play them with graphics (tilesets)...

---

### Post by dougsko on 2006-10-20
Lotusleaf already posted some cheat hacks I've made. They make you never get hungry and have infinite hp/mp. However, it seems you can still become paralyzed, and when being attacked by yellow wasps, get stuck. So here is another change I've made to fight.cc that should take care of the problem. This has not been tested and I can't guarantee it works. This is the diff file, made against the orginal fight.cc from the source code available at [http://www.dungeoncrawl.org](http://www.dungeoncrawl.org). You can grab all my hacked files at [http://www.dougtko.com/crawl](http://www.dougtko.com/crawl).


```

2400c2400,2402
<                         mpr("You still can't move!", MSGCH_WARN);
---
>                         mpr("Your paralysis just disapeared!", MSGCH_WARN);
>
>                         you.paralysis == 0;
2402c2404
<                         mpr("You suddenly lose the ability to move!", MSGCH_WA
RN);
---
>                         mpr("Whoohoo! Wasps can't paralyze you!", MSGCH_WARN);
2404c2406
<                     you.paralysis += 1 + random2(3);
---
>                     you.paralysis == 0;

```

---

### Post by MrBlond83 on 2006-10-20
And I thought playing Nethack makes me a weirdo.

Good to see I'm among my kind...

---

### Post by em3raldxiii on 2006-10-20
Haha, that's awesome.  But here's the thing ... I quite like the game the way it is without TOO much.  Is there such thing as "mild" cheating?

For example, saving your game just in case you die - so you can reload your character when you are killed by something stupid.  Tweak the hunger so you *can* get hungry, just not quite as fast - say at 50% the current rate.  A slight increase in how much you can carry by say 25%.  Increase your max HP by 2d6 from the very beginning (once you are past Level 4 or so it's not quite as important IMO) and increase your max MP near the beginning by 1d4.

Now ... off to check that cheats page :D

---

### Post by em3raldxiii on 2006-10-20
Also ... I don't know how to compile my own version using your new files .... some instructions?

---

### Post by dougsko on 2006-10-27
One note before I begin. The last diff file I posted for fight.cc has a syntax error in it. I've since fixed it and posted the new fight.cc at [http://www.dougtko.com/crawl](http://www.dougtko.com/crawl). To use my hacks, just go to [http://www.dungeoncrawl.org](http://www.dungeoncrawl.org), and download the newest source. Untar it, and go into dc400b26-src/source. Now download the files from my site and copy them into this folder. Now just type, "make", and the game will compile, leaving you with a cheat version. The diff files that were posted earlier just show the differences between the original source code and my versions. That way, you can actually go in and make the changes yourself instead of just trusting me ;) Check out "man diff" for more info on it, because it is pretty useful for stuff like this. You can even use the diff file along with the "patch" command to automatically make the changes for you. But the quick and easy way is to just replace the original files with the ones on my site. BTW, does anyone know how to get out of the labrynth? I entered it on level 14 and can't seem to find the exit :( Here is the updated diff file that includes all the cheats I've added so far:

```

diff -r dc400b26-src/source/AppHdr.h dc400b26-src-mine/source/AppHdr.h
380c380
<     #define SAVE_DIR_PATH       "/opt/crawl/lib/"
---
>     #define SAVE_DIR_PATH       ""
Only in dc400b26-src/source: crawl.gdt
Only in dc400b26-src/source: crawl.gpr
Only in dc400b26-src-mine/source: cscope.out
diff -r dc400b26-src/source/fight.cc dc400b26-src-mine/source/fight.cc
2399,2402c2399,2400
<                     if (you.paralysis > 0)
<                         mpr("You still can't move!", MSGCH_WARN);
<                     else
<                         mpr("You suddenly lose the ability to move!", MSGCH_WARN);
---
>                     if (you.paralysis > 0){
>                         mpr("Your paralysis just disapeared!", MSGCH_WARN);
2404c2402,2409
<                     you.paralysis += 1 + random2(3);
---
>                         you.paralysis == 0;
>                   }
>                     else{
>                        mpr("Whoohoo! Wasps can't paralyze you!", MSGCH_WARN);
>                       
>                       you.paralysis == 0;
>                   
>                   }
diff -r dc400b26-src/source/food.cc dc400b26-src-mine/source/food.cc
71,72c71,73
< 
<     you.hunger -= hunger_amount;
---
>       
>       //I commented this out
>     //you.hunger -= hunger_amount;
Only in dc400b26-src-mine/source: morgue.txt
diff -r dc400b26-src/source/player.cc dc400b26-src-mine/source/player.cc
3181a3182,3183
>     fatal = 0;    
> 
3185c3187,3190
<     you.hp -= hp_loss;
---
>     you.hp += hp_loss;
> 
>     if (you.hp > you.hp_max)
>         you.hp = you.hp_max;
3200c3205
<     you.magic_points -= mp_loss;
---
>     //you.magic_points -= mp_loss;
diff -r dc400b26-src/source/religion.cc dc400b26-src-mine/source/religion.cc
56,67c56,67
<     {" glows silver and disappears."},
<     {" glows a brilliant golden colour and disappears."},
<     {" rots away in an instant."},
<     {" crumbles to dust."},
<     {" is eaten by a bug."},    /* Xom - no sacrifices */
<     {" explodes into nothingness."},
<     {" is consumed in a burst of flame."},
<     {" is consumed in a roaring column of flame."},
<     {" glows faintly for a moment, then is gone."},
<     {" is consumed in a roaring column of flame."},
<     {" glows with a rainbow of weird colours and disappears."},
<     {" evaporates."}
---
>     " glows silver and disappears.",
>     " glows a brilliant golden colour and disappears.",
>     " rots away in an instant.",
>     " crumbles to dust.",
>     " is eaten by a bug.",    /* Xom - no sacrifices */
>     " explodes into nothingness.",
>     " is consumed in a burst of flame.",
>     " is consumed in a roaring column of flame.",
>     " glows faintly for a moment, then is gone.",
>     " is consumed in a roaring column of flame.",
>     " glows with a rainbow of weird colours and disappears.",
>     " evaporates."

```

---

### Post by em3raldxiii on 2006-10-27
I can't remember where I read this, but I remember something saying that you had to go to "the center" of the labyrinth, fight something big, and sometimes there's an orb in a vault there.  this is going purely off memory only, but it might help a little.  I've never even made it to the Labyrinth, let alone try to escape from it. :D

---

### Post by em3raldxiii on 2006-10-27
And thanks for the outline of how to patch it.  I will review your "cheats" and see if I can tweak them to "just how I want them" :D  Thanks a lot.  This game has been driving me bananas for months hehe

---

### Post by em3raldxiii on 2006-10-28
WHen I MAKE, I get a HUGE number of errors:

cclplus: warning: command line option "blabla" is falid for Ada/C/ObjC but not for C++ 

And a few other types or errors.  What's going on?

---

### Post by B0rsuk on 2006-10-28
> **em3raldxiii said:**
> Haha, that's awesome.  But here's the thing ... I quite like the game the way it is without TOO much.  Is there such thing as "mild" cheating?

For example, saving your game just in case you die - so you can reload your character when you are killed by something stupid.  Tweak the hunger so you *can* get hungry, just not quite as fast - say at 50% the current rate.  A slight increase in how much you can carry by say 25%.  Increase your max HP by 2d6 from the very beginning (once you are past Level 4 or so it's not quite as important IMO) and increase your max MP near the beginning by 1d4.

Now ... off to check that cheats page :D

If you have to resort to cheats, you won't get much enjoyment from crawl. Cheating kills excitement. Some more tips:
- take a sharp item and 'D'issect a corpse. Pick up the meat chunk and eat once you're hungry. Orcs, trolls, ogres, kobolds don't need to be hungry to eat raw meat. Once you realize you can eat most corpses without harm (other than occasional illness), you'll be hard pressed to starve to death. I play crawl A LOT, and also die A LOT, and I can't remember any death from starvation.
- instead of cheating, be smart. Pick up darts, stones etc, and throw them at more dangerous enemies to soften them. Poisoned needles with a blowgun (or just poison in general) is especially effective in early levels. If yo see an early dangerous monster (gnoll, snake, ogre, orc priest, orc wizard, hound, giant frog...) you can dash for nearest staircase, even down staircase. Or read a scroll of teleportation in advance.
- for most characters, it's a good idea to temporarily wear first found heavy armor, such as ring mail or scale mail. Extra protection points are very valuable early
- drink-identify all found potions. There's no potion that instakills you, this is not nethack. Even poison potions are rarely lethal, and certainly not instant. Ones you want to save for dire circumstances are might, speed, heal wounds, healing(a bit weaker). These potions save lives.
- anyone who can compile the game himself knows that crawl by default compiles to two binaries, ncrawl and wcrawl (wizard mode crawl, with cheats enabled for debug). You don't need some obscure patches from untrusted source.

In general, if you refuse to think tactically and learn, crawl is not a game for you. If you'd rather die from boredom than battle wounds, pick angband or T.O.M.E.

---

### Post by em3raldxiii on 2006-10-29
I am fully aware of all of these strategies B0rsuk, however I will assume you have posted these for the benefit of new users.  I am a strong advocate of using blowguns, particularly with poisoned needles.  It is indeed a very effective way of softening up your foe ahead of time.

Now, in defense of my request for "mild" cheats, I would like to repeat that I do indeed like to play the game with it's current configuration.  However, I find the inability to save the game against accidental death to be quite vexing.  The game is large enough in scale that it should (in my opinion) support a basic game-save.  To force a player to start from scratch again after playing through 15 levels of Crawl is nothing short of torture.  There are a number of accidental deaths that are particularly annoying to me (and please don't preach to me about strategy, I am fully aware of various strategic techniques).

1.  Random "extra-hard" monsters.  These don't occur often, and I don't mind that they DO happen.  In most cases I can successfully escape (teleport, run, scroll of polymorph, etc).  But it does occur on occasion where one does not have these things available - either because you've already exhausted your resources, or perhaps haven't even come across them.
2.  Poisoning.  This can happen to even the most robust character, and if you don't have any poison resistance (as has happened to me on many occasions), and/or potions to help yourself out, then you are pretty much S.O.L.  This is a prime example of why I might want to have a saved game to back myself up.
3.  Randomly teleported into a very bad place.  Particularly Pandemonium, the Abyss, or any other extra nasty place that comes to mind.  In most cases, I haven't been able to recover from these particularly bad experiences.  Again, if one could have a saved game to back himself up, this needn't be a terrible worry.
4.  Accidentally walking into something that you can't handle.  Again, this doesn't happen very often, but it does once in awhile.  For example, I was once swarmed from all directions by killer bees.  Now under most circumstances this isn't terribly worrisome, except that at this time I had no poison resistance, and nothing else to rescue me from poison.  I killed enough bees to begin escaping, but died of VERY heavy poisoning.  Strangely, this was not on a dungeon level one would expect to encounter large swarms of bees.  Save Game would be wonderful here.
5.  Accidental suicide.  Face it, it happens.  For example, you're fighting a big nasty, and have got 'im down to "Heavily Wounded" but you only have 20HP left.  You have no potions of speed or invisibility, so you likely can't escape.  You pull out your trusty wand of Lightning (cuz you don't have a wand of draining), and fire it at your opponent.  The lightning misses, hits a wall at what you THOUGHT was a safe distance, it rebounds and kills your opponent.  Sadly, it also hits you and kills you.  This is an example of a time when a save-game file would make you feel very much happier.

Unfortunately, I don't know how to back up my saved game files.  In addition, coding the game to include save-game files is beyond the scope of my coding ability.

This is where cheating comes in.  Some simple tweaks just to decrease the overall difficulty of the game would really make my gaming experience more enjoyable.  Why?, you might ask.  I'll tell you.  I don't spend hours and hours and hours playing computer games in general.  I like to have a quick go at a game, play for awhile, save, and come back to it another day.  With Crawl, if you play this way, chances are you will never see past level 18 of the dungeon, and never have the chance to gather up runes or anything.  Now, if you are a lucky bugger and have done well with a minimum of TIME input, well all the power to you.  But for me, and I repeat *ME*, the game has become a frustration.  If I cannot make the game easier OR if I cannot enable save-games as insurance against "stupid death", I will simply uninstall the game and not play it.  Which, of course, is not the path I wish to choose.

Many games have a "difficulty" setting, and often the last level of difficulty is enabled only AFTER you have successfully completed one of the previous difficulty settings.  The last level of difficulty in this situation would include ALL of the existing restrictions (no saves, constant issues with hunger, etc).  In this situation, I would happily play the game.  In addition, my 7 year old son (who is actually a pretty decent strategest), would have more fun at the game.

If the game simply included the save-game approach, and/or the difficulty approach, this thread likely would not exist, and I would be playing VERY happily whenever the compulsion struck me.  Trust me, it has nothing at all to do with a refusal "to think tactically and learn".  And I am willing to bet there are a number of other users who would agree with me.

---

### Post by B0rsuk on 2006-10-29
I can't help but get the impression crawl is, in fact, not a game for you. It is brutal at times, but all crawl players I know (rec.games.roguelike.misc newsgroup) seem to like it. There were one or two castrated versions of crawl, basically making sure certain monsters can't appear too early or don't use wands. And they died, because they weren't popular enough .You say the game became a frustration for you - why bother, if you're not getting paid for it ? There are other roguelike games, too. Some people really like A.D.O.M., Nethack, T.O.M.E. or other angband variants. Some of them (like nethack, I heard) allow you to stay in one safe place forever, making sure you effortlessly gain experience and can't die if boredom doesn't kill you. Frankly, I've found hunger to be much bigger problem in A.D.O.M., because you're much more dependant on randomly generated food items you find. Races/classes without Food Preservation skill can have it really hard.
I can't comprehend how can you be so experienced at playing crawl and mention hunger among one of major difficulties, for example. Hunger is important for several balance reasons, it prevents you from farming one level forever or abusing Sif Muna. After certain point, say, dungeon level 5-8, all my deaths seem to come from my own mistakes, usually overestimating my strenght and trying to save my resources too much (particularly wands). That's what I love about crawl, it rewards prepared.

**There is, in fact, difficulty setting in crawl.** And an unusually flexible one. It's called character generation. Some races and classes are simply much easier than others. Minotaur, hill orc, naga, and some others make MUCH better fighters than kobolds, humans or elves(unless you're playing as crusader, perhaps). Heavy armor characters are generally easier(if less flexible), because it gets you better protection from invisible monsters, poison, guaranteed minimum damage absorbtion, and it's much more reliable. Relying on dodging, on the other hand, can be quite frustrating because you either take no hits at all or get hit very hard. Still, it opens up more options such as stealth and better spellcasting.

Race selection lets you to selectively disable various threats. No one says you HAVE TO win as that 1337 treehugger elven warrior. Mummies, kobolds, hill orcs are very hard to starve. Nagas come with strong poison weapon, strong AC and partial independence on armor, poison immunity, see invisible, undocumented resistance to 'armor fits poorly on your deformed body', huge base hp. All this at small price of movement speed. As a naga fighter, I only rarely *need* to run away. Speed penalty hardly matters if you can easily kill Sigmund first time you meet him.

There are other strategic decisions to make, of course. The lair is generally considered safer than going too deep into main dungeon branch. There are some hardhitters in there, sure. There are some swarms, and strong poison. But there's also more than enough food, typically several shops, no invisible enemies (important for lig.., er, random armor characters). Lair is generally quite friendly place, and Snake Pit considered trivial with poison resistance.
Orcish Mines can be either easy or murderous, depending on how many trolls, orcish warriors, knights, high priests, sorcerers, warlords you get. Either way, it's a big gamble. You adjust the difficulty the way you play.

---

### Post by dougsko on 2006-10-29
> **B0rsuk said:**
> 
- anyone who can compile the game himself knows that crawl by default compiles to two binaries, ncrawl and wcrawl (wizard mode crawl, with cheats enabled for debug). You don't need some obscure patches from untrusted source.


Ok, maybe I'm missing something here, but I've never seen crawl compile into two binaries. If it did, I never would've starting messing around with the code. Second thing, is that I have not posted "obscure patches from untrusted source.", what I posted where some changes I made to the code to make things easier. You can see the changes plain as day, and most of them are either just adding comments, or changing a -= to a +=. There's nothing tricky going on here. As to whether you cheat or not, who cares? I modified the code to see if I could, and I thought I'd share my changes with others who like to play the game. It's no big deal...really...you can relax, we all still enjoy crawl. And btw, the warnings you get while compiling on Ubuntu are OK, don't worry about them.

---

### Post by em3raldxiii on 2006-11-02
Here's a nice little link for people who would like to find out what's past level 6 without playing for 14 years:

[http://anxietyofinfluence.ca/crawl/](http://anxietyofinfluence.ca/crawl/)

The changes are not extraordinarily drastic.  At the moment, I have increased the random object count, increased the number of monsters on each level, and increased the starting stats.  This should allow your character to build up a bit faster and have a better chance of reaching a more sustainable level.  Note, however, that you are not invincible and can still die from those occasionally annoying "extra hard random monsters".  Feel free to PM me if you need help using the files included in that link.

---


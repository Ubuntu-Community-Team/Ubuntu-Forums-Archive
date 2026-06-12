---
title: "Buntoids"
date: 2009-12-20
forum: Gaming &amp; Leisure
---

### Post by Zayfox on 2009-12-20
**Note:**
The codebase for FreeMon (my  continuation of Buntoids) has been moved to [Rogue Bytes]("http://www.roguebytes.org/"). This allows greater flexibility with the development team  as the Rogue Bytes community is based around this style.
This means your issues go there, thanks.

**Useful links:**
Project Home: [http://www.roguebytes.org/forumdisplay.php?fid=6](http://www.roguebytes.org/forumdisplay.php?fid=6)
personjerry's Buntoids [Stable] Repo: [http://www.github.com/personjerry/buntoids](http://www.github.com/personjerry/buntoids)
Zayfox' Buntoids [BETA] Repo: [URL="http://www.github.com/Zayfox/buntoids-beta"]http://www.github.com/Zayfox/buntoids-beta
[/URL] 
**Posting a problem:**
If you can't get it to work, post the version ([Stable] or [BETA]), and also run it via terminal and give us the error message.

**Posting a fix:**
Post the version ([Stable] or [BETA]). PATCH or DIFF files appreciated.

[B]Downloading and Compiling:
[/B]For those not completely Ubuntu inclined.

*Downloading:*
Download GIT:
```
sudo aptitude install git-core
```Pick either the stable or BETA release (or both).

For stable:
```
git clone git://github.com/personjerry/buntoids.git
```For BETA:
```
git clone git://github.com/Zayfox/buntoidsbeta.git
```Download the required libraries:
```
sudo aptitude install libsdl-ttf2.0-dev libsdl-image1.2-dev libsdl-gfx1.2-dev libalut-dev libvorbis-dev libopenal-dev
```[I]Compiling:
[/I]```
cd <buntoids or buntoidsbeta directory>/source
make
```

---

### Post by scragar on 2009-12-20
The arch PKGBUILD```

## Use one and only one of:
pkgname=buntuoids
#pkgname=buntuoidsbeta


pkgver=0.0.1
pkgrel=1
pkgdesc="Buntoids for linux"
arch=('i686' 'x86_64')
url="http://www.buntoids.co.cc/"
license=("GPL")
depends=('sdl_ttf' 'sdl_image' 'sdl_gfx' 'libvorbis' 'freealut' 'openal')
makedepends=('git')

build() {
    cd $srcdir
    if [[ "$pkgname" = 'buntuoids' ]]; then
      git clone git://github.com/personjerry/buntoids.git
    else
      git clone git://github.com/Zayfox/buntoidsbeta.git
    fi
    cd buntoids*/source
    make
    cd ..

    ## Here I'd move stuff but there doesn't appear to be a good place
    ## to do that, so I'm using /opt/$pkgname

    installdir=${pkgdir}/opt/${pkgname}/
    mkdir -p ${installdir}
    install -m 0755 buntoids_$(uname -m) ${installdir}/${pkgname}
    cp -r data ${installdir}
    chmod -R 0744 ${installdir}data
    chown -R root: ${installdir}data
    mkdir -p ${pkgdir}/usr/bin/
    ln -s ${installdir}${pkgname} ${pkgdir}/usr/bin/
}
```
If I've done that right it should work(and after a few changes it works for me at least).

I do hope in future we can come up with some sort of standardisation on what the program is actually going to be called once it's compiled, for now I'm just holding onto the hope that it's going to be called some_{ARCH} where ARCH is the architecture returned by `uname -m` I've seen pokemon and buntoids as executables, that's just not confusing.

Similarly I ran into an issue of install not being able to copy directories, if anyone has any info on why that is or how to fix it I'd love a solution.

---

### Post by Zayfox on 2009-12-22
My BETA repository has changed. Please check the original post.
There are also concerns about the revision that my BETA is currently based off. If possible, kindly refrain from using the BETA until this is sorted out.

---

### Post by gnuwtey on 2010-01-01
I'd like to just suggest an idea that's been stirring in my mind for a little while now.

It's not canon to the game, but I think it might be a useful idea. It's a new stat called Endurance.

Any move that a Pokemon makes will cost "endurance points", the max of which is the Endurance stat. If the Pokemon is low on endurance points, there will be a message that says, "(name of Pokemon) is tired." or "(name of Pokemon) is very tired." If the Pokemon runs completely dry of endurance points, then any moves it makes will start deducting from the HP (on a 1-to-1 basis with what it would deduct from endurance points). During a battle, endurance points would not be visible on the screen, but you would get the "very tired" message.

Taking damage would also affect endurance points. Here's a (relatively) complete list of what would affect endurance points:

Any non-status move that has 40 PP by default: -1 point
Any non-status move that has 30 or 35 PP by default: -2 points
Any non-status move that has 20 or 25 PP by default: -3 points
Any non-status move that has 10 or 15 PP by default: -5 points
Any non-status move that has 5 PP by default: -8 points
The move "Endure": -9 points
The move "Focus Energy": +50 points (and temporarily doubles the max stat), but each move made drains double the Endurance points from then on until Focus Energy's effect wears off
The move "Splash": 0 points, since nothing happens.
Any move that has multiple hits, such as Fury Attack: -(above criterion) points per hit / 2 (rounds down)
So for example, if Fury Swipes were to hit 5 times, it would drain the attacker of 12 endurance points.
Taking damage from poison: - (Damage taken) / 8 points
Taking damage from a burn: - (Damage taken) / 8 points
Taking damage from Curse: - (Damage taken) / 3 points
Taking damage from Wrap, Bind, etc. : - (Damage taken) / 6 points
Taking damage from confusion: - (Damage taken) / 6 points
Taking damage from any regular attack: - (Damage taken) / 4 points (rounds down, so taking 1 damage wouldn't affect endurance at all.)
Walking 16 steps outside of battle with a poisoned Pokemon: -1 point

(These numbers are arbitrary, and can be changed at will.)

Walking one step outside of battle: +1 point
Going one battle turn without being active: +5 points
Going one battle turn active but asleep: +5 points
Revive: Restore half of missing Endurance (So for example, if I used Revive on a fainted Bulbasaur with an Endurance stat of 12/125, it would regain 56 points, ending up with 68/125.)
Healing your Pokemon at a Center: Restore Endurance to full

Here would be a few new items (This list is very incomplete):

Adrenaline (Temporarily increases the endurance of your Pokemon. Kind of works like an "X Endurance". Would cost about P1200 in Marts.)
Hype Up (Increases the EV of the Endurance stat by 8, would cost about P6500 in Marts. The stat cannot be raised above 100 using Hype Up.)
Full Restore would also restore Endurance to its max.

Of course, this would mean that the IV system would have to be revised to make room for 7 stats... Perhaps for the better, really. Make it 64-bit integers, and have each IV go up to 255. Pwnage.

Endurance would not factor into the EV stat total limit of 510, having its own limit of 255. The actual stat would be calculated with 40 instead of 5 as a minimum.

Also, some moves might be revised to specifically lower or raise endurance. For example, Recover would increase endurance as well.

Whatdya think?

---

### Post by scragar on 2010-01-01
I think endurance is a good idea, but your system would be fundamentally flawed, it's only reasonable that endurance would go up with level, but having constants for PP based consumption would make it neglegable at higher levels, meanwhile having it consume HP is an even worse idea, suffering 1/4 extra damage from an attack? That's crazy, however losing 2 HP after using your most powerful attack again at level 100 with 300+ HP is meaningless.
Honestly there's no good reason to produce such a system, the PP system pokemon has always had is actually very sufficient at serving the intended goal of not letting you spam the same moves forever, in fact, it does a much better job.

I'm not opposed to an endurance system, I just think it needs a lot more work.

---

### Post by gnuwtey on 2010-01-02
> **scragar said:**
> Honestly there's no good reason to produce such a system, the PP system pokemon has always had is actually very sufficient at serving the intended goal of not letting you spam the same moves forever, in fact, it does a much better job.

I'm not opposed to an endurance system, I just think it needs a lot more work.

Alright, I'll work on it. After all, the system is only a very early prototype.

And the point of Endurance isn't solely to prevent spamming a single move. (It works in conjunction with the PP system, not as a replacement.) It's also to simulate the fact that Pokemon get tired after making a lot of moves, even if those moves are used in balanced proportions. It prevents people from using one or two Pokemon all the time, basically, which some trainers will inevitably do.

> Having it consume HP is an even worse idea. Suffering 1/4 extra damage from an attack? That's crazy.Moves will only consume HP once all the endurance points run out. (The last move where endurance is positive will reduce points to zero, but the extra damage to endurance will not carry over to HP. So for example, if you were to use Hydro Pump when you had only 1 endurance point left, you would not suffer 7 damage to HP.)

And why not? It basically means, "If Pokemon are tired, they will be more easily damaged."

> It's only reasonable that endurance would go up with level, but having constants for PP based consumption would make it neglegable at higher levels.Well, I think that just means that higher-level Pokemon have more endurance, and will be able to use more moves. The theoretical power of an attack, for example, is constant, but the actual power goes up with the Attack and Sp.Attack stats of the Pokemon using it.

For example, a level 16 Furret with an Endurance stat of 45 shouldn't really be able to use Hyper Beam 5 times in a row (the PP for that move) without getting extremely tired. But that same Furret at level 40, when its Endurance stat is 100, probably could use Hyper Beam 5 times in a row without getting as tired as it might.

Okay, the minimum of 40 is overkill, I think it should be 15 instead...that was one thing I didn't think through very well.

A few new changes that are a little more dubious:

Fainting: reduce Endurance to zero
Walking 2 steps outside of battle: +1 point (After reflecting on previously played games, I think 1 point per step is a little too much.)
(Note, walking 2 steps outside of battle will also give fainted Pokemon 1 endurance point. This is important, as endurance-restoring items will not have any effect on fainted Pokemon.)
Having a fainted Pokemon refill its endurance gauge by walking: Revive the Pokemon with 1/4 its maximum HP.

That last one is probably going to chucked out as it's suggested, but I'm just putting it out there. It might be especially difficult to implement because this would mean that fainted Pokemon of a higher level are harder to revive than lower-level fainted Pokemon.


As well, I sincerely hope that "Buntoids" is just the name of the engine.

---

### Post by personjerry on 2010-01-06
What's wrong with the name Buntoids? Though seeing as though it's just an engine, the scenarios that can be written for it, even maybe the main plot will probably be a subtitle; so thus different.

As for endurance, my thoughts are similar to scragar's but more like:
I think the endurance idea needs to be completely separate from hp and pp, etc., mixing these adds complexity while not neccesarily adding gameplay value. Other than that all I can say is still "maybe..."

---

### Post by gnuwtey on 2010-01-06
> **personjerry said:**
> What's wrong with the name Buntoids? Though seeing as though it's just an engine, the scenarios that can be written for it, even maybe the main plot will probably be a subtitle; so thus different.

As for endurance, my thoughts are similar to scragar's but more like:
I think the endurance idea needs to be completely separate from hp and pp, etc., mixing these adds complexity while not necessarily adding gameplay value. Other than that all I can say is still "maybe..."

Alright, just putting it out there. (Let's keep tweaking it until it *does *add some gameplay value, hm? Or, if the idea seems hopeless and has little potential, scrape it away. It's not really important.)

As well, I'm interested in how endurance could be completely separated from HP. (I understand how it might be separated from PP, but I'm just wondering.) I think I miscommunicated something - when endurance points are still above zero, HP is completely unaffected by endurance.

Of course, I would need to test it out first, to see how we could fit it into the existing system and make it a useful, relevant, and important part of the game. (After all, that's why this project is open-source, right?)

Also, there's nothing wrong with the name "Buntoids" by itself, but personally it makes me think too much of bunny rabbits and the Ubuntu project.

---

### Post by portets on 2010-01-06
> **gnuwtey said:**
> Also, there's nothing wrong with the name "Buntoids" by itself, but personally it makes me think too much of bunny rabbits and the Ubuntu project.


i think of ubuntu-themed bunnies in space....

---

### Post by personjerry on 2010-01-06
well I see endurance as a requirement for using moves, idk if my impression was correct.
Heh, sorry the base battle system isn't up yet, even I need my holidays, in addition I'm not sure of the exact mechanics of pokemon so I'll probably pull some simpler calculations instead.

As for the name Buntoids... Yeah I guess thats the engine name, probably a game released as the included example would go like "Buntoids: Ubuntumon: Chapter One" or w/e, name isn't that big a deal (many classes and files of the source are still named "pokemon"). Besides, whats wrong with bunnies? We should have a few in every scenario just for that sake :)

---

### Post by Zayfox on 2010-01-07
> **personjerry said:**
> As for the name Buntoids... Yeah I guess thats the engine name
I'm trying to think up a new name before I buy a top-level domain.

> **personjerry said:**
> (many classes and files of the source are still named "pokemon").
I'll fix that ASAP. We need to move entirely to our own structs/classes and names.

> **personjerry said:**
> Besides, whats wrong with bunnies?
Damn things multiply quicker than a times-table class.

---

### Post by Zayfox on 2010-01-07
> **gnuwtey said:**
> Text-damn-wall
I've read the post, I only put that in the quote to save people scrolling.

If they don't want to go ahead with the endurance idea just yet, it looks like I've found the first use for my BETA build. I'll update you when I've begun work on it. If you want to look early, search for a branch called "endurance_inclusive".

**Edit: **Damn automerge!

**Edit 2:** Wait does the Ubuntu forums even HAVE automerge?

---

### Post by personjerry on 2010-01-07
Don't make the name changes yet, they're not a vital part, and probably cause more trouble due to the problems we've had with git. When we come up with a better name, then we can change the names once and for all.

---

### Post by DrWer2 on 2010-01-07
Endurance could effect the likelihood that a "creature's" attack will cause damage. The more endurance the longer a "creature" can go before it begins to miss repeatedly. 

It could be replenished after every battle or after using restore. This may only effect longer battles in terms of gameplay. I don't think there needs to be another potion for this imho, there are so many already.

---

### Post by personjerry on 2010-01-08
If it just affects a pokemon's attacking ability and is reduced after every attack, it just becomes PP.

---

### Post by DrWer2 on 2010-01-08
> **personjerry said:**
> If it just affects a pokemon's attacking ability and is reduced after every attack, it just becomes PP.

It wouldn't effect the attacking ability per say. PP effects whether or not a pokemon can use a certain attack. What I meant was that it would effect the chance that a pokemon's attack would cause damage.

For example, lets say that an attack has a 70 percent chance of causing normal damage, a 5 percent chance of a critical hit, and a 25 percent chance of missing. Should all of these variables be static? 

If the endurance gets to 0 the chance of getting a critical hit should go to 0 and the chance of missing should be increased by 15 at least. This action could be put in with the stats or it could be done in the background out of site of the user.

Please keep in mind that the numbers given are just examples.
Also note that this take on endurance does not necessarily coincide with gnuwtey's. It's just my own take on it.

Does that make sense?

---

### Post by personjerry on 2010-01-09
The thing is, you can change numbers and effects, but the concept remains the same: the more you attack, the less attacks you can do. Thats why endurance should not be added as that, instead at most a change to PP. 

Also:
GUYS MY COMPUTER BROKE, IM ON MY IPHONE, SO DEVELOPMENT WILL ONLY BE BY ZAYFOX FOR A WHILE SORRY :(

---

### Post by portets on 2010-01-09
awww......

you didn't lose any progress did you?

---

### Post by Zayfox on 2010-01-10
> **personjerry said:**
> The thing is, you can change numbers and effects, but the concept remains the same: the more you attack, the less attacks you can do. Thats why endurance should not be added as that, instead at most a change to PP. 

Also:
GUYS MY COMPUTER BROKE, IM ON MY IPHONE, SO DEVELOPMENT WILL ONLY BE BY ZAYFOX FOR A WHILE SORRY :(
Better get myself in gear then, lol.

What compiler do you use btw, jerry?

---

### Post by personjerry on 2010-01-10
Nah my hard drive is intact, so my work is saved (but not uploaded).

I use good old g++ for compiling, as does the makefile.

---

### Post by gnuwtey on 2010-01-10
> **personjerry said:**
> The thing is, you can change numbers and effects, but the concept remains the same: the more you attack, the less attacks you can do. Thats why endurance should not be added as that, instead at most a change to PP.

B-b-b-but... I never said to remove the PP system...

(Another thing - if we are going to do endurance, some of the PP values will have to be increased.)

BTW, if the "taking of extra damage" part seems extreme, maybe have the Pokemon use Struggle once its endurance points are below zero?

> well I see endurance as a requirement for using moves, idk if my impression was correct.Yes, endurance is a requirement for using moves. It's just that it controls the total amount of moves you can make, instead of the amount for each move. (If you run out of PP for one move, you still have all the PP for another.) The system I posted was extremely oversimplified; it was just a first impression.

Basically, you could think of endurance as a "collective PP", which would usually be less than the sum of the endurance drain of all the moves combined.

*edit* Ah yes, a third point. You wanted to make your Buntoids game a little *different* from Pokemon, right? (Of course, the game's script would have the option of using the classic PP system. I'm not advocating throwing PP out altogether.)


Actually... because this is a project trying to spawn innovation (at least I hope it is), I'm going to try and throw out PP completely in favour of Endurance and see how it works. (As soon as the battle engine is done, of course. I can't program it myself, seeing as I don't even know how the code flows as it is now, and it might conflict with the official engine later on.) I don't even necessarily want it to be an official feature.

(For that person who said PP does a much better job [scragar, I think it was], from whose experience are you saying it? The feature hasn't even been tested yet.)


*edit2* I'm looking at the code now... how come Wiggle only has 30 PP? Don't status moves from a starter usually have 40? (That's been the case from pretty much *every* single game from Red on, so no reason to break it now unless you're completely overhauling the system.)

---

### Post by Zayfox on 2010-01-10
> **gnuwtey said:**
> unless you're completely overhauling the system.)
We're completely overhauling the system.





This isn't Pokemon.

---

### Post by portets on 2010-01-10
how about the ability to defend?

like, pick an attack and a defense, then the other buntoid picks an attack and defense, and you hope the defense you chose will make their attack do a little less damage, vice versa......

i think that would fit very well in this type of game. i wonder why the original company didn't do that......

---

### Post by gnuwtey on 2010-01-10
> **Zayfox said:**
> We're completely overhauling the system.

This isn't Pokemon.

In that case, I'm wondering why people are so against the idea of Endurance. (In its present form, I mean. They keep wanting to keep the old PP system. I say test both of them to see if either one makes sense. XD)

Even the PP system isn't that effective against spamming an attack - simply stock up on Leppa Berries (by waiting a few days, XD), or go to the Pokemon Center after every battle. The higher-power moves don't usually need that many landed hits to knock out a Pokemon.

That being said, like Stepmania, it should have the capability of emulating Pokemon, even if it does branch out into its own product. So the PP system should be left in anyway for "backward" compatibility.

(And please don't use "Buntoids", "Ubuntumon", etc. for the name of the game. Naming the engine "Buntoids" is 100% okay, but if you're going to create a "marketable" product like Stepmania, you shouldn't affiliate it with Canonical [I know Ubuntu is actually a word meaning 'humanity toward others', but we all know where you actually got it from], or any other organization, for that matter. I know the Ubuntu concept is really nice, but it seems out of place in a children's game.)

> like, pick an attack and a defense, then the other buntoid picks an attack and defense, and you hope the defense you chose will make their attack do a little less damage, vice versa.

i wonder why the original company didn't do that......I can think of many reasons why they didn't do that.

1. Lack of space. The original Game Boy games were a puny 1 MB in size. Although the programming was probably less than 10% of that, adding this kind of feature wouldn't leave room for some of the graphics that they decided to include. And because the first game pretty much set the precedence for others, they're kind of stuck with the system they have now.

The reason they had so many glitches in the first place in Red and Blue was because they had to take a lot of programming shortcuts to fit the code into such a small space. At least that's my take on it.

2. Complexity. This is a game played by 10-year-olds. You can't have it be *too* complex. As well, choosing both an attack and a defense at the same time isn't really practical, even in the real world. Some of the moves are defense moves anyway. Not to mention the mayhem it would cause when two real people battled their Pokemon.

3. Annoyance. Pokemon battles, as they were in the original game and even in today's games, took long enough as it was, and take long enough as it is. Making it take twice as long would kind of kill it for a lot of people.

Anyway, talk is cheap. Let's talk about this further once the battle engine gets started.

---

### Post by scragar on 2010-01-10
> **gnuwtey said:**
> 1. Lack of space. The original Game Boy games were a puny 1 MB in size. Although the programming was probably less than 10% of that, adding this kind of feature wouldn't leave room for some of the graphics that they decided to include. And because the first game pretty much set the precedence for others, they're kind of stuck with the system they have now.

The reason they had so many glitches in the first place in Red and Blue was because they had to take a lot of programming shortcuts to fit the code into such a small space. At least that's my take on it.
Actually more true than you realise, the battle encounters consisted of 2 bytes of information for the pokemon, sadly this actually meant that:
0000-00FF was the pokemon you encounter normally(with a few errors and trainers that didn't fit otherwise).
0100-01FF was trainers that could be encountered.
0200-08FF was each trainers pokemon, your rival had multiple entries here(3 sets of pokemon for each fight you had with him).
After that you run into all sorts of weird and wonderful errors by modifying the values(including using moves, glitching the entire pokedex and teleporting to various places on the map).
> 2. Complexity. This is a game played by 10-year-olds. You can't have it be *too* complex. As well, choosing both an attack and a defense at the same time isn't really practical, even in the real world. Some of the moves are defense moves anyway. Not to mention the mayhem it would cause when two real people battled their Pokemon.
Seconded, that would be too much to teach a new player to the game, remember, pokemon was accessible, you had 2 moves at the start of the game and 1 pokemon, you started off easy. Throw in 2 attacking moves, 2 defensive moves, then try to explain to someone the importance of guessing the right defence for keeping healthy.

Perhaps defences could be rethought though, I always thought it strange that agility in the show usually resulted in a one off dodge, yet in the game this normally wasn't the case...
> 
3. Annoyance. Pokemon battles, as they were in the original game and even in today's games, took long enough as it was, and take long enough as it is. Making it take twice as long would kind of kill it for a lot of people.

Anyway, talk is cheap. Let's talk about this further once the battle engine gets started.
You ever tried to kill a level 5 metapod with a level 2 pidgey? Long doesn't begin to explain it.
Would be nice to see a timer in trainer battles, no-one wants to battle a trainer and have the battle run on for 30+ rounds, it should be over quickly.

Also might be nice to see other things we can compete using the monsters for, battles are great, but something else once in a while would be nice(always optional, we don't want people getting annoyed because they can't complete a particular mini-game style thing).

---

### Post by DrWer2 on 2010-01-10
> **gnuwtey said:**
> 
2. Complexity. This is a game played by 10-year-olds. You can't have it be *too* complex. As well, choosing both an attack and a defense at the same time isn't really practical, even in the real world. Some of the moves are defense moves anyway. Not to mention the mayhem it would cause when two real people battled their Pokemon.

3. Annoyance. Pokemon battles, as they were in the original game and even in today's games, took long enough as it was, and take long enough as it is. Making it take twice as long would kind of kill it for a lot of people.I agree completely



About the name, we could call it pocket monsters or something like that but in a different language like pokemon did.
japanese: pocket monster = **poke**tto **mon**sut&#257;

---

### Post by DrWer2 on 2010-01-10
> **scragar said:**
> 
Also might be nice to see other things we can compete using the monsters for, battles are great, but something else once in a while would be nice(always optional, we don't want people getting annoyed because they can't complete a particular mini-game style thing).

I agree. Some times pokemon battles start to get repetitive. If we could somehow improve the game to use a little more skill. More than just hitting the A button over and over again](*,) would be nice.


edit: Does Anyone like my take on endurance? I should probably stop calling it that to help reduce confusing it with gnuwtey's idea.

---

### Post by scragar on 2010-01-11
> **DrWer2 said:**
> 
About the name, we could call it pocket monsters or something like that but in a different language like pokemon did.
japanese: pocket monster = **poke**tto **mon**sut&#257;

A naming system would depend on the game, I think for a pokemon remake it'd be nice to just refer to them as animals(or critters, or anything to that effect), since they take the place of animals in the world.

Oh, and I have one demand of the game, Bills PC should become BOFH's PC, just for the geeky reference. Anyone who disagrees needs to present a really good reason why. I'm waiting.

---

### Post by gnuwtey on 2010-01-11
> **scragar said:**
> A naming system would depend on the game, I think for a pokemon remake it'd be nice to just refer to them as animals(or critters, or anything to that effect), since they take the place of animals in the world.

Oh, and I have one demand of the game, Bills PC should become BOFH's PC, just for the geeky reference. Anyone who disagrees needs to present a really good reason why. I'm waiting.

BOFH is okay, too. But not "Buntoids". Seriously? (But mind telling me what that is? If I hear what it means, I might start to disagree on it...) 

> You ever tried to kill a level 5 metapod with a level 2 pidgey? Long doesn't begin to explain it.Nope, I'd use my Squirtle for that. XD

> edit: Does Anyone like my take on endurance? I should probably stop calling it that to help reduce confusing it with gnuwtey's idea.No, it's fine, you can call it endurance. And it might work, but we'd have to test it. (My idea is no exception.) We should probably hold off arguing about whether to keep them or not until the battle engine is actually done.

---

### Post by DrWer2 on 2010-01-11
> **gnuwtey said:**
> BOFH is okay, too. But not "Buntoids". Seriously? (But mind telling me what that is? If I hear what it means, I might start to disagree on it...) 

Google it.


> **gnuwtey said:**
> 
No, it's fine, you can call it endurance. And it might work, but we'd have to test it. (My idea is no exception.) We should probably hold off arguing about whether to keep them or not until the battle engine is actually done.

My idea doesn't really need a name because it would most likely be part of the battle engine and therefore out of sight by the user.:D

---

### Post by gnuwtey on 2010-01-11
> **DrWer2 said:**
> Google it.

Actually, I looked on Wikipedia. But yeah, that might not be the best idea... (I mean, sure, you can use it as an easter egg, but as an essential part to the game, it's unsuitable for a general audience. I can just imagine people going, "What the hell does BOFH have to do anything?")

---

### Post by personjerry on 2010-01-11
About endurance:
See what I'm trying to say is that endurance and pp all revolve on the same concept: using moves makes u able to use less moves. Thus instead of adding complexity in the form of endurance, we integrate it into pp, or something like that.

Very glad there's a lot of discussion going on :).

The moves defined are just for testing purposes for now, there are no animations, heck the battle system is not in place (mind, we just need to code the battle menu and drawing pokemon for it, then some number changing and the system is done, however if you look at my classes you'll realize we'll need to copy pokemon for battles so that stat changes are not permanent other than to exp/lvl/hp).

I may get a new laptop soon, so if we can cross our fingers and not lose this enthusiasm...

Finally we could name the professor Ox in honour of GNU, so it would be Ox's PC, what do we think?

---

### Post by gnuwtey on 2010-01-11
> **personjerry said:**
> About endurance:
See what I'm trying to say is that endurance and pp all revolve on the same concept: using moves makes u able to use less moves. Thus instead of adding complexity in the form of endurance, we integrate it into pp, or something like that.

I may get a new laptop soon, so if we can cross our fingers and not lose this enthusiasm...

Finally we could name the professor Ox in honour of GNU, so it would be Ox's PC, what do we think?

Well no, Ox's PC would be for the "Pokedex", as it is in most of the games. (And no, not even GNU should influence the game's branding. Just look at Neverball... The name "Ox" isn't entirely unacceptable, but you can have it as "Ox" for other reasons as well. Make sure not to officially state that the name "Ox" is based on GNU.)

And I have no intention of adding any unnecessary complexity. I'm not just going to tack the endurance system on and do nothing else with it. It's going to have a lot of work on my part put into it. (BTW, each move will still have a "PP count", so to say, even if I do throw out the PP system entirely in my own separate build. I do realize that each move should have its own counter in some way, because sometimes, you just run out of magic and have to go with physical moves, even in RPG's. But it would mean that physical moves have a very high PP. Say, 50 or 60. But practically, the endurance drain for that move would prevent all of it from being used.)

Oh, BTW, about the temporary stat changes, use that as a temporary variable in the battle, so that no variables are actually changed during the battle, and no Pokemon copying is needed (reduces bugs FTW :D). For example, if your Pokemon class has the following:

class Pokemon{
int attack, defense, sp_atk, sp_def, speed;
} // obviously it's larger than this, but for the current example we only need these variables

Then during the battle, create an entirely new class, which is always initialized in the same way:

class Pokemon_statmod{
int attack = 0, defense = 0, sp_atk = 0, sp_def = 0, speed = 0, accuracy = 100, evasion = 100, status = 0;
}

The variables in this Pokemon_statmod class that are currently initially set to zero indicate the "stage" of the attack/defense/etc. level.

A list of the actual stages they use in Pokemon:

+6 gives a 8/2x multiplier to the stat.
+5 gives a 7/2x multiplier.
+4 gives a 6/2x multiplier.
etc.
0 gives a 2/2x multiplier (normal stats).
-1 gives a 2/3x multiplier.
-2 gives a 2/4x multiplier.
etc.
-6 gives a 2/8x multiplier.

Basically, a positive statmod adds abs(statmod) to the numerator of the multiplier, while a negative statmod adds abs(statmod) to the denominator.

So when damage is calculated, simply multiply the attack and defense by their respective statmods to get the attack and defense used in the calculation.

---

### Post by Zayfox on 2010-01-11
May I remind you all that no matter your idea, it needs to be feasible. Personjerry and I are coding this, and I don't believe either of us have masters in computer sciences or information technology.

Jerry: Professor Gnu? :P
But I must also point out that this is cross-platform. So I don't see any point in referencing Ubuntu, Linux, SDL, or GNU in the game other than to point out what platform it was built on.

In regards to my BETA version; I know I haven't done much recently but I've been busy with a 3D game engine I've been working on.

**Edit:**
> 
class Pokemon_statmod{
int attack = 0, defense = 0, sp_atk = 0, sp_def = 0, speed = 0, accuracy = 100, evasion = 100, status = 0;
}Why do this in-battle? Items like X-Speed have temporary effects anywhere, as do some pokemon moves.


Mods, could we get this stickied? :3

---

### Post by gnuwtey on 2010-01-11
> **Zayfox said:**
> May I remind you all that no matter your idea, it needs to be feasible. Personjerry and I are coding this, and I don't believe either of us have masters in computer sciences or information technology.

Oh, don't worry. I'm sure that the actual game mechanics don't require a master's degree in computer science to implement. It's not like we need Markov chains (except maybe for the AI, but that's optional) or non-linear programming or (dare I say it?) computational geometry to do the stuff that we need to do.

> Jerry: Professor Gnu? :P
But I must also point out that this is cross-platform. So I don't see any point in referencing Ubuntu, Linux, SDL, or GNU in the game other than to point out what platform it was built on.Well, that's like 90% my point... but not because it's cross-platform. Because it's simply an unsuitable thing to do. Pokemon isn't cross-platform, but they didn't name the original game "Game Boy Monsters" or "Nintendomon". That would have been horrible.

> In regards to my BETA version; I know I haven't done much recently but I've been busy with a 3D game engine I've been working on.

**Edit:**
Why do this in-battle? Items like X-Speed have temporary effects anywhere, as do some pokemon moves.I thought X Speed, etc. only worked in battle. They increased whatever status by one stage. (Okay, the status ailments shouldn't be included in the battle-only part, that was a boo-boo on my part. But stuff like confusion and love are strictly in-battle, and so should be included in the in-battle modifier.)

X (stat) only increases the stat in-battle. After the battle is over, the stat is returned to normal.

Stuff like Poison affects you outside of battle, but those outside-of-battle status ailments should be stored in the Pokemon class itself. (Like I said, that was a boo-boo on my part.)

> Mods, could we get this stickied? :3(I don't see why... it's going to be constantly bumped anyway.)

---

### Post by personjerry on 2010-01-11
I do believe the suggestions are very much able to be implemented, though while I await the computer we should sort out fine details.

GNU could refer to the license or even just the animal, or not, I'm just putting ideas out there. 

Fairly sure X Speed, etc only work in battles, but again, added complexity (especially big clunky classes) is, at least in my opinion, not worth just creating a temp copy of the pokemon for. just make another instance of the same class, and you're done. 

Sorry, I'd quote and answer but quote is difficult on here (my iPod).

---

### Post by gnuwtey on 2010-01-11
> **personjerry said:**
> Fairly sure X Speed, etc only work in battles, but again, added complexity (especially big clunky classes) is, at least in my opinion, not worth just creating a temp copy of the pokemon for. just make another instance of the same class, and you're done.

Not sure what you mean, I was trying to make it simpler.

By creating a copy and working on that, you have to keep track of which class is the temp one, and also, when you make attack, speed, etc. rise and fall, how will you keep track of the coefficient? Not to mention, when you have a status ailment, you have to update both Pokemon's stats - the original and the copy.

(For example, let's say the speed of a Pokemon is 73 at state 0, and it falls by two stages in one move (its current state is -2). Then, the new speed is 36. Let's say the next turn, the trainer uses an X Speed. The new speed is actually 48 (with current state -1), but if it had been at state -1 initially (when the speed was at 73), the speed would have changed to 43 and then 55.)

By trying to make it simpler, you're actually making it more complex programming-wise.

(what I'm suggesting is to save some space, and keep the coefficient separate, only factoring it in when damage is calculated. Hell, you don't even need a second class for that, if you really want to make it simple. You can make it part of the main Pokemon class, without having to make a copy at all. What I'm saying is, when the game says, "(Pokemon)'s speed fell!", it doesn't affect the actual speed stat of the Pokemon.)

*edit* No reason for the class to be big and clunky. It's maybe 7 or 8 variables, tops.

> though while I await the computer we should sort out fine details.

Some of these fine details (like the one you just mentioned) can only be sorted out once you have the computer anyway.

---

### Post by Zayfox on 2010-01-11
If we're going ahead with endurance that critter stat class would need to be out of battle. Couldn't we just wrap that inside the already created critter class for per-critter stats?

---

### Post by Zayfox on 2010-01-11
> **gnuwtey said:**
> 
(I don't see why... it's going to be constantly bumped anyway.)
Because it's a project with community input.
People read stickies.

---

### Post by scragar on 2010-01-11
Quick thing I want to add, the X-something items always raised stats 2 levels, not one. It has no real effect, I'm just a bit annoyed keep seeing the wrong number everwhere(Also in the origional games 2 level increase wasn't double stats, not even close).

---

### Post by gnuwtey on 2010-01-11
> **Zayfox said:**
> Because it's a project with community input.
People read stickies.

Ah. But stickies are for extremely important topics, and a lot of projects on these forums have community input as it is. What makes this one stand out?

As for the "critter stats" thing, we can work that out once I've had a good look at the source code. (Yes, Endurance is a lasting stat...)

---

### Post by Zayfox on 2010-01-11
> **gnuwtey said:**
> Ah. But stickies are for extremely important topics, and a lot of projects on these forums have community input as it is. What makes this one stand out?

As for the "critter stats" thing, we can work that out once I've had a good look at the source code. (Yes, Endurance is a lasting stat...)
You're not helping our progress. Be quiet.

**Edit:** What if for each pokemon in the 'inventory', it was pre-declared and we work from that? There's no point constantly declaring variables per-battle.

**Edit 2:** Or declare them but don't discard for pokemon switch, simply set to 0. So have an 'active' class, and then an 'inactive'?

---

### Post by gnuwtey on 2010-01-11
> **Zayfox said:**
> You're not helping our progress. Be quiet.

I shall.

---

### Post by scragar on 2010-01-11
> **Zayfox said:**
> **Edit:** What if for each pokemon in the 'inventory', it was pre-declared and we work from that? There's no point constantly declaring variables per-battle.

**Edit 2:** Or declare them but don't discard for pokemon switch, simply set to 0. So have an 'active' class, and then an 'inactive'?
I figure there's two ways to look a this, the first would be something like:
```
startBattle(trainer Rival){
  foreach critter
     set critter stat multipliers to 0
  do normal init battle stuff
  curPokemon = 0;
}
switchPokemon(int num){
  curPokemon = num;
  change icons and stuff
}

```
Where you leave the battle stats alone, like in the origional pokemon games, the second would work like this
```

startBattle(trainer Rival){
  set first critter stat multipliers to 0
  do normal init battle stuff
  curPokemon = 0;
}
switchPokemon(int num){
  curPokemon = num;
  set current pokemons stat multipliers to 0
}

```This would mean any time a pokemon is removed from battle it's multipliers are reset, it does lead to situations where benching a monster for a single turn to remove the 5 growls your rival just used becomes acceptable, but it also makes for much cleaner code.


Of course here I assume you're OK with the critters each using an extra 10 or so(at most) bytes of information, this isn't anything worth complaining about, and if need by if you're using the second solution it might be more acceptable to simply have a global curPokemon multipliers system, this would most of the time be turned off, so you'd never have to worry much about the ram usage.

---

### Post by personjerry on 2010-01-12
Adding two temporaries are not hard..

void battle()
{
  Poke play = party[0], cpu = target;
}


And then that get rids of coefficients because you actually CHANGE the stats by multiplying them, as opposed to multiply them every time you need a value.

---

### Post by gnuwtey on 2010-01-12
> **personjerry said:**
> Adding two temporaries are not hard..

void battle()
{
  Poke play = party[0], cpu = target;
}

And then that get rids of coefficients because you actually CHANGE the stats by multiplying them, as opposed to multiply them every time you need a value.

When the status move up and down a stage, the change is not constant. For example, if you wanted to raise a stat at -4 by 2 stages, you'd have to multiply the stat by 1.5, but if you wanted to raise a stat at -2 by 2 stages, you'd have to multiply the stat by 2. Either way, you still have to keep track of the stage of the stat. (And coefficients are not really that complex. At least, I'm more comfortable with doing that than actually multiplying the stats. How's this, when the battle engine is done, I'll code a separate version that uses a different temp Pokemon class, and save it as a different branch. Then we'll compare the two methods and actually see which method is simpler. Because for some reason, each party in this argument thinks the other party's method is more complex.)

Sometimes, you just need the stats to be easier to manage, even if it does take a few more cycles to compute. (It's a negligible change, really. We're not coding this for the Game Boy, so we don't really need to cut so many corners. It's not like the stats change 1 million times every second.)

Secondly, we can just use a lookup table for the coefficients that correspond to each stage. It's like 30 or 40 bytes, max. Actually, I think this is where I caused the confusion. I meant that we needed to keep track of the stage, not the actual coefficient that corresponded with the stage. So, for example, in my Pokemon_statmod class, the possible range of the Attack/Defense/Speed/etc. mods is from -6 to 6. Then, when calculating damage, you can use a lookup table to multiply the Attack and Defense stats properly.

Also, about the resetting stat stages thing, keep the coefficient with each Pokemon until the end of the battle, instead of when they're switching out. The code is equally as clean, and we can keep the stats. If we're going to use temp Pokemon during the battle, that translates to: Keep temp objects of all the Pokemon, instead of just the active one, and discard all of them once the battle is finished.

---

### Post by personjerry on 2010-01-12
I'd like to say, why create a new class when you can just change numbers?

for example:
```

//enemy used mud slap
player->setAccuracy(player->accuracy/1.5);
//player turn
player->attack;
//player used some accuracy increasing ability
player->setAccuracy((player->accuracy+1)/2);

//where accuracy is between 0 and 1

```

whereas new classes mean more checking and work to make sure the class conforms to input/output requirements, which could be handled by the existing class, meaning extra maintenance, more potential for bugs. That is to say, in my experience whenever classes are not neccesary, don't add extra classes, because they are a large commitment. 

If still not convinced though, I guess we'll see from the future fork.

---

### Post by gnuwtey on 2010-01-12
> **personjerry said:**
> I'd like to say, why create a new class when you can just change numbers?

for example:
```

//enemy used mud slap
player->setAccuracy(player->accuracy/1.5);
//player turn
player->attack;
//player used some accuracy increasing ability
player->setAccuracy((player->accuracy+1)/2);

//where accuracy is between 0 and 1

```

Your example is wrong, though. The accuracy-raising and -lowering stats don't work that way in the actual game.

Also, there is a way of implementing the "stat stages" without creating a new class, or creating copy objects, which would be to use the stage variables I was talking about earlier, and resetting them to 0 after a battle. I'm sorry I didn't suggest that initially, but it was just an idea at the time.

So for example, what would happen in my code is:

```

// (pkmn2) used Mud Slap
pkmn1->ChangeAccuracy(-1);
// (trainer) used X Accuracy
pkmn1->ChangeAccuracy(1);

// ...

// inside the class:
void ChangeAccuracy(int n){
    accuracy_statmod -= n;
}

// ...

// when calculating whether the attack will miss or not: (accuracy is a floating point number, where 1 is 100%)

int nProbability = 65535 * (curmove->accuracy * coeff[accuracy_statmod + 6]); // assuming rand() goes from 0 to 65535; change to 32767 if required
// each move has its own accuracy modifier - some moves, for example, have an accuracy of 0.8 by default. Pokemon do not have Accuracy stats, and at the start of a battle, it is always set to be 1.

// the +6 is implemented because you can't do a array[-6] pointer without occasionally getting errors.

if(rand() < nProbability){
    attack(pkmn2);
}else{
    // nothing happens, the attack missed.
}

```And in damage calculation:

```

void attack(Pokemon enemy){

double randmod = 0.85 + (rand() / 65535.0 * 0.15); // once again, this assumes that rand() goes to 65535.

damage = (((level*2) + 10) * (attack * coeff[attack_statmod + 6]) * curmove->damage / (250 * (enemy->GetDefense() * coeff[enemy->GetDefenseStatmod() + 6])) + 2) * stab * type_modifier * randmod;

enemy->TakeDamage(damage);
}
// original damage calculation formula from Pokemon; source: Bulbapedia

```And the lookup tables would look like so:

```

double coeff[13] = {2.0/8.0, 2.0/7.0, 2.0/6.0, 2.0/5.0, 2.0/4.0, 2.0/3.0, 2.0/2.0, 3.0/2.0, 4.0/2.0, 5.0/2.0, 6.0/2.0, 7.0/2.0, 8.0/2.0};

```

---

### Post by personjerry on 2010-01-12
it was an example, you can just change coefficient or use *x and /x

anyway, just using variables could work.

---

### Post by gnuwtey on 2010-01-12
> **personjerry said:**
> it was an example, you can just change coefficient or use *x and /x

anyway, just using variables could work.

I guess. But you would have to keep track of the stage, is what I'm saying.

And when I said they don't work that way, I meant, they use an entirely different system altogether. The change is not constant, meaning that lowering a stat by two stages does not always mean multiplying it by 1/2, for example. So *x or /x would not work.

---

### Post by personjerry on 2010-01-12
Well first we don't need to adapt their system, second how does it change?

And by the law of powers, multiplying or dividing every time according to stages of change will always work, and keeping track of the stage is redundant when the actual attribute can just be multiplied when raising, divided when lowering.

---

### Post by gnuwtey on 2010-01-12
> **personjerry said:**
> Well first we don't need to adapt their system, second how does it change?

And by the law of powers, multiplying or dividing every time according to stages of change will always work, and keeping track of the stage is redundant when the actual attribute can just be multiplied when raising, divided when lowering.

I know that changing it to a powers system will definitely work, and will eliminate the need for stages.

But the way it changes in the Pokemon games is simply by what I said earlier - stages. At each stage, a different, predetermined multiplier is applied to the stat when factoring damage and probability of hitting.

Since I don't seem to be doing a very good job of explaining what it is, may I turn you to [Bulbapedia]("http://bulbapedia.bulbagarden.net/wiki/Stat#Stat_modifiers").

(Actually, the article says that accuracy and evasion are calculated differently, but doesn't specify how. We could use a log scale for that.)

---

### Post by DrWer2 on 2010-01-12
I assume that buntoids, or whatever the name will be, will need to use different "creatures" than those used in the pokemon games. If this is true will we just change the names and the sprites? 
Would this require a separate thread in order to better organize the discussions?   

Also I thought I would mention something I've been thinking about for a while now. This game has slightly more potential than the original Pokemon games had. Multi-player over the internet has so many more possibilitys. 
The menu based communication system in pokemon was limited, and for good reason.  
One, gameboys are not ideal for entering text. And two, As stated earlier in this thread, 10 year olds will likely be playing this game. It needs to be safe for all ages.  

A choice must be made. Text based communication or menu based communication. A method of censoring text could also be used but it would be more complicated to code.

---

### Post by personjerry on 2010-01-12
Yes we'll need our very own creatures. Multiplayer has not been mentioned, but is a definite possibility.


btw we should have a vote soon on mechanic details.

---

### Post by gnuwtey on 2010-01-12
> **DrWer2 said:**
> wall-o'-text

NOTE: I'm replying to the whole thing, so to save space I'm not quoting it all.

Based on what I know of the developers' intentions, the Buntoids engine is meant to be concept-neutral - that is, it does not favour one game over another, but instead aims to be supportive of all sorts of these games, as long as they follow a certain standard of gameplay that Pokemon also follows.

This means that a game might have all 493 current Pokemon, but also be extensible to new species of monsters, which would be categorized differently.

For example, the finished product should probably have full support for a plugin for a game called "[Keitai Denjuu Telefang]("http://en.wikipedia.org/wiki/Keitai_Denjuu_Telefang")" - which was bootlegged here in N.A. as "Pokemon Diamond" and "Pokemon Jade" about seven or eight years ago. (Freaky, isn't it. There's a real Pokemon Diamond and a bootlegged game called "Pokemon Diamond" that has completely different monsters. It would be an even bigger coincidence if the other one was "Pearl". :D)

BTW, as a generic name for these "critters", I'd suggest simply "monsters". Pretty much all Japanese games (at least, the ones I know of) revolving around fictional creatures use the same word for them - "monsters". And most games from this genre are Japanese, so we should probably not try and get away from that. (Pokemon calls them... well, "pocket monsters", Telefang calls them "E-monsters/Denjuu" [which just means E-monsters anyway], and Yu-Gi-Oh and Monster Rancher calls them just plain "monsters". This is a very incomplete list, but pretty much constitutes all I know about them.)

For the purposes of the game, text-based communication would be too hard to recognize when playing against the system. We'd have to include maybe a gigabyte of code for that, and it's simply not feasible given the crack team we have now. (Well, I wouldn't say it's a *crack* team, exactly, but it's not exactly a team of full-time professionals.) For multiplayer games, it would "simply" be a matter of relay chat.


Actually - instead of emulating Pokemon, we could make our goal to emulate this lesser-known game first (Telefang), and *then* build in support for Pokemon.

*edit* Even worse, the Telefang website is from a company called "[Rocket Company]("http://www.rocketcompany.co.jp/telefang/")". WTF.

---

### Post by gnuwtey on 2010-01-15
*bump* Have people forgotten about this already...? (Or is everybody suddenly very busy with their lives? I'd understand.)

BTW, just another suggestion, in the beginning of the alpha trials, we could put in some Engrish to be funny.

For example:

"It's super effective!" changes to "It's very good effect!"
"It's super effective! (4x damage)" changes to "Is excellent effective!"
"It's not very effective..." changes to "It's very not effective!"
"It's not very effective... (1/4 damage)" changes to "Is utterly ineffective!"
"It didn't affect (Pokemon)!" changes to "The attack damaged not at all!"
"Critical hit!" changes to "Critical hit!"

"The attack did 48 damage!" changes to "Enemy lost 48 points!" (Only applies if we're doing the Telefang port.)

Etc. You get my idea.

But only during the alpha trials. During the alpha trials we'll also have stuff like BOFH's PC and Professor Ox.

---

### Post by portets on 2010-01-16
i like that idea. i think...   but only in the early alpha stuff.

when it starts to get more stable i'd like to see some sarcastic/abstract humor

---

### Post by scragar on 2010-01-16
> **portets said:**
> i like that idea. i think...   but only in the early alpha stuff.

when it starts to get more stable i'd like to see some sarcastic/abstract humor

I think the villans of the game should be based on peta, trying to stop people capturing creatures and forcing them into fights, sounds like the sort of thing they'd be involved in. :p

---

### Post by gnuwtey on 2010-01-16
> **scragar said:**
> I think the villans of the game should be based on peta, trying to stop people capturing creatures and forcing them into fights, sounds like the sort of thing they'd be involved in. :p

YES. WANT. O_O

But what would they be called? The "Pokemon's Ethical Treatment Association?"

---

### Post by DrWer2 on 2010-01-16
> **gnuwtey said:**
> *bump* Have people forgotten about this already...? (Or is everybody suddenly very busy with their lives? I'd understand.)

BTW, just another suggestion, in the beginning of the alpha trials, we could put in some Engrish to be funny.

For example:

"It's super effective!" changes to "It's very good effect!"
"It's super effective! (4x damage)" changes to "Is excellent effective!"
"It's not very effective..." changes to "It's very not effective!"
"It's not very effective... (1/4 damage)" changes to "Is utterly ineffective!"
"It didn't affect (Pokemon)!" changes to "The attack damaged not at all!"
"Critical hit!" changes to "Critical hit!"

"The attack did 48 damage!" changes to "Enemy lost 48 points!" (Only applies if we're doing the Telefang port.)

Etc. You get my idea.

But only during the alpha trials. During the alpha trials we'll also have stuff like BOFH's PC and Professor Ox.

Why not do it right the first time? That way we don't need to go back and change it.


> **scragar said:**
> I think the villans of the game should be based on peta, trying to stop people capturing creatures and forcing them into fights, sounds like the sort of thing they'd be involved in. :p

I like the idea, but how would you battle them if peta doesn't fight with creatures? Other than that, sounds great.:D

---

### Post by scragar on 2010-01-16
> **DrWer2 said:**
> 
I like the idea, but how would you battle them if peta doesn't fight with creatures? Other than that, sounds great.:D

Well I was actually thinking two fold here, the enemy in the game is usually more of a hindrance than a threat, and in the anime team rocket used machines more than actual pokemon.
If you are making the game yourself it's only too easy to add a few creatures to the list that don't appear in the dex, can't be caught and don't appear in the wild at all. These would be the machines that PETA use against you in an attempt to stop you competing in the league, thus depriving the league of competition and eventually income.

---

### Post by portets on 2010-01-16
well peta has bombed buildings, which hurt/kill people.

i think they *should *battle with animals because that's something they would do. brainwash themselves into thinking if they sacrifice a few animals, it would save millions.

but yeah, i'd like to see them more as a hindrance.

and awesome idea scragar! that's something i'd definitely like to see

---

### Post by Zayfox on 2010-01-16
> **scragar said:**
> I think the villans of the game should be based on peta, trying to stop people capturing creatures and forcing them into fights, sounds like the sort of thing they'd be involved in. :p
That is possibly the best idea I've heard from anyone other than the core devteam yet. Awesome!

---

### Post by gnuwtey on 2010-01-16
> **DrWer2 said:**
> Why not do it right the first time? That way we don't need to go back and change it.

Because it's going to pretty hard to do it right the first time when we don't even have a solid idea about what exactly we're doing with the story. We're going to have to go back and change everything when doing the betas/gammas/release candidates anyway. When we're doing the betas, then we'll go back and do another overhaul of the text.

What I mean by language files:

Different languages will place the variables in different places.

So for example, we might have "The attack did %d damage!", but in French, it would change to "L'attaque a fait %d points des dommages!", and in Japanese, it might be "&#25915;&#25731;&#12398;&#12480;&#12513;&#12540;&#12472;&#12509;&#12452;&#12531;&#12488;&#12399;%d&#12391;&#12375;&#12383;&#65281;" (Excuse my horrible Japanese, I'm still learning.)

---

### Post by portets on 2010-01-17
hey, i made a few critters just as placeholders to test the battle mechanism!

this way you won't have to use pokemon images. ;)

it's called an Amebo. you guessed it, it's an amoeba.

shapeshifter critter. i'll refine it later

[ATTACH]143876[/ATTACH] battle

[ATTACH]143877[/ATTACH] pose

[ATTACH]143878[/ATTACH] icon

---

### Post by personjerry on 2010-01-17
I must say, thats the first submission so far, thank you!

So basically I'll be using a crappy computer for a bit until I can scrape up for a new one. But hopefully I'll be able to code.And no I haven't forgotten, it would be a shame to have caused so many ideas only to toss them out :)

Lastly, about the PETA idea, remember that this is an engine, feel free to make PETA scenarios. Or for the core game, if desired.

---

### Post by gnuwtey on 2010-01-17
> **personjerry said:**
> Lastly, about the PETA idea, remember that this is an engine, feel free to make PETA scenarios. Or for the core game, if desired.

Mm hmm.

Of course, we'd need to make a excellent engine and a very small core game. XD

BTW, how are things going so far? With the coding, I mean. I don't check the repositories very often, unfortunately, so I don't know if any progress has been made or not when I do check them, simply because I don't know where or how things were before.

(Also: )

> **portets said:**
> hey, i made a few critters just as placeholders to test the battle mechanism!

this way you won't have to use pokemon images. ;)

it's called an Amebo. you guessed it, it's an amoeba.

shapeshifter critter. i'll refine it later

For Amebo (Amiba; I feel like making a Japanese name for it right off the spot), how come it doesn't have a face? And it looks an awful lot like Ditto. (Oh well.)

(*edit* Whoops, I didn't understand the "you'll refine it later" part. Sorry!)

How do these names sound:

Japanese: &#12450;&#12511;&#12496; (Amiba)
German: Amöbo
French: Amibo
Spanish: Amebo

> this way you won't have to use pokemon images. ;)What's wrong with using Pokemon images in the prototype before the alpha stages? It's not like we're repulsed to it, and it's not like the engine cares. (Although your Amiba is good for something; I'm not trying to say that it's bad. It might be one of the final core-game monsters.)

Another point: There are a lot of people on the "Interwebs" that have created their own fanmade Pokemon. Perhaps we could hold a contest on some site or whatever to have their Pokemon included in this game? Once the project gains some more momentum, that is.

---

### Post by personjerry on 2010-01-17
I seem to be the lead developer, idk where zayfox has gone, but I've just returned from a computer absence. The battle system is still the topic at hand, and if I stop procrastinating maybe I'll get it done before the summer ;P

nah i'm kidding it should be done well before March.

---

### Post by gnuwtey on 2010-01-17
> **personjerry said:**
> I seem to be the lead developer, idk where zayfox has gone, but I've just returned from a computer absence. The battle system is still the topic at hand, and if I stop procrastinating maybe I'll get it done before the summer ;P

That would certainly be nice, considering it took the original developers three years...

BTW, as an engine, we need to come up with generic terms for the various variables and items that might come up.

(The existing stat names in Pokemon are pretty generic already, actually. "HP", "Attack", "Defense", "Special Attack", "Special Defense", "Speed". Doesn't get much more generic than that.)

But things like "Potion", "Antidote", etc. might need to be changed.

For example, in Telefang, the equivalent of a "Potion" is called "Herb". In Japanese, it is called "wound medicine" (&#20663;&#34220;, *kizugusuri*, wound medicine).

And the pyen issue. What shall we call pyen? (the currency in Pokemon, I mean. We can't use dollars, because that's a real-world currency and the game isn't set in America or any British colonies.)

---

### Post by scragar on 2010-01-17
> **gnuwtey said:**
> That would certainly be nice, considering it took the original developers three years...

BTW, as an engine, we need to come up with generic terms for the various variables and items that might come up.

(The existing stat names in Pokemon are pretty generic already, actually. "HP", "Attack", "Defense", "Special Attack", "Special Defense", "Speed". Doesn't get much more generic than that.)

But things like "Potion", "Antidote", etc. might need to be changed.

For example, in Telefang, the equivalent of a "Potion" is called "Herb". In Japanese, it is called "wound medicine" (&#20663;&#34220;, *kizugusuri*, wound medicine).

And the pyen issue. What shall we call pyen? (the currency in Pokemon, I mean. We can't use dollars, because that's a real-world currency and the game isn't set in America or any British colonies.)

Not really, it's an engine, everything is going to be defined by data files, that means the items list can be edited later, for now we can be happy with "HP restore" or some such. It's nice to think of ideas for what you could do with a completed engine, but most of the stuff we've been thinking off is related to what will go in the data file, not the engine(I sort of forgot this was going to be an engine, and not a game myself actually).

---

### Post by gnuwtey on 2010-01-17
> **scragar said:**
> (I sort of forgot this was going to be an engine, and not a game myself actually).

As did I. But it is an engine that, upon completion, should have a full Pokemon port. (And perhaps a full Telefang port, if somebody could salvage that game.)

And I was thinking of words that would appear in the code. We could just use Pokemon terms for everything in the original code before we go back and revise it, but I seem to see that some people are against that.

---

### Post by portets on 2010-01-18
> **gnuwtey said:**
> Mm hmm.

For Amebo (Amiba; I feel like making a Japanese name for it right off the spot), how come it doesn't have a face? And it looks an awful lot like Ditto. (Oh well.)

It doesn't have a face because i always thought that Ditto wouldn't need a face if it changes forms.

> (*edit* Whoops, I didn't understand the "you'll refine it later" part. Sorry!)

exactly that, i will soon make it less like Ditto. how can you make a glob not look like ditto though?

> How do these names sound:

Japanese: &#12450;&#12511;&#12496; (Amiba)
German: Amöbo
French: Amibo
Spanish: Amebo
i don't know. i guess Amebo and Amibo both work. we can figure out more specicific names/translation/whatever later anyway.

> Another point: There are a lot of people on the "Interwebs" that have created their own fanmade Pokemon. Perhaps we could hold a contest on some site or whatever to have their Pokemon included in this game? Once the project gains some more momentum, that is.and yeah! that's actually a good idea. we'd just need to get them to agree on licensing their work in an open license.

---

### Post by Zayfox on 2010-01-18
> **portets said:**
> Iand yeah! that's actually a good idea. we'd just need to get them to agree on licensing their work in an open license.

I'll sort promotion out soon.

---

### Post by portets on 2010-01-18
we should probably wait until the battle system is somewhat working and available.

people like instant gratification....;)

---

### Post by personjerry on 2010-01-18
Zayfox is here, I'm back, work will continue I guess.

---

### Post by personjerry on 2010-01-19
I'll probably post an update every few revisions about what's going on with the code. Zayfox, if I could get admin access to the site, I'll mirror it there too.

Development Update:
My most recent revision of the code instated new music! Any time in the game, if you press the BACKQUOTE/TILDE key (the one to the left of the "1" or "!" key) it activates a "cheat" which will take you to "battle mode". However since drawing menus take a copious amount of time I have not made the menu yet, but you can hear the sound of the battle take place (I had to splice the music into two parts so that the loop can loop, and because we don't have a queue for music yet). Beware that after doing so your keys will not do anything because they are shifted to affect the menu which does not exist. If I could get comments on how the music sounds... this computer is having problems. In addition the Ogg errors should now be more detailed.

-Jerry

---

### Post by portets on 2010-01-20
hello. my computer was also having sound problems until i made a new blank text file in my home directory ".alsoftrc", and inside had it say "drivers = oss". hope that might help.

and yes, the battle music works just fine

---

### Post by portets on 2010-01-20
and here's a battle menu! :D

just whipped it up in twenty minutes or so. i'll refine it later. (again)
haha

[ATTACH]144232[/ATTACH]        (click for fulll size, albeit tiny)

edit: added battle scene

[ATTACH]144288[/ATTACH]

suggest what you would like to change. and sorry if you don't like it, i can make things different.

---

### Post by DrWer2 on 2010-01-20
> **portets said:**
> and here's a battle menu! :D

just whipped it up in twenty minutes or so. i'll refine it later. (again)
haha

[ATTACH]144232[/ATTACH]        (click for fulll size, albeit tiny)

edit: added battle scene

[ATTACH]144288[/ATTACH]

suggest what you would like to change. and sorry if you don't like, i could make things different.
I like it.(the checkerboard background reminds me of Earthbound)  
The new take the HP graph is nice, although it does take up more space than necessary imho (this leaves  little room for the rest of the menu). The only other thing that worries me is the absence of the EXP graph. Other than those things, it's great. :D

---

### Post by gnuwtey on 2010-01-20
I think, once the final thing is done, the "Sans" font has to go. It's hard on the eyes (at least mine, anyway). Same with the checkerboard, or at least the checkerboard's colour scheme. The way it looks now, it's like a transparent background in Photoshop (or even GIMP).

As well, the shape of the lifebar is unappealing. It's too thick at the top, and most bars of this nature are thin, simply to provide more accurate judgment of proportions. (It's the same reason graduated containers are thin.)

But, as you said, you'll refine it later. I don't intend to criticize the project destructively. I'll see if I can't whip a font up for you to use on this project. (instead of Sans... *shudders*) But you'd have to wait about a week, as I have exams coming up around that time. As is normal for this type of project, it will be released under an open license.

The general layout is fine, but don't round the corners of the boxes so much. (As well, don't align one column to the right and one to the left. It makes the command box look uneven. Alignment is one of the most critical things when designing a layout. If things don't align correctly, the whole product looks bad.)

*edit* Also, why are you making the graphics 144x144? Shouldn't the game, as it is being designed for a PC, have slightly better graphics than the portable game version? I'd recommend a window size of at least 320x240.

---

### Post by portets on 2010-01-20
yes, the life bar is a bit big, i'll change it. the font; i just used gimps default, i'll change it to a better one.

the checker background is something jerry or zayfox made, i'm not responsible ;)

also, the rounded corners; i just flipped the games menu on it's side, shrank it, and made it solid. to fit with the theme better.

the resolution of this game is VERY tiny. i just made the battle scene the size of the game.

i actually made a fork of this project that is 640x480 and all textures and tile based events are now 32x32 instead of 16x16 in my version. i also had to adjust menu positions. i don't have my fork uploaded anywhere yet though

it takes a surprising amount of coding to change the resolution and image sizes for a tile-based game if you didn't know. and also having to change the image size of each texture

---

### Post by gnuwtey on 2010-01-20
> **portets said:**
> it takes a surprising amount of coding to change the resolution and image sizes for a tile-based game if you didn't know. and also having to change the image size of each texture

I could help with that, when I have the time. But I still think the original resolution is bad for the eyes.

---

### Post by portets on 2010-01-20
where would be the best place to upload my work?
i don't know how to use git. and i'm pretty much done, so i don't need something as powerful as git

edit: i think i'm creating a sourceforge

---

### Post by personjerry on 2010-01-20
IMO any  file upload service would do (filefront, megaupload, etc). once it's zipped up, unless further changes are to be made

The background I drew for the pokemon selection menu, we could change it to some slow gradient (green?) like the pokmon games. if I remember correctly though it only covers the centre of the screen not the whole screen.

 Btw did you guys know the game has a "Zoom" function? command line: ./buntoids -f will give you full screen game with the pixels blown up.

 But yeah we definitely need more precision for the images.

---

### Post by Zayfox on 2010-01-20
> **portets said:**
> where would be the best place to upload my work?
i don't know how to use git. and i'm pretty much done, so i don't need something as powerful as git

edit: i think i'm creating a sourceforge
If you want, I can +git it to the BETA branch, just zip it up and upload it somewhere.

Sorry I haven't been particularly active guys, I've been busy with a lot of other stuff (work, school, WoW guild, etc.)

---

### Post by portets on 2010-01-20
> **Zayfox said:**
> If you want, I can +git it to the BETA branch, just zip it up and upload it somewhere.

Sorry I haven't been particularly active guys, I've been busy with a lot of other stuff (work, school, WoW guild, etc.)

alright. let me just copy and paste my work into jerry's latest revision. i'm also going to make my battle scene come up when hitting the backquote/tilde key.

---

### Post by portets on 2010-01-21
hopefully the below link works.

[https://docs.google.com/leaf?id=0ByBA2iQHjx06ZDAzOGE4YjAtYzdjNC00NTlhLWFiMWUtNmFjNzUzMzNiNzgw&hl=en](https://docs.google.com/leaf?id=0ByBA2iQHjx06ZDAzOGE4YjAtYzdjNC00NTlhLWFiMWUtNmFjNzUzMzNiNzgw&hl=en)

---

### Post by gnuwtey on 2010-01-21
> **portets said:**
> yes, the life bar is a bit big, i'll change it.

It's not the size I'm worried about, it's the shape.

(Who am I kidding, though, I'm not going to be able to work on this until about a week later. I can help with layout design, though, when I do work on it.)

---

### Post by personjerry on 2010-01-24
For the record, portets your sound fix worked wonders.
The version you uploaded was of my latest revision, right? Then I'll start fixing some problems with your version and "merge" it.

EDIT: Not going to work, the resizing has created collision errors and other issues. To speed the player up though in the version use this, replacing the similar existing part in player.cpp:
```
		switch(move) {
			case 2:		if(walk[0]) pos_x+=2; angle=3; frame=103+extra;		break;
			case 4:		if(walk[2]) pos_x-=2; angle=8; frame=108+extra;		break;
			case 8:		if(walk[3]) pos_y-=2; angle=0; frame=100+extra2;		break;
			case 16:	if(walk[1]) pos_y+=2; angle=5; frame=105+extra2;		break;
```

(just change the ++ and -- to +=2 and -=2 )

---

### Post by personjerry on 2010-01-24
Revision Update Number 2:

The menu for battles is finished, while not nearly fully functional. I'm going to try to implement basic moves' damage effects and such soon, probably as the next step. This will also open another option for the battle menu. You can now see your buntoid and the one you're facing. And while switching is not functional yet, you can open your BNTD menu to check on your party.

In addition, I need someone to go flip all the pose images in the gfx/pokemon folder so they face the left.

Thanks for your interest!
-Jerry

---

### Post by portets on 2010-01-24
i can flip those images for you. and about my version; collision errors? could you post them? edit: because i can't find *any *at all

i think that my original mod was error-free, but i didn't check very much. afterall, i did just copy and paste my modded work into your latest revision....

edit: forgot to mention i'm pretty new to coding..   :D

and **great **about helping with your sound. glad to have helped. although, every once in a while it seems that oss won't load causing games not to have sound and when a new sound event is triggered it will crash the game you're playing.
hopefully all of this will be fixed for ubuntu 10.04

edit again: tested your latest. everything seems solid, but you forgot to put 00.ogg in the sfx folder. i just copied and pasted 01.ogg from an older version and renamed it. i assume that's the file you wanted there because it was the only one missing

---

### Post by personjerry on 2010-01-24
I'm not sure exactly how but I got stuck at the roof of a few buildings (especially the corners).

And yeah I think OSS just likes working one sound at a time... sometimes.
But the sound workaround isn't a solution, we need to ensure it doesn't happen, so I'm thinking switching to sdl sounds may be a good idea.

Finally, yes I forgot to add 00.ogg to the repository after naming... my bad :) Thanks for catching that!

---

### Post by portets on 2010-01-24
oh, i think that happened to me too. twice.

the first one was after i was talking to nerd 1, i couldn't move. i could face different directions but couldn't go anywhere. the other was outside after talking to someone.
is that what happened to you too, but you didn't talk to anyone?

i'll look into this further

**EDIT: also happens in the original pokemon engine by** **Robin Stjerndorff**. before you and zayfox even picked it up.

i'd post a screenshot, but that wouldn't help. maybe i could post a video. but try talking to the guy that talks about technology. it happens with him the most it seems. just keep trying to talk to him at various angles

---

### Post by personjerry on 2010-01-24
Yeah I just walked past a house and got stuck. Could still turn though.

---

### Post by portets on 2010-01-24
i just edited my above post. could you attempt getting stuck in your latest revision?

---

### Post by personjerry on 2010-01-24
Okay, I walked for around 5 minutes around the buildings, especially the corners, but could not duplicate the bug in my revision.

Then I opened the big version, proceded to a building and promptly got stuck. :S
Perhaps the engine did have an issue, but resizing certainly makes the bug much more inconvenient. I'll attempt to check the code, but it's somewhat obfuscated...

---

### Post by portets on 2010-01-24
> **personjerry said:**
> Perhaps the engine did have an issue, but resizing certainly makes the bug much more inconvenient. I'll attempt to check the code, but it's somewhat obfuscated...

i'm starting to think that may be it.

i also noticed that it will go long periods without getting stuck on any of the versions. then when i do get stuck in one, eg. mine, i can close the game and open up a different version, eg. the original, and it will get stuck in that one.

what i'm trying to say is that there will be about 5 minute periods that i can get stuck in any version, but after that i fail to get stuck.

coincidence? i don't see this being a time-based issue. so it probably is a coincidence

---

### Post by portets on 2010-01-24
okay, the code you posted on page 9 to make my character move faster; are you testing my big version with that code?

i just tried your code and now i get stuck wherever i go.

i think your peice of code just uncovered a bug in colision detection.

it also messes up your version of the engine

---

### Post by gnuwtey on 2010-01-24
BTW, another seemingly trivial matter - when a trainer runs out of Pokemon, are we making him lose half his money, or are we going to use the formula that FR/LG onwards uses?

(I can't reproduce the formula exactly, but I think it's like this:)

8 * L * (badges + 1)

where L is the level of the highest-level Pokemon in the trainer's party, and badges is the current number of Gym Badges that the trainer has.

Personally, I prefer the new formula, as it allows for us to make it much easier for the trainer to lose.

(BTW, sorry if I'm interrupting any discussion. I still can't work on this until Thursday.)

---

### Post by portets on 2010-01-24
these are the flipped poses

[https://docs.google.com/uc?id=0ByBA2iQHjx06Mjg2YjdhYzItMjRiMC00MjliLTliNDEtNTVhMmQ2ODdmMTBm&export=download&hl=en](https://docs.google.com/uc?id=0ByBA2iQHjx06Mjg2YjdhYzItMjRiMC00MjliLTliNDEtNTVhMmQ2ODdmMTBm&export=download&hl=en)

---

### Post by personjerry on 2010-01-25
Thanks, I've updated them.
And yeah my code has issues I guess, the boundary testing does not work very flexibly.

---

### Post by portets on 2010-01-25
okay. i think i forgot to flip 2_pose.png. a few of the other poses beyond that number look like they haven't been flipped, but they have. just something nintendo did.

is changing 1000
```

if(fps.get_ticks()<1000/FRAMERATE)
        SDL_Delay((1000/FRAMERATE)-fps.get_ticks());
```to 500 a reliable way of doing things?

because that doubles my players speed without causing any more collision issues than we already have.

gosh, i really need to start reading more of my c++ book

---

### Post by personjerry on 2010-01-25
That will make the program take double processing power. it basically reduces the delay before each calculation, raising fps.

---

### Post by portets on 2010-01-25
okay, i had a feeling it was bad. (dealing with fps and all)

---

### Post by gnuwtey on 2010-01-25
> **personjerry said:**
> That will make the program take double processing power. it basically reduces the delay before each calculation, raising fps.

What system requirements are we aiming for? If the game is unplayable on half the world's systems, that doesn't bode very well for the game.

That being said, raising fps might be a good testing measure for just one computer when you're testing something that's not the graphics/overworld engine and need it to run quickly. (The accuracy of an attack, for example, or damage calculation.)

In that case, you can do what VisualBoyAdvance does, have a toggle key that sets the "1000" in the code above to 1 and watch the madness unfold.

---

### Post by personjerry on 2010-01-25
In theory the game should be able to be played even on relatively low end computers, seeing as it's a port of games from older systems.

The fps increase was an attempt to reduce some lag that the resized version gets.

Finally I don't see the craziness of 3826838472 fps in a turn based system such as this :p

---

### Post by gnuwtey on 2010-01-25
> **personjerry said:**
> Finally I don't see the craziness of 3826838472 fps in a turn based system such as this :p

Well, in a game where you have 2 million fps, you can't control where you walk... :P

---

### Post by portets on 2010-01-25
> **personjerry said:**
> In theory the game should be able to be played even on relatively low end computers...

i'm actually hoping to get it working on the pandora.

---

### Post by gnuwtey on 2010-01-25
> **portets said:**
> i'm actually hoping to get it working on the Pandora.

That's *low-end*?!? The Nintendo DS runs on less than half that much resources. (I know, the OS takes up a lot of it, but still...)

Perhaps you should make a DS homebrew version of Buntoids, once you're finished the PC version. (But that would piss Nintendo off.)

---

### Post by portets on 2010-01-25
> **gnuwtey said:**
> That's *low-end*?!? The Nintendo DS runs on less than half that much resources. (I know, the OS takes up a lot of it, but still...)

Perhaps you should make a DS homebrew version of Buntoids, once you're finished the PC version. (But that would piss Nintendo off.)

actually one tenth of the resources if i remember corectly(roughly).
ds has a 66 mhz arm. pandora has a 600 mhz arm, plus a graphics core, and alot more ram.

not making ds homebrew because that'd require more development. 
why wold people play our legal homebrew when they can just as easily play illegal companybrew anyway:(? 
and because:

> that would piss Nintendo offhaha, it seriously would.

what do you consider lowend that's not a ds/psp/cellphone?
(although porting to android would be ***great***!)

---

### Post by gnuwtey on 2010-01-26
> **portets said:**
> what do you consider lowend that's not a ds/psp/cellphone?
(although porting to android would be ***great***!)

Well, my old computer, for one. It has 128 MB RAM, a 10-GB hard drive, and a 350MHz Pentium II processor. (And it has Windows 2000.) It can't run VBAdvance at any higher than 20% with zero frame skip, and with frame skip set to 9, it runs at about 70%. But for a native PC program, it should be faster.

---

### Post by portets on 2010-01-26
well it should be fine. i think....
but it worries me that buntoids has 22% cpu usage.

on my 2ghz core2 duo.

and changing the get_ticks to 500 raises cpu usage up to 45%

this is not total cpu usage, this is just buntoid usage

---

### Post by gnuwtey on 2010-01-26
> **portets said:**
> well it should be fine. i think....
but it worries me that buntoids has 22% cpu usage.

on my 2ghz core2 duo.

and changing the get_ticks to 500 raises cpu usage up to 45%

this is not total cpu usage, this is just buntoid usage

Whoa. That is a lot. Perhaps, when you're done developing the thing, you should work on optimizing every single little things you do. But only after you're done the basic engine. I forget it was who said that premature optimization is a sin.

---

### Post by personjerry on 2010-01-26
I get about 33% on my current dev (old) computer, intel celeron 1.8ghz.

EDIT: nvm that was just system monitor, it takes only around 5%

---

### Post by portets on 2010-01-26
a reboot helped. now my larger buntoids is at 16% and the original engine is a 7%. jerry's latest revision at 8%.

maybe my monitoring program is wrong. :confused:

it would seem accurate if all of those numbers were devided by two...

oh, and it says my firefox is at 40% usage

---

### Post by personjerry on 2010-01-27
Development Update 3:

Battle menu now has a new "working" function: Fight. Currently it simply displays moves. I had to use a new font though, public domain, taken from [http://openfontlibrary.org/media/files/rursus/368](http://openfontlibrary.org/media/files/rursus/368) (apparently the font is nsfw... anyone confirm this?). With very few modifications move selection will be finished, and basic numbers can be dealt with. I have a question though, how did the pokemon games deal with long move names? Currently "Mushroom" goes outside the boundary of the screen.

Opinions please :)

-Jerry

---

### Post by portets on 2010-01-27
i'm redoing all of the textures in the game. i'm about 20% complete.

(all except for pokemon images)

it's something i should do, right? i doubt nintendo would *sue *us.

but nintendo *did *contact an open source zelda project that reused all of nintendo's old zelda images.
they just made the project come up with their own images, they never really got in trouble.

---

### Post by portets on 2010-01-27
the only thing i remember nintendo doing is shortening the word "pokemon" to:

p m
  k n

i think they just chose moves that barely fit....


just shorten it to "mshrm toss" for now i guess

edit: early versions had moves in a list.

move
move
move
move


after that, they changed to the way you made your menu. but that was on gba with a wider screen. bigger screen would help. :D

---

### Post by DrWer2 on 2010-01-28
> **personjerry said:**
> 

 I have a question though, how did the pokemon games deal with long move names? Currently "Mushroom" goes outside the boundary of the screen.

Opinions please :)

-Jerry

My opinion is that the user interface should strive to be as efficient as possible(effectively display text, images, HP bar, etc.). This becomes a challenge when using smaller screens. Therefore getting rid of wasted or unnecessary space is a must. The Pokemon games have done a good job at balancing beauty with ease of use in spite of the limited screen size.
I have not seen a recent screenshot of a battle so I don't know if this is an issue.

Scrolling the text could be another alternative albeit a bad one imho. Just throwing it out there. 

Another thing that may help is increasing the resolution by increasing the viewing window. This would give a more zoomed out view of everything. Increasing the resolution this way makes more space available for text without making the images blocky.
This may be taxing/annoying on older computers or devices with small screens, but this would be nice to have for computers with more memory and larger screens. Maybe there could be a different mode or something.


> 

A game similar to Pokemon, but open-source, and heavily moddable. Originally by Robin Stjerndorff.


If Buntoids is just an engine than this should be reworded to remove the possibility of confusion.

---

### Post by portets on 2010-01-28
> **DrWer2 said:**
> Another thing that may help is increasing the resolution by increasing the viewing window. This would give a more zoomed out view of everything. Increasing the resolution this way makes more space available for text without making the images blocky.
This may be taxing/annoying on older computers or devices with small screens, but this would be nice to have for computers with more memory and larger screens. Maybe there could be a different mode or something.

i'm actually working on a version that's 640x480 instead of 166x144 or whatever it is.
right now there are a few problems with it, but they will hopefully get worked out soon.
you can find it here:

[https://docs.google.com/leaf?id=0ByBA2iQHjx06ZDAzOGE4YjAtYzdjNC00NTlhLWFiMWUtNmFjNzUzMzNiNzgw&hl=en](https://docs.google.com/leaf?id=0ByBA2iQHjx06ZDAzOGE4YjAtYzdjNC00NTlhLWFiMWUtNmFjNzUzMzNiNzgw&hl=en)

---

### Post by gnuwtey on 2010-01-28
> **DrWer2 said:**
> My opinion is that the user interface should strive to be as efficient as possible(effectively display text, images, HP bar, etc.). This becomes a challenge when using smaller screens. Therefore getting rid of wasted or unnecessary space is a must. The Pokemon games have done a good job at balancing beauty with ease of use in spite of the limited screen size.

One thing we definitely can do is use a different font. The Sans font is much too wide and bulky for this kind of display. (I think I've said this about 3 times already...)

I can finally work on things now! But I still need to get Linux. (I'll just run it on VMWare, I don't think I want to mess with my laptop, and running MinGW is a pain in the [...].)

It shouldn't be too hard to create an 8-point font for use in the game. (I've actually created numerical fonts, before you say anything. XD Now I need to work on letters.) I'll have to get the charset, though.

(As for the screen resolution, it should probably be 240x180, which is the screen size of the GBA and NDS. The NDS is technically 240x360 if you count both screens, though.)

---

### Post by personjerry on 2010-01-28
For the record the screen resolution is 160x144.
I just went through the most painful debugging (there's still an unexplained phenomenon which is not important) and managed to get the selection display done for move selection. As for font, I'm open to any thing that looks professional and nice, but also fits.
Preferably public domain.

---

### Post by gnuwtey on 2010-01-28
> **personjerry said:**
> As for font, I'm open to any thing that looks professional and nice, but also fits.
Preferably public domain.

Well, actually, it's something that I'm creating myself (released under the same license as the game, XD) that aims to look similar to the font already used in the Pokemon games, only a little nicer. It's a very rough draft at the moment, and I'll upload it here once it's finished.

(and 160x144 is way too small... the aspect ratio should be 4:3. That's probably why the font didn't fit. That, and the fact that Sans is too wide and bulky.)

---

### Post by personjerry on 2010-01-28
gnuwtey, portets:
portets I know you're doing the resizing port but I'd like to say to both of you that resizing the game would take humongous amounts of work. All the numbers for locations are hardcoded in, not based on size, and so I'll have to go through every single number and change it. When we need to do that, I will, but it'll put the gameplay on delay for a while.

---

### Post by portets on 2010-01-28
aww.  :(
so my port should be scrapped, at least until i get better with coding? maybe when i get good, you can continue working while i make a new port.
i thought this engine was a little more scalable than it is though.

and, i guess it's a common beginners mistake to jump in too quickly.
i'll just stick to making graphics for the project and *minor *coding. :D

so what's the phenomena that you encountered when debugging?

---

### Post by gnuwtey on 2010-01-28
> **personjerry said:**
> gnuwtey, portets:
portets I know you're doing the resizing port but I'd like to say to both of you that resizing the game would take humongous amounts of work.
Oh, don't worry about workload. If it's something I know, it's something I can handle.
(But we should make final decisions about game resolution while it's still early into the project. I support 240x180.)

> When we need to do that, I will, but it'll put the gameplay on delay for a while.We should worry about a resize port only *after* gameplay is finished. The font I'm currently making is suitable for a 240x180 display, but it might be workable into 160x144. Might.

[quote=personjerry]I have a question though, how did the pokemon games deal with long move names? Currently "Mushroom" goes outside the boundary of the screen.[/quote]

One thing we definitely can do is use a different font. The Sans font is much too wide and bulky for this kind of display. (I think I've said this about 3 times already...)

I can finally work on things now! But I still need to get Linux. (I'll just run it on VMWare, I don't think I want to mess with my laptop, and running MinGW is a pain in the [...].)

It shouldn't be too hard to create an 8-point font for use in the game. The font is pretty much standard in these types of games, anyway. (I've actually created numerical fonts, before you say anything. XD Now I need to work on letters.) I'll have to get the charset, though.

---

### Post by portets on 2010-01-28
> **gnuwtey said:**
> (But we should make final decisions about game resolution while it's still early into the project. I support 240x180.)

i'm more for 320x240. being that it's a standard resolution. and it's just small enough that it won't need the large amount of work for the changing of 16x16 to 32x32 tiles. i just really don't want that tiny 160x144

and changing the resolution is easy.

---

### Post by gnuwtey on 2010-01-28
> **portets said:**
> And changing the resolution is easy.

I think what personjerry was referring to is the huge amount of work that it would be to reconfigure the positions of each graphic. So where an original graphic was at (12,24), now it would have to be at (23,31).

---

### Post by personjerry on 2010-01-28
portets: don't have to scrap it, I'm just saying it'll be a lot of work.

---

### Post by gnuwtey on 2010-01-28
> **personjerry said:**
> portets: don't have to scrap it, I'm just saying it'll be a lot of work.

Much more work than my prototype font, I bet.

This took me about an hour to make. I made it using the GIMP and the pencil tool. Right now it's simply black-and-white, but in the actual games, there are a few softening effects and shadows. Basically, however, the fonts used in their games are black-and-white just like this one.

The symbols in order are:

[LIST]
[*]the numbers
[*]the pyen symbol (should be represented in code by "$")
[*]degree sign
[*]special X and O (the X is actually a multiplication sign)
[*]various brackets
[*]the capital letters
[*]various punctuation symbols
[*]the lowercase letters
[*]various other punctuation symbols
[*]the male and female symbols
[*]the PK and MN symbols
[*]various accented characters, for international support
[*]various other symbols (the dollar sign should be represented with the yen symbol in code), including three more signatures (the "RS" is for the "Pokerus", which is represented by [PK][RS] in the actual games.
[/LIST]

---

### Post by personjerry on 2010-01-28
Two things:
1. would it be possible to have it as a .ttf file instead? The current systems revolve around truetype and ttf is much more common than bitmap fonts.
2.the PkMn should be BnTd (PkRs could be BnCh for Bunchies :D)

---

### Post by gnuwtey on 2010-01-28
> **personjerry said:**
> Two things:
1. would it be possible to have it as a .ttf file instead? The current systems revolve around truetype and ttf is much more common than bitmap fonts.
2.the PkMn should be BnTd (PkRs could be BnCh for Bunchies :D)

Oh, the file now is just a preview. I'll change it later. I just wanted to know how it looked.

(As for the PkMn thingy, I can do that. But "Bunchies"? Come on, I thought we said "Buntoids" was only going to be the name of the engine!)

BTW, the font is fixed at 9 point. You can't scale it or do anything like that because it's a black-and-white font.

---

### Post by DrWer2 on 2010-01-28
We also need a Pokedex. The name should be based on the final name of the creatures(followed by -dex, -pedia, etc.)

---

### Post by gnuwtey on 2010-01-28
> **DrWer2 said:**
> We also need a Pokedex. The name should be based on the final name of the creatures(followed by -dex, -pedia, etc.)

I really think that we don't really need that big of a base game. Nobody's going to play it for what it is, anyway - eventually, a data file for Pokemon will be made for it, and perhaps some other games, and people will play *those*. Kind of like what happened to Warcraft III - everybody plays DotA on that, not the original game.

Oh, another thing to consider (but not to program for the time being), how are we going to prevent cheating? If that's even something we want to do, of course.

I still support generic terms like "monster" for the name of the creatures as a whole. The word "Pokedex" is short for "Pocket Index". Perhaps we could just use "Catalog"?

(We also need a version numbering system. The current revision, under my personal system, is "predev 5".)

*edit* BTW, I'm looking at the "Poke" class right now. Your "attack per lvl" stat is simply the base stat of a Pokemon divided by 100, am I correct?

---

### Post by portets on 2010-01-28
> **gnuwtey said:**
> I think what personjerry was referring to is the huge amount of work that it would be to reconfigure the positions of each graphic. So where an original graphic was at (12,24), now it would have to be at (23,31).

but i actually did all of the moving of graphics in my port. that wasn't *that *hard.
he's talking about how the collision detection and other elements have to be reworked in order to upscale the engine to 32x32 tile events(i think). and probably a few other things i don't know about yet.

> I really think that we don't really need that big of a base game...a data file for Pokemon will be made for it, and perhaps some other games, and people will play *those.*i completely agree.

---

### Post by gnuwtey on 2010-01-28
> **portets said:**
> he's talking about how the collision detection and other elements have to be reworked in order to upscale the engine to 32x32 tile events(i think). and probably a few other things i don't know about yet.

Shouldn't collision detection work regardless of resolution? Unless the system is dependent on multiples of 16 or 32.

*edit* On second thought, I think I'll settle with MinGW. My main hurdle is trying to learn how to install development libraries for MinGW on Windows... I'm too used to doing that on Linux T_T

*edit2* Hey, there's a Buntoids page on Google when I search for libsdl_image! (Result 15 of about 1,090.)

*edit3* On third thought, I'm going back to using VMWare Linux.

---

### Post by portets on 2010-01-28
> **gnuwtey said:**
> Shouldn't collision detection work regardless of resolution? Unless the system is dependent on multiples of 16 or 32.

it's not the resolution that broke it. you can happily set this game at 1920x1200 without any issues, other than severe insane eyestrain :popcorn:
it seems it's dependent upon it's 16x16 tiles. although, my 32x32 port only created a few problems. fixable problems. it's just that in my version your character moves at half the speed. raising the speed crushes the collision system right now.
you can even take the original engine, speed up the charcter, and collision stops working.

even in jerry's latest revision, you can run into collision issues. (very rare, i seem to be the only one to have found them). so effectively, my port works, but speeding up player walking in any version breaks it.

---

### Post by portets on 2010-01-28
> **gnuwtey said:**
> On second thought, I think I'll settle with MinGW.

that's good, from my knowledge nobody has compiled it on windows yet. hopefully it works:confused:

---

### Post by gnuwtey on 2010-01-28
> **portets said:**
> it's not the resolution that broke it. you can happily set this game at 1920x1200 without any issues, other than severe insane eyestrain :popcorn:
it seems it's dependent upon it's 16x16 tiles. although, my 32x32 port only created a few problems. fixable problems. it's just that in my version your character moves at half the speed. raising the speed crushes the collision system right now.
you can even take the original engine, speed up the charcter, and collision stops working.

even in jerry's latest revision, you can run into collision issues. (very rare, i seem to be the only one to have found them). so effectively, my port works, but speeding up player walking in any version breaks it.

Okay, so it's speeding it up that causes problems... In that case, maybe have the position as an integer-coordinate system, and have fixed animations. Except that wouldn't work because we want to make it Telefang-compatible... damn.

Maybe it's the system itself that's causing problems. Once I've compiled it, I'll try to figure it out.

(Screw VMWare, I'm going to try Wubi instead, first.)

---

### Post by personjerry on 2010-01-28
Yes it would be nice to have a windows executable. I'd also like to cut down on some libraries soon, probably libalut.

I was referring to the actual numbers like the (12,23) example, maybe I was wrong about that (check the menus out and make sure they're centered, if you look into the video cpp file every blit is hardcoded.

My numbers for "pokemon" are arbitrary. They can be anything. basically each has a base stat and a stat per level, the example copies start at level one. To make a computer's pokemon we take a copy and level it accordingly. with player controlled pokemon we'll take into IVs and EVs and stuff and save them so that they're distinct. however all the example copies (and thus wild pokemon) are loaded from an identical example, maybe I'll need to introduce some variation.

Lastly IMO one of the best parts of an engine IS making the story itself, or designing creatures etc., or maybe thats just me.

Oh when I say "pokemon" I mean buntoid, buntoids, etc.

---

### Post by gnuwtey on 2010-01-28
> **personjerry said:**
> Lastly IMO one of the best parts of an engine IS making the story itself, or designing creatures etc., or maybe thats just me.

You're entirely right. But what I'm saying is that we should make it a separate project. And please, no faux cuteness like "Bunchies"... (If you want an example of faux cuteness, go to OMGPOP. It's like a 99% example of what I'm talking about.)

BTW, the base stats in Pokemon work differently than in Telefang (which is the system you have right now). If you'd like to see how they work, go check it up on Bulbapedia. If we were to use Telefang's system, each Pokemon would have every single base stat as 5 (10 for HP), and the growth rates would be the stats listed on a strategy guide divided by 50. (sorry, I said 100 before, it's actually 50.)

---

### Post by portets on 2010-01-28
> **personjerry said:**
> I was referring to the actual numbers like the (12,23) example, maybe I was wrong about that (check the menus out and make sure they're centered, if you look into the video cpp file every blit is hardcoded.

okay. well, i guess i have a lot to learn. i was thinking that the "(12,23)" example that he used meant:

```
    //Text box
    if(text || text2) {
        imglist[500].draw_static(8,96);
        imglist[lines.size()?501:502].draw_static(142,122);

        SDL_Rect pos={15,102,0,0};
        SDL_BlitSurface(text,&text->clip_rect,screen,&pos);
        pos.y=118;
        SDL_BlitSurface(text2,&text2->clip_rect,screen,&pos);
    }
```which i changed to:

```
    //Text box
    if(text || text2) {
        imglist[500].draw_static(170,390);
        imglist[lines.size()?501:502].draw_static(435,450);

        SDL_Rect pos={190,400,0,0};
        SDL_BlitSurface(text,&text->clip_rect,screen,&pos);
        pos.y=430;
        SDL_BlitSurface(text2,&text2->clip_rect,screen,&pos);
    }
```sorry, if i was just confused, again..

 but *is *this what was being talked about? i'm just all mixed up :(

> Lastly IMO one of the best parts of an engine IS making the story itself, or designing creatures etc., or maybe thats just me.
i agree, and i could help come up with the story along with you guys and other people, then we can have a private vote on how the story will unfold. private as to not spoil it for players of the game.
and we have that plan to check out a forum and hold a buntoid design contest that zayfox wanted to do, i think.

---

### Post by gnuwtey on 2010-01-28
> **portets said:**
> well, we i could help come up with the story along with you guys and other people, then we can have a private vote on how the story will unfold. private as to not spoil it for players of the game.
and we have that plan to check out a forum and hold a buntoid design contest that zayfox wanted to do, i think.

We'd need a private website for ourselves in order to have that private vote, which Zayfox has with the buntoids.co.cc stuff.

And portets and I (and all other developers) would need access to that. We'd also have to put our names in the credits. (Real names, please. I don't think acknowledging that you helped develop a game engine is something that interferes with your privacy much. I mean, personjerry and Zayfox have their real names on there.)

---

### Post by portets on 2010-01-29
> **gnuwtey said:**
> We'd need a private website for ourselves in order to have that private vote, which Zayfox has with the buntoids.co.cc stuff.

yeah, but we won't have to worry about that until we start coming up with the plot.

> And portets and I (and all other developers) would need access to that. We'd also have to put our names in the credits. (Real names, please. I don't think acknowledging that you helped develop a game engine is something that interferes with your privacy much. I mean, personjerry and Zayfox have their real names on there.)

i guess so.....
but we don't need to quite yet. i think they should worry about the website when the game comes into a more usable state.

and we don't need to worry about being credited for our work until we make some larger contributions.

---

### Post by gnuwtey on 2010-01-29
> **portets said:**
> i guess so.....
but we don't need to quite yet. i think they should worry about the website when the game comes into a more usable state.

True. But like I said, it would be a private website. It would only turn public once we got to about "version 0.6" (pre-alpha by 2 stages).

> and we don't need to worry about being credited for our work until we make some larger contributions.

Of course. But eventually we will be making those contributions, so it's good to discuss these things a little while we're at it.

(On another note, I've installed Ubuntu because I really don't want to manually install those packages on Windows. The only reason for this is that I can't get them to work *at all* on Windows. I have no idea how to install packages for MinGW.)

---

### Post by personjerry on 2010-01-29
Yes that sample code is what I thought would take time, though I am wrong I guess.

I've had same issues for installing libraries on windows, thats why I couldn't make a port myself via virtualbox

---

### Post by gnuwtey on 2010-01-29
I'm going to go around and familiarize myself with the code now... now that I've compiled a working version of the program. But for some reason, my processor (a Pentium dual-core) is listed as an x86_64. (I dunno, I thought my processor was 32-bit.)

I'll also insert oodles of comments that somebody'll need to verify so that I know exactly what each part of the program does. Is that okay?

(The use of comments in a multi-person project such as this should not be sparing, so that newcomers into the project know exactly what's going on. It doesn't add to the final compiled program's size, as the compiler ignores 'em all anyway. XD)

---

### Post by gnuwtey on 2010-01-29
Oh, something else:

```

std::vector<int> keydown_queue;

void delete_from_queue(int m){ // deletes all instances of a value "m" from the queue
    for(unsigned int a = 0; a < keydown_queue.size(); ++a){
        if(keydown_queue[a] == m)
            keydown_queue.erase(a);
    }
}

```

I'm reworking the movement procedures, and right now, the line that says "keydown_queue.erase(a);" is giving me a compile error, shown below:

```

 error: no matching function for call to ‘std::vector<int, std::allocator<int> >::erase(unsigned int&)’

```

What might the problem be? The function is a valid one, unless I'm missing something.

---

### Post by DrWer2 on 2010-01-29
> **gnuwtey said:**
> I really think that we don't really need that big of a base game... , a data file for Pokemon will be made for it.

Sorry if I was being vague. I was not implying that we create a data file for the different types of Pokemon. I was suggesting that a method for handling and displaying these data files be devised. I just thought I would bring it up in case someone was looking for something else to do that would help the project. 

> **gnuwtey said:**
>  The word "Pokedex" is short for "Pocket Index". Perhaps we could just use "Catalog"?

I like that. :D Good idea.

> **gnuwtey said:**
>  Nobody's going to play it for what it is, anyway - eventually, a data file for Pokemon will be made for it, and perhaps some other games, and people will play *those*. Kind of like what happened to Warcraft III - everybody plays DotA on that, not the original game.

Of course their not going to play if the develpers have an attitude like that. :D 
I agree that few people will play it as it is now, but that doesn't mean we treat this half heartedly and  leave out important features because "other people" will add them. After all, if other developers don't want them they can take those features out or replace them.

I love this stimulating conversation. :popcorn:

---

### Post by portets on 2010-01-29
> **DrWer2 said:**
> Of course their not going to play if the develpers have an attitude like that. :D 
I agree that few people will play it as it is now, but that doesn't mean we treat this half heartedly and  leave out important features because "other people" will add them. After all, if other developers don't want them they can take those features out or replace them.

actually, i think the plan is to make it a fully featured *engine*. then me and others will use the engine to come up with the plot, items, animals, maps, etc.

having so much free time right now will allow me to develop sprites for the game and a story/maps.

---

### Post by gnuwtey on 2010-01-30
> **DrWer2 said:**
> Of course they're not going to play if the develpers have an attitude like that. :D 
I agree that few people will play it as it is now, but that doesn't mean we treat this half heartedly and  leave out important features because "other people" will add them. After all, if other developers don't want them they can take those features out or replace them.

I'm not saying that we shouldn't create a full base game at all, I'm just saying that if we are going to create one, we should at least make an effort to determine what appeals to people, and we should make it separate from the engine.

We're not creating this game for ourselves only, we're creating it for others. For example, if you put a Tux symbol on the slot machines by default, people will be all "WTF is a penguin doing on the slots".

What I'm saying is that right now we're trying to put too many references to Linux/GNU/etc. branding and "nerdy computer lingo" into the game, and it's not something that everybody appreciates. ("BOFH's box"? "Ubuntumon"?) Any serious open-source game you see out there, like Stepmania or Neverball, have absolutely zero reference to these things within the game itself, except where technically required. (For example, we're not going to make "SuSEon" an evolution of Kecleon. It's just not happening. :D)

If we do eventually put these references into a default game, it would be a "placeholder" game, kind of a proof of concept, not a serious game. What I suggest doing with the final release is, have the engine come with a placeholder game (the "small base game" I was talking about), and have a separate download for the actual game files, including the official Buntoids game.

[quote=portets]actually, i think the plan is to make it a fully featured *engine*.[/quote]

But in order to make the engine, we need the data files... XD They're not separately developed, you know.


Also, a licensing issue. We probably can't license the game under the GPL for too long once we're finished with it. Stepmania eventually licensed their game under the MIT License because Roxor Games wanted to create In The Groove. (Sure, they later got sued for it, but it's the same thing here.)

We shouldn't force people to put their game data files under the GPL, is what I'm saying.

---

### Post by personjerry on 2010-01-30
gnuwtey: I'm not sure what your keyqueue tries to do, as keys can be simultaneously pressed in theory. Meanwhile, the erase function for vectors are based on iterators, check cplusplus.com for reference.

As for licensing, I'm sure GPL won't be a problem, just look at wesnoth: plenty of user created content, still GPL.
And so in order to test the game, and have some fun while developing, the base game will be made along with the game.

EDIT: The original base/test scenario does not have to be very long at all, just comprehensive for engine functions, and be the group effort. Afterwards who knows, we could raise a contest to make the best scenario to be included with the engine or we can each make one.

---

### Post by portets on 2010-01-30
> **personjerry said:**
> As for licensing, I'm sure GPL won't be a problem, just look at wesnoth: plenty of user created content, still GPL.

i agree, GPL should be just fine. and we'd have to talk to Robin Stjerndorff to see if he was okay with relicensing. i don't think it's worth it.

> And so in order to test the game, and have some fun while developing, the base game will be made along with the game.

EDIT: The original base/test scenario does not have to be very long at all, just comprehensive for engine functions, and be the group effort. Afterwards who knows, we could raise a contest to make the best scenario to be included with the engine or we can each make one.

that sounds good. so, i think we should start developing the basic testing storyline when the battle system is complete and you can hold real buntoids in your party that remember stats. so that means; you can walk in the grass and be pulled into battle, moves work, you can flee, you can catch it(not sure if that's necessary for beginning the story), healing centers should work.
but items don't need to work, other trainers don't need to work, etc.

sound good jerry? that's about the point of development that we should find a forum for people to submit their best creatures. while we wait for people to submit, we can work on the basic story.

i can start developing maps and sprites until we reach that development milestone.
should we call it milestone one?

---

### Post by personjerry on 2010-01-30
Ah we probably won't reach all those goals for a while, here's my organization of it: I'll add this to a TODO in the git repo later.
Milestone 1:
1. Moves deal damage.
2. Moves are animated (optional)
3. Moves have effects.

4.  Buntoids remember stats
5. Levelling works
6. Variants in wild and trainer buntoids

7. Snap character to grid (also solves zoom bug)
8. Encounters in tall grass.
9. Animate when possible (grass, bntds, etc)

Fleeing and healing should be relatively trivial.

---

### Post by portets on 2010-01-30
> **personjerry said:**
> 7. Snap character to grid (also solves zoom bug)

i was actually going to ask you if you would be okay with it that way.
and solves zoom bug, as in it might fix collision? that makes sense.

or at least makes it easier to double speed the character without actually fixing collision issues, or making them worse?

oh, i messed with the code of changing to "pos_x+=2". if you change 2 to 3 it prevents some collision problems. x and y negative axis' don't get stuck, but positive does. anything above that turns back to getting you stuck anywhere again. but 9 also is a little different. just thought that was weird behavior and you might want to know....

---

### Post by gnuwtey on 2010-01-30
> **personjerry said:**
> gnuwtey: I'm not sure what your keyqueue tries to do, as keys can be simultaneously pressed in theory. Meanwhile, the erase function for vectors are based on iterators, check cplusplus.com for reference.

But your code right now will stop the player as soon as a key is released. The KEY_DOWN function you have right now only activates when a key is pressed, not as it's held down. What my code is trying to ensure is that as long as a key is being held down, the player will move.

> As for licensing, I'm sure GPL won't be a problem, just look at wesnoth: plenty of user created content, still GPL.Oh, I was concerned that the user-created *content *would also have to be licensed under the GPL. (It shouldn't have to be, is what I'm saying.)

> And so in order to test the game, and have some fun while developing, the base game will be made along with the game.

EDIT: The original base/test scenario does not have to be very long at all, just comprehensive for engine functions, and be the group effort. Afterwards who knows, we could raise a contest to make the best scenario to be included with the engine or we can each make one.Great idea... I think that's what I meant to say in the first place.

---

### Post by personjerry on 2010-01-30
> **gnuwtey said:**
> But your code right now will stop the player as soon as a key is released. The KEY_DOWN function you have right now only activates when a key is pressed, not as it's held down. What my code is trying to ensure is that as long as a key is being held down, the player will move.

Actually SDL Key events include Key Down and Key Up, and both are tested for, so that when key down occurs for a key the function is turned "on" and when the key is released another event occurs which stops the function.

---

### Post by gnuwtey on 2010-01-30
> **personjerry said:**
> Actually SDL Key events include Key Down and Key Up, and both are tested for, so that when key down occurs for a key the function is turned "on" and when the key is released another event occurs which stops the function.

Yes, but when your key is released in the current code, it doesn't check whether any other keys are being held down, and thus the player stops.

For example, in the current game, if I press and hold W, and then press D, the character moves to the right as required. But when I release D while still holding W, the character stops instead of moving down again. What my key queue does is that it moves the character down in this scenario.

And how exactly do iterators work, then...?

---

### Post by portets on 2010-01-31
> **gnuwtey said:**
> For example, in the current game, if I press and hold W, and then press D, the character moves to the right as required. But when I release D while still holding W, the character stops instead of moving down again. What my key queue does is that it moves the character down in this scenario.

oh, i get what you're saying now. i don't like how the key situation is right now either.

it would be really important for later on when we allow the riding of a bicycle.(i might add that if nobody else does)

---

### Post by personjerry on 2010-01-31
Iterators are special STL objects for container templates that don't count as pointers or objects, but can be incremented to "point" to the next object in the container anyway.

I could make a quick fix for that key thing though, which is just, on key ups to test if other keys are still down.

---

### Post by gnuwtey on 2010-01-31
> **personjerry said:**
> Iterators are special STL objects for container templates that don't count as pointers or objects, but can be incremented to "point" to the next object in the container anyway.

I could make a quick fix for that key thing though, which is just, on key ups to test if other keys are still down.

I still think the key queue is more efficient, it's just that problem with the iterators. I could just use a regular array instead.

---

### Post by gnuwtey on 2010-01-31
> **personjerry said:**
> 1. Moves deal damage.
2. Moves are animated (optional)
3. Moves have effects.

The optional milestones generally go last... o_O

And I'm having a really hard time with FontForge right now... is there a bitmap font creator that anyone here could recommend? (Can't use Pixel Font Creator, the maximum bounding-box size is too small [10x10]. I need it to be at least 12x7.)

---

### Post by gnuwtey on 2010-02-01
Oh boy, a spambot. (And a keyqueue would work better because it keeps track of which key was the *last* one [or the one most *recently*] pressed, instead of just all the ones that *were* pressed. Just saying.)

---

### Post by Perfect Storm on 2010-02-01
Spambot nuked with a 500tons.

---

### Post by personjerry on 2010-02-01
There was a spambot here? Aw what a shame, I wish I had witnessed it.\
Anyway I've made moving smooth in the latest revision.

EDIT: I think the efficiency is fine, as a queue would take unneccesary storage mechanisms, whereas we don't need such detailed control over the keys and their roles. We can still try them and compare though, and see what works for us.

---

### Post by portets on 2010-02-01
> **personjerry said:**
> Anyway I've made moving smooth in the latest revision.

nice! even smoother than that other rpg.
now we can hold down as many keys as our keyboards can handle. not just two

---

### Post by personjerry on 2010-02-02
I added a new map to the west of the city which can demonstrate some map engine bugs, showing that even that will need to be reworked sometime in the future.

---

### Post by gnuwtey on 2010-02-02
[quote=personjerry]EDIT: I think the efficiency is fine, as a queue would take unneccesary storage mechanisms, whereas we don't need such detailed control over the keys and their roles. We can still try them and compare though, and see what works for us.[/quote]

We could just use a simple array, then... I still think it's important to keep track of which key was pressed last. If not for extremely detailed control, just to have some sense of order in which the keys are checked.

By the way, besides new Pokemon, we also need some new moves for them. I took the liberty of making a list of 17 moves, one of each type:

(Normal) Mega Slam
 Description: Slams into the foe hard. May paralyze. High critical-hit ratio.
 Power: 120    Accuracy: 90%    PP: 10
 Effect: Has a 50% probability of paralyzing the target, and a 12.5% critical-hit ratio.

 (Fire) Blaze Punch
 Description: A blazing punch that may cause a burn. Very high critical-hit ratio.
 Power: 120    Accuracy: 95%    PP: 5
 Effect: Has a 40% probability of burning the target, and a 25% critical-hit ratio.

 (Water) Tsunami
 Description: Creates a giant wave, twice as high as the move Surf.
 Power: 120    Accuracy: 125%    PP: 5
 Effect: None
 Notes: This move cannot be used as a substitute for HM03 Surf outside of battle. It has the exact same Power and PP as Hydro Pump, but is more accurate. An accuracy of 125% means that the move only has a chance to miss if the Pokémon's accuracy decreases by at least one stage.

 (Grass) Massive Growth [Mass Growth]
 Description: Raises Attack, Defense, Sp.Atk, and Sp.Def by two stages each, over two turns.
 Power: n/a    Accuracy: n/a        PP: 5
 Effect: Raises Attack, Defense, Sp.Atk, and Sp.Def by one stage each, for two turns. The user cannot attack or use items while this happens.
 
(Flying) Hurricane
 Description: An extremely powerful wind that will blow the enemy away without fail.
 Power: 120    Accuracy: ---        PP: 5
 Effect: This attack never misses. However, the user must rest to recover from energy loss the next turn.
 Notes: The move has the exact same description and effect as Hyper Beam, except it is Flying-type, is less powerful, and never misses.

(Electric) Tesla Bolt  
 Description: A million-volt jolt of electricity, it shocks even the user.
 Power: 160    Accuracy: 80%    PP: 10
 Effect: This attack has a 30% chance of paralyzing the target. It also does recoil damage, calculated at a power of 80.

 (Poison) Botulinum
 Description: An extremely powerful poison that quickly rots from the inside out.
 Power: 40    Accuracy: 85%    PP: 10
 Effect: The target is "very badly poisoned" &#8211; the first turn gone with Poison gets rid of 1/8 of the target's HP, the next turn 2/8, etc

 (Bug) Bug Bite
 Description: Bites the foe on a small area on its skin, causing it to thrash around trying to scratch it.
 Power: 20    Accuracy: 90%    PP: 10
 Effect: The target has a 75% probability of hurting itself (at 80 power) trying to scratch the bump on its skin. Lasts 2 to 5 turns. (The text would read, "[Foe] is itchy! / It hurt itself trying to scratch!")

 (Ground) Armageddon
 Description: Creates an earthquake so intense that the ground shakes 30 cm up and down.
 Power: 150    Accuracy: 100%        PP: 5
 Effect: None.

 (Psychic) Morbid Vision [MorbidVision]
 Description: Shows the target a morbid vision of the future, causing it to freeze in fear, and lower its defenses.
 Power: n/a    Accuracy: n/a        PP: 10
 Effect: Lowers the target's Attack, Defense, and Speed stats by two stages each.
 Notes: This attack has a very high (but dynamically calculated) probability of failing in an even match. The probability is calculated using the current stats of the user, using the following formula:
 P = Pa * Pd * Ps
 Pa = cubrt( sin( (CLAMP[stage(Af / Au), -2, 4] + 2) / 12 * pi ) )
 Pd = cubrt( sin( (CLAMP[stage(Df / Du), -2, 4] + 2) / 12 * pi ) )
 Ps = cubrt( sin( (CLAMP[stage(Sf / Su), -2, 4] + 2) / 12 * pi ) )
 
 Where cubrt() is the cube root function, sin() is the trigonometric sine function, pi refers to 3.1415926..., and CLAMP[a,b,c] returns a if b < a < c, b if a <= b, and c if c <= a. (Basically, it "clamps" the value of a between b and c.) Ap refers to the Attack stat of Pokémon p, where f is the foe, and u us the user. Similarly, D refers to Defense, and S refers to speed.
 
Stage() is the "stage" function, which determines the approximate relative stage of the foe's stat compared to the user's. It is calculated as follows:
 
 If n = 1, stage(n) = 0.
 If n < 1, stage(n) = (2 / n) * -1) + 2.
 If n > 1, stage(n) = (2 * n) &#8211; 2.
 
 This works the same way as actual stages when considering Pokémon stats. For example, if my Giratina with speed 160 is battling an Arceus with speed 290 (which should never happen, but hypothetically), then the Arceus' relative stage is stage(290/160) = 1.625, so I can say that the Arceus' Speed is 1.625 stages above my Giratina's, and similarly, my Giratina's speed is 1.625 stages below the Arceus' &#8211; if I calculate stage(160/290) instead, the result is -1.625.
 
 For an example of the probability calculation, if I have a Gardevoir with Speed 40, Attack 59, and Defense 37 that uses Morbid Vision on a Swellow with Speed 190, Attack 95, and Defense 97, the probability of success is calculated as follows:  
 Pa = cubrt( sin( (CLAMP[stage(95 / 59), -2, 4] + 2) / 12 * pi ) )
 = cubrt( sin( (1.22033... + 2) / 12 * pi ) )
 = cubrt( 0.74669... )
 = 0.90722...
 Similarly, Pd and Ps are 0.993436... and 1.00000 respectively.
 Multiply the three together, and the probability that Morbid Vision will succeed is about 90.1%. The probability will be much lower the second time, though.

 (Dark) Zero Lumen
 Description: Shrouds the user in complete darkness for five turns, making it impossible to see where it is.
 Power: n/a    Accuracy: n/a        PP: 5
 Effects: Makes Psychic attacks completely ineffective, and all other attacks that are not Dark have only 25% normal accuracy. Dark attacks done by the user are powered up to 150%. (The effects of Miracle Eye are negated under Zero Lumen, and any evasiveness-reducing attacks will fail under Zero Lumen.)
 
 (Ghost) Mortal Curse
 Description: Cuts the user's HP in half to KO the other player in 2 turns.
 Power: n/a    Accuracy: n/a        PP: 10
 Effects: Cuts the user's HP in half (but not of maximum HP. So if my Banette that knows Mortal Curse used it with an HP of 49/67, it would turn to 24/67, not 16/67 like it would with Curse). During the two turns it takes for the attack to charge, no items can be used.

(Fighting) Rising Punch
 Description: A powerful punch that takes power from dragons. Has a very high critical-hit ratio, but misses often.
 Power: 160    Accuracy: 80%    PP: 10
 Effects: Has a 25% chance of landing a critical hit, in which case it is practically a one-hit KO anyway if used on a Normal, Ground, or Steel type (in which case the effective power is 640. Go figure).

(Steel) Diamond Cutter [Diamond Cut]
 Description: Cuts the enemy with an extra-hard blade that can cut through diamonds like butter. Has a very high critical hit ratio.
 Power: 120    Accuracy: 100%    PP: 10
 Effects: Has a 25% critical hit ratio.

(Rock) Asteroid Smash [Rock Impact]
 Description: Smashes an asteroid into the foe, from outer space.
 Power: 240    Accuracy: 50%    PP: 10
 Effects: None.

 (Ice) Absolute Zero [AbsoluteZero]
 Description: Brings the temperature of the battlefield down to negative 273 degrees, and gradually warms up over five turns.
 Power: n/a    Accuracy: n/a        PP: 5
 Effects: Lowers the Speed of the foe by seven stages (including the stages below the -6 stage), and has a 50% chance of freezing it. Each turn that Absolute Zero lasts (a total of five), the Speed of the foe will increase by one stage as the field warms up again. Also, each turn that Absolute Zero lasts, the extreme cold will damage the opponent with an Ice-type attack starting at 100 power and gradually fading to 0.
 Notes: This card has a weather effect. The text appearing would be "The field is very cold. / The coldness hurt [foe]!"

 (Dragon) Summoning
 Description: Summons four Dragons, each with one type of elemental attack.
 Power: n/a    Accuracy: n/a        PP: 5
 Effects: Four dragons will now circle the dragon that used the attack. The current move list of the dragon is replaced with the four P-class moves of Electric, Fire, Water, and Grass, each with 5 PP. As well, each dragon acts as a Substitute for the user, with a quarter of the user's current HP going to each dragon. Once all the PP of all the moves are depleted, the dragons disappear and the normal move list returns. Any attacks that the opponent uses are directed towards these four dragons, and if any of these dragons are knocked out, they do not come back until the attack is used again.
 
These moves fit into what I call a "P-class" move type. They are of a standard level of power, but at a very *powerful* standard level. As well, each move type has exactly one P-class move.

Each move has a class assigned to it, BTW. We'll have to determine which class during the course of making the game.


 What do you think?

Some other notes: -273 degrees would be changed to -459 degrees for the US release. (Just like 200 degrees was changed to 392 degrees for the US release of Pokemon Ruby/Sapphire/Emerald when you go into Flannery's Gym and one of the trainers asks you if you can withstand heat of that degree. I don't see why they had to convert it exactly to 392, but anyway.)

---

### Post by personjerry on 2010-02-02
I have to question both the balance (tsunami, summoning, etc.) and gameplay value (dark lumen, morbid vision, etc.) of some of those skills, but many are just fine.

In addition I'm not sure how some of these could be coded, or be scripted for an engine, so that may take some time.

Finally the battle system is not done yet, so all we can do for now is add some more data fields to support the description I guess.

---

### Post by gnuwtey on 2010-02-02
> **personjerry said:**
> I have to question both the balance (tsunami, summoning, etc.) and gameplay value (zero lumen, morbid vision, etc.) of some of those skills, but many are just fine.

To the balance part: I tried to normalize these moves so that they have approximately the same net effect if used properly. For example, although Tsunami has an accuracy of 125%, it has no other effect, while every other move except for Asteroid Smash and Armageddon has a secondary effect or is primarily an effect modifier. And while Asteroid Smash only has an accuracy of 50%, its power is 240, so when it does hit, it hits hard.

As for Summoning, once you have the four dragons on there, you can't use any items on them. However, they are resistant to many attacks, working together to defend against them. For example, let's say my level 74 Dragonite with HP 279/279, while fighting against a level 81 Pikachu with HP 179/179, uses Summoning, creating four other dragons each with HP 70/70. If Pikachu then decides to use a Thunderbolt, the Electric dragon will jump in and defend against it, taking 29 damage. My Dragonite then calls upon the Fire dragon to use Blaze Punch, doing 74 damage to the Pikachu. Let's say Pikachu uses Thunder this time. This time, the Electric dragon jumps in again, but this time it does 41 damage, knocking the dragon out.

Another thing - once one of the dragons is knocked out, you can't use its move anymore. And Summoning uses up all the user's HP (1/4 each for 4 Substitutes), so once all the dragons are knocked out, the user also gets knocked out. Not to mention that none of the moves get STAB because none of the Dragon-types that can *learn* Summoning are any of those four types... (Neither Dialga nor Palkia can learn Summoning. Don't ask. ^_^)

To the gameplay value part: For the most part, I don't think any of these moves really take away from the value. (Some moves already in the game don't add much to it either, but are there for the sake of completion.) The purpose of Morbid Vision is to equalize the game a little when fighting against an extremely powerful Pokemon, hence the very complicated formula for probability calculation. It will fail (and fail hard) if the opposing Pokemon isn't very strong.

As to Zero Lumen, the point of it is to power up the not-very-powerful Dark-type moves. Currently, the maximum power of a Dark-type move is 80, and most of these moves don't have any special effects that the other types don't already have.

As to coding, I'll take on the responsibility of putting these specific moves in if the need arises. (And of course when the battle system is completed. I didn't say otherwise. ^_^)

> **portets said:**
> nice! even smoother than that other rpg.

What other RPG?

*edit* I found a bug in the map engine... XD

When you enter Pallet Town from Route 1, that guy who sells stuff in Viridian City disappears and reappears in his original position before the map is completely invisible.

*edit2* Another thing I'd like to point out, with our discussion about moves above, I've realized that the data files also need to be able to support some form of scripting language, in case people want moves to have certain effects, or they want to plug-in a new feature entirely. (Of course, that comes much later, but I mean, it's good to keep in mind, right?)

*edit3* Another subject I'd like to just touch on: EVs.

I don't really like the current EV formula because it allows too much of a Pokemon's stat to depend on simple randomness (that is, IV's. Depending on how you distribute the EVs, an IV can count for as much as 3/5 of a Pokemon's stat difference, which, IMO, is too much). This isn't because of the fact that any individual stat can only go up to 255 (in which case, only 1/3 of the stat difference depends on IV's), it's that the total limit is 510.

What I'd suggest, is to allow Pokemon with lower IVs to grow more in total. So each Pokemon caught will have the same average potential, but the ones with lower IVs will just take longer to get there, and the ones with lower IV's will never grow a lot in one certain stat.

The formula I'd suggest is:

Tot_limit = 1254 - (Total IV's * 4)

Where Total IV's is the sum of all six IV stats, that can go from 0 to 31. (The formula is set so that a Pokemon with all IVs at 31 will have a limit of 510.) If we're going to use the old EV formula, in which the limit for one stat is 65535 and the total limit is 131070 (and the maximum IV stat is 15), the formula changes to this:

Tot_limit = 315390 - (Total IV's * 2048)

And if we're allowing IV's to go to 31 but still keeping the 65535 limit:

Tot_limit = 321534 - (Total IV's * 1024)

*edit4* I think we should have support for both systems built in. How it works in Generation I and Generation II:

When a Pokemon A defeats a Pokemon B, Pokemon B's base stats get added to Pokemon A's EV totals, point for point.

(In the following example, the EV's are arranged as HP, Attack, Defense, Sp.Atk, Sp.Def, Speed).

So let's say that I have a Level 13 Arcanine with EV's at (1836, 2049, 1997, 1243, 2098, 2160) that defeats a Pikachu (regardless of what it is, all Pikachu will yield the same EV's), its EV's increase by (35, 55, 30, 50, 40, 90), giving Arcanine a new EV value of (1871, 2114, 2027, 1293, 2138, 2250).

For each 1024 EV's a Pokemon gains, its stats will increase by one point. No stat can have more than 65535 EV's, but there is no total limit.

*edit^2* Actually, in Generation I, the difference in stats is given by dividing the current EV value by 16, adding 1, and *square-rooting* it. But anyway.

In Generation III and Generation IV:

When a Pokemon A defeats a Pokemon B, Pokemon B adds a certain "EV yield" to Pokemon A's EV's.

So let's say that my level 13 Arcanine, with Gen.3 EV's at (10, 8, 4, 5, 3, 7) defeats the same Pikachu. Its EV's increase by (0, 0, 0, 0, 0, 2) [Speed raised by 2], giving my Arcanine a new EV stat of (10, 8, 4, 5, 3, **9**). Only one value ever changed.

For each 4 EV's a Pokemon gains, its stats will increase by one point. No stat can have more than 255 EV's, and there is a total limit of 510.

How the hybrid system might work:

Each Pokemon can still gain EV's both ways, depending on the program. But in a Gen.3 remake game, instead of defeating a Pikachu yielding 2 EV's in Speed, it yields 512, since all Gen.3 (and Gen.4, as a result) EV's are multiplied by 256. (For each 1024 EV's instead of 4, so a factor of 256.)

*edit5* But, of course, all this talk and calculation is useless until the battle engine is finished. Carry on. ^_^

---

### Post by gnuwtey on 2010-02-12
*bump* Where is everybody...? Status report, please?

---

### Post by gnuwtey on 2010-02-13
> **goodgod said:**
> I agree. Some times Pokemon battles start to get repetitive. If we could  somehow improve the game to use a little more skill.

Could you please tell us what you agree *with*? You don't reference another post, so I'm confused as to what you're talking about.

---

### Post by Perfect Storm on 2010-02-13
> **gnuwtey said:**
> Could you please tell us what you agree *with*? You don't reference another post, so I'm confused as to what you're talking about.

It was just another spambot, which I've throwed back to the pit.

---

### Post by gnuwtey on 2010-02-13
> **Artificial Intelligence said:**
> It was just another spambot, which I've thrown back to the pit.

Oh. Sorry then.

---

### Post by Perfect Storm on 2010-02-13
> **gnuwtey said:**
> Oh. Sorry then.

No problem, usually you can tell it's a spambot on its spam signature and somehow out of place responds. Though the spambots sometimes now copy/paste related text to avoid getting detected. (To no avail, I've been hunting spambots now for years).

---

### Post by personjerry on 2010-02-15
Oh boy, I have returned and will continue development now... sorry about that delay.

I need an image which has enough room for status text, as well as an empty rectangular shaped space where the health bar will go.

---

### Post by gnuwtey on 2010-02-16
> **personjerry said:**
> Oh boy, I have returned and will continue development now... sorry about that delay.

I need an image which has enough room for status text, as well as an empty rectangular shaped space where the health bar will go.

I was wondering where you had gone... XD

I'll submit a design for the health bar space, I have something you might want to consider.

And make the screen 240 x 180, please. It just gives you more space to do things.

*edit* I realized that my font looks kind of ugly, I'm going to revise it... as well, I'm going to make the numbers equally spaced - right now, the 1 is too thin.

As well, I really don't think we need the status text. The current abbreviations in the actual Pokemon games suit the purpose quite nicely.

*edit2* The Design!

It's nothing new, really, just that the singular bar on the bottom now has two uses, and the status window has up to three different displays - one for HP, one for Total EXP, and one for EXP until the next level. The second one will be the least used.

As well, it's in black and white now because it's only a prototype, like everything else. As well, it will only work on a 240 x 180 screen. Any more or less and the proportions are hard on the eyes.

Oh, another thing about the image below, the reason there are three are just to show the different modes. Only one of those images will ever be displayed at a time on the window. When the Pokemon (or Buntoid, as the case may be) gains experience points, the *third* bar is the one displayed, because this is the one that gives the most appealing number when a Pokemon levels up - at level-up, the number will be zero, instead of a strange number like 121570.

(The example below is of a Ho-oh named Peroxide.)

---

### Post by DrWer2 on 2010-02-16
Separating both bars is ok but I always liked the way pokemon games have handled it. If it takes up too much space maybe the Hp bar could be back-lit(glow) to show the number of exp till the next level.
Why would you need a bar to represent total exp? Is there an end value to be met? I think it would be more annoying than useful.

---

### Post by gnuwtey on 2010-02-16
> **DrWer2 said:**
> Why would you need a bar to represent total exp? Is there an end value to be met? I think it would be more annoying than useful.

No, the bar representing total exp is identical to the bar representing remaining exp, it's just that the numbers are different. (At all times, the bar at the bottom is the percentage of exp gained towards the next level.)

The second bar is, like I said, primarily useless, but in there anyway just in case.

---

### Post by DrWer2 on 2010-02-17
> **gnuwtey said:**
> No, the bar representing total exp is identical to the bar representing remaining exp, it's just that the numbers are different. (At all times, the bar at the bottom is the percentage of exp gained towards the next level.)

The second bar is, like I said, primarily useless, but in there anyway just in case.

Please explain how the bars would be the same but use different numbers. 
I still don't see how you can show total exp in a graph.

---

### Post by gnuwtey on 2010-02-17
> **DrWer2 said:**
> Please explain how the bars would be the same but use different numbers. 
I still don't see how you can show total exp in a graph.

In the second display mode, the bar on the bottom does not represent the number on top, but rather, it represents what it always represented in the past - the total experience points earned for *this specific level*. The reason it's at 45% now is because for this level, my Ho-oh has earned 3526/7764 experience points for Level 45.

In the third display mode, the bar on the bottom doesn't represent the number on top either - the number on top represents the number of experience points required to get to the *next* level (represented as a negative number), not the number of experience points earned in *this* level. (My Ho-oh has already earned 3536/7764 exp. towards the next level, so it needs 4238 more.)

I think you're confused as to what I mean in those graphs. Only one of the three bars in that picture will ever be displayed at once.

Such as in the following attachments:

1. The statbar as it appears in battle.
2. The statbar as it appears after the enemy faints.
Here, when the level goes up, the "NEXT LV." at the left changes to "EXP" to display the total gained EXP as soon as the number changes from 9 to 10.
3. The statbar as it is when the level goes up, before the stat changes are reviewed.
4. The statbar as it is after the level goes up.

(Sprites are from Bulbapedia. You think I can make those myself?)

P.S. Oh yes, and defeating a Level 9 Bulbasaur actually *will* give the Charmander 82 Experience points. All the stats are accurate. ^_^

---

### Post by personjerry on 2010-02-17
Well I didn't make the window as requested, but I made the important one taller to fit more information :D

---

### Post by gnuwtey on 2010-02-17
> **personjerry said:**
> Well I didn't make the window as requested, but I made the important one taller to fit more information :D

That window is getting seriously crowded. I'm serious, expanding the screen to 240 x 180 would be the best thing to do at this point. (I believe you also said that renumbering everything would be the hardest part of that job. I can help with that too, I'm not too busy right now.)

Also, you need space to put text. With the info bar the way it is now, you barely have room for anything else. Look at the images I made on my previous post, please? ^_^

---

### Post by personjerry on 2010-02-17
I think portets showed that the numbers aren't too difficult, the two problems now are the immense slowdown we seem to get from scaling up as well as the problem of getting stuck.

---

### Post by gnuwtey on 2010-02-17
> **personjerry said:**
> I think portets showed that the numbers aren't too difficult, the two problems now are the immense slowdown we seem to get from scaling up as well as the problem of getting stuck.

Alright, but keeping it at 160 x 144 is going to make the battle screen look horrible. Better to revise the collision engine to work at all resolutions than to just have it fixed there.

I think portets' build was 640 x 480, which *is* extremely slow, but a window 1/8 that size shouldn't be *too* bad, should it?

As well, I'll hunt around for problems with the code. Is it revised yet? And how does one get stuck, exactly?

*edit* As well, I'm having no luck with FontForge, could somebody suggest another font maker I could use?

Another thing, I have my own build that uses the Z key as a "speed-up" key - basically, it sets the 1000 in the frame rate to 1, to speed up walking and other slow things like that. Could I commit that change?


*edit2* Hmm. Changing the resolution to 240 x 180 doesn't seem to really do much. I meant increase just the screen size, not the resolution of the textures. (That's what Nintendo did in Generation III. The characters' sprites are still 16 x 16, but the screen is larger, allowing for more tiles per row and column instead of just 10 x 9.) It gives you more room. Where do you experience the bugs by upping the screen size?

As well, you should use #defines to define the keys for now, in case somebody wants to change them. I know I'm personally not comfortable with the current configuration, which is why I started using #defines in my own little "branch".

Basically, do this:

```

#define _upkey SDLK_UP
#define _downkey SDLK_DOWN
#define _leftkey SDLK_LEFT
#define _rightkey SDLK_RIGHT
#define _Akey SDLK_SPACE
#define _Bkey SDLK_x
#define _startkey SDLK_n

```And then replace the existing keys with _upkey, etc.

---

### Post by portets on 2010-02-17
> **gnuwtey said:**
> ...I think portets' build was 640 x 480, which *is* extremely slow, but a window 1/8 that size shouldn't be *too* bad, should it?...
...And how does one get stuck, exactly?

yes, it was 640x480. and my build wasn't slow, it's just that the player needed to move twice as fast due to me doubling the size of the game.
our problem now is that when we make the player move *any *faster than it already does, it gets stuck. getting stuck happens when the player collides with anything. like if you walk into a building you get glued to it. you can rotate in place but can't walk anywhere.

this also happens in buntoids right now, unmodified. it's just very rare.

about changing the resolution; it isn't difficult, you just change four numbers in the code. two in shared.cpp, and two in video_sdl.cpp.

but along with that, all of the menu positions need to be changed, it takes a bit of work to get them all in correct places so i recommend that we either fix the sticky bug and go to something big like 640x480 or we remain permanently at anything under 320x240 without fixing the bug. if we go with the latter, the bug will need to get fixed before a stable release anyway.

so what do you think jerry? keep the game at 16x16 tiles and fix the bug later, or 32x32 tiles and fix the bug now?

but of course i'm fine with keeping the resolution at 160x144 for now, until we get features then decide about resolutions later.

i just personally think it's best to decide the resolution and tile size now. that way we don't have to change every single menu in the game after they are developed and set in place.

edit: i'm also more than willing to change the resolution and all of the menu positions when those things are figured out

---

### Post by gnuwtey on 2010-02-17
> **portets said:**
> but along with that, all of the menu positions need to be changed, it takes a bit of work to get them all in correct places so i recommend that we either fix the sticky bug and go to something big like 640x480 or we remain permanently at anything under 320x240 without fixing the bug. if we go with the latter, the bug will need to get fixed before a stable release anyway.

so what do you think jerry? keep the game at 16x16 tiles and fix the bug later, or 32x32 tiles and fix the bug now?

I'm not Jerry, but I'd prefer we keep it at 16x16 tiles and fix the bug later. But the resolution should definitely be at least 240 x 180.

The *official*, official release should be the small one.

If we are going to make a larger version, we should make it once we have the small version down pat. Because if people want, they can simply scale the 16x16 textures, already rendered, up by a factor of 2 or 3. That's what most emulators do to give bigger windows. (Not that we're an emulator, but I'm just giving an example.)

As well, about the moving thing, the actual Pokemon games used a tile-based moving system. So once you press Left, you'll always move exactly one step to the left.

---

### Post by DrWer2 on 2010-02-18
I agree with portets. The bug should be fixed as soon as possible. Letting it be Buried under new code could cause more problems.
Ultimately, it is not my decision since I will not be debugging it.

P.S. I'm not Jerry either :-$.

---

### Post by gnuwtey on 2010-02-18
> **DrWer2 said:**
> I agree with portets. The bug should be fixed as soon as possible. Letting it be Buried under new code could cause more problems.
Ultimately, it is not my decision since I will not be debugging it.

P.S. I'm not Jerry either :-$.

Sorry, when I said "later", I didn't mean "much later". I'd actually rather we fix it now, but if it's not an option, then later is fine.

---

### Post by personjerry on 2010-02-18
sorry I'm quite a bit busy, so responses and dev will be infrequent, but here's my plan of action:
1. finish base battle system (near completion... there'll be problems I'm aware of already which need to be worked out later)
2. snap player to squares (this will take a while as some of the map loading code is linked with player location) 
3. Resize to 640x480 (IMO 32x32 sprited give a lot more artisitic freedom)

---

### Post by gnuwtey on 2010-02-18
> **personjerry said:**
> sorry I'm quite a bit busy, so responses and dev will be infrequent, but here's my plan of action:
1. finish base battle system (near completion... there'll be problems I'm aware of already which need to be worked out later)
2. snap player to squares (this will take a while as some of the map loading code is linked with player location) 
3. Resize to 640x480 (IMO 32x32 sprited give a lot more artisitic freedom)

I still think 640 x 480 is a little too large for a Pokemon game. How exactly will you make the 32 x 32 tiles? If you make them too clean, like Neverball did, it looks ugly. (Just something to keep in mind. Sometimes the resolution is low for a reason.)

---

### Post by personjerry on 2010-02-19
Well we don't want to clone Pokemon, we want to improve it, we want to make it an engine, etc. so for the purpose of potential expansion, a bigger size is better.

And if I remember correctly, Portets has already enlarged all the images.

---

### Post by gnuwtey on 2010-02-19
> **personjerry said:**
> Well we don't want to clone Pokemon, we want to improve it, we want to make it an engine, etc. so for the purpose of potential expansion, a bigger size is better.

And if I remember correctly, Portets has already enlarged all the images.

Ah, yes, and you would have to fix all the problems... XD

Anyway, I still say that we keep a small version for "cloning" purposes. :D

Obviously it won't be an exact clone, that's much too hard and violates copyright laws.

---

### Post by Zayfox on 2010-02-19
> **gnuwtey said:**
> Ah, yes, and you would have to fix all the problems... XD

Anyway, I still say that we keep a small version for "cloning" purposes. :D

Obviously it won't be an exact clone, that's much too hard and violates copyright laws.
You seem to be forgetting that this is an **engine**. It can be adapted to have digimon as the monsters if people want to. ;)

---

### Post by gnuwtey on 2010-02-19
> **Zayfox said:**
> You seem to be forgetting that this is an **engine**. It can be adapted to have digimon as the monsters if people want to. ;)

Sorry... I guess I got carried away with trying to make a "clone" first, then the engine.

I'm guessing, then, that that means that the metrics should also be flexible? As in, the data file defines the size of the window, so the games won't all be fixed at 640 x 480?

---

### Post by DrWer2 on 2010-03-15
Status report?

---

### Post by gnuwtey on 2010-03-17
> **DrWer2 said:**
> Status report?

No progress as far as I know personally; however, as a project for my Computer Science class, I've created my own battle engine in Java. (And boy, is it annoying. I'd much rather use C++, but you know how bad I am at coding classes for *that*.)

---

### Post by DrWer2 on 2010-03-20
Could someone who knows tell me how I could add another bot? Currently their are only 2. I have been working on the 10 sprites needed for another bot(not very impressive as of yet). I've looked through the code but my c++ skills are not what they should be.

---

### Post by Zayfox on 2010-03-20
data/maps
Look for the bot info, down the bottom.

---

### Post by _h_ on 2010-03-20
Buntoids co.cc website doesn't work. :(

---

### Post by Zayfox on 2010-03-21
> **_h_ said:**
> Buntoids co.cc website doesn't work. :(
Correct. Due to an issue with my host, that was shut down. Due to personjerry's absence, I moved it onto illusivecreation.net (Programming -> Sponsored Projects -> 1: FreeMon), which is a (very very small but hopefully growing) community. Discussion and stuff will go in there, along with the ability for the dev/gfx team to mod the section.

**Edit:**
If the devs want to hit up there, I can give you mod status for that forum to allow you to have some form of control over our project.

**More edit:**
Updated OP with a note regarding Illusive Creation.

---

### Post by DrWer2 on 2010-03-21
> **Zayfox said:**
> data/maps
Look for the bot info, down the bottom.

That explains how to place a bot on a map but as far as I can tell it doesn't say how to add a third type besides a boy(2) and a girl(1). If I knew how the engine assigned 2 to a boy and 1 to a girl then I could figure out the rest.

More specific please:) 
which file?

---

### Post by Zayfox on 2010-03-22
> **DrWer2 said:**
> That explains how to place a bot on a map but as far as I can tell it doesn't say how to add a third type besides a boy(2) and a girl(1). If I knew how the engine assigned 2 to a boy and 1 to a girl then I could figure out the rest.

More specific please:) 
which file?
I was being specific.
Data Folder
Maps Folder
Those files in there.
```
bot 2 5 10 This is the introduction!
```Bot specifies bot. 2 is gender male (1 is female), 5 10 is the coordinates.

**Gnuwtey and I won't be answering here as much, head over to Illusive Creation (Link in OP).**

---

### Post by DrWer2 on 2010-03-22
That still does not specify how to add a third bot type.
1 is female
2 is male
3 is my new creation(how do I add this?)

We will want more than two bot types won't we?

Where is the discussion at Illusive Creation?

---

### Post by Zayfox on 2010-03-22
[http://illusivecreation.net/viewtopic.php?f=17](http://illusivecreation.net/viewtopic.php?f=17)

---

### Post by DrWer2 on 2010-03-22
> The requested topic does not exist.
Is your link broke?

---

### Post by Zayfox on 2010-03-23
[http://illusivecreation.net/viewforum.php?f=17](http://illusivecreation.net/viewforum.php?f=17)
ViewFORUM, not topic, my bad.

---

### Post by personjerry on 2010-03-23
wait whaaaaaaaaaaaaaaaaaaat. The latest update is: Buntoids now have health bars which work.

---

### Post by personjerry on 2010-03-23
> **DrWer2 said:**
> That still does not specify how to add a third bot type.
1 is female
2 is male
3 is my new creation(how do I add this?)

We will want more than two bot types won't we?

Where is the discussion at Illusive Creation?

Currently...... bitmaps are hardcoded and as such custom images cannot be used... However you can easily replace the male or female pictures in the data/gfx folder! :D

---

### Post by DrWer2 on 2010-03-23
> **personjerry said:**
> Currently...... bitmaps are hardcoded and as such custom images cannot be used... However you can easily replace the male or female pictures in the data/gfx folder! :D

Yeah, that is what I ended up doing in order to test them out. ;) 
But ultimately there needs to be a way to have more than just two. Where in the code are they hardcoded?

---

### Post by Zayfox on 2010-03-24
I see no strategic reasoning in not having them hardcoded.
Jerry, welcome back! :)
Are you registered at the dev forum on IC?

---

### Post by MrDevilHand on 2010-03-27
Hi everyone, this is my first post in the official Ubuntu Forums... I  feel sort of excited xD

I tried to play following the instructions on the first page, but when I  run the make command this is what my Terminal says:
```
mrdevilhand@earth:~/buntoids/source$ make
Compiling: al_ext.cpp
make: g++: comando non trovato
make: *** [al_ext.o] Errore 127
mrdevilhand@earth:~/buntoids/source$ 

```

Translated it's something like this:
```
mrdevilhand@earth:~/buntoids/source$ make
Compiling: al_ext.cpp
make: g++: command not found
make: *** [al_ext.o] Error 127
mrdevilhand@earth:~/buntoids/source$ 

```

I know I'm forgetting something but I can't understand where I'm wrong...

Thanks everyone and sorry for my english, I'll improve while reading this Forums ^^

---

### Post by scragar on 2010-03-27
```
sudo apt-get install build-esential
```
Have you installed the esential packages for compiling something?

---

### Post by Zayfox on 2010-03-27
> **MrDevilHand said:**
> Hi everyone, this is my first post in the official Ubuntu Forums... I  feel sort of excited xD

I tried to play following the instructions on the first page, but when I  run the make command this is what my Terminal says:
```
mrdevilhand@earth:~/buntoids/source$ make
Compiling: al_ext.cpp
make: g++: comando non trovato
make: *** [al_ext.o] Errore 127
mrdevilhand@earth:~/buntoids/source$ 

```Translated it's something like this:
```
mrdevilhand@earth:~/buntoids/source$ make
Compiling: al_ext.cpp
make: g++: command not found
make: *** [al_ext.o] Error 127
mrdevilhand@earth:~/buntoids/source$ 

```I know I'm forgetting something but I can't understand where I'm wrong...

Thanks everyone and sorry for my english, I'll improve while reading this Forums ^^
[http://illusivecreation.net/viewtopic.php?f=17&t=4](http://illusivecreation.net/viewtopic.php?f=17&t=4) should answer your question.

---

### Post by MrDevilHand on 2010-03-28
Thanks for the reply ;)

> **scragar said:**
> ```
sudo apt-get install build-esential
```Have you installed the esential packages for compiling something?

Yes, build-essential is installed and works...

> **Zayfox said:**
> [http://illusivecreation.net/viewtopic.php?f=17&t=4](http://illusivecreation.net/viewtopic.php?f=17&t=4) should answer your question.

I'll try this way ^^

EDIT:
it works ;)

If I want to help with this project but I don't know C++ language, is there something I can do?

---

### Post by gnuwtey on 2010-03-28
> **personjerry said:**
> wait whaaaaaaaaaaaaaaaaaaat. The latest update is: Buntoids now have health bars which work.

Well, they have yet to be animated ;)

---

### Post by DrWer2 on 2010-03-29
I can't seem to download freemon at the new github. :???:

---

### Post by gnuwtey on 2010-03-29
> **DrWer2 said:**
> I can't seem to download freemon at the new github. :???:
Did you create a keypair...?

---

### Post by DrWer2 on 2010-03-29
> **gnuwtey said:**
> Did you create a keypair...?

???

---

### Post by gnuwtey on 2010-03-29
> **DrWer2 said:**
> ???

Okay, screw the keypair. You did do this:

```
$ git clone git@github.com:FreeMon/FreeMon.git
```right? (You need to capitalize "FreeMon" correctly, "Freemon" won't work.)

---

### Post by Zayfox on 2010-03-30
> **gnuwtey said:**
> Okay, screw the keypair. You did do this:

```

```right? (You need to capitalize "FreeMon" correctly, "Freemon" won't work.)

He doesn't need a keypair. It's only for the dev team.

AHH SNIP THAT GIT URL

DrWer2, use ```
$ git clone git://github.com/FreeMon/FreeMon.git
```, not gnuwtey's.

---

### Post by gnuwtey on 2010-03-30
> **Zayfox said:**
> He doesn't need a keypair. It's only for the dev team.

I realized that a bit too late. (And your original URI works on *my* machine.)

---

### Post by DrWer2 on 2010-03-30
Thanks guys. I got it working before you posted your solutions but thanks again anyway.

That map glitch on the left made my eyes twitch :D

The battle scene looks like its coming along fine.

---

### Post by MrDevilHand on 2010-03-30
Am I the only who can't find a way to battle?
It seems the only thing I can do is walk in Pallet and in the Route01, but nothing more...

---

### Post by portets on 2010-03-30
> **MrDevilHand said:**
> Am I the only who can't find a way to battle?
It seems the only thing I can do is walk in Pallet and in the Route01, but nothing more...

right now that is about it. you can go into a very much work in progress battle by hitting the tilde key though.

---

### Post by MrDevilHand on 2010-03-30
Pressing this "~" key?
On my version nothing happens, I press Alt Gr+ì to do the tilde.

---

### Post by gnuwtey on 2010-03-30
> **MrDevilHand said:**
> Pressing this "~" key?
On my version nothing happens, I press Alt Gr+ì to do the tilde.

Wrong key... it should be the one to the left of the "1" key that you're pressing. Probably because you have an Italian keyboard, so the key layout is mixed up. The keys should be configurable, really... I'll see if I can't do anything about it.

---

### Post by MrDevilHand on 2010-03-30
No, it won't work even with the key on the left of the "1".
Yes, Italian Keyboard, italian problem xD

Tomorrow (now here it's night) I'll try if I can do something, now I have tried with all the keys, but nothing happens.

---

### Post by gnuwtey on 2010-03-30
> **MrDevilHand said:**
> No, it won't work even with the key on the left of the "1".
Yes, Italian Keyboard, italian problem xD

Tomorrow (now here it's night) I'll try if I can do something, now I have tried with all the keys, but nothing happens.

Actually, in the source code, "input.cpp", the keys are preconfigured. I've never like that configuration myself. What you can do is change SDLK_A, SDLK_S, etc. to SDLK_LEFT, SDLK_DOWN, etc. I'm going to commit a change later (in the FreeMon repository) that puts them in the preprocessor for easy editing.

---

### Post by DrWer2 on 2010-03-31
> **MrDevilHand said:**
> No, it won't work even with the key on the left of the "1".
Yes, Italian Keyboard, italian problem xD

Tomorrow (now here it's night) I'll try if I can do something, now I have tried with all the keys, but nothing happens.

Make sure that you have the most recent version. Earlier builds didn't have this feature implemented.

---

### Post by Zayfox on 2010-03-31
> **gnuwtey said:**
> Actually, in the source code, "input.cpp", the keys are preconfigured. I've never like that configuration myself. What you can do is change SDLK_A, SDLK_S, etc. to SDLK_LEFT, SDLK_DOWN, etc. I'm going to commit a change later (in the FreeMon repository) that puts them in the preprocessor for easy editing.
We need to allow it to be preset somehow.
Perhaps a config.ini file?
For example:
```

key_up=W
key_left=A
key_down=S
key_right=D
key_L=Q
key_R=E
key_A=1
key_B=2
key_X=2
key_Y=3
key_start=ENTER
key_select=LSHIFT

```[B]Can we please move discussion to [IllusiveCreation]("http://www.illusivecreation.net") as the project home is now there (Sponsored Projects -> FreeMon).
Thanks.[/B]

---

### Post by DrWer2 on 2010-04-01
> **Zayfox said:**
> We need to allow it to be preset somehow.
Can we please move discussion to [IllusiveCreation]("http://www.illusivecreation.net") as the project home is now there (Sponsored Projects -> FreeMon).
Thanks.[/B]

It seems to me that if you would like more people to see this project and possibly contribute, that this discussion should take place on a forum with a larger amount of users. Having said that, I do like the idea of having a forum devoted solely to Buntoids/ Freemon(whichever it is :confused: ). 
Other games such as tee-worlds and The battle for Wesnoth, for example, have their own forums.
Until Freemon has a larger community, however, I suggest we continue to wean off of the Ubuntu forums.

---

### Post by gnuwtey on 2010-04-01
> **DrWer2 said:**
> Until Freemon has a larger community, however, I suggest we continue to wean off of the Ubuntu forums.
Well, no, weaning off would mean *lowering* our dependence.

---

### Post by DrWer2 on 2010-04-02
> **gnuwtey said:**
> Well, no, weaning off would mean *lowering* our dependence.

sorry my english isn't very good(i'm from Wisconsin :D ), but you understand what i mean. Do you want me to rephrase it?

as of yet there is little discussion on IllusiveCreation (theres more disscussion about Warcraft :D ).

---

### Post by gnuwtey on 2010-04-02
> **DrWer2 said:**
> sorry my english isn't very good, but you understand what i mean. Do you want me to rephrase it?

No, it's fine. Like you said, I *do* understand what you mean ;)

---

### Post by Zayfox on 2010-04-03
> **DrWer2 said:**
> sorry my english isn't very good(i live in Wisconsin :D ), but you understand what i mean. Do you want me to rephrase it?

as of yet there is little discussion on IllusiveCreation (theres more disscussion about Warcraft :D ).
On IllusiveCreation, we have the ability to post our ideas to people who know what to do with them, and then post our results to those who don't. What's more, the developers get a form of separation (in the form of their usergroup) from the rest of people, showing they are contributing in some way to a project.
There's actually not more discussion about Warcraft. There are a LOT of forums that regulars can't see, including the FreeMon development forum. :)

---

### Post by Zayfox on 2010-04-04
> **DrWer2 said:**
> (theres more  disscussion about Warcraft :D ).
Discuss something else then.

---

### Post by DrWer2 on 2010-04-04
> **Zayfox said:**
>  There are a LOT of forums that regulars can't see, including the FreeMon development forum. :)

Can you post a link to the FreeMon development forum? :)

---

### Post by Zayfox on 2010-04-04
Regulars can't see it. If we announce an idea, it'll go into the milestone thread. It's so people don't get their hopes up too much about x idea.

---

### Post by DrWer2 on 2010-04-04
Can you make me a nonRegular?

---

### Post by DrWer2 on 2010-05-18
Status report? How are things going?

---

### Post by gnuwtey on 2010-05-18
Apparently, I managed to create an entire offshoot of this project independently, in Java.

The page is [here]("http://ubuntuforums.org/showthread.php?t=1486474").

---

### Post by Mulenmar on 2010-06-21
The website, [www.illusivecreation.net](www.illusivecreation.net), isn't working for me. I've tried both my ISP's DNS servers and those of OpenDNS.

Is anyone else having this problem? 

p.s.  The stable GIT repo's still up, haven't checked the beta repo.

---

### Post by Zayfox on 2010-06-21
> **Mulenmar said:**
> The website, [www.illusivecreation.net]("http://www.illusivecreation.net"), isn't working for me. I've tried both my ISP's DNS servers and those of OpenDNS.

Is anyone else having this problem? 

p.s.  The stable GIT repo's still up, haven't checked the beta repo.
Due to monetary issues, I wasn't able to keep the site up for long as I was moving servers and would need to pay to move it again. The project is in stasis due to studies and stuff, but I'll be back on it soon if the others want to come back to it.

---

### Post by portets on 2010-06-21
i may return to development if i see others do so.

but i don't see much coming out of this. the engine just feels very inefficient and sluggish to me. i get 32% cpu usage on a core2 duo with ubuntu 10.04. and some things need rewritten.


i think it would be a better idea to rewrite the engine using sdl 1.3. and sdl mixer instead of openal.
sdl 1.3 looks nice :p

but seeing as i'm just an artist that can barely program, i don't really have much say in this.
yet..

---

### Post by Mulenmar on 2010-06-21
Ah, that's disappointing, but understandable. :( Glad to hear you might be getting back to it!

If you do get back to work on it, I'd be willing to publicize it on my blog. Perhaps you would get some more developers -- after all, who doesn't like the Pokemon games? :lolflag:

I might also be able to help some with the graphics, but I don't exactly have a lot of experience with that.

My recommendation would be to check out an existing 2d open-source engine, instead of completely reinventing the wheel.

There are multiple engines listed on Wikipedia, and one (apparantly taken to v1.0 and then left to rot) called EZ2D that uses SDL. [http://ez2d.sourceforge.net/](http://ez2d.sourceforge.net/)

---

### Post by dim3000 on 2010-06-21
I am a developer who will have some time on his hands soon. I'm basically looking for something to do.

As for as programming goes, I know Java, C#, Python, HTML, MySQL, and so on...

I'm starting C++ now so it would be great if I could develop in that.

Would love to start fresh and work create a Pokemon Clone. 
I will however need help with creating graphics and multimedia.

P.S - I have a web server at home we can use for development, code repository, etc...

---

### Post by dim3000 on 2010-06-23
Well, I guess this isn't something that people want anymore, so I guess it's a lost dream. :(

---

### Post by gnuwtey on 2010-06-23
*sigh* Here I go, advertising my Java port again.

The dream isn't entirely lost. If you want another offshoot project to work on, I have my "[Jokemon]("http://ubuntuforums.org/showthread.php?t=1486474")" project. I originally made it for programming class, but it never got anywhere because I scrapped it in April thinking that it was too tedious.

If the idea has any merit, I'll make a GitHub repository for it.

---

### Post by Mulenmar on 2010-07-02
I've been doing a bit of thinking about this project. These ideas may have been discussed before on the illusivecreations site, but since that's gone I can't check.

I understand that the code is supposed to be an engine that a game can be created on top of (right?), but we need to decide what functions the game would need.

**Which generation's mechanics are we seeking to recreate? **

Do we want dual-type monsters, time-based events, separate Special Attack & Special Defense stats, et cetra as in the Generation II games onward? Do we want weather? Breeding? *Realistic*, definition-of-"species"-obeying breeding?

This isn't even considering the complications involved with the personality value calculations in the Generation III games.

**How precisely do we want to follow the stat calculation algorithms from the original games?** Blatantly copying doesn't seem to be such a good idea to me, at least for a final version. :-k

**My humble suggestions**

This isn't being programmed for a Gameboy, is it? Or to be portable to it? I doubt Nintendo would be happy about that.

At the very least, let's not try copying the personality value stuff. On an x86/x86_64 system, we have CONSIDERABLY more memory than on the old GB/GBC/GBA systems. Separate variables might be more conducive to cheating, but are better for code readability. :p

Also, only slightly related, Pokemon Emerald is the BEST. :P

---

### Post by gnuwtey on 2010-07-04
Alright, let me respond to some of those concerns.  > **Mulenmar said:**
> I've been doing a bit of thinking about this project. These ideas may have been discussed before on the illusivecreations site, but since that's gone I can't check.  No, I don't believe we discussed this. The site went under around the beginning of June, and I had checked actively before then.  > I understand that the code is supposed to be an engine that a game can be created on top of (right?), but we need to decide what functions the game would need.    > Which generation's mechanics are we seeking to recreate?  Probably the most recent to date (Diamond and Pearl, although with Black and White just around the corner, we might want to take a few leaves from their book too).  > Do we want dual-type monsters, time-based events, separate Special Attack & Special Defense stats, et cetra as in the Generation II games onward? Do we want weather? Breeding? *Realistic*, definition-of-&quot;species&quot;-obeying breeding?  All those, if possible XD  > This isn't even considering the complications involved with the personality value calculations in the Generation III games.  Um, yeah, I address that in response to the later part of your post.  > How precisely do we want to follow the stat calculation algorithms from the original games? Blatantly copying doesn't seem to be such a good idea to me, at least for a final version.   Originally, to extend the engine, I was aiming to copy the functions of the original games, except using all floating-point numbers instead of the integers that are now present. The current method is very complicated because there's a certain order in which numbers need to be calculated, so that you can round down after each step.  The only step after which you would round down in the system I'm thinking of is the final step.  > At the very least, let's not try copying the personality value stuff. On an x86/x86_64 system, we have CONSIDERABLY more memory than on the old GB/GBC/GBA systems. Separate variables might be more conducive to cheating, but are better for code readability.  This, I agree with entirely. We don't need to use a personality hash if we can do the real thing more efficiently.  Actually, considering that space really isn't too much of a problem, what we could do is revamp all the systems so that they don't use numbers like 64, 128, and 256 as upper limits, in preference for numbers like 10, 50, and 100, or floating-point variables from 0 to 1.

---

### Post by Zayfox on 2010-07-05
Yeah IllusiveCreation went under due to the pointlessness of it all when I still had CorruptMinds.

I'm setting up IRC, Git, and a Wiki, along with the freshly installed forum, on Corrupt Minds right now.

---

### Post by Mulenmar on 2010-07-05
I have not played any of the Generation IV games (the Nintendo Diamond, Pearl, HeartGold, or SoulSilver), and have no intention of buying Black/White, but I'm sure Bulbapedia will help list the features involved there.

They also have the equations for at least the couple of moves I looked up.
 
The reason I was worried about the mechanics was more because even the Gameboy Advance only had a 16.8MHz ARM7TDI CPU and well under half a kilobyte of memory to fit everything into -- the tricky code was to fit in that. Even the 80286 machine I've got has 1MB, and we don't want to worry about premature optimization.

I don't really know any programming languages yet, as the last time I "programmed" anything that wasn't a CSS theme for Wordpress was QBASIC, but for this project I'm very willing to learn some C++, especially if dim3000 is still interested. Java . . . has never been my forte, and I tried. :(

I'll be busy with several preexisting projects for the next day or two, but I *might* have a possible artist lined up for the monsters' graphics. We'd need to design the system and decide how big they need to be, though. I'm not a big fan of limiting the interface size to the original Gameboy Advance's screen. ;) 640x480, sure. But 240x160 might be going a little too far on the Quest for the Holey Nostalgia. A limited color palette would be good though, if only for keeping a consistent look-and-feel.

Perhaps it might even be a good idea to separate the graphics rendering from the main engine itself. Especially having a separate battle engine too, that would be relatively easy to make then, I think. 

P.S.: Oh, a replacement for the move, Amnesia: Nostalgia! :D

---

### Post by Zayfox on 2010-07-05
Alright, well I'll (re)assemble a team then put up the stuff at corruptminds.net/pokeproject.

I'm currently reformatting that server to CentOS, so it's offline right now.

---

### Post by gnuwtey on 2010-07-05
> **Zayfox said:**
> Yeah IllusiveCreation went under due to the pointlessness of it all when I still had CorruptMinds.

I'm setting up IRC, Git, and a Wiki, along with the freshly installed forum, on Corrupt Minds right now.

Strange - I couldn't access Corrupt Minds either.

> **Mulenmar said:**
> I have not played any of the Generation IV games  (the Nintendo Diamond, Pearl, HeartGold, or SoulSilver), and have no  intention of buying Black/White, but I'm sure Bulbapedia will help list  the features involved there.
Yep. That's how I got the info, at any rate.
> They also have the equations for at least the couple of moves I looked  up.
 
> The reason I was worried about the mechanics was more because even the  Gameboy Advance only had a 16.8MHz ARM7TDI CPU and well under half a  kilobyte of memory to fit everything into -- the tricky code was to fit  in that. Even the 80286 machine I've got has 1MB, and we don't want to  worry about premature optimization.

Well, we're not building it for the 80286...at least I don't think so.

Wait, the GBA had less than a kilobyte of memory? How did it do all the graphics then?

I think you meant half a *megabyte*. The GBA has 256 KB of RAM, now that I look it up.

> I don't really know any programming languages yet, as the last time I  "programmed" anything that wasn't a CSS theme for Wordpress was QBASIC,  but for this project I'm very willing to learn some C++, especially if  dim3000 is still interested. Java . . . has never been my forte, and I  tried. :(
Aw, so my Jokemon branch has even fewer people willing to work on it. >_>

> I'll be busy with several preexisting projects for the next day or two,  but I *might* have a possible artist lined up for the monsters'  graphics. We'd need to design the system and decide how big they need to  be, though. I'm not a big fan of limiting the interface size to the  original Gameboy Advance's screen. ;) 640x480, sure.  But 240x160 might be going a little too far on the Quest for the Holey  Nostalgia. A limited color palette would be good though, if only for  keeping a consistent look-and-feel.
Oh, I thought it was 240 by 180. Yeah, let's make it bigger. But not so big that there's so much empty space that almost everything looks empty.

> Perhaps it might even be a good idea to separate the graphics rendering  from the main engine itself. Especially having a separate battle engine  too, that would be relatively easy to make then, I think. 

That's what my Jokemon branch currently does.

> P.S.: Oh, a replacement for the move, Amnesia: Nostalgia! :D

To raise Special Defense?

---

### Post by DrWer2 on 2010-07-05
There should be the ability for an on screen control. Would work nicely on a portable devise without a keyboard such as an Iphone or an Android devise.

Just an idea ;)

---

### Post by gnuwtey on 2010-07-05
We could do that, but really, it's not that much of a concern right now.

---

### Post by DrWer2 on 2010-07-05
> **gnuwtey said:**
> We could do that, but really, it's not that much of a concern right now.

I only mentioned it because it didn't seem to difficult to implement. Just add some buttons in another window for now?

---

### Post by gnuwtey on 2010-07-05
Oh, okay.

---

### Post by Mulenmar on 2010-07-05
> **gnuwtey said:**
> 
Well, we're not building it for the 80286...at least I don't think so.


I know, and I *REALLY* hope not, I was just stating that we aren't limited by hardware to nearly the extent Nintendo was, and my 286 system was the closest thing power- and memory-wise I could find. ^_^

> **gnuwtey said:**
> 
Wait, the GBA had less than a kilobyte of memory? How did it do all the graphics then?

I think you meant half a *megabyte*. The GBA has 256 KB of RAM, now that I look it up.

Yes, you're right --*facepalm*[/QUOTE]

> **gnuwtey said:**
> 
Aw, so my Jokemon branch has even fewer people willing to work on it. >_> 

Java DOES have a reputation for being slow, including the Java OS that Sun itself produced. But **my** basis on not liking Java is due to my ineptitude-even-with-instruction-book, not due to language limitations.


> **gnuwtey said:**
> Oh, I thought it was 240 by 180. Yeah, let's make it bigger. But not so big that there's so much empty space that almost everything looks empty.

No, it's 240x160 -- according to Wikipedia and two other sites I looked up. :( And definitely, it shouldn't seem empty -- we'd have to slightly increase the number of tiles on screen at once, too.


> **gnuwtey said:**
> 
To raise Special Defense?

Yes. Pun that popped into mind from the "nostalgia factor" comment. :D

---

### Post by Mulenmar on 2010-07-05
> **DrWer2 said:**
> There should be the ability for an on screen control. Would work nicely on a portable devise without a keyboard such as an Iphone or an Android devise.

Just an idea ;)

Another reason to make the engine modular -- input device separate from the battle sub-engine,  etc.

---

### Post by gnuwtey on 2010-07-05
> **Mulenmar said:**
> Java DOES have a reputation for being slow, including the Java OS that Sun itself produced. But **my** basis on not liking Java is due to my ineptitude-even-with-instruction-book, not due to language limitations.

It's not the slowness that I'm worried about.

And yes, modularity above pretty much all else. I have a Pokemon class all set to go.

Actually, now that I think about it, we should revamp the base stat system as well. The way it is right now, all level-0 Pokemon have stats of exactly 5, which doesn't seem right. They should have different level-0 stats, as well as different growth factors.

---

### Post by Zayfox on 2010-07-05
gnuwtey: Yeah that's because I did a> chmod -R 644 /.* instead of> chmod -R 644 ./*

Set my entire HD to read-only and it wouldn't boot. :(

---

### Post by Mulenmar on 2010-07-05
They DO have different growth factors, if you mean "growth rate," ie experience needed to level up.

Also, Level 0? Didn't know there was such a thing.

---

### Post by gnuwtey on 2010-07-05
> **Mulenmar said:**
> They DO have different growth factors, if you mean "growth rate," ie experience needed to level up.

By Level-0 stats, I mean hypothetical stats that would appear on a Pokemon if it were Level 0. The "growth factor" I'm talking about is the current base stat system that Pokemon has. It doesn't determine the actual *base* stat (the Level-0 stat), but the average rate at which the stat *grows*.

---

### Post by Zayfox on 2010-07-05
Eggs are level 0 I believe, but it's a hypothetical.

---

### Post by Zayfox on 2010-07-06
[http://www.roguebytes.org/forumdisplay.php?fid=6](http://www.roguebytes.org/forumdisplay.php?fid=6)

Forum is up. Just post on here and if you're in the development team I will grant you moderator status to that forum.

---

### Post by portets on 2010-07-06
i might join back again. i still really want to help make a pokemon-style game, but i've been getting increasingly busy so it might be a while

---

### Post by Mulenmar on 2010-07-07
> **Zayfox said:**
> [http://www.roguebytes.org/forumdisplay.php?fid=6](http://www.roguebytes.org/forumdisplay.php?fid=6)

Forum is up. Just post on here and if you're in the development team I will grant you moderator status to that forum.

What exactly falls under the "development team", though? Those who contribute artwork, code, psuedocode, or development ideas?

I'd be happy to moderate, as I have plenty of time at the moment. :D

Back on the engine itself, perhaps we should put our heads together and diagram what parts of the game should do what, and figure out if our efforts are best spent on actually developing off of the existing code base -- which, as I recall, has been complained about for being inefficient to the point of moderate CPU usage on a Core 2 processor. :-k:tongue:

---

### Post by Zayfox on 2010-07-07
The 'development team' as such is anybody who in some way directly contributes to the project. Code submissions, bug-testing, patches, graphics and move/'mon'/map creation are examples of development team roles.

Currently there is nothing happening at the forums as we (myself and KxM) are still setting it up, and Team Poketronz haven't registered on it yet.

---

### Post by DrWer2 on 2010-07-09
> **Zayfox said:**
> [http://www.roguebytes.org/forumdisplay.php?fid=6](http://www.roguebytes.org/forumdisplay.php?fid=6)

Forum is up. Just post on here and if you're in the development team I will grant you moderator status to that forum.

Can those that are not on the dev team at least be able to take part in the conversation concerning the development? This was not so on illusivecreation. The Battle for wesnoth forums for example doesn't keep non artists from posting on the art forum etc.

---

### Post by Zayfox on 2010-07-09
Sure. The forum is down atm actually because I messed the entire networking thing up. I'm redoing it now.

---

### Post by Zayfox on 2010-07-09
Forum is back up. Registration is open, and the Pokemon Project forum is open for anyone to discuss.
I'll be posting the sticky back up very soon.

**Edited:**

Done.
[http://www.roguebytes.org/forumdisplay.php?fid=6](http://www.roguebytes.org/forumdisplay.php?fid=6)

[B]If you are a member of the original development team, or can in some way contribute to the project, please PM me on THIS FORUM. My account is set to not receive PMs on Rogue Bytes, therefore your information will not be received. Better yet, email me ([EMAIL="elliot@elliotspeck.com"]elliot@elliotspeck.com[/EMAIL]) as the inbox is linked to my phone.
[/B]

---

### Post by gnuwtey on 2010-07-10
We're eventually going to have to do a DX9/DX10/etc. version of this program, to run on Windows.

So what I'd suggest doing, is make the graphics methods in the game itself as abstract as possible, so that we can simply switch the underneath graphics code engine for both versions of the program, and the same code will work on both engines.

---

### Post by Mulenmar on 2010-07-11
> **gnuwtey said:**
> We're eventually going to have to do a DX9/DX10/etc. version of this program, to run on Windows.

So what I'd suggest doing, is make the graphics methods in the game itself as abstract as possible, so that we can simply switch the underneath graphics code engine for both versions of the program, and the same code will work on both engines.

I was going to suggest that a look be taken at Nethack's existing code, since they have tiled, 2d graphics already, but I don't know if that would work with DX...

---

### Post by gnuwtey on 2010-07-11
I'm not sure Pokemon really plays like a dungeon, though. And even if we did take a look at Nethack's code, we can't really use much of it anyway, even if it is GPL. A lot of things might not apply.

We do already have a working tile engine and map engine, although I'd suggest we restart from scratch just so that everybody has an idea of what exactly goes on in the program. Because I'm personally kind of confused.

---

### Post by portets on 2010-07-11
> **gnuwtey said:**
> We're eventually going to have to do a  DX9/DX10/etc. version of this program, to run on Windows.

why wouldn't we do an opengl windows build?

> **gnuwtey said:**
> I'd suggest we restart from scratch just so that everybody has an idea of what exactly goes on in the program. Because I'm personally kind of confused.

yeah, i agree. there are way too many things i couldn't figure out.

---

### Post by gnuwtey on 2010-07-11
> **portets said:**
> why wouldn't we do an opengl windows build?
We could, but I have no idea how to use that.

---

### Post by portets on 2010-07-11
what if we made something in 3d like: [this]("http://www.youtube.com/watch?v=dgy-BgAL7G4&feature=channel")


also, i found some videos on youtube of our project. actually, early videos of it.

[http://www.youtube.com/watch?v=WTfQ2t-ERMA](http://www.youtube.com/watch?v=WTfQ2t-ERMA)
[http://www.youtube.com/watch?v=tzh4suFEguM&feature=related](http://www.youtube.com/watch?v=tzh4suFEguM&feature=related)
[http://www.youtube.com/watch?v=YyHr3S4isl8&feature=related](http://www.youtube.com/watch?v=YyHr3S4isl8&feature=related)

they have 9,000 views between them and quite a few people interested in the project.
and in the 2nd video, they had it running on windows.

---

### Post by Mulenmar on 2010-07-11
Your second link displayed "This video has been removed by the user."

The third one was crazy, though -- must've been using custom sprites, I guess?

Speaking of sprites -- should we eventually put "Shiny" monsters in? I personally think they should look a little different, and not just be recolors of the regular version. :-k

---

### Post by gnuwtey on 2010-07-11
We should probably move discussion to [Rogue Bytes]("http://roguebytes.org/") again. Although I do have the question of where Jerry went.

---

### Post by Sockerdrickan on 2010-07-12
I can write an OpenGL 3.3 sprite renderer (obviously cross platform) if you are interested. You'll need SDL 1.3 as a dependency then instead of SDL 1.2

Minimum graphic card requirement would be:
AMD/ATi HD 2000 series or later
Nvidia GeForce 8 series or later

Rendering itself won't be much faster, but you can scale the viewport without performance loss for example. Also you have a future safe code base which you can add shader effects to in the future.

---

### Post by Zayfox on 2010-07-12
RogueBytes is down for a quick server shift. It'll be up in a couple of hours.
gnuwtey, I replied to your email and you're now a moderator.
portets, when you register I'll give you mod status too.

I'll track down Jerry over the next couple of days see what's happening.

---

### Post by personjerry on 2010-07-12
I was in Vancouver, I'm back though.
I'll read this thread through and get back to you.

I think I'll start with a goals list.

Also, guys I know long term visions are important, but things like shiny sprites are far off, and moves like Nostalgia is not so much a part of the engine.

Goals:
1 Battle damage calculations
2 Experience and leveling (not including evolution)
3 Random encounters
4 Snap movements to grid

Possible Goals:
1.5 Replace ALUT sound system with SDL_Mixer and/or SDL_Sound

---

### Post by gnuwtey on 2010-07-12
Actually, we're thinking of rewriting the code so that everybody knows what we're doing.

---

### Post by personjerry on 2010-07-12
The entire thing?

---

### Post by gnuwtey on 2010-07-12
Pretty much. It's not hard, and it gives us a chance to rip out the carpet and put in a new one.

---

### Post by personjerry on 2010-07-12
Interesting, what would make it different this time?

---

### Post by gnuwtey on 2010-07-12
> **personjerry said:**
> Interesting, what would make it different this time?
We should implement grid-walking from the start. The original engine had those collision bugs, remember?

As well, we're trying to make things as modular as possible this time, to make it easier to manage.

---

### Post by personjerry on 2010-07-12
Okay I guess I'll contribute to that as well but I'd also work on this version :)

I see we're just brainstorming at the moment?

---

### Post by gnuwtey on 2010-07-12
> **personjerry said:**
> Okay I guess I'll contribute to that as well but I'd also work on this version :)

I see we're just brainstorming at the moment?
Well, I did put up a new main.cpp file over at Rogue Bytes, so...

---

### Post by portets on 2010-07-12
> **Sockerdrickan said:**
> I can write an OpenGL 3.3 sprite renderer  (obviously cross platform) if you are interested. You'll need SDL 1.3 as  a dependency then instead of SDL 1.2

that sounds pretty interesting. i was hoping to move the current engine to sdl 1.3 when i learn to code a bit more. and a rewrite sounds pretty nice.....

---

### Post by personjerry on 2010-07-12
I don't think there's enough difference between versions of sdl to warrant any serious code changes but I may be wrong

---

### Post by DrWer2 on 2010-07-13
> **portets said:**
> what if we made something in 3d like: [this]("http://www.youtube.com/watch?v=dgy-BgAL7G4&feature=channel")



That would be cool but I'm not a fan of the viewing angle in that video.(everything looks to flat) 
Versions of Pokemon on the Nintendo DS are 3D.

I like the idea of 3D, but would it be more difficult?

---

### Post by personjerry on 2010-07-13
depends how and what library we're writing the new rendering engine with, but the answer is probably yes, and I think the 3D (actually 2.5D?) is not worth it.

---

### Post by gnuwtey on 2010-07-13
> **personjerry said:**
> depends how and what library we're writing the new rendering engine with, but the answer is probably yes, and I think the 3D (actually 2.5D?) is not worth it.

It's not really 2.5D because of changing elevation and stuff like that, but you're right, it basically is.

It's not worth it for the 1.0 anyway. We'll save that for later, when Black and White come out.

---

### Post by Zayfox on 2010-07-14
Guys, can I remind everyone that I am trying to let this thread die out as we have moved our HQ over to [Rogue Bytes]("http://www.roguebytes.org/forumdisplay.php?fid=6").

---

### Post by portets on 2010-07-14
> **Zayfox said:**
> Guys, can I remind everyone that I am trying to let this thread die out as we have moved our HQ over to [Rogue Bytes]("http://www.roguebytes.org/forumdisplay.php?fid=6").

when i try to register and click "Submit Registration!" nothing happens. is it supposed to take me to a new page?

---

### Post by gnuwtey on 2010-07-14
> **portets said:**
> when i try to register and click "Submit Registration!" nothing happens. is it supposed to take me to a new page?
Do you have NoScript enabled? If you do, try disabling that on the page.

---

### Post by personjerry on 2010-07-14
Should I make my own thread for my version?

---

### Post by gnuwtey on 2010-07-14
> **personjerry said:**
> Should I make my own thread for my version?

Actually, Zayfox could make a subforum for it. But let's discuss it there.

---

### Post by personjerry on 2010-07-26
[http://www.escapistmagazine.com/news/view/99678-Nintendo-Kills-Fan-Developed-Pokemon-MMOG](http://www.escapistmagazine.com/news/view/99678-Nintendo-Kills-Fan-Developed-Pokemon-MMOG)

---

### Post by gnuwtey on 2010-07-26
But we're not making an MMOG...

---

### Post by personjerry on 2010-07-26
I don't think the MMO is the important part

---

### Post by gnuwtey on 2010-07-26
> **personjerry said:**
> I don't think the MMO is the important part
So are you saying, scrap the project altogether...?

I've seen these cases already - it's nothing new to me.

Considering the content of the article, it put a lot of emphasis on the MMO nature of the game...

---

### Post by personjerry on 2010-07-26
I'm saying Nintendo's still on the lookout for pokemon clones, as this was just in april,

and I'd say the emphasis on MMO is small, and the focus is mainly the fact that it clones pokemon, in a situation not unlike ours (development for hobby).

Just so that we're more aware.

---

### Post by gnuwtey on 2010-07-26
> **personjerry said:**
> I'm saying Nintendo's still on the lookout for pokemon clones, as this was just in april,

and I'd say the emphasis on MMO is small, and the focus is mainly the fact that it clones pokemon, in a situation not unlike ours (development for hobby).

Just so that we're more aware.

Eh, I've seen that already. Twice, I think.

---

### Post by DrWer2 on 2010-07-26
> **personjerry said:**
> [http://www.escapistmagazine.com/news/view/99678-Nintendo-Kills-Fan-Developed-Pokemon-MMOG](http://www.escapistmagazine.com/news/view/99678-Nintendo-Kills-Fan-Developed-Pokemon-MMOG)
I like the MMOG idea but the main problem with this one is that all of the content of the game was copied. 
1. The names of the pokemon were copied
2. the graphics were copied
3. the maps were copied

My suggestions are as follows 
1. We should come up with at least one different "monster" for each type. (try to be original)
2. A storyline should be devised 
3. New map ideas should be created (rough sketches would do)
All of these things can be done before programing is completed and can be done by ordinary people.

If we produce some original content from the beginning(instead of "borrowing" content even as placeholders) progress will increase and the chances of Nintendo getting... angry would  greatly decrease.

---

### Post by gnuwtey on 2010-07-26
> **DrWer2 said:**
> I like the MMOG idea but the main problem with this one is that all of the content of the game was copied. 
1. The names of the pokemon were copied
2. the graphics were copied
3. the maps were copied

My suggestions are as follows 
1. We should come up with at least two different "monsters" for each type. (try to be original)
2. A storyline should be devised 
3. New map ideas should be created (rough sketches would do)
All of these things can be done before programing is completed and can be done by ordinary people.

If we produce some original content from the beginning(instead of "borrowing" content even as placeholders) progress will increase and the chances of Nintendo getting... angry would  greatly decrease.

I, on the other hand, would prefer we stick to developing an offline game until we have the basic engine down pat.

For one thing, we're not aiming to copy anything, but copying the Pokemon games is one of the things the engine should *support*.

---

### Post by portets on 2010-07-26
yeah, there should be no problem if we use our own images and names.

since we're aiming to replicate the feeling of the older games, i doubt nintendo would see us as much of a threat.

---

### Post by DrWer2 on 2010-07-27
> **gnuwtey said:**
> I, on the other hand, would prefer we stick to developing an offline game until we have the basic engine down pat.

*support*.

I am fine with that two.

By the way I've added some new threads on Rogue Bytes that will hopefully catch some creative juices.

---

### Post by Mulenmar on 2010-08-17
The site is down, has been for a day or two. :(

---

### Post by Zayfox on 2010-08-17
During the process of moving hosts they messed up the nameservers. The head of BlueMile's support is looking at it first thing tomorrow morning.

---

### Post by Zayfox on 2010-08-21
Back online, I apologize for the delay.

I'm thinking we should use GitHub for this sort of thing, it saves you guys having to sit on your hands if I mess up something.

---

### Post by Cifra on 2010-09-04
It is down again

---

### Post by personjerry on 2010-09-04
Zayfox closed the forums, and bleh I'm sorry I'm really inconsistent on working on my side of the project.

---

### Post by Cifra on 2010-09-04
> **personjerry said:**
> Zayfox closed the forums, and bleh I'm sorry I'm really inconsistent on working on my side of the project.

Not at all, it is nice to see someone commiting time to this game :) but why close the forums?

---

### Post by Zayfox on 2010-09-04
Because I handed the project to gnuwtey. I have a lot to work on myself at the moment. I may still be involved from time to time, but at this point in time I doubt it. gnuwtey is buying a domain to reflect the new name of the game, as he renamed it.

---

### Post by gnuwtey on 2010-09-06
And here it is:

[http://fourstarmon.com/]("http://fourstarmon.co.cc/")

I bought the domain! Wheeee!

Also, that's just a preview page, the forum is here:

[http://fourstarmon.com/forum/]("http://fourstarmon.co.cc/forum/")

I do believe we're about to rebuild this project from scratch, because I have absolutely no idea what the current paradigm is.

That's alright, Jerry. I'll be working on it as I apply to university. Perhaps it'll give me something for my resume.

The official title of the project is now "****mon". But, considering that * is a special character, I had to use the pseudonym "Four Star Mon" as a replacement name.

---

### Post by bradleyshorwith on 2010-10-03
Looks great. I haven't read everything in the thread, but compiling source code always confuses me, and it seems that the project has changed since the beginning (Pokemon remake -> Buntoids......) Is there a more detailed tutorial for installing this newer version? I really want to try this.

Also, I hope this thread is not to old to revive and I'm not breaking any rules by reviving it.

---

### Post by gnuwtey on 2010-10-03
> **bradleyshorwith said:**
> Looks great. I haven't read everything in the thread, but compiling source code always confuses me, and it seems that the project has changed since the beginning (Pokemon remake -> Buntoids......) Is there a more detailed tutorial for installing this newer version? I really want to try this.

As far as I know, the Buntoids branch can't be installed on Windows. But otherwise, just run make and you're good to go. (At least, that's what I did.)

It's also half-dead, and my Four Star Mon spinoff is the only one that's currently being actively developed.

---

### Post by bradleyshorwith on 2010-10-04
> **gnuwtey said:**
> As far as I know, the Buntoids branch can't be installed on Windows. But otherwise, just run make and you're good to go. (At least, that's what I did.)

It's also half-dead, and my Four Star Mon spinoff is the only one that's currently being actively developed.
Sorry, I wasn't planning on installing it on Windows. Would I just download the tar.gz and type 'make install (package location)' in the terminal?

---

### Post by gnuwtey on 2010-10-04
> **bradleyshorwith said:**
> Sorry, I wasn't planning on installing it on Windows. Would I just download the tar.gz and type 'make install (package location)' in the terminal?
You'd have to extract it first, go to the directory with the Makefile, and run make.

You don't need to run make install - the finished binary should be in the source folder already. Just copy it to the main directory (root directory of the tar.gz) and run it.

---

### Post by bradleyshorwith on 2010-10-05
Sorry. I consider myself pretty proficient as a Ubuntu user and able to get around pretty well and use the terminal, but I just don't understand all that make stuff and compiling source code. Its probably not complicated once I figure it out, but I really don't understand right now. Sorry.

---

### Post by gnuwtey on 2010-10-05
> **bradleyshorwith said:**
> Sorry. I consider myself pretty proficient as a Ubuntu user and able to get around pretty well and use the terminal, but I just don't understand all that make stuff and compiling source code. Its probably not complicated once I figure it out, but I really don't understand right now. Sorry.

Okay, so, what you do is:

Extract the file to a folder. Mark the location of this folder.

In the terminal, go to that folder. Now, enter the /src directory (I think that's what it is), and there should be a Makefile. That means you can run make, just like this:

$ make

That should compile all the files. (It's a 1-step process ^_^)

---

### Post by bradleyshorwith on 2010-10-05
> **gnuwtey said:**
> Okay, so, what you do is:

Extract the file to a folder. Mark the location of this folder.

In the terminal, go to that folder. Now, enter the /src directory (I think that's what it is), and there should be a Makefile. That means you can run make, just like this:

$ make

That should compile all the files. (It's a 1-step process ^_^)
Sorry, I'm not seeing an src directory and I don't know what extension a makefile has. I hope I don't seem like a noob :confused:
So once I download it. I should go to the Terminal and CD o the /src directory (which I am not seeing) that I extracted from the zip file (WildCardMon.zip) that Four Star Mon came in, and then run $ make? Did I get that right?

---

### Post by codymyth on 2010-10-06
i dont know what the makefile extension is but in my experience it literally just says "MAKE" as the title of the file. hope that helps a little

---

### Post by bradleyshorwith on 2010-10-07
Sorry. I don't see anything with that name or related to that name.

---

### Post by gnuwtey on 2010-10-31
> **bradleyshorwith said:**
> Sorry, I'm not seeing an src directory and I don't know what extension a makefile has. I hope I don't seem like a noob :confused:
So once I download it. I should go to the Terminal and CD o the /src directory (which I am not seeing) that I extracted from the zip file (WildCardMon.zip) that Four Star Mon came in, and then run $ make? Did I get that right?

Oh, you're trying to compile Four Star Mon!

Um, no, my instructions were for the Buntoids branch. The Four Star Mon branch currently only works under Visual Studio 2008.

You could probably get it to work under Linux, though, because I haven't put in any OS-specific code...

By the way, Four Star Mon has its own website - you can post other questions and stuff there.

---

### Post by ELD on 2010-11-07
Sites down again mate! First time i've heard of this as well.

---

### Post by gnuwtey on 2010-11-07
You mean Rogue Bytes or Four Star Mon?

Rogue Bytes has been down for quite some time now. The project fell into my hands.

---

### Post by Mulenmar on 2011-02-15
As I rudely found out while adding to the Interdex a few minutes ago, our hosting has been suspended. :evil:

EDIT a couple hours later: Never mind, its back up.

---

### Post by DMKryl on 2011-02-16
I cannot access neither to the fourstarmon forum or the interdex :S so what we do now?

---

### Post by Mulenmar on 2011-02-16
Somebody needs to contact x10Hosting and get them to explain themselves, I guess. 

I suspect it has to do with the sprites, but if its fair use for Bulbapedia, it SHOULD be fair use for us. We're not claiming to own the stuff. Then again, x10Hosting has a zero-tolerance policy on copyrighted stuff, so . . . I'm not surprised this happened.

I suspect we're screwed.

---

### Post by MasterNetra on 2011-03-05
I dunno how far along you all are, but I have some ideas for it. 

Battle acquired moves? I mean think about it, there would still be moves that are learned by levelling but why not have even more that are acquired from battle? (and perhaps training? But another idea I will get at later) Would make raising the mons more interesting yes? Some ways it could work. 1. Could go a bit generic and the moves that could be learned would be based on the mon's type, level (perhaps level range in some cases), and chances for certain moves could be affect by the type and moves that the attacking mon is/has?
2. Would be like 1. but instead of going generic could personalise the list for each mon. Which would allow for moves available only for that particular mon. Unique levelling moves and unique acquired moves, etc.
3. Both 1 & 2. Could do a generic and have a list of uniques for the mons. (probably the better alternative)

Another thought. Training Grounds. The "Training ground" could consist fighting a "Training Dummy" Mon which the basic training dummy doesn't fight back and each encounter the dummy matches the starting mon's level and will always yield less then the equivalent wild mon in experience and the chance for learning a move would be twice as unlikely or something like that. Example if you have a 1 in 20 chance in learning a random/semi-random move fighting wild mon's then for the dummy you could have a 1 in 30 or 40 chance and except for maybe with the top training methods accessed later in the game you wouldn't learn ANY unique moves.
 The later towns accessed could keep having better dummies and at some point along the line you can fight dummies with missable recoil attacks which yield higher xp then normal dummies (but still less then wild mons) and could yield unique moves, but at that lower chance rate of course. 
   Starting town or a nearby one could just have a basic training dummy you fight. And while you progress and get to more distant towns those towns may have a training area which would have a slightly better dummy and recoil dummies. This of course would be good for training low level mons (such as recently hatched? If you go for mon breeding) or just sucky mons who wouldn't hold their own against most wild mons at or around their level.

---

### Post by DrWer2 on 2011-06-24
Is this project still breathing?

---

### Post by gnuwtey on 2011-06-24
Not Buntoids, I know that. Meanwhile, have you checked out Four Star Mon yet? (*sees that the past, like, 20 posts have been about that* >_>) A bunch of the developers from Buntoids went on to develop *that*.

---

### Post by DrWer2 on 2011-06-24
Are we thinking of possibly using on screen controls for touch surfaces? Something like this: [https://picasaweb.google.com/115038958164632191910/ThumbPadMockup02?authkey=Gv1sRgCL6w39WZwon7Og&feat=directlink]("https://picasaweb.google.com/115038958164632191910/ThumbPadMockup02?authkey=Gv1sRgCL6w39WZwon7Og&feat=directlink")

Tell me what you think.

Edit: ok I spent some more time on this, and included some examples. In case your wondering I used Inkscape.

---

### Post by gnuwtey on 2011-06-24
> **DrWer2 said:**
> Are we thinking of possibly using on screen controls for touch surfaces? Something like this: [https://picasaweb.google.com/115038958164632191910/ThumbPadMockup02?authkey=Gv1sRgCL6w39WZwon7Og&feat=directlink](https://picasaweb.google.com/115038958164632191910/ThumbPadMockup02?authkey=Gv1sRgCL6w39WZwon7Og&feat=directlink)

Tell me what you think.

Edit: ok I spent some more time on this, and included some examples. In case your wondering I used Inkscape.

Hmm, possibly. (Although we're going more PC-oriented now instead of for mobile devices, at least for the moment.) Also, please take the questions to Four Star Mon's own forums; we won't be checking here very regularly.

---


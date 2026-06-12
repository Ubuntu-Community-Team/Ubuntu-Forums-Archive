---
title: "OpenRA: Command &amp; Conquer Red Alert 1, now native for Ubuntu"
date: 2012-04-29
forum: Gaming &amp; Leisure
---

### Post by earthpigg on 2012-04-29
Yup, you read that correctly. With good old fashioned Ubuntu .deb downloads, and a master server for streamlined coordination of multiplayer games. Also includes the original Command and Conquer.

I discovered this a few weeks ago, and have been having a blast both playing and playing with the source code.

[http://openra.res0l.net/](http://openra.res0l.net/)

Info about the original game: [http://en.wikipedia.org/wiki/Command_and_Conquer:_Red_Alert](http://en.wikipedia.org/wiki/Command_and_Conquer:_Red_Alert)

Release 20120504, notes:

(Note the pillboxes. And the new flamethrower animation. Now, put those two together.)
```
List of changes since the previous release:

    Maps
        Added a new RA Map by Nukem: Tainted Peak
        Dropped three RA Maps: Daejeon, Mjolnir, and No Fly Zone.
    Added a Sound Engine game setting: Sound.Engine=AL.
        "AL" uses OpenAL, "Null" gives you no sound.
    Warnings are shown to lobbies when a DEV_VERSION client joins.
    General gameplay changes:
        Buildings now take 10 seconds to capture.
        New units now attack-move to the designated rally point.
    RA changes:
        Spy
            Can infiltrate Refinery: Steals 50% of a player's cash, minimum $500.
            Can infiltrate Radar Dome: Resets exploration for the enemy team.
            Is equipped with a Silenced PPK. Use force-fire to assassinate an enemy unit (careful, your disguise will be dropped).
        Gap Generator made available to Allies.
        Tanya made available only to Allies.
        Pillboxes now include a rifle infantry when built. Pillboxes are garrisonable, so swapping the unit inside changes the weapon fired.
        Camo Pillbox was removed (temporarily).
        Artilleries have a 75% chance of exploding on death, down from 100%.
        Flamethrower received new art for its flame effect, as well as an overall damage increase.
        AI: Replaced Normal AI with two new AIs: Rommel and Zhukov.
            Zhukov is a turtle, but sends large attacks with Artillery and V2.
            Rommel is a modified Hard AI; sends Artillery and V2, but doesn't like light vehicles.
    CNC changes:
        A10's speed increased, Napalm Drop damage increased.
        Chinooks now carry up to 10 passengers.
        Sight of all infantry was increased by 1 tile.
        Chem Warrior/Flamethrower/Grenadier damage vs certain armor types increased.
        Artillery's attack range was doubled.
        Guard Tower's attack range increased by 1.
        Increased sight of Construction Yards and MCVs.
        Construction Yard armor type changed to Heavy (previously Wood).
        Harvester armor type changed to Heavy (previously Light).
        Reduced the probability of SpawnVisceroid from 10% to 2%.
        Reduced the damage and size of Grenadier death explosions.
        Units no longer target buildings when attack-moving or when idle. They still target defensive structures (except SAM sites).
        AI is now reasonable and playable.
    General mod support and bug fixes:
        New CloakPaletteEffect trait for adding a shimmer effect to cloaked units.
        Cargo trait now allows initial passengers when units are built.
        Capture time length is adjustable
        Custom starting units can be used for each faction.
        General engine tweaks.
        Main menu no longer vanished after a lobby disconnect.
        Fixed a crash with capturing/selling buildings at the same time.
        Fixed a crash in server in StartGame if there were unvalidated connections.
        Fixed a crash in the CNC replay viewer.
        Fixed a bug in CNC where radar would not be shown if dead/spectating.
        Fixed a bug where passengers could shoot from transports.
        Improved error messages given with bad MiniYaml indentations.
```

Rommel and Zhukov are mine, please stomp their guts and let me know how it compared to Hard AI.

---

### Post by UnknownFearNG on 2012-04-29
Thank you :D I used to play this game over and over again when I was 6 years old. Ahh, nostalgia memories :). And I absolutely love the music!! :P

---

### Post by Avaritia on 2012-04-30
Thanks for letting us know about this, ill have to try and dig out my old discs.

---

### Post by earthpigg on 2012-04-30
> **Avaritia said:**
> Thanks for letting us know about this, ill have to try and dig out my old discs.

You don't need them, Command & Conquer and C&C: Red Alert are both freeware downloads. 

OpenRA automatically downloads the needed parts, and loads them as mods.

---

### Post by synaptix on 2012-04-30
Oh my...

If I could give rep, you'd get some right now.

(Love the C&C series)

---

### Post by Kodeine on 2012-05-01
Never even knew this existed. Played red alert so much on the PS1 (never got it for the PC). Thank god you made this thread!

---

### Post by Erik1984 on 2012-05-01
Nice! However I can't seem to join any of the hosted games.

---

### Post by Dngrsone on 2012-05-01
Hrm... I may have to get it myself.

---

### Post by earthpigg on 2012-05-01
> **Euroman said:**
> Nice! However I can't seem to join any of the hosted games.

They're (well, technically "we" as I've made a few contribs) are in the middle of the <1 week period of playtests before pushing a new stable. So I'm guessing lots of those games you are seeing are the playtest version. If you get "playtest 20120502" from the downloads page, your odds of finding a game that you can join may increase. Or you can wait a few days and dload the next stable release.

Hopping on #openra on freenode is also a good place to find a game.

EDIT: a quick note on hosting games. If you host, that means you're implicitly committing to the others *not* to quit the game until the game is over - even if you die in the first 10 min.

---

### Post by Dngrsone on 2012-05-01
Earthpigg, you have 'Sempter Fi' in your signature; is that an unintentional spelling, or are you purposely deviating from the normal 'Semper Fi' which is the short form of *Semper Fidelis* the motto of the US Marine Corps?

---

### Post by earthpigg on 2012-05-01
No, it's a typo that's apparently gone unnoticed until now.

*pushing*.

---

### Post by Dngrsone on 2012-05-01
> **earthpigg said:**
> No, it's a typo that's apparently gone unnoticed until now.

*pushing*.


I suppose this is an indication of how few squids or jarheads frequent these forums.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/rolleyes.gif[/IMG]

---

### Post by earthpigg on 2012-05-02
You might appreciate that the very first code contrib I made to that game was to [make grunts more aggressive]("http://www.youtube.com/watch?v=yWPz796ZEL0").

---

### Post by Erik1984 on 2012-05-02
Just completed a C&C skirmish game (against 1 easy AI but you have to start somewhere :P) Good stuff.

---

### Post by Erik1984 on 2012-05-02
> **earthpigg said:**
> They're (well, technically "we" as I've made a few contribs) are in the middle of the <1 week period of playtests before pushing a new stable. So I'm guessing lots of those games you are seeing are the playtest version. If you get "playtest 20120502" from the downloads page, your odds of finding a game that you can join may increase. Or you can wait a few days and dload the next stable release.

Hopping on #openra on freenode is also a good place to find a game.

EDIT: a quick note on hosting games. If you host, that means you're implicitly committing to the others *not* to quit the game until the game is over - even if you die in the first 10 min.

Thanks. I'll wait and have some fun with battling Easy bots in C&C Skirmish :P

---

### Post by Dngrsone on 2012-05-02
> **earthpigg said:**
> You might appreciate that the very first code contrib I made to that game was to [make grunts more aggressive]("http://www.youtube.com/watch?v=yWPz796ZEL0").

Hahahaha!  My favorite was always the civilian running around in a panic, arms waving in the air, punctuated by the occcasional small-arms fire.

Those grunts *were* pretty passive, though.

When is the next stable release?  Does this come with all the episodes on the original disc?

---

### Post by earthpigg on 2012-05-02
> **Dngrsone said:**
> When is the next stable release?  Does this come with all the episodes on the original disc?

In a few days. 

It contains none of the old single player campaign, though once you re-acquaint yourself with the game you can challenge yourself by doing skirmishes of you vs multiple bots at once and similar.

---

### Post by Dngrsone on 2012-05-02
Hrm... I have the Decade Box set with all the C&C titles prior to 3, but running them under Wine is problematic at best.

---

### Post by earthpigg on 2012-05-03
New release is out today.

---

### Post by beboylips on 2012-05-04
Red Alert 2 would be awesome! That game was so good :)

---

### Post by Erik1984 on 2012-05-04
> **earthpigg said:**
> New release is out today.

Installed :p Played some actual multi player games last night. I totally suck at this game (against human players) but it was fun.

---

### Post by earthpigg on 2012-05-04
> **Euroman said:**
> Installed :p Played some actual multi player games last night. I totally suck at this game (against human players) but it was fun.

Watching replays and learning from them is very helpful. 

The bots are not an effective learning tool for multiplayer; you've kind of just got to suck it up, get destroyed in multiplayer a bunch, use the replays as a learning tool, and do some innovating from there. (early on, the the *whole point* of playing multiplayer is to generate these valuable replays. Don't *avoid* playing against people you know to be better than yourself, *seek them out*.)

One of the first multiplayer games I was in was 3vs7; the 3 won. The value of watching that replay >3 times cannot be overstated. 

But I *still* am not that great.

---

### Post by Erik1984 on 2012-05-05
Good idea. I watched large parts of the replay and it is fun to see the other players build. I noticed that I'm a very passive player compared to the other human players. In a one versus one game I saw my opponent immediately went out exploring the map with a ranger and picking up crates. I also saw him sneaking a spy in my base... never noticed during the actual game. I feel so dumb now :P

---

### Post by Modplanman on 2012-05-06
Already have C&C installed via the first decade DVD. Where do I copy the files for OpenRA to find them? Don't want to re-download the games when I already have them on disc...

---

### Post by earthpigg on 2012-05-06
> **Modplanman said:**
> Where do I copy the files for OpenRA to find them? Don't want to re-download the games when I already have them on disc...

When you start OpenRA for the first time, it loads the default Red Alert mod and asks you if you want to download or insert game disc. If you select download, it only downloads those bits of the full game you need and not the entire thing.

When you click 'mods' and select CnC for the first time, it gives you the same choice.

---


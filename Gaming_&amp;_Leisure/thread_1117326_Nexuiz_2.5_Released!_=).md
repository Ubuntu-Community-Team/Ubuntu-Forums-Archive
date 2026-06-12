---
title: "Nexuiz 2.5 Released! =)"
date: 2009-04-05
forum: Gaming &amp; Leisure
---

### Post by wingnux on 2009-04-05
From: [http://sourceforge.net/project/shownotes.php?release_id=672474&group_id=81584](http://sourceforge.net/project/shownotes.php?release_id=672474&group_id=81584)


> Release Name: Nexuiz 2.5

Notes:
Almost a year of hard work, 3000 single changes, new developers and players, a few tourneys and lots of matches have passed since the last release.
Today the Alientrap team is proud to bring you a new and improved Nexuiz! Still trying to achieve this fine balance between fun and a challenge, you will notice lots of small additions that will make playing even more fun.
Some larger changes like the new guns and particle effects will make you want to dive into the great and friendly Nexuiz community, while the large additions including the race game mode, some new maps and improved netcode will take away lots of hours of your free time.
Do you dare to take a look and see for yourself what a totally free and open source game can be?

New features include:

    * Completely redone HUD and user adjustable scoreboard
    * Totally rewritten Client/Server communication to cut the bandwidth usage in half
    * New gamemode "Race". Try to get from start to end of a level as fast as possible. Available as free-for-all and team variant. Further allows to play with or without a qualification period.
    * Added several new weapons (on-hand Grappling Hook, Port-O-Launch, T.A.G. Seeker, Heavy Laser Assault Cannon, Rifle)
    * Map editor NetRadiant included
    * Improved all effects for eye candy and tweakability
    * All maps recompiled with external lightmaps which allow for much crisper shadows
    * Added maps desertfactory (DM, TDM, MinstaGib), racetrack (Race) and made aggressor support Key Hunt
    * New player sounds, announcer sounds/voices, textures, crosshairs, weapon models, effects and menu skins
    * Added support for video capture to OggTheora
    * Integrated the Havoc mod into the menu! Havoc servers use quite different physics and weapons, give it a try!
    * Fixed a crash with ATI drivers on shutdown or vid_restart
    * Fixed several problems with lagging gameplay/crashes/wrong display of effects
    * Improved bots (teamworking, bunnyhopping, swimming, better way finding, support for ladders, less CPU usage, faster map loading)
    * Better visual display of carried items (Strength, Shield, flags and keys)
    * Better parental guidance support with cl_gentle and cl_nogibs
    * Lots of tourney-related features (timeout/in, spectator-slots, allready, warmup mode, lockteams, unlockteams, movetoteam_red/blue/..., nospectators, records, cointoss)
    * Added some effects customization options like cl_casings, cl_weaponpriority
    * Many more map entities allowing for more dynamic maps
    * Restructured and improved menu: demos menu and multiple campaigns are back, also added an advanced menu containing ALL settings of the game 

For a more complete list of changes see: [https://sourceforge.net/project/shownotes.php?release_id=672474&group_id=81584](https://sourceforge.net/project/shownotes.php?release_id=672474&group_id=81584)

As usual, you can download the newest release from our download page.
To see the changes in action check out our new video on the front page.
If you are providing a mirror of the release, please notify us so we can add it to the official mirror list. For any comments, suggestions or questions, please refer to our forum or the FAQ.

Because of many major changes there is NO PATCH available.
To make sure nothing breaks, you should use a new directory to unzip Nexuiz 2.5!

If you use 2.5 and see a server with no gametype it's an 2.4.2 server, don't play on those. :)

Alientrap is also currently looking for new coders, modellers, mappers and people experienced with creating sound effects.
If you feel like helping improve Nexuiz or Zymotic please contact the team via forum or IRC. 


Download link: [http://sourceforge.net/project/showfiles.php?group_id=81584](http://sourceforge.net/project/showfiles.php?group_id=81584)

---

### Post by Polygon on 2009-04-05
as i posted in another thread about this:

opinion of game:

some maps look terrible

the UI is also terrible. Flashing colors on all sides and the fact that Every message has to have at least two colors in it just makes it an eyesore

the game does not tell you what weapon you were killed with

i actually was lagging in a few parts (with my nvidia 9800 gtx? um.....)

the 'hook' is stupid, i played a few maps where the games lasted less then 2 minutes because the veterans just hooked all around the map and got 7 captures.

i ended up with like -26 points one round, either because it was subtracting points from me every time i die, or someone suggested i lost the flag a lot...either way, its either buggy/bad design. No game should punish you for dying or dying while having the flag.

on ctf maps, its hard to tell what team your on. I guess you have to look at the weapons, but some of them don't have much color on them, so its hard to see if its red / blue

I lagged out and i was just stuck at the console and i could not rejoin the server, im not sure what was happening there

all in all, its just another generic deathmatch clone , with the same weapons every other quake/unreal/deathmatch game or clone has, and provides nothing new or interesting, besides that stupid hook. Just becuase a game is open source does not automatically make it a good game....sorry =/

---

### Post by Chemical Imbalance on 2009-04-05
> **wingnux said:**
> From: [http://sourceforge.net/project/shownotes.php?release_id=672474&group_id=81584](http://sourceforge.net/project/shownotes.php?release_id=672474&group_id=81584)





Download link: [http://sourceforge.net/project/showfiles.php?group_id=81584](http://sourceforge.net/project/showfiles.php?group_id=81584)

Thanks for the notice!  Upgrading my current install now...

---

### Post by Melcar on 2009-04-05
A very good update.  Most "2.5" servers have horrible lag mostly because they are actually using a SVN snapshot and not the final release... at least that's what some of the guys were babbling about during a match.  Still, the networking issues are apparent (pings are insanely high for me now), and taking into consideration that online play easily eats up 20fps of what you would normally get playing locally, you end up with laggy gameplay some of the times; and if you're playing on a custom map (which are often poorly thrown together)  the lags are even worse.  There is also the fact that not everyone is using 2.5 yet, which I'm told also causes problems.

---

### Post by Polygon on 2009-04-05
i dont understand the rationale of even LETTING different versions of the client and the server play together...almost every single commercial game out there will not let you play on a server that has a different version then your client.... i assume it would just cause problems

---

### Post by wingnux on 2009-04-06
> **Polygon said:**
> 

i actually was lagging in a few parts (with my nvidia 9800 gtx? um.....)



What is your nvidia driver version? I'm running 185.13 (beta) here and I didn't experience any lag playing on 1152x864 with ultimate effects settings in-game and hdr on. 
My card is a GF 8600GS 384RAM btw.

---

### Post by Polygon on 2009-04-06
im running the newest one, 185.13, and it ran fine for the most part, but in high chaos areas like a flag room , sometimes people were like warping around and stuff and my shots took a second to actually appear

---

### Post by Inkpot on 2009-04-06
I'm having an issue where all sound will inadvertently shut off in the middle of a game and stay that way until I restart. The sound works fine up until that point, though.

Also, as FPS's aren't my main gaming fare - is there any way to slow everything down in botmatches? The movement speed seems insanely fast to me.




Inkpot

---

### Post by Melcar on 2009-04-06
Speed is the main thing in the game.  I don't know why you would want to slow it down.  Anyway, if you tag vsync. and the "wait for GPU to finish each frame" your game will slow down.

---

### Post by jdunn on 2009-04-06
> **Inkpot said:**
> I'm having an issue where all sound will inadvertently shut off in the middle of a game and stay that way until I restart. The sound works fine up until that point, though.
Inkpot

Same thing for me.  From the Nexuiz forums I found two options that were supposed to resolve the sound issue on Ubuntu 8.10.  Both options didn't work for me.  

Option 1:  run the sdl version instead of the glx version of the game.  This turned off both the sound and mouse support for me.

Option 2:  run the glx version with 'pasuspender'.  This supposedly suspends pulse audio processes until the game ends...However, I'd still lose sound in the middle of the game.

Someone in game suggested I use 'pkill pulseaudio'.  I believe this kills the pulseaudio daemon (but still gets reloaded if you reboot).  Anyway, I tried this and it seems to resolve the sound issue in Nexuiz.

---

### Post by Inkpot on 2009-04-06
> **Melcar said:**
> Speed is the main thing in the game.  I don't know why you would want to slow it down.  Anyway, if you tag vsync. and the "wait for GPU to finish each frame" your game will slow down.

As I said in my original post, FPS games aren't my usual fare. I find Open Arena much more enjoyable than Nexuiz simply because everyone is running at a realistic speed instead of zipping around at Mach 10. Speed isn't a 'feature' to me....it's a deterrant. Having said that, I'm liking everything else about Nexuiz. They've clearly bumped things up a notch with this latest release.


Inkpot

---

### Post by Vadi on 2009-04-06
Ubuntu .debs: [http://www.getdeb.net/app/Nexuiz](http://www.getdeb.net/app/Nexuiz)

---

### Post by Polygon on 2009-04-06
> **jdunn said:**
> Same thing for me.  From the Nexuiz forums I found two options that were supposed to resolve the sound issue on Ubuntu 8.10.  Both options didn't work for me.  

Option 1:  run the sdl version instead of the glx version of the game.  This turned off both the sound and mouse support for me.

Option 2:  run the glx version with 'pasuspender'.  This supposedly suspends pulse audio processes until the game ends...However, I'd still lose sound in the middle of the game.

Someone in game suggested I use 'pkill pulseaudio'.  I haven't tried this yet.

the game runs fine for me with pulseaudio, i highly doubt that is the problem.

---

### Post by aceplayer97 on 2009-04-06
> **Polygon said:**
> as i posted in another thread about this:

opinion of game:

some maps look terrible

the UI is also terrible. Flashing colors on all sides and the fact that Every message has to have at least two colors in it just makes it an eyesore

the game does not tell you what weapon you were killed with

i actually was lagging in a few parts (with my nvidia 9800 gtx? um.....)

the 'hook' is stupid, i played a few maps where the games lasted less then 2 minutes because the veterans just hooked all around the map and got 7 captures.

i ended up with like -26 points one round, either because it was subtracting points from me every time i die, or someone suggested i lost the flag a lot...either way, its either buggy/bad design. No game should punish you for dying or dying while having the flag.

on ctf maps, its hard to tell what team your on. I guess you have to look at the weapons, but some of them don't have much color on them, so its hard to see if its red / blue

I lagged out and i was just stuck at the console and i could not rejoin the server, im not sure what was happening there
[B]
all in all, its just another generic deathmatch clone , with the same weapons every other quake/unreal/deathmatch game or clone has, and provides nothing new or interesting, besides that stupid hook. Just becuase a game is open source does not automatically make it a good game....sorry =/[/B]

This is the exact way I feel about this game. People should just play Unreal instead

---

### Post by jdunn on 2009-04-06
> **Polygon said:**
> the game runs fine for me with pulseaudio, i highly doubt that is the problem.

See my modified post.  The sound issue in Nexuiz goes away if I kill the pulseaudio daemon with 'pkill pulseaudio'.  I believe pulseaudio is part of the problem.  I have seen many forum threads (both here and on the Nexuiz forums, Savage2 forums, etc) regarding problems with games and pulseaudio.  Having said that, I think pulseaudio is here to stay...It provides many great features but being a new addition to linux, the kinks have to be worked out of it.  Hopefully, future versions of PA will be a little less CPU intensive, too.

---

### Post by wingnux on 2009-04-06
> **aceplayer97 said:**
> This is the exact way I feel about this game. People should just play Unreal instead


Nexuiz is free, Unreal isn't.

---

### Post by SOULRiDER on 2009-04-06
I tried nexuiz a LONG time ago, I should chekc out this new version!

---

### Post by Polygon on 2009-04-09
ok i played it some more. I am still confused about some of the weapons, and why they don't do as much damage as they shoudl....but overall its pretty fun

except there were three ctf servers

one had hook (which makes the game terrible)
one had JETPACKS, which basically meant that you could just freaking rocket across the map in record time, making it almost impossible to hit or to catch up.
and one had 8 players

seriously, why do they even think to include stupid stuff like these hooks and jetpacks. Even the unreal translocator isn't this annoying.

---

### Post by detrate on 2009-04-09
You can learn more about the weapons here: [http://ouns.nexuizninjaz.com/item:weapons](http://ouns.nexuizninjaz.com/item:weapons)

But also in your Docs folder


Here is the official high def version of the front page video: [http://www.youtube.com/watch?v=me3KeOj4MHY](http://www.youtube.com/watch?v=me3KeOj4MHY)


I know some people above have called it a generic this or that clone but it's really much much more.  The things you don't see like the community of individuals who have brought a **Quake 1 engine** (forked to [Darkplaces](http://icculus.org/twilight/darkplaces/)) up to the level of a ~Quake 3 (with better effect capabilities) engine, going through similar trials and tribulations of a game development company.

There's just been a recent separation in client and server code which allows for such things as the new Client-side QuakeC menu, which if you played 2.4 you'd know is a _vast_ improvement.  This also reduces bandwidth and increases effect possibilities amongst other things.

To call it unoriginal is a little harsh.  Sure, you have your mix of generic weapons but we've just added 5 new ones that aren't so common.  Your grappling hook with gravity bomb, a porto-gun inspired by the game portal (this one works differently :-P), Heavy Laser Assault Cannon, camping rifle (the first reloaded gun in the game) and the Tag Seeker.

Now with 24 available weapon slots, who knows what else _anyone_ can contribute.


We also have amazing new sounds by [Tenshihan](http://www.nexuizninjaz.com/forum/member.php?action=profile&uid=210), who's really started to bring the game to live.


Some of the maps are dated but there are still some amazing new ones, like Racetrack by morphed and Desert Factory by sev.

The majority of the player models are bad, the problem with them is they are .zym, which lacks a lot of documentation / software to create.  There have been a lot of efforts to patch this together, and a few modelers (like ai, the guy that made the ammo pickups, the flag models, portals for the porto gun and DOM points) that are starting to create new models.  Finding skilled modelers in open-source isn't always easy.


A note about the sound issue, I have "pkill pulseaudio" in my startup programs.   Everything's been hunky-dory since.



The hook and the jetpack are modifiers set by server admins.  The jetpack was a last minute addition that some people love, other people hate.  I do not run any servers with jetpack (minus a part in a race map :-P).

I do however run the CTF Veteran's hook server.  If you ended up with -26 on a server with hook it's because you spent too much time picking up and dropping the flag instead of working together with your team to capture the flag.


If you have any questions, I'll do my best to answer them or advise you.

We also offer classes, if you need help you can find me, [-z-] on irc.quakenet.org and I will be more than happy to help you out in the dojo.



Happy fragging :)

---

### Post by Polygon on 2009-04-10
i still don't like the hook or the jetpack. You can't exactly kill someone when they are just spiderman'ing through the level or flying in the air. i can't count how many times today i was chasing someone with the flag and they just jetpacked up into the air and basically landed straight into their flag capture area. Gee thats fun. And its even worse becuase there are like 3 ctf servers running at any one time...one has hook....the other has jetpack...and the other is a small server (i think like 10 or 12 man)....so if i want a full game i have to deal with the jetpack / hook

Also, losing points for dropping the flag is stupid in my opinion. I was playing a very small level (i have no idea what it was called, but it had a little catwalk above that lead to a tunnel), but the area with the flag was cramped to begin with, combined with the spawn points for the team is RIGHT next to the flag, so if anyone takes the flag, you are almost always going to get fragged instantly, unless you are lucky. 

I spend a lot of time playing ctf on many different games, i'm not a noob at it, and this is the first game that i have seen give you a point reduction for dropping the flag, cause in some maps, you can't HELP but die...and sometimes your death leads to someone else on your team picking up the flag and running....etc

also, another thing. This is a problem with a lot of games, including anything unreal/quake/deathmatchy......why are weapons bound to number keys higher then 5? i cannot physically hit these buttons accurately. So having weapons bound to 6,7,8,9 is just annoying, as it makes me resort to the scroll wheel and then in a firefight i can never get the weapon i want and i always die

solution? do what half life does, bound several weapons to one number and pressing that number repeatedly scrolls down the list. Like the combine pistol is the first slot in 2, the alyx pistol (in a mod i play) is slot number 2, and the magnum is in slot 3. I can hit 2 three times easier then looking down on my keyboard and seeing where '9' is so i can switch to that weapon, or scrolling through my weapons.

and another thing, the weapons seriously need to be color coded or something, now with 15 weapons to worry about, i have no idea what weapons i have and what i don't have. Lots of games do this, quake is a great example. Rocket launcher = red, lightning gun = white, machine gun = yellow....etc. And same goes towards the ammo...i have no idea what type of ammo i am picking up...but open arena and quake live fix this in a great way, they have an option to remove the 'models' and just have a color coded box that has the weapon icon on it, so you can quickly identify that this is rocket ammo cause its red, and this is machine gun ammo because its yellow..etc

---

### Post by detrate on 2009-04-10
Okay, so you're both upset that Nexuiz is like other games but not like other games...

You're trying to play it like other games but it has it's differences that you need to learn if you want to excel.  Sure, capturing the flag is fun for you... but if you don't quite understand the movement techniques in Nexuiz and you pick up the flag 4 times and die every time with it, I think it's fair that you lose points because you're putting YOUR TEAM at a disadvantage.  And CTF is a TEAM game.

It takes getting used to... the Veterans server is harsher... as when you pickup the flag, you lose points... but you have a hook... which takes some time to learn.  I know the concept seems easy but it's really an advanced type of game play.

CTF light doesn't punish you for pickups but it does for drops, and even heavier for a suicide drop.


As for keybinds, here's what I use
[http://toolz.nexuizninjaz.com/keybinds](http://toolz.nexuizninjaz.com/keybinds)

I offer a package, "the ninja pack" which has a bunch of advanced configurations.  To download it, [right click save as this link](http://github.com/z/nn_ninja_pack/raw/be50312046bf72aae406230f8a227ae13e1c1f15/nn_ninja_pack_022509.pk3) and put it in your ~/.nexuiz/data directory.

.pk3 is just a renamed zip file, so you can open it as an archive and read the documentation.  Optionally, there is documentation ready to read online [here](http://github.com/z/nn_ninja_pack/blob/be50312046bf72aae406230f8a227ae13e1c1f15/NINJAPACK_README)


I agree with you on the weapon colorization bit... I actually designed a new hud with weapons that are colorized that victim was working on making a reality now that we have better CSQC support... but I haven't heard/seen much of it lately.

[[IMG]http://pics.nexuizninjaz.com/images/pmu9m35ax5vafzjmc1o5_thumb.png[/IMG]](http://pics.nexuizninjaz.com/viewer.php?file=pmu9m35ax5vafzjmc1o5.png)


Again, I'd like to extend my offer to help you learn more about Nexuiz live if you'd like to learn some tips and tricks to help you out.  Also, [watching other players](http://www.youtube.com/user/nexuizninjaz) is always a good start.

---

### Post by Polygon on 2009-04-10
EDIT: before i start, that screenshot, if thats a mockup hud, please get that included. The hud for CTF is terrible at the moment, for many reasons, but that mockup or whatever you posted pretty much fixed all my complaints

No. nexiuz is like other games. It offers nothing new gameplay wise, maybe a few  new modes...maps..weapons..but it still feels like i have played this game so many times before. Hl2 deathmatch, quake live, all the endless quake 3 mods that are for linux. you are claiming that the only  'defining' parts of this game is a hook and or a jetpack, and a weird scoring scheme, which honestly is nothing to brag about..... but at least i have fun playing it, so who cares if its unoriginal, right? =P

And i still don't know how picking up the flag and dying with it is considered bad teamwork. The point of ctf is to get their flag to the enemy base right? everyone in the game has big guns that kill people right? you are going to DIE with the flag a lot even if you have your team helping you. 

I played a mod for half life 2 called hl2ctf ([www.hl2ctf.com](www.hl2ctf.com)) in that game, you can use the gravity gun to literally punt the flag far distances. In nexuiz, you can't do that. Once you have the flag, you carry it unless you cap or get killed with it. So what is so wrong about running with the flag and getting killed with it, leaving the flag open to be picked up by other teammates and taken further to your base? It seems to me that losing points for dying with the flag is actually hurting teamwork, as nexiuz is assuming that you MUST CAPTURE THE FLAG WITHOUT DYING....well guess what, in ctf that is a very unrealistic assertion. Not everyone is 'super pro' at video games, but if a noob can get the flag out of the base and die, but some other team mate picks it up where he died, then thats teamwork.

and the hook. i already explained why i hate this, but you don't seem to understand. I played on your server, in 2 seperate maps, the game was over before i even downloaded the map, cause some 'pro' just hooked around the map, stole the flag 7 times and capped it, all within a minute. HOW IS THIS FUN?  In another map, someone takes the flag and instantly hooks at like 100 miles per hour, and before i even realize what happens, he caps. How the hell am i supposed to stop this? the closest thing to this is the Unreal translocator, and that is a: slow and B: doesn't go that far, and it doesn't lead to instant caps where you can't do anything to stop them.

Not to mention this just promotes 'rambos', and takes away from teamwork. if you have a hook that makes you move super fast, then you just run into the base alone, take the flag, and spiderman out of there. No teamwork is necessary. But if you don't have that hook, then you have to actually run out of the base, with lots of angry people from the other team shooting at you. 

I'm not saying i know everything, its just i have played many of the more 'successful' commercial games, and I know how ctf is played, and what makes it fun, and what makes it unfun. (at least for me) Things like hooks, jetpacks, and losing points unnecessarily make it unfun, but apparently those are what define nexuiz. I would love to have fun playing this game, but like i said. only 2 ctf servers, and one has jetpack, one has hook. I just want to play a normal ctf game, where people arn't flying all over the place, cause when i was playing last night, (and people wern't using the stupid jetpack), it was great fun.

---

### Post by Bios Element on 2009-04-10
Polygon, This is not the place to post your flame rant about horrid the game is. If you don't like it, don't play it and go away. If you have actual suggestions, make a post on the nexuiz forums.

---

### Post by Vadi on 2009-04-10
Seconded. Thanks

---

### Post by detrate on 2009-04-10
I'm not sure it's really worth countering your "arguments" because it's clear you didn't listen to what I said in my previous posts.  You're trying to play the game your way but you need to learn to ride a bike before hopping on a motorcycle.

Nexuiz is like fast paced chess.


However, I'm not so sure you're as into this style of play as you might think and for this reason, there exists another gamemode called 'Havoc', with different physics and weapon settings.


[QUOTE=Polygon]And i still don't know how picking up the flag and dying with it is considered bad teamwork. The point of ctf is to get their flag to the enemy base right? everyone in the game has big guns that kill people right? you are going to DIE with the flag a lot even if you have your team helping you.[/quote]

If you have 12 minutes in a match and you waste 6 of those minutes dying with the flag, you've just screwed over your teammates chances of capturing the flag for those 6 minutes.  Your selfishness has stopped someone (probably faster than yourself) from capturing the flag when you could be earning more points for yourself and the team as backup.  Not everyone is the quarterback.


> I played a mod for half life 2 called hl2ctf ([www.hl2ctf.com](www.hl2ctf.com)) in that game, you can use the gravity gun to literally punt the flag far distances. In nexuiz, you can't do that. Once you have the flag, you carry it unless you cap or get killed with it. So what is so wrong about running with the flag and getting killed with it, leaving the flag open to be picked up by other teammates and taken further to your base? It seems to me that losing points for dying with the flag is actually hurting teamwork, as nexiuz is assuming that you MUST CAPTURE THE FLAG WITHOUT DYING....well guess what, in ctf that is a very unrealistic assertion. Not everyone is 'super pro' at video games, but if a noob can get the flag out of the base and die, but some other team mate picks it up where he died, then thats teamwork.

Before 2.5, players would sit on the flag for a respawn in the enemy base, die short their after and repeat.  How is this fun for anyone?

> and the hook. i already explained why i hate this, but you don't seem to understand. I played on your server, in 2 seperate maps, the game was over before i even downloaded the map, cause some 'pro' just hooked around the map, stole the flag 7 times and capped it, all within a minute. HOW IS THIS FUN?  In another map, someone takes the flag and instantly hooks at like 100 miles per hour, and before i even realize what happens, he caps. How the hell am i supposed to stop this? the closest thing to this is the Unreal translocator, and that is a: slow and B: doesn't go that far, and it doesn't lead to instant caps where you can't do anything to stop them.

The hook server is titled "veterans" for a reason.  I told you it's an advanced gaming style, you're trying to go down a black diamond without learning the bunny slope.  It's no wonder you hate it because your brain doesn't comprehend the information as quickly as some of the other players who are able to finish the match in < 1 minute.  I don't mean that as an insult either.  Nexuiz is an extremely fast paced game and if you were to take the time to watch some of the videos I posted, you would begin to learn how to edit out unnessescary information that's slowing you down.

> I'm not saying i know everything, its just i have played many of the more 'successful' commercial games, and I know how ctf is played, and what makes it fun, and what makes it unfun. (at least for me)




I offered you very detailed information on how to improve your skills in the game.  **Nexuiz _is_ different**, you refusing to believe this will make you dislike it even more.  There are video tutorials, advanced keybinds and I've even offered to give you a 1on1 class live.

You have chosen to ignore everything I wrote except the ~pretty picture~ and say, "I want it nao!"


I find that disrespectful and I hope maybe you read this post and go back and watch some of those videos.

You can't expect to be a pro in something you've been playing for a day.  Heck, I've been playing for 2 years and I'm still no pro :-P



As the posters above me said, if you want to flame the game with your infinite commercial game, FPS wisdom, please do so on the [Alientrap forums](http://alientrap.org/forum).

---

### Post by CharmyBee on 2009-04-10
> **Inkpot said:**
> 
Also, as FPS's aren't my main gaming fare - is there any way to slow everything down in botmatches?

there is a 'slowmo' console variable I think, that in local games it slows down the game

---

### Post by Chemical Imbalance on 2009-04-10
Detrate, Nexuiz is an awesome game, keep it up!  Dare I say it is the most polished and creative free opensource game?

---

### Post by Bios Element on 2009-04-10
> **Chemical Imbalance said:**
> Detrate, Nexuiz is an awesome game, keep it up!  Dare I say it is the most polished and creative free opensource game?

It's the most polished and creative free opensource 3D game. I can think of a handful (Not off the top of my head though) of opensource 2D games that have more polish in the general UI. But Nexuiz is totally one of the best.

---

### Post by detrate on 2009-04-10
> **Bios Element said:**
> It's the most polished and creative free opensource 3D game. I can think of a handful (Not off the top of my head though) of opensource 2D games that have more polish in the general UI. But Nexuiz is totally one of the best.

Two things about this / the above comment.

1) I can only take a little credit, there are many contributors involved in the development of Nexuiz, ones that have been involved years before I was.  Rudolph "divVerent" Polzer is by far and large one of the biggest more productive, helpful, selfless contributors the game has seen.  He's basically written most of the QuakeC as well as many helpful tools around the game, such as the recent port of GtkRadiant to [NetRadiant](http://icculus.org/netradiant/), as well as many wonder perl scripts I use every day to manage my servers.

There are many great modelers, mappers and hobbyists that submit patches as well as friendly players who form this unique community.


My role has mainly been to give rebrand and promote the game through various redesigns of websites, creation of web tools, running of game servers, building software to control them, share statistics, and create skins/themes for AT/Nexuiz.


2) The UI had a recent overhaul, the old menu was horrible, divVerent recoded it from scratch to make it more scalable.  At lot of options were dropped in 2.4 but they are back in AND EXTENDED in 2.5.  The addition of the in game cvar/cmd search that mimic's my original [Nexuiz cvar search tool](http://toolz.nexuizninjaz.com/cvar/) is among the examples.

Something important to note about the 2d games with more polished UI interfaces, is they are probably working with a more powerful theming engine.  As I said above this was coded from scratch, in QuakeC, which is a lot more limited than C or C++.  There are a lot of interesting challenges current game engines not longer deal will but we are still working to overcome... but that's part of the fun.

A lot of knowledge is still being obtained, understood and passed around and this system will continue to grow and get stronger.  There have been so many improvements in the UI, I can't even begin to explain.  If you have a specific problem with it, please let us know so we can try and address the issue at hand.



I'm glad you guys enjoy the game.  If you have any questions, let me know :).

---

### Post by Polygon on 2009-04-11
i did not ignore your post, i posted my reasonings on why i feel certain aspects of this game are handled wrong, based on what you said,  but since 4+ people just told me i'm stupid, i'm disrespectful and i'm just ranting on a soapbox, i'll stop.

---

### Post by detrate on 2009-04-12
If that's all you got out of this the thread, that's a shame.  I spent a lot of time replying to your complaints but you kept telling me how you want the game _to_be_ instead of seeing how _it_is_.  I offered advice and many resources that I don't feel you acknowledged.

No one said you're stupid.

---

### Post by KhaaL on 2009-04-12
I really think that its unjustified to flame Polygon for his opinions which he laid out clearly and without being like a drama-queen. You should look at his argument and see they are valid in some points. The hook, while the best hook implementation i've seen in a game, needs balancing. did you know that you can hook an opponent and the hook won't let go? this opens up for a world of griefing where players can be pushed into a place and get stuck, without the ability to get loose.

Still, 2.5 is the first version of nexuiz that made me actually play *and* enjoy it. It's a great game and if anyone wants to play vs me tonight, PM me and let me know ;-) (my timezone is gmt +1).

---

### Post by detrate on 2009-04-12
Again this is an issue with server admin's setting.  If you're going to play on a noob server, expect noob settings, which simple entails unlimited everything and tons of features that don't necessarily go together.

There are actually 2 (basic) limitations available in the hook.

1) Ammo for the hook (using cells)
2) Amount of time the hook can be hooked

There are [extended tweaks](http://toolz.nexuizninjaz.com/cvar/index.php?search=hook) available as well.


Also note that there are 2 different types of hook in the game... there is the hook weapon and the off hand hook.

Off hand hook is a classic EXTENDED gametype.  It's played a different way and usually for more experienced players because it's throws the game into hyper-speed.

---

### Post by stoopnagle on 2009-04-12
nexuiz is a lot of fun.  super fast paced, good graphics and excellent controls.  check it out if you like fps games.

---


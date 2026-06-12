---
title: "Strange Sauerbraten-question"
date: 2008-09-25
forum: Gaming &amp; Leisure
---

### Post by ZarathustraDK on 2008-09-25
Egged on by another Sauerbraten-thread I was wondering just how big (xyz) is it possible to make levels/worlds in Sauerbraten?

Would it be possible to, for instance, recreate the Kalimdor-continent from WoW to scale in a Sauerbraten-map?

I have this strange picture of hundreds/thousands of players flying around sculpting the WoW-world fram scratch. That'd be pretty neat. :lolflag:

Think it could be done with enough man-power and server-power? That'd be quite a community-effort hehe...

---

### Post by ZarathustraDK on 2008-09-25
Argh... can't get it out of my head now. The idea just seems so enticing.

I mean in theory, wouldn't that be the most optimal way to harness the power of the community in creating games? The big problem, as I see it, is that there are a throng of people who really want to help out in the game-arena, but doesn't possess the necessary coding-skills to do so. If something like Sauerbraten could handle huge maps and lots of users editing it, then you could unleash a throng of "newbs" to do the basic geometry and entity placement while coders et al do their specialty.

Given Sauerbratens modus operandi visitors and other people interested could visit the "construction-site" garnering more attention and publicity.

Kinda like Second Life I guess, but with a purpose.

That could be such a cool project. :popcorn:

---

### Post by Zyphrexi on 2008-09-26
yeah but what about tk'ers? (teamkillers)

you gotta know there's gonna be some jerks who just start messin around with junk, justa piss ya off.

that'd be a  pain. here I am working on some windmill, and some jerk comes along and destroys it. The digital equivalent of kindergarten bullies.

EDIT: btw zara, just so you know, don't double post, just edit your posts. I agree that making easy-to-use, accessible tools would undoubtedly boost game development. For map-making though, handing out parts to willing team members (or not) based on criteria is probably good enough. Just because the area in WoW looks like it's one big area, doesn't mean it necessarily is. Also check out the eisenstern project, though I think it's sort of been forked.

---

### Post by ZarathustraDK on 2008-09-26
Well of course it would need some kind of undo-function. Also I was thinking about some kind of tiered editing-permissions and zone/area-assignment for preventing gross vandalism.

It's given, of course, that Sauerbraten doesn't contain those elements as it is now. But that's a matter implementing said fuctions, not impossible. I'm more interested in if it's possible computation-wise to do something like that. That is, having a lot (thousands) of people working on the same size 16 (or bigger) cube simultaneously. And would a player be able to run such a big map at all (it's probably necessary to limit view-distance, but still)?

---

### Post by Zyphrexi on 2008-09-26
I think platinum arts sandbox (built off of sauer) is what you're thinking about. If you haven't taken a look at it, try it out. It's been a while since I've used it, at the time it seemed like sauerbraten minus heavy metal music and guns.

I don't know how it looks now. I'd think it be cool to have something like gmod, a game like sauerbraten but you had tools/weapons that allowed you to add/remove stuff without switching to an edit mode. 

I kind of imagine myself building stairs leading to a platform in the sky, or something along those lines.

EDIT: the platinum arts website is really busy and confusing. The webpage could really use an overhaul. I managed to find the link to a download. here.

[http://platinumarts.net/ccount/click.php?id=37](http://platinumarts.net/ccount/click.php?id=37)

let me know if that works.

---

### Post by Holonet on 2008-09-28
> **ZarathustraDK said:**
> I'm more interested in if it's possible computation-wise to do something like that. That is, having a lot (thousands) of people working on the same size 16 (or bigger) cube simultaneously. And would a player be able to run such a big map at all (it's probably necessary to limit view-distance, but still)?

I have crap for programming knowledge, so pardon this if it's obvious to some of you, but I've always wondered how this sort of multiplayer thing works.  It would make sense to me that if the graphics (maps, models, objects, etc...) were downloaded prior to someone joining the game, then the positions of other players and such could be conveyed over the network by simple x, y, z coordinates in a grid, letting the computer at home do the rest...  point being, that if the events in the game like position, damage, etc... are limited to sets of numbers (data files), then there wouldn't be a lot to clog up and cause net lag.  I'm confident I'm understating or misunderstanding something about it though...but I'm curious--if anyone could clear me up on this.

---

### Post by ZarathustraDK on 2008-09-28
You pretty much nailed it. All ressources in a MMORPG are located client-side so all the server has to do is send calls for animations, objects and the likes. There's no easy way around playerpositioning though, so that's a steady stream of information that has to be relayed from the server to any observers of the player, more observers = more pressure on the server. The usual way to get around this is to limit the distance which a player can see in-game (which is also good for the players fps if there's a lot of graphic-intensive stuff in the world), thus reducing the amount of players able to see each other. For the same reason realtime-physics (like in Half-Life 2) are a no-no in MMORPGS, as a single particle working this way will have to be positioned by the server in order to make it look the same everywhere. That's pretty nasty given a good explosion can contain hundreds of particles, it'd be the same as tracking a hundred non-observing players. And since explosions seldom come alone...well, you get the point.

Good example: When the gates of Ahn'Qiraj opened in World of Warcraft, almost every player on the server went down there to see it. I think that I heard somewhere that a full WoW-server has around 50.000 players, so let's say 25.000 of them went to Ahn'Qiraj, that's 25.000 players observing each other = 25.000^2 = 625000000 different information streams on player-tracking that the server has to relay = dead server.

---

### Post by Holonet on 2008-09-29
Cool, thanks for the explanation.  I guess it's true, in some cases, the sheer number of players is reason enough for lag.  I was essentially thinking that for computers, simply relaying streams of data would be a walk in the park, as opposed to *calculating* anything.  Then again, the stuff connecting the servers and computers is probably the weakest link of that equation.

---


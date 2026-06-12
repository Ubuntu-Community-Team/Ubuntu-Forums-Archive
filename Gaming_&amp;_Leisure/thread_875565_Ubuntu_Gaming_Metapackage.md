---
title: "Ubuntu Gaming Metapackage"
date: 2008-07-31
forum: Gaming &amp; Leisure
---

### Post by Oponium on 2008-07-31
Hi all.

Would anyone be interested in a metapackage (an installation package that tells the package management system what packages to install) for Ubuntu 8.04, specialized for gamers?

I was thinking something along the lines of Openbox, a nice looking default theme, and a bunch of games.

Suggestions?

---

### Post by eragon100 on 2008-07-31
great idea!

Nexuiz

Openarena

tremulous

Battle for Wesnoth

sauerbraten and warsow, from getdeb.net (Repo version outdated)

Vegastrike

That would be nice for starters, right?

---

### Post by jimi_hendrix on 2008-07-31
> **eragon100 said:**
> great idea!

Nexuiz

Openarena

tremulous

Battle for Wesnoth

sauerbraten and warsow, from getdeb.net (Repo version outdated)

Vegastrike

That would be nice for starters, right?


that looks nice but i would balance it a bit more with another strategy if there are any a rpg (mmo or offline doesnt matter) and finally a sports game because right now its leaning twards shooter

---

### Post by detrate on 2008-07-31
I am well in favor of this :)

---

### Post by Frem on 2008-07-31
What's the point? Games generally take a while to download, so I'd rather pick and choose. IMHO, more would be accomplished by having a way to filter the "real" games out of all the board, card, and rubux cube games. Having screenshots and user ratings would also do a lot more to help.

Because honestly, the popularity rating isn't very helpful. All the default games get high marks because everyone has them installed (even though they aren't particularly exciting), and wesnoth has one star.

---

### Post by Oldsoldier2003 on 2008-07-31
> **Frem said:**
> What's the point? Games generally take a while to download, so I'd rather pick and choose. IMHO, more would be accomplished by having a way to filter the "real" games out of all the board, card, and rubux cube games. Having screenshots and user ratings would also do a lot more to help.

Because honestly, the popularity rating isn't very helpful. All the default games get high marks because everyone has them installed (even though they aren't particularly exciting), and wesnoth has one star.
+1
Although I applaud the intent of the OP, I'm with you here.

---

### Post by compiledkernel on 2008-07-31
2 cents here. 

Metapackaging a whole build for gaming purposes would create a massive large download schema. Nexuiz, OpenArena, Sauerbraten, ET, and TCE would top over a gig in download size. Thats pretty big, so if a Dialup user decided to hit that (not that many dialup users would but im sure there would be at least one), theyd be at it a LONG time. 

Perhaps Metapackaging by game type, rather than just games as a whole would be more acceptable.

---

### Post by alt3rn1ty on 2008-07-31
Looks like a very attractive package for noobs such as I who are experiencing incompatible problems and would like an experienced pointer as to what and how to install on x64, trimming down afterwards should be easy?.
Also attractive for windows converts who previously thought linux would just have chess/pong and solitaire <uhm, yep that would be me too lol>

---

### Post by Oldsoldier2003 on 2008-07-31
> **compiledkernel said:**
> 2 cents here. 

Metapackaging a whole build for gaming purposes would create a massive large download schema. Nexuiz, OpenArena, Sauerbraten, ET, and TCE would top over a gig in download size. Thats pretty big, so if a Dialup user decided to hit that (not that many dialup users would but im sure there would be at least one), theyd be at it a LONG time. 

Perhaps Metapackaging by game type, rather than just games as a whole would be more acceptable.

Meta by type would be a good alternative. Regardless of how you select the games someone is bound to take issue with selection or size. 

I think the key criteria of the meta package contents will need to be troublefree installation and play on most systems. If this isn't a major consideration we're just shooting ourselves in the foot. The gnome games are cheesy, but they work...

---

### Post by Oponium on 2008-07-31
> **compiledkernel said:**
> 2 cents here. 

Metapackaging a whole build for gaming purposes would create a massive large download schema. Nexuiz, OpenArena, Sauerbraten, ET, and TCE would top over a gig in download size. Thats pretty big, so if a Dialup user decided to hit that (not that many dialup users would but im sure there would be at least one), theyd be at it a LONG time. 

Perhaps Metapackaging by game type, rather than just games as a whole would be more acceptable.
I think this is a good idea.

I'll include separate metapackages, here's what I was thinking:

ubuntu-games-desktop -- metapackage for desktop environment + games
ubuntu-games-base -- just the openbox desktop environment
ubuntu-games-rts -- obvious
ubuntu-games-fps -- obvious
ubuntu-games-rpg -- obvious
ubuntu-games-strategy -- obvious
ubuntu-games-misc -- obvious

i was also thinking of a very simple installable dvd that would include ubuntu-games-desktop. Thoughts?

I'll upload some test debs here soon (mainly the rts, fps, rpg, strategy, and misc).

My whole way of thinking here is a simple package to install for a side, lightweight desktop environment for games, virtualization, and other heavy tasks. that way, all you have to do is install this package, and whenever you want to do something heavy (mainly play games) all you have to do is select openbox as the session. obviously this wouldn't be AS effective on a regular ubuntu install (more effective on the dvd), but it's a start.

Thoughts? Suggestions?

---

### Post by Vadi on 2008-08-09
This is something similar: [http://ubuntuforums.org/showthread.php?t=884936](http://ubuntuforums.org/showthread.php?t=884936)

But as already said, the bandiwdth and size requirements are huge on this, so donate if you want to help it happen (and stay alive).

---


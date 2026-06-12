---
title: "A chess game should be included!"
date: 2006-10-01
forum: Gaming &amp; Leisure
---

### Post by trommas on 2006-10-01
Like OS X, Ubuntu should include a chessgame by default!

I love chess!

---

### Post by Josh1 on 2006-10-01
Something even better, a multiplayer chess that you can verse other people on the internet with (Like the XP version but with actual chat ;)).
How awesome would that be :D.
- Josh

---

### Post by jdunn on 2006-10-01
There are chess games in the repositories.  Most are made of two seperate components:  the UI and the chess engine.  Examples of UI are xboard, eboard and Knights.  Examples of chess engines are gnuchess, phalanx and sjeng.  Some of the UI components allow you to log into FICS (Free Internet Chess Servers) where you can play against other players and "chat".

---

### Post by billyfoxtrot on 2006-10-02
What I want to know is why the Crafty chess engine isn't included in any of the repositories (at least as far as I know), even though it's included in the Debian repositories.  It's probably the best free chess engine for GNU/Linux.

---

### Post by scourge on 2006-10-02
> **billyfoxtrot said:**
> What I want to know is why the Crafty chess engine isn't included in any of the repositories (at least as far as I know), even though it's included in the Debian repositories.  It's probably the best free chess engine for GNU/Linux.

Crafty may be the strongest Xboard engine, but it's not the strongest open source engine. Toga, Fruit and Glaurung for example are stronger, and even though they're UCI engines they work without problems in Xboard with Polyglot.

---

### Post by Fingolfin on 2006-10-07
> **scourge said:**
> Crafty may be the strongest Xboard engine, but it's not the strongest open source engine. Toga, Fruit and Glaurung for example are stronger, and even though they're UCI engines they work without problems in Xboard with Polyglot.

In the last year's World Computer Chess Championship held in Reykyavik 2005, Fruit has really won the game against Crafty, and given that Toga is Fruit's derivative, perhaps they are both stronger. 
However, the performance of the remaining chess engine Glaurung is a bit more difficult to track as it did not compete against other programs (Fruit did not compete in WCCC 2006), so how was it established that Glaurung is stronger than Crafty? (just curious)

---

### Post by jISh on 2006-10-07
Knights is my favourite chess GUI.

---

### Post by jdunn on 2006-10-07
> **jISh said:**
> Knights is my favourite chess GUI.

It is currently my favorite too.  One of my favorite chess games of all time was Battlechess for the old Apple ][e.  The closest thing to Battlechess that I've seen recently is [http://brutalchess.sourceforge.net]("http://brutalchess.sourceforge.net")

---

### Post by scourge on 2006-10-08
> **Fingolfin said:**
> In the last year's World Computer Chess Championship held in Reykyavik 2005, Fruit has really won the game against Crafty, and given that Toga is Fruit's derivative, perhaps they are both stronger. 
However, the performance of the remaining chess engine Glaurung is a bit more difficult to track as it did not compete against other programs (Fruit did not compete in WCCC 2006), so how was it established that Glaurung is stronger than Crafty? (just curious)

Isn't the WCCC for chess-playing systems (hardware + chess program + opening book + endgame tablebases) rather than just chess programs? And even if the engines all ran on the same hardware, each engine would have to play hundreds of games before we could say which one is the best. So I think the WCCC is not that relevant.

Here are some ratings based on a decent number of games: [http://wbec-ridderkerk.nl/html/BayesianElo_ed12.htm](http://wbec-ridderkerk.nl/html/BayesianElo_ed12.htm)
As you can see, Glaurung has a higher rating than Crafty. You can actually verify it by yourself: just get Glaurung to work with Polyglot, then run a 100-game match between the two engines in Xboard.

---

### Post by Josey on 2006-10-08
Ubuntu is great as is but yeah, for people new to ubuntu a multiplayer chess would be pretty impressive the first time they look under games.

They also have to consider the size of it too though as making ubuntu not fit on one cd would be a bad idea.

---

### Post by MrBlond83 on 2006-10-08
They should make a chess game that when the soldiers take each other there is cool fighting animation.

Long long time ago I had a game like that for DOS, I remember whenever you took the enemy's queen with your rook, the rook would crush the queen with hands made of stone and you could see her blood.

Man that game was awesome, going to try and find it on google now.

---

### Post by trommas on 2006-10-09
> **MrBlond83 said:**
> They should make a chess game that when the soldiers take each other there is cool fighting animation.

Long long time ago I had a game like that for DOS, I remember whenever you took the enemy's queen with your rook, the rook would crush the queen with hands made of stone and you could see her blood.

Man that game was awesome, going to try and find it on google now.

Battlechess :)

There is a similar game on sourceforge, think it's called "Brutal Chess"

The games that are included now are quite lame..

---

### Post by Fingolfin on 2006-10-11
> **scourge said:**
> Isn't the WCCC for chess-playing systems (hardware + chess program + opening book + endgame tablebases) rather than just chess programs? 
Here are some ratings based on a decent number of games: [http://wbec-ridderkerk.nl/html/BayesianElo_ed12.htm](http://wbec-ridderkerk.nl/html/BayesianElo_ed12.htm) 

Yes, I completely forgot about the hardware; engines competing in WCCC are running on different machines. I might as well put Glaurung, Fruit and recently compiled Crafty 20.14 against each other and check out the outcome.

But more to the topic, Crafty and these other top engines deserve to be in the Ubuntu repositories. If I am not mistaken, Novell Suse Linux comes with recent version of Crafty precompiled on installation DVD (and Red Hat Linux used to), so why not Ubuntu.

---

### Post by scourge on 2006-10-11
> **Fingolfin said:**
> But more to the topic, Crafty and these other top engines deserve to be in the Ubuntu repositories. If I am not mistaken, Novell Suse Linux comes with recent version of Crafty precompiled on installation DVD (and Red Hat Linux used to), so why not Ubuntu.

Fruit and Sjeng are already in universe. The reason we don't have more of the top engines in the repositories is probably because they don't use the Xboard protocol. As for Crafty, its license is a lot more restrictive than GPL, so it shouldn't be on the installation dvd. But maybe in universe.

---

### Post by fng on 2006-10-12
Is there some kind of chess teaching program? Like Chess Mentor Deluxe on windows.

---

### Post by Fingolfin on 2006-10-12
> **scourge said:**
> Fruit and Sjeng are already in universe. The reason we don't have more of the top engines in the repositories is probably because they don't use the Xboard protocol. As for Crafty, its license is a lot more restrictive than GPL, so it shouldn't be on the installation dvd. But maybe in universe.

Thank you for pointing this out, I was not very careful when combing the repositories for chess programs (I guess my attention drifted elsewhere after I couldn't find Crafty). But, just realised that chess database program SCID 3.6.1 [http://scid.sourceforge.net/](http://scid.sourceforge.net/) is already there :-)  How long is it since it has been made available from the Universe?

---

### Post by Fingolfin on 2006-10-12
> **fng said:**
> Is there some kind of chess teaching program? Like Chess Mentor Deluxe on windows.

BabyChess! 
Wonderfully composed application loaded with chess learning, studying and other helpful features.
[http://user.cs.tu-berlin.de/~kunegis/babychess/features/](http://user.cs.tu-berlin.de/~kunegis/babychess/features/)

(This one deserves to be in the Universe, too.)

---

### Post by Ziggurat on 2006-10-27
I agree, but ive think a problem in the games (engines) isee so far is that is too complicated to set the parametres of this great chess engines for the "normal" and above player.

Would be nice some app on top of one of this engines that lets you select difficult levels and handles the parametres.

---

### Post by maxdevis on 2006-10-31
where do i find themes for knights?

---

### Post by slimdog360 on 2006-10-31
agreed, get rid of that robots game and put in chess with some cool multiplayer thingy which lets the Ubuntu community play against one another easily.

---

### Post by jdunn on 2006-10-31
> **maxdevis said:**
> where do i find themes for knights?

I'm disappointed this game hasn't been updated in a while.  Nevertheless, I still prefer this chess game above all the others.  You can get the themes here: (Select 'Themepack' in Step 1) [http://knights.sourceforge.net/download.php](http://knights.sourceforge.net/download.php)

---

### Post by jdunn on 2006-10-31
> **trommas said:**
> Battlechess :)

There is a similar game on sourceforge, think it's called "Brutal Chess"


If you have Edgy, you'll find Brutal Chess in the repositories.  I haven't tried it so I can't comment.

---

### Post by Village on 2006-10-31
Are Battle Chess, how I fondly remember thee, 

Could never win though, I don't have the right sort of brain for chess. As a kid though I did like the animation.

Village

---

### Post by UbuWu on 2006-11-01
Gnome 2.18 will include [glChess]("http://glchess.sourceforge.net/"), so it will be in feisty too. [PyChess]("http://pychess.googlepages.com/") is very nice as well.

---

### Post by LateNighter on 2006-11-02
> **trommas said:**
> Like OS X, Ubuntu should include a chessgame by default!

I love chess!

This is TRUE but What about GOOD OLD Checkers as well????

I've never seen a Plain Old Checkers Game for any sort of Linux?

Either Online or Player vs Computer...:confused:

---

### Post by glotz on 2006-11-02
Yeah, if Ubuntu is to come with some games then it needs a decent chess game.

---

### Post by opticyclic on 2006-11-13
Vista comes with chess now. It is a nice 3D version.
pouetChess is a 3D chess in the repositories and it looks nice.
However, I can't get input to it via my mouse or keyboard :-k 

Brutal Chess only gives me about 1.3 FPS and doesn't seem to have any help files on how to play/interface :confused: 

I am most interested in a 3D chess program because it looks nice. :) 
I also want it to start at a low level AI with plenty of gradually increasing levels.

[glChess]("http://glchess.sourceforge.net/?q=node/11") certainly looks nice, but it isn't in the repositories.
[pyChess]("http://pychess.googlepages.com/screenshots") isn't 3D but it has extra features that make up for it, however, it isn't in the repositories either. ](*,)

Chess should definitely be a game installed by default.

---

### Post by ekravche on 2007-01-14
Yahoo has a great multiplayer online chess now. It's flash based and has a dedicated user base!
> **Josh1 said:**
> Something even better, a multiplayer chess that you can verse other people on the internet with (Like the XP version but with actual chat ;)).
How awesome would that be :D.
- Josh

---

